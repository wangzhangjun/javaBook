# java方法重写与重载

## 1.方法重写和重载

```text
/*
    方法重写：子类中出现了和父类中方法声明一模一样的方法。

    方法重载：
        本类中出现的方法名一样，参数列表不同的方法。与返回值无关。

    子类对象调用方法的时候：
        先找子类本身，再找父类。

    方法重写的应用：
        当子类需要父类的功能，而功能主体子类有自己特有内容时，可以重写父类中的方法。
        这样，即沿袭了父类的功能，又定义了子类特有的内容。

    案例：
        A:定义一个手机类。
        B:通过研究，我发明了一个新手机，这个手机的作用是在打完电话后，可以听天气预报。
        按照我们基本的设计，我们把代码给写出来了。
        但是呢?我们又发现新手机应该是手机，所以，它应该继承自手机。
        其实这个时候的设计，并不是最好的。
        因为手机打电话功能，是手机本身就具备的最基本的功能。
        所以，我的新手机是不用在提供这个功能的。
        但是，这个时候，打电话功能就没有了。这个不好。
        最终，还是加上这个功能。由于它继承了手机类，所以，我们就直接使用父类的功能即可。
        那么，如何使用父类的功能呢?通过super关键字调用
*/
class Phone {
    public void call(String name) {
        System.out.println("给"+name+"打电话");
    }
}

class NewPhone extends Phone {
    public void call(String name) {
        //System.out.println("给"+name+"打电话");
        super.call(name);
        System.out.println("可以听天气预报了");
    }
}

class ExtendsDemo9 {
    public static void main(String[] args) {
        NewPhone np = new NewPhone();
        np.call("林青霞");
    }
}
```

## 2.方法重写的注意事项

```text
/*
    方法重写的注意事项
        A:父类中私有方法不能被重写
            因为父类私有方法子类根本就无法继承
        B:子类重写父类方法时，访问权限不能更低
            最好就一致
        C:父类静态方法，子类也必须通过静态方法进行重写
            其实这个算不上方法重写，但是现象确实如此，至于为什么算不上方法重写，多态中我会讲解

        子类重写父类方法的时候，最好声明一模一样。
*/
class Father {
    //private void show() {}

    /*
    public void show() {
        System.out.println("show Father");
    }
    */

    void show() {
        System.out.println("show Father");
    }
    /*
    public static void method() {

    }
    */

    public void method() {

    }
}

class Son extends Father {
    //private void show() {}

    /*
    public void show() {
        System.out.println("show Son");
    }
    */

    public void show() {
        System.out.println("show Son");
    }


    public static void method() {

    }

    /*
    public void method() {

    }
    */
}

class ExtendsDemo10 {
    public static void main(String[] args) {
        Son s = new Son();
        s.show();
    }
}
```
