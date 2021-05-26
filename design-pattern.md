# Design Pattern

<!-- TABLE OF CONTENTS -->
<details open="open">
  <summary>Table of Contents</summary>    
  <ul>
    <li>
      Machine Learning Questions
      <ol type="1">
        <li><a href="#q1">Q1</a></li>
        <li><a href="#q2">Q2</a></li>
        <li><a href="#q3">Q3</a></li>
      </ol>
    </li>
    <li>
      Coding Questions
      <ol type="1">
        <li><a href="#coding-questions">Q1</a></li>
      </ol>
    </li>
  </ul>
</details>

---

## Creational Pattern

### 1. Abstract Factory Pattern

The intuition behind an abstract factory pattern is to encapsulate a group of factories that have a common behaviour with no need of specifying their classes. This pattern allows to exchange concrete implementations with no need of changing the code that uses those implementations. This is because the factory typically returns an abstract pointer and the client does not care about internal details. In this example the class Widget has a pure virtual method. The two classes derived by the Widget are implementing a specific `draw()` behaviour. In this illustrative situation we just print a different text.

```c++
namespace Abstract_Factory {
    
    // The Factory pattern suggests defining a
    // creation services interface in a Factory
    // base class, and implementing each "platform"
    // in a separate Factory derived class.
    
    class Widget {
        public:
            virtual void draw() = 0; // make it pure virtual
    };
  
    class OSX_Button : public Widget {
        public:
            void draw() {
                std::cout << "OSX button" << std::endl;
            }
    };
    
    class Windows_Button : public Widget {
        public:
            void draw() {
                std::cout << "Windows button" << std::endl;
            }
    };
}; 

void testAbstractFactory() {
    using namespace Creational_Patterns::Abstract_Factory;
    
    Widget* w = new OSX-Button();
    w->draw();
    delete w;
}
```









