# Lab-8_202001160


# **Software Engineering: IT 314**

# Raj Vegad
# 202001160


Date: April 20th  2023

Lab Assignment: **8**

*** 
*** 
 **Unit Testing JUnit**  
 
 ### 3. To test the Boa class:

#### Code:

~~~
import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {

    private Boa healthyBoa;
    private Boa unhealthyBoa;

    @Before
    public void setUp() throws Exception {
        healthyBoa = new Boa("Healthy Boa", 6, "granola bars");
        unhealthyBoa = new Boa("Unhealthy Boa", 8, "mice");
    }

    @Test
    public void testIsHealthy() {
        assertTrue(healthyBoa.isHealthy());
        assertFalse(unhealthyBoa.isHealthy());
    }

    @Test
    public void testFitsInCage() {
        assertTrue(healthyBoa.fitsInCage(7));
        assertFalse(unhealthyBoa.fitsInCage(6));
    }

}
~~~

 ![image](https://user-images.githubusercontent.com/84800957/233317126-07c0c12b-4d7a-4bb2-b1df-769e322fe3ab.png)
#### Explanation:

We first import the necessary JUnit classes and the Boa class we want to test.
We then create two Boa objects in the setUp() method. One is a healthy Boa and the other is an unhealthy one.
In the testIsHealthy() method, we test the isHealthy() method of both Boa objects. We expect the healthy Boa to be healthy and the unhealthy Boa to be unhealthy.
In the testFitsInCage() method, we test the fitsInCage() method of both Boa objects. We expect the healthy Boa to fit in a cage of length 7 and the unhealthy Boa not to fit in a cage of length 6.
We use the assertTrue() and assertFalse() methods to make assertions about the expected results of the methods being tested.

### 4. Modifying the set-up method

#### Code:

~~~
public class BoaTest {

    private Boa jen;
    private Boa ken;

    @Before
    public void setUp() throws Exception {
        jen = new Boa("Jennifer", 2, "grapes");
        ken = new Boa("Kenneth", 3, "granola bars");
    }

    // test methods go here
}
~~~

![image](https://user-images.githubusercontent.com/118908997/233040685-8d50be60-301d-4bd4-9d4b-0a3143bfba94.png)

#### Explanation
This creates two Boa objects named jen and ken with different values for their name, length, and favorite food properties. The jen object has a name of "Jennifer", a length of 2 feet, and a favorite food of "grapes". The ken object has a name of "Kenneth", a length of 3 feet, and a favorite food of "granola bars". The private fields jen and ken are added to the BoaTest class so that they can be accessed in the test methods.

### 5. @Test stubs

#### A.

##### Code:

~~~
@Test
    public void testIsHealthy() {
        assertTrue(healthyBoa.isHealthy());
        assertFalse(unhealthyBoa.isHealthy());
    }
~~~

##### Output

~~~
import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {

    private Boa healthyBoa;
    private Boa unhealthyBoa;

    @Before
    public void setUp() throws Exception {
        healthyBoa = new Boa("Healthy Boa", 6, "granola bars");
        unhealthyBoa = new Boa("Unhealthy Boa", 8, "mice");
    }

    @Test
    public void testIsHealthy() {
        assertTrue(healthyBoa.isHealthy());
        assertFalse(unhealthyBoa.isHealthy());
    }

    @Test
    public void testFitsInCage() {
        assertTrue(healthyBoa.fitsInCage(7));
        assertFalse(unhealthyBoa.fitsInCage(6));
    }

}
~~~

The first assertion in the testIsHealthy() method tests that the isHealthy() method returns true for the healthyBoa object, and the second assertion tests that it returns false for the unhealthyBoa object.

#### B.

##### Code:

~~~
@Test
    public void testFitsInCage() {
        assertTrue(healthyBoa.fitsInCage(7));
        assertFalse(unhealthyBoa.fitsInCage(6));
    }
~~~

##### Output

~~~
import static org.junit.Assert.*;

import org.junit.Before;
import org.junit.Test;

public class BoaTest {

    private Boa healthyBoa;
    private Boa unhealthyBoa;

    @Before
    public void setUp() throws Exception {
        healthyBoa = new Boa("Healthy Boa", 6, "granola bars");
        unhealthyBoa = new Boa("Unhealthy Boa", 8, "mice");
    }

    @Test
    public void testIsHealthy() {
        assertTrue(healthyBoa.isHealthy());
        assertFalse(unhealthyBoa.isHealthy());
    }

    @Test
    public void testFitsInCage() {
        // Test when cage length is less than length of the boa
        assertFalse(healthyBoa.fitsInCage(4));
        assertFalse(unhealthyBoa.fitsInCage(6));

        // Test when cage length is equal to length of the boa
        assertTrue(healthyBoa.fitsInCage(6));
        assertTrue(unhealthyBoa.fitsInCage(8));

        // Test when cage length is greater than length of the boa
        assertTrue(healthyBoa.fitsInCage(7));
        assertTrue(unhealthyBoa.fitsInCage(10));
    }

}
~~~
![image](https://user-images.githubusercontent.com/84800957/233317690-7e143453-b68a-431b-a0cb-3f03286368c4.png)


##### Explanation

The modified testFitsInCage() method tests the results of the fitsInCage() method when the cage length is less than, equal to, and greater than the length of the boa for both healthyBoa and unhealthyBoa objects.

Since the setUp() method initializes two different Boa objects, healthyBoa and unhealthyBoa, there is no need to write separate tests for "jen" and "ken". The tests should cover both objects as specified in the setUp() method.



### 7. Adding a new Method

~~~
private Boa healthyBoa;
private Boa unhealthyBoa;

@Before
public void setUp() throws Exception {
    healthyBoa = new Boa("Healthy Boa", 6, "granola bars");
    unhealthyBoa = new Boa("Unhealthy Boa", 8, "mice");
}

@Test
public void testIsHealthy() {
    assertTrue(healthyBoa.isHealthy());
    assertFalse(unhealthyBoa.isHealthy());
}

@Test
public void testFitsInCage() {
    assertTrue(healthyBoa.fitsInCage(7));
    assertFalse(unhealthyBoa.fitsInCage(6));
}

@Test
public void testLengthInInches() {
    assertEquals(healthyBoa.lengthInInches(), 72);
    assertEquals(unhealthyBoa.lengthInInches(), 96);
}
~~~
![image](https://user-images.githubusercontent.com/84800957/233317974-9cdc5053-f099-4f59-b30d-6796d9ed3673.png)

#### Explanation
After adding the lengthInInches() method to the Boa class, I can write a test case to verify its implementation in the BoaTest class. The test case should compare the expected result with the actual result from invoking the method on both the healthy and unhealthy Boa objects. The expected length in inches for a Boa with a length of n feet is n * 12 inches.

