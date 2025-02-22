.. qnum::
   :prefix: 5-5-
   :start: 1

.. |CodingEx| image:: ../../_static/codingExercise.png
    :width: 30px
    :align: middle
    :alt: coding exercise
    
    
.. |Exercise| image:: ../../_static/exercise.png
    :width: 35
    :align: middle
    :alt: exercise
    
    
.. |Groupwork| image:: ../../_static/groupwork.png
    :width: 35
    :align: middle
    :alt: groupwork
    
.. image:: ../../_static/time45.png
    :width: 250
    :align: right
    
Mutator Methods
=================

Corresponding to each get method, programmers also provide a public **set method** to change the value of a private instance variable in a class. These are called **mutator methods** (or settters or set or modifier methods). They are **void methods** meaning that they do not return a value, but they do take a **parameter**, the new value for the instance variable. Here are some examples of how to write a set method for an instance variable:

.. code-block:: java
     
     class ExampleTemplate {
 
         //Instance variable declaration
         private typeOfVar varName;

         // Mutator (setter) method template
         public void setVarName(typeOfVar newValue)
         {
            varName = newValue;
         }
     }
     
Here's an example of the Student class with a mutator method called setName():

.. code-block:: java

  class Student {
 
     //Instance variable name
     private String name;
     
     /** setName sets name to newName
      *  @param newName                */
     public void setName(String newName)
     {
        name = newName;
     }
     
     public static void main(String[] args)
     { 
        // To call a set method, use objectName.setVar(newValue)
        Student s = new Student();
        s.setName("Ayanna");  
     }
    }
     
Notice the difference between set (mutator) and get (accessor) methods in the following figure. Getters return an instance variable's value and have the same return type as this variable and no parameters. Setters have a void return type and take a new value as a parameter to change the value of the instance variable.

.. figure:: Figures/get-set-comparison.png
    :width: 600px
    :align: center
    :figclass: align-center

    Figure 1: Comparison of set and get methods
    
    
|CodingEx| **Coding Exercise**

Try the Student class below which this time has set methods added. You will need to fix one error. The main method is in a separate Tester class and does not have access to the private instance variables in the other Student class. Change the main method so that it uses a public mutator method (set method) to access the value instead.

.. activecode:: StudentObjExample2
  :language: java
  :autograde: unittest

  Fix the main method to include a call to the appropriate set method.
  ~~~~
  public class TesterClass 
  {
     // main method for testing
     public static void main(String[] args)
     {
        Student s1 = new Student("Skyler", "skyler@sky.com", 123456);
        System.out.println(s1);
        s1.setName("Skyler 2");
        // Main doesn't have access to email, use set method!
        s1.email = "skyler2@gmail.com";
        System.out.println(s1);
     }   
   }
  
  class Student 
  {
     private String name;
     private String email;
     private int id;
     
     public Student(String initName, String initEmail, int initId)
     {
        name = initName;
        email = initEmail;
        id = initId;
     }
     // mutator methods - setters
     public void setName(String newName)
     { 
       name = newName; 
     }
     public void setEmail(String newEmail)
     { 
       email = newEmail; 
     }
     public void setId(int newId)
     { 
       id = newId; 
     }
     // accessor methods - getters 
     public String getName() 
     { 
        return name;
     }
     public String getEmail() 
     { 
        return email;
     }
     public int getId() 
     { 
        return id;
     }
     public String toString() {
        return id + ": " + name + ", " + email;
     }
  }
  ====
  import static org.junit.Assert.*;
    import org.junit.*;

    import java.io.*;

    public class RunestoneTests extends CodeTestHelper
    {
        public RunestoneTests()
        {
            super("TesterClass");
        }

        @Test
        public void test1()
        {
            String target = "s1.setEmail(\"skyler2@gmail.com\");";
            boolean passed = checkCodeContains("call to setEmail()", target);
            assertTrue(passed);
        }

        @Test
        public void testMain()
        {
            String output = getMethodOutput("main");
            String expect = "123456: Skyler, skyler@sky.com\n123456: Skyler 2, skyler2@gmail.com";

            boolean passed = getResults(expect, output, "Checking main()", true);
            assertTrue(passed);
        }
    }
  
|Exercise| **Check your understanding**




.. mchoice:: setSignature
    :practice: T

    Consider the class Party which keeps track of the number of people at the party.
    
    .. code-block:: java

        public class Party
        {
            //number of people at the party
            private int numOfPeople; 

            /* Missing header of set method */
            {
                numOfPeople = people;
            }
        }
    
    Which of the following method signatures could replace the missing header for the set method in the code above so that the method will work as intended?

    - public int getNum(int people)
   
      - The set method should not have a return value and is usually named set, not get.
     
    - public int setNum()
   
      - The set method should not have a return value and needs a parameter.
     
    - public int setNum(int people)
   
      - The set method should not have a return value.
     
    - public void setNum(int people)
   
      + Yes, the set method should take a parameter called people and have a void return value. The name of the set method is usually set followed by the full instance variable name, but it does not have to be an exact match.
     
    - public int setNumOfPeople(int p)
   
      - The parameter of this set method should be called people in order to match the code in the method body.
   
.. dragndrop:: AccessorMutator
    :feedback: Review the vocabulary.
    :match_1: gets and returns the value of an instance variable|||accessor method
    :match_2: sets the instance variable to a value in its parameter|||mutator method
    :match_3: initializes the instance variables to values|||constructor 
    :match_4: accessible from outside the class|||public
    :match_5: accessible only inside the class|||private

    
    Drag the definition from the left and drop it on the correct word on the right.  Click the "Check Me" button to see if you are correct.

Mutator methods do not have to have a name with "set" in it, although most do. They can be any methods that change the value of an instance variable or a static variable in the class, as can be seen in the AP Practice questions below.     
    

|Groupwork| Programming Challenge : Class Pet Setters
-----------------------------------------------------

.. image:: Figures/animalclinic.png
    :width: 150
    :align: left
    :alt: Animal Clinic
    
1. Copy your Awesome Animal Clinic Pet class from the last lesson into this Active Code window. 
2. Add set methods for each of the 5 instance variables. Make sure you use good commenting!
3. Test each of the set methods in the main method.


.. activecode:: challenge-5-5-Pet-Class
  :language: java
  :autograde: unittest
  
  Create a Pet class that keeps track of the name, age, weight, type of animal, and breed for records at an animal clinic with 2 constructors, accessor (get) methods, a toString method, and mutator (set) methods for each instance variable.
  ~~~~
  /**
      Pet class (complete comments)
      @author
      @since 
      
  */
  class Pet 
  {
     // complete class definition with set methods
     
  }
  
  public class TesterClass 
  {
     // main method for testing
     public static void main(String[] args)
     {
        // Create Pet objects and test all your set methods
        
     }   
   }  
   ====
   import static org.junit.Assert.*;
    import org.junit.*;

    import java.io.*;

    public class RunestoneTests extends CodeTestHelper
    {
        public RunestoneTests()
        {
            super("TesterClass");
        }

        @Test
        public void testConstructors()
        {
           changeClass("Pet");
            int count = 0;

            for (int i = 0; i < 6; i++) {
                if (checkConstructor(i).equals("pass"))
                    count++;
            }

            boolean passed = count >= 2;

            getResults("2+", ""+count, "Checking for 2 constructors", passed);
            assertTrue(passed);
        }

        @Test
        public void testPrivateVariables()
        {
            changeClass("Pet");
            String expect = "5 Private";
            String output = testPrivateInstanceVariables();

            boolean passed = getResults(expect, output, "Checking Private Instance Variables");
            assertTrue(passed);
        }

        @Test
        public void test1()
        {
            String code = getCode();
            String target = "public * get*()";

            int num = countOccurencesRegex(code, target);

            boolean passed = num >= 5;

            getResults("5", ""+num, "Checking accessor (get) methods for each variable", passed);
            assertTrue(passed);
        }

        @Test
        public void test2()
        {
            String code = getCode();
            String target = "public void set*(*)";

            int num = countOccurencesRegex(code, target);

            boolean passed = num >= 5;

            getResults("5", ""+num, "Checking mutator (set) methods for each variable", passed);
            assertTrue(passed);
        }

        @Test
        public void test3()
        {
            String target = "public String toString()";
            boolean passed = checkCodeContains("toString() method", target);
            assertTrue(passed);
        }

        @Test
        public void test4()
        {
            String code = getCode();
            String target = "Pet * = new Pet(";

            int num = countOccurencesRegex(code, target);

            boolean passed = num >= 3;

            getResults("3", ""+num, "Checking main method creates three Pet objects", passed);
            assertTrue(passed);
        }


        @Test
        public void testMain()
        {
            String output = getMethodOutput("main");

            String expect = "3+ line(s) of text";
            String actual = " line(s) of text";

            int len = output.split("\n").length;

            if (output.length() > 0) {
                actual = len + actual;
            } else {
                actual = output.length() + actual;
            }
            boolean passed = len >= 3;

            getResults(expect, actual, "Checking main method prints info for 3 Pet objects", passed);
            assertTrue(passed);
        }
    }

|Groupwork| Design a Class for your Community 
----------------------------------------------------------

In the previous lessons, you came up with a class of your own choice relevant to your community. 

1. Copy your class with its instance variables, constructors, and accessors from the last lesson. 

2. Add mutator set methods for each of the instance variables. 

3. Test each of the set methods in the main method.



.. activecode:: community-challenge-5-5
  :language: java
  :autograde: unittest

  Copy your class with its instance variables, constructors, and accessors from the last lesson. Add mutator set methods for each of the instance variables. Test each of the set methods in the main method. 
  ~~~~
  public class          // Add your class name here!
  {
      // 1. Copy your class with its instance variables, constructors, and accessors from the last lesson. 

      // 2. Add mutator set methods for each of the instance variables. 

      /// 3. Test each of the set methods in the main method. 

      public static void main(String[] args)
      {  
         // Construct an object of your class  
         
         
         // call the objects' mutator methods and toString methods and print them out. 
      
      }
  }
  ====
  import static org.junit.Assert.*;
  import org.junit.*;
  import java.io.*;

  public class RunestoneTests extends CodeTestHelper
  {
         @Test
        public void test1()
        {
            String code = getCode();
            String target = "public * get*()";

            int num = countOccurencesRegex(code, target);

            boolean passed = num >= 3;

            getResults("3", ""+num, "Checking accessor (get) methods for each variable", passed);
            assertTrue(passed);
        }

        @Test
        public void test2()
        {
            String code = getCode();
            String target = "public void set*(*)";

            int num = countOccurencesRegex(code, target);

            boolean passed = num >= 3;

            getResults("3", ""+num, "Checking mutator (set) methods for each variable", passed);
            assertTrue(passed);
        }
        @Test
        public void test3()
        {
            String target = "public String toString()";
            boolean passed = checkCodeContains("toString() method", target);
            assertTrue(passed);
        }
        @Test
        public void testMain() throws IOException
        {
            String output = getMethodOutput("main");//.split("\n");
            String expect = "3+ line(s) of text";
            String actual = " line(s) of text";
            int len = output.split("\n").length;

            if (output.length() > 0) {
                actual = len + actual;
            } else {
                actual = output.length() + actual;
            }
            boolean passed = len >= 3;

            getResults(expect, actual, "Checking output", passed);
            assertTrue(passed);
        }
    }
    
Summary
--------

- A void method does not return a value. Its header contains the keyword void before the method name.

- A **mutator method** is often a void method that changes the values of instance variables or static variables.

AP Practice
------------

.. mchoice:: AP5-5-1
    :practice: T

    Consider the following class definition.
    
    .. code-block:: java
    
        public class Liquid
        {
            private int currentTemp;

            public Liquid(int temp)
            {
                currentTemp = temp;
            }

            public void resetTemp()
            {
                currentTemp = newTemp;
            }
        }

    Which of the following best identifies the reason the class does not compile?
    
    - The constructor header does not have a return type.
        
      - The constructor should not have a return type.
      
    - The resetTemp method is missing a return type.
    
      - Mutator methods usually have a void return type.
      
    - The constructor should not have a parameter.
    
      - Constructors can have parameters.
      
    - The resetTemp method should have a parameter.
    
      + Correct! The resetTemp method should have a parameter for the newTemp value to set the currentTemp.
      
    - The instance variable currentTemp should be public instead of private.
    
      - Instance variables should be private variables.


.. mchoice:: AP5-5-2
    :practice: T
    :answer_a: Replace line 12 with numOfPeople = additionalPeople;
    :answer_b: Replace line 12 with return additionalPeople;
    :answer_c: Replace line 12 with additionalPeople += 3;
    :answer_d: Replace line 10 with public addPeople (int additionalPeople)
    :answer_e: Replace line 10 with public void addPeople(int additionalPeople)
    :correct: e
    :feedback_a: This method should add additionalPeople to numOfPeople.
    :feedback_b: This method should add additionalPeople to numOfPeople.
    :feedback_c: This method should add additionalPeople to numOfPeople.
    :feedback_d: Mutator methods should have a void return type.
    :feedback_e: Mutator methods should have a void return type.

    In the Party class below, the addPeople method is intended to increase the value of the instance variable numOfPeople by the value of the parameter additionalPeople. The method does not work as intended.
    
    .. code-block:: java

        public class Party
        {
            private int numOfPeople;

            public Party(int n)
            {
                numOfPeople = n;
            }

            public int addPeople(int additionalPeople) // Line 10
            {
                numOfPeople += additionalPeople; // Line 12
            }
        }

    Which of the following changes should be made so that the class definition compiles without error and the method addPeople works as intended?