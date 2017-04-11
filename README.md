# RXJava

```
       RXJava简单使用，项目集成lambda和ButterKnife
       /**
         * 完整引用
         */
        //        //被观察着
        //        Observable<String> myObservable = Observable.create(
        //                new Observable.OnSubscribe<String>() {
        //                    @Override
        //                    public void call(Subscriber<? super String> sub) {
        //                        sub.onNext("RXJavaTest");
        //                        sub.onCompleted();
        //                    }
        //                }
        //        );
        //        //观察者
        //        Subscriber<String> mySubscriber = new Subscriber<String>() {
        //            @Override
        //            public void onNext(String s) {
        //                text.setText(s);
        //            }
        //
        //            @Override
        //            public void onCompleted() {
        //            }
        //
        //            @Override
        //            public void onError(Throwable e) {
        //            }
        //        };
        //        //将观察者跟被观察者关联
        //        myObservable.subscribe(mySubscriber);

        /**
         * 简化代码使用Action1只关心onNext的回调忽略onError和onComplete
         */
        //        Observable<String> myObservable = Observable.just("RXJavaTest");
        //        //我们并不关心onError和onComplete
        //        Action1<String> onNextAction = new Action1<String>() {
        //            @Override
        //            public void call(String s) {
        //                text.setText(s);
        //            }
        //        };
        //        //myObservable.subscribe(onNextAction, onErrorAction, onCompleteAction);
        //        myObservable.subscribe(onNextAction);
        /**
         * 继续简化
         */
        //        Observable.just("RXJavaTest").subscribe(new Action1<String>() {
        //            @Override
        //            public void call(String s) {
        //                text.setText(s);
        //                SDToast.showToast(s);
        //            }
        //        });
        /**
         * 使用lambda深度简化（需要装retrolambda插件需要JDK8环境）
         */
        //        Observable.just("RXJavaTest")
        //                .subscribe(s -> SDToast.showToast(s));
        /**
         * 操作符就是为了解决对Observable对象的变换的问题，操作符用于在Observable和最终的Subscriber之间修改Observable发出的事件。
         * RxJava提供了很多很有用的操作符。
         * 比如map操作符，就是用来把把一个事件转换为另一个事件的。
         */
        //        Observable.just("RXJavaTest")
        //                .map(new Func1<String, String>() {
        //                    @Override
        //                    public String call(String s) {
        //                        return s + " -Jack";
        //                    }
        //                }).subscribe(s -> SDToast.showToast(s));
        /**
         * 使用lambda简化
         */
        //        Observable.just("RXJavaTest")
        //                .map(s -> s+"-Jack")
        //                .subscribe(s->text.setText(s));
        /**
         * map进阶返回Integer类型的值
         */
        //        Observable.just("RXJavaTest")
        //                .map(new Func1<String, Integer>() {
        //                    @Override
        //                    public Integer call(String s) {
        //                        return s.length();
        //                    }
        //                })
        //                .subscribe(i->text.setText(Integer.toString(i)));
        /**
         * 使用lambda简化
         */
        //        Observable.just("RXJavaTest")
        //                .map(s -> s.length())
        //                .subscribe(i -> text.setText(Integer.toString(i)));
        /**
         *使用两个map操作符
         */
        Observable.just("RXJavaTest")
                .map(s -> s.length())
                .map(i -> Integer.toString(i))
                .subscribe(s -> text.setText(s));
```
