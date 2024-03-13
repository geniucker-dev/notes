```cpp
class Base {
  public:
    void f1() {
        cout << "Base::f1() is called" << endl;
    }
    virtual void f2() {
        f1();
    }
};

class Derived : public Base {
  public:
    void f1() {
        cout << "Derived::f1() is called" << endl;
    }
    virtual void f2() {
        f1();
    }
};


int main() {
    Derived obj;
    Base& ref = obj;
    ref.f2();
}
```
