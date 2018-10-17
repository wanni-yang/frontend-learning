<code>
class Promise {

    //由于new Promise((resolve, reject)=>{})，所以传入一个参数函数executor传入就执行。
    //executor里面有两个参数，一个叫resolve决议，一个叫reject拒绝。
    constructor(executor) {
        // Promise存在三个状态（state）pending、fulfilled、rejected
        // pending等待态为初始态，并可以转化为fulfilled成功态和rejected失败态
        this.state = 'pending';
        //完成时，不可转为其他状态，且必须有一个不可改变的值value
        this.value = undefined;
        //拒绝时，不可转为其他状态，且必须有一个不可改变的原因reason
        this.reason = undefined;
        //存放then完成的回调
        this.onResolvedCallbacks = [];
        //存放then拒绝的回调
        this.onRejectedCallbacks = [];

        //决议函数
        let resolve = value => {
            if (this.state === 'pending') {
                //改变promise状态为完成
                this.state = 'fulfilled';
                //保存完成值
                this.value = value;
                //一旦resolve执行，调用完成数组的函数
                this.onResolvedCallbacks.forEach(fn => fn());
            }
        };

        //拒绝函数
        let reject = reason => {
            if (this.state === 'pending') {
                //改变promise状态为拒绝
                this.state = 'rejected';
                //保存拒绝原因
                this.reason = reason;
                //一旦reject执行，调用拒绝数组的函数
                this.onRejectedCallbacks.forEach(fn => fn());
            }
        };
        try {
            //立即执行
            executor(resolve, reject);
        } catch (err) {
            reject(err);
        }
    }
    then(onFulfilled, onRejected) {
    
        // onFulfilled如果不是函数，就忽略onFulfilled，直接返回value
        onFulfilled = typeof onFulfilled === 'function' ? onFulfilled : value => value;
        // onRejected如果不是函数，就忽略onRejected，直接扔出错误
        onRejected = typeof onRejected === 'function' ? onRejected : err => { throw err };
        //为了达成promise链式在第一个then里面返回一个promise,将这个promise返回的值传到下一个then
        let promise2 = new Promise((resolve, reject) => {
            if (this.state === 'fulfilled') {
                //onFulfilled异步调用
                setTimeout(() => {
                    try {
                        //x是第一个then的返回值
                        let x = onFulfilled(this.value);
                        //判断第一个then的返回值和默认返回的promise的关系
                        resolvePromise(promise2, x, resolve, reject);
                    } catch (e) {
                        reject(e);
                    }
                }, 0);
            };
            if (this.state === 'rejected') {
                //onRejected异步调用
                setTimeout(() => {
                    try {
                        let x = onRejected(this.reason);
                        resolvePromise(promise2, x, resolve, reject);
                    } catch (e) {
                        reject(e);
                    }
                }, 0);
            };
            //当promise状态为等待时，promise还有决议好
            if (this.state === 'pending') {
                //完成回调函数onFulfilled传入完成数组
                this.onResolvedCallbacks.push(() => {
                    setTimeout(() => {
                        try {
                            let x = onFulfilled(this.value);
                            resolvePromise(promise2, x, resolve, reject);
                        } catch (e) {
                            reject(e);
                        }
                    }, 0);
                });
                //拒绝回调函数onRejected传入拒绝数组
                this.onRejectedCallbacks.push(() => {
                    setTimeout(() => {
                        try {
                            let x = onRejected(this.reason);
                            resolvePromise(promise2, x, resolve, reject);
                        } catch (e) {
                            reject(e);
                        }
                    }, 0)
                });
            };
        });
        // 返回promise，完成链式
        return promise2;
    }
    catch (fn) {
        return this.then(null, fn);
    }
}

//规定onFulfilled()或onRejected()的值，即第一个then返回的值，叫做x，判断x的函数叫做resolvePromise

function resolvePromise(promise2, x, resolve, reject) {

    //若第一个then返回值和then默认返回的promise2一样会引起循环引用报错
    if (x === promise2) {
        return reject(new TypeError('Chaining cycle detected for promise'));
    }
    //防止多次调用
    let called;
    //x不是null且x是对象或者函数
    if (x != null && (typeof x === 'object' || typeof x === 'function')) {
        try {
            //A+规定，声明then = x的then方法
            let then = x.then;
            // 如果then是函数，就默认x是promise了
            if (typeof then === 'function') {
                then.call(x, y => {
                    // 完成和拒绝只能调用一个
                    if (called) return;
                    called = true;
                    // y可能还是个promise，所以递归继续解析直到返回一个普通值
                    resolvePromise(promise2, y, resolve, reject);
                }, err => {
                    // 完成和拒绝只能调用一个
                    if (called) return;
                    called = true;
                    reject(err);
                })
            } else {
              // x.then不是promise直接完成即可
                resolve(x);
            }
        } catch (e) {
            if (called) return;
            called = true;
            //then出错了那就不要再继续执行了
            reject(e);
        }
    } else {
        resolve(x);
    }
};
Promise.resolve = function(val) {
    return new Promise((resolve, reject) => {
        resolve(val);
    });
};
Promise.reject = function(val) {
    return new Promise((resolve, reject) => {
        reject(val);
    });
};
Promise.race = function(promises) {
    return new Promise((resolve, reject) => {
        for (let i = 0; i < promises.length; i++) {
            promises[i].then(resolve, reject);
        }
    });
};
Promise.all = function(promises) {
    let arr = [];
    let i = 0;
    function processData(index, data) {
        arr[index] = data;
        i++;
        if (i == promises.length) {
            resolve(arr);
        }
    }
    return new Promise((resolve, reject) => {
        for (let i = 0; i < promises.length; i++) {
            promises[i].then(data => {
                processData(i, data);
            }, reject);
        }
    });
}
</code>
