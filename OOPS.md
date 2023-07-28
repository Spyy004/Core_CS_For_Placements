# OOPS

- Access Modifiers
    - There are 3 types of access modifiers. 1) Private, 2) Protected, and 3) Public
    - Private variables/functions can only be accessed from inside the class.
    - Public ones can be accessed from anywhere
- Constructors
    - Constructors are methods that gets initialized whenever an object is created.
    - Constructors do not have any return type
    - Name of the constructor is same as the name of the class
    - There are 3 types of constructors. Default, parametrized, and copy.
    - Copy Constructors accepts an object of the same class and copies all its members to the object on the left part of the assignment
- Encapsulation
    - Encapsulation is bundling of data that work together.
    - Encapsulation means setting the variables which we don't want other classes to use as private.
    - We create methods which are public and via those methods we will be able to access our private data members.
    - A real life example would be that suppose you are going to dominos to order a pizza. Suppose the guy at counter is a member function of the class Dominos. You are from some other class. Let's say the pizza is a private variable/data member. Once the pizza is ready, you cannot go and bring the pizza because private data members can only be accessed by the member functions of the class. Hence the counter guy will get the pizza for you.
- Abstraction
    - Abstraction is basically abstracting all the complex part of the code so that some other developer doesn't have to deal with it and only deal with things necessary to him/her.
    - A real life example would be ordering food from Dominos. When you go to dominos, the person on the counter only shows you the food menu. He never shows you the kitchen and how your pizza is being made.
    - Here the counter guy acts as an abstract class.
- Virtual Functions and Abstract Classes
    - Virtual Functions are the functions whose latest implementation will be used whenever it is called. If there is no implementation of a virtual function in the derived classes, then the default implementation in the base class will be used.
    - Pure Virtual Functions do not have a default implementation. It forces the derived classes to implement the function on their own.
    - Abstract Classes are the classes who have atleast one Pure Virtual Function.
    - An example of virtual function and pure virtual function
    
    ```cpp
    // CPP program to illustrate
    // concept of Virtual Functions
    
    #include <iostream>
    using namespace std;
    
    class base {
    public:
    	virtual void print()
    	{
    		cout << "print base class" << endl;
    	}
     // pure virtual void doSomethin()=0; // this is how pure virtual functions are declared
    };
    
    class derived : public base {
    public:
    	void print()
    	{
    		cout << "print derived class" << endl;
    	}
      doSomethin(){
    	cout<<"Example of pure virtual function"<<endl;
    }
    };
    
    int main()
    {
    	base* bptr = new d();
    	// virtual function, binded at runtime
    	bptr->print();
      bptr->doSomethin();
    }
    ```
    
- Diamond Problem Multiple Inheritance
    - Diamond Problem is a famous problem in multiple inheritance.
    - Suppose a Class C is derived from Class A and Class B. Now suppose both the base classes have a function with the same name.
    - Now suppose you create an object of class C and call C.function(). Now since C has inherited from both A and B, the compiler is confused. It doesn't know which function should it call. So it throws an ambiguity error.
    - So to resolve this, we use a scope resolution. We do something like this.
    
    ```cpp
    #include<bits/stdc++.h>
    using namespace std;
    class A{
        public:
        void print()
        {
            cout<<"I am A"<<endl;
        }
    };
    class B{
        public:
        void print()
        {
            cout<<"I am B"<<endl;
        }
    };
    class C: public A,public B{
        public:
        void print()  
        {
            A::print(); // using scope resolution to resolve ambiguity.
            B::print();
        }
    };
    int main()
    {
        C obj;
        obj.print();
    }
    ```
    
- Polymorphism
    - Polymorphism means many forms.
    - Polymorphism are of two types. 1) Compile time and Run time.
    - Compile Time Polymorphism is also known as early binding.
    - There are three ways to achieve compile time polymorphism. 1) Function Overloading, 2) Operator Overloading, 3) Templates
    - Runtime Polymorphism is also called as late binding.
    - Runtime Polymorphism is achieved by using function overriding.
- Templates
    - We use templates in order to reduce extra code. Templates are useful to make things more generic.
    - If there are many functions with the same name but different parameters, it is better to use templates rather than Function overloading.
    - Here is an example of a template.
    
    ```cpp
    #include<bits/stdc++.h>
    using namespace std;
    template<typename T> // typename and template are keywords. We can use multiple data types
    T solve(T x, T y)  // T is our datatype
    {
        return x+y;
    }
    int main()
    {
        int t;
        cin>>t;
        while(t--)
        {
            long long int n;
            int a,b;
            cin>>n>>a>>b;
    // we can even pass an int and a double.
            cout<<solve<int>(a,b)<<endl;
            cout<<solve<double>(3.5,2.1)<<endl; 
            cout<<solve<float>(6.8f,9.2f)<<endl;
        }
    }
    ```
    
- Friend Function
    - A function that doesn't belong to a class but can access all the private and protected data members of that class is called as friend function. Here is an example of it
    
    ```cpp
    #include<bits/stdc++.h>
    using namespace std;
    class Data
    {
        private:
        int marks;
        public:
        void showMarks()
        {
            cout<<marks<<endl;
        }
        friend void addMarks(Data &d);
    };
    void addMarks(Data &d)
    {
        d.marks+=10;
    }
    int main()
    {
            Data d1;
            d1.showMarks();
            addMarks(d1);
            d1.showMarks();
    }
    ```
- Static KeyWord
    - No matter how many instances of class are created only one copy of static member, function is available for all objects of that class.
        - When the static keyword is used with a data member inside a class, it declares a static data member.
A static data member is shared among all instances (objects) of the class. It means that all objects of the class have access to the same static data member, and modifying it in one object will affect its value in all other objects.
Static data members are declared inside the class definition but need to be defined outside the class using the class name and scope resolution operator ::.
They are often used to store class-level information or shared data that needs to be accessed by all objects of the class.
Static Member Functions:

       - When the static keyword is used with a member function inside a class, it declares a static member function.
Static member functions are not associated with any particular object of the class. They can be called using the class name and the scope resolution operator ::, without needing to create an instance of the class.
Static member functions can only access static data members and call other static member functions of the class. They cannot access non-static data members or call non-static member functions directly.
They are often used for utility functions or operations that are not specific to any particular object but are related to the class as a whole.
Static Local Variables:

       - When the static keyword is used with a local variable inside a function, it declares a static local variable.
Static local variables are initialized only once when the function is first called, and their values are preserved across multiple function calls.
They have a "static" lifetime, meaning they exist throughout the entire program execution.
Static local variables are useful when you want to retain the value of a variable between function calls, while ensuring it is not accessible outside the function.
    
    ```cpp
    // CPP program to illustrate
    #include <iostream>
 
    using namespace std;

    class Box {
       public:
          static int objectCount;
      
          // Constructor definition
          Box(double l = 2.0, double b = 2.0, double h = 2.0) {
             cout <<"Constructor called." << endl;
             length = l;
             breadth = b;
             height = h;

             // Increase every time object is created
             objectCount++;
          }
          double Volume() {
             return length * breadth * height;
          }
          static int getCount() {
             return objectCount;
          }
      
           private:
              double length;     // Length of a box
              double breadth;    // Breadth of a box
              double height;     // Height of a box
    };

    // Initialize static member of class Box
    int Box::objectCount = 0;

    int main(void) {
       // Print total number of objects before creating object.
       cout << "Inital Stage Count: " << Box::getCount() << endl;

       Box Box1(3.3, 1.2, 1.5);    // Declare box1
       Box Box2(8.5, 6.0, 2.0);    // Declare box2

       // Print total number of objects after creating object.
       cout << "Final Stage Count: " << Box::getCount() << endl;

       return 0;
    }
    ```
- Are C++, Java, and Python purely OOP Languages?
    - No, they are not, Python doesn't support encapsulation, Java has some primitive data types and C++'s main function is defined outside the class.
    - Smalltalk is the first pure OOP language.
- Limitation of OOPS
    - Learning Curve is steep
    - Length of Program is huge
    - Execution time is slow compared to procedural program
- Difference between C and C++
    - C does not support OOP whereas C++ supports OOP
    - C Contains 32 keywords, C++ contains 63 keywords
    - Data and functions are seperated in C because it is procedural whereas Data and Functions are encapsulated in C++ in form of an object
    - Functions in C are not defined inside the structures whereas in C++ it can be defined in it.
    - Namespace is not available in C but available in C++
    - C uses malloc and calloc whereas C++ uses new operator.
- Difference between new and malloc?
    - New initializes the allocated memory by calling the constructor whereas malloc allocates to unitialized memory.
    - In new, delete  keyword is use to free memory, in malloc, free keyword is used to free memory.
- Difference between Structure and Class?
    - Structures does not provide data hiding, classes do.
    - Structures contain only data whereas classes contain both data and member functions.
    - Data members of structure is public by default but private by default in classes
