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


### 2. Builder Pattern

The builder aims at separating the construction of complex objects from their representation. Instead of using different constructors, the pattern defines a single object: the builder. This object builds the desired object step-by-step according to the configuration parameters defined by the user. The Builder is different from the Abstract factory because the former delegates the construction of the actual object to a specific auxiliary class/object, while the latter uses inheritance for exchanging concrete implementations.

In this example the class Builder is implemented according to a pure virtual method configure which is defined in each subclass for setting up the parameters used to drive each subclass building process. A set of specific tests based on different conditions can be added to the skeleton code for driving the specific action items taken by the ‘Simple Builder’ and by the ‘Advanced Builder’ respectively.

```c++
namespace Builder {
    
    // Separate the construction of a complex object from its
    // representation so that the same construction process
    // can create different representations.
    
    class Build { // base class
        public:
            virtual void configure() = 0;
            
            // here can add methods to see the internal state
        
        protected:
            int configuration_1_;
            int configuration_2_;
            // ...
            int configuration_n_;
    };
    
    class SimpleBuilder : public Build { // a derived class
        public:
            SimpleBuilder() {
                // here you can add explicit tests on configuration
                // parameters for driving the 'simple builder' creation steps
            };
            
            void configure() {
                // here you can add additional configuration steps
            };
    };
    
    class AdvancedBuilder : public Build { // a derived class
        public:
            AdvancedBuilder() {
                // here you can add explicit tests on configuration
                // parameters for driving the 'advaned builder' creation steps
            }
            
            void configure() {
                // here you can add additional configuration steps
            };
    };
    
    class ClientClass {
        public:
            ClientClass (Build* builder) : builder_(builder) {};
        private:
            Builder* builder_;
    };
};

void testBuilder() {

    using namespace Creational_Patterns::Builder;
    Build* builder = new AdvancedBuilder();
    Client c(builder);
    delete builder;
}
```




