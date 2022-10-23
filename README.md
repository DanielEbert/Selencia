# Selencia

Unit Test Framework aimed to run on an embedded device.


### TODO

- SEL_UnitTests
    - Singleton
    - Stores Vector of Tests (TODO: how? Unit Tests must register)
    - method to run all tests, returns test result

- SEL_TestParent
    - virtual void testbody = 0

- SEL_TEST(testname)
    - https://github.com/google/googletest/blob/7735334a46da480a749945c0f645155d90d73855/googletest/include/gtest/internal/gtest-internal.h#L1531
    - macro
    - inherits from abstract class
    - does 3 things:
        - define class with static testinfo* variable and testbody functions
        - outside class body, init static testinfo* var with call to func that registers that test at SEL_UnitTests (register via pointer to SEL_TestParent, because childs have different names)
        - header for testbody, the {} that follows the SEL_TEST(..) macro will define that function
    
- testinfo* optional, store test name, whether test should run