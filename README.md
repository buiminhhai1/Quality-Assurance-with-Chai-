# Quality-Assurance-with-Chai-
A part of back-end challenge freecodecamp

## Introduction
As your programs become more complex, you need to test them often to make sure any new code you add doesn't break the program's original functionality. Chai is a JavaScript testing library that helps you check that program still behaves the way you expect it to after you make changes. Using Chai, you can write tests that describe your program's requirements and see if your program meets them.
### 1.Learn How JavaScript Asserntions Work
Use assert.isNull() or assert.isNotNull() to make the tests pass.
### 2. Test if a Variable or Function is Defined
Use assert.isDefined() or assert.isUndefined() to make the tests pass.
### 3. Use Assert.isOK and Assert.isNotOK
Use assert.isOK() or assert.isNotOK() to make the tests pass.
### 4. Test for Truthiness
Use assert.isTrue() or assert.isNotTrue() to make the test pass
### 5. Use the Double Equals to Assert Equality
.equal(), .notEqual()
.equal() compares objects using '=='
### 6. Use the Triple Equals to Assert Strict Equality
.strictEqual(), .notStrictEqual()
.strictEqual() compares objects using '==='
### 7. Assert Deep Equality with .deepEqual and . notDeepEqual
.deepEqual(), .notDeepEqual()
.deepEqual() asserts that two object are deep equal
### 8. Compare the Properties of Two Elements
.isAbove() => a > b , .isAtMost() => a <= b 
### 9. Test if One Value is Below or At Least as Large as Another
.isBelow() => a < b, .isAtLeast() => a >= b
### 10. Test if a Value Falls within a Specific Range
.approximately
.approximately(actual, expected, range, [messmage])
actual = expected +/- range
Choose the minimum range (3rd parameter) to make the test always pass
It should be less than 1.

### 11. Test if a Value is An Array
### 12. Test if an Array Contains an Item.
### 13. Test if a Value is a String
#isString asserts that the actual value is a string.
### 14. Test if a String Contains a Substring.
#include (#notInclude) works for string too!
It asserts that the actual string contains the expected substring.
### 15. Use Regular Expressions to Test a String.
#match Asserts that the actual value
matches the second argument regular expression.
### 16. Test if an Object has a Property
#property asserts that the actual object has a given property.
Use #property or #notProperty where appropriate
### 17. Test if a Value is of a Specific Data Structure Type
#typeOf asserts that value's type is the given string, as determined by Object.prototype.toString.
Use #typeOf or #notTypeOf where appropriate
### 18. Test if an Object is an Instance of a Constructor
#instanceOf asserts that an object is an instance of a constructor.
Use #instanceOf or #notInstanceOf where appropriate.
```python
var chai = require("chai");
var assert = chai.assert;

suite("Unit Tests", function(){
  // Make all tests pass
  // ! Don't scamble the Assertions. We rely their order to check the results !!!
  suite("Basic Assertions", function(){
    /** assert.fail() will always fail. Change it into something more useful... **/
  
    /** 1 - Use assert.isNull() or assert.isNotNull() to make the tests pass. **/
    test("#isNull, #isNotNull", function(){
      assert.isNull(null, "this is an optional error description - e.g. null is null");
      assert.isNotNull(1, "1 is not null");
    });
    //2. Use assert.isDefined() or assert.isUndefined() to make the test pass
    test("#isDefined, #isUndefined", function(){
      assert.isDefined(null, "null is not undefined");
      assert.isUndefined(undefined, "undefined is undefined");
      assert.isDefined("hello", "a string is not undefined");
    });
    //3. Use assert.isOK() or assert.isNotOK() to make the tests pass.
    test("#isOk, #isNotOk", function(){
      assert.isNotOk(null, "null is falsey");
      assert.isOk("I'm truthy", "a string is truthy");
      assert.isOk(true, "true is truthy");
    });
    /** 4 - Use assert.isTrue() or assert.isNotTrue() to make the tests pass. **/
    // .isTrue(true) and .isNotTrue(everything else) will pass.
    // .isFalse() and .isNotFalse() also exist.
    test("#isTrue, #isNotTrue", function(){
      assert.isTrue(true, "true is true");
      assert.isTrue(!!'double negation', "double negation of a truthy is true");
      assert.isNotTrue({value: 'truthy'}, 'A truthy object is NOT TRUE (neither is false...)');
    });
    
    suite("Equality", function(){
      /** 5 - .equal(), .notEqual() **/
      // .equal() compares objects using '=='
      test("#equal", "#notEqual", function(){
        assert.equal(12, "12", "numbers are coerced into strings with == ");
        assert.notEqual({value:1}, {value:1}, '== compares object references');
        assert.equal(6* '2', '12', 'no more hints...');
        assert.notEqual(6 + '2', '12','type your error message if you want');
      });
      /** 6 - .strictEqual(), .notStrictEqual() **/
      // .strictEqual() compares objects using '==='
      test("#strictEqual, #notStrictEqual", function(){
        assert.notStrictEqual(6,'6');
        assert.strictEqual(6, 3*2);
        assert.strictEqual(6 * '2', 12);
        assert.notStrictEqual([1,'a', {}], [1, 'a', {}]);
      });
      /** 7 - .deepEqual(), .notDeepEqual() **/
      // .deepEqual() asserts that two object are deep equal
      test("#deepEqual, #notDeepEqual", function(){
        assert.deepEqual( { a: '1', b: 5 } , { b: 5, a: '1' }, "keys order doesn't matter" );
        assert.notDeepEqual( { a: [5, 6] }, { a: [6, 5] }, "array elements position does matter !!" );
      });
    });
    // ------------------------------------------------------------------------------
    
    // This function is used in the tests. Don't Edit it.
    function weirdNumbers(delta){
      return (1 + delta - Math.random());
    }
    
    suite("Comparisons", function(){
      /** 8 - .isAbove() => a > b , .isAtMost() => a <= b **/
      test("#isAbove, #isAtMost", function(){
        assert.isAtMost("hello".length, 5);
        assert.isAbove(1,0);
        assert.isAbove(Math.PI, 3);
        assert.isAtMost(1 -Math.random(), 1 );
      });
      /** 9 - .isBelow() => a < b , .isAtLeast =>  a >= b **/
      test("#isBelow, #isAtLeast", function(){
        assert.isAtLeast('world'.length , 5);
        assert.isAtLeast(2 * Math.random(), 0);
        assert.isBelow(5 % 2, 2);
        assert.isBelow(2/3, 1);
      });
      
      /** 10 - .approximately **/
      // .approximately(actual, expected, range, [message])
      // actual = expected +/- range
      // Choose the minimum range (3rd parameter) to make the test always pass
      // it should be less than 1
      });
      test("#approximately", function(){
        assert.approximately(weirdNumbers(0.5) , 1, 0.5);
        assert.approximately(weirdNumbers(0.2) , 1, 0.2);
      });
  });
  //--------------------------------------------------------------------------
  
  // These variables are used in the tests. Don't Edit them.
  var winterMonths = ['dec,','jan', 'feb', 'mar'];
  var backendLanguages = ['php', 'python', 'javascript', 'ruby', 'asp'];
  suite('Arrays', function(){
    /** 11 - #isArray vs #isNotArray **/
    test("#isArray, #isNotArray", function(){
      assert.isArray("isThisAnArray?".split(""), "String.prototype.split() return an array");
      assert.isNotArray([1,2,3].indexOf(2), 'indexOf returns a numbers.');
    });
    
    /** 12 - #include vs #notInclude **/
    test("Array #include, #notInclude", function(){
      assert.notInclude(winterMonths, 'jul', "It's summer in july...");
      assert.include(backendLanguages, 'javascript', 'JS is a backend language !!');
    });
  });
  
  // These variables are used in the tests. Don't edit them.
  var formatPeople = function(name, age) {
    return '# name: ' + name + ', age: ' + age + '\n';
  };
  suite('Strings', function(){
    /** 13 - #isString asserts that the actual value is a string. **/
    test("#isString, #isNotString", function(){
      assert.isNotString(Math.sin(Math.PI/4), "a float is not a string");
      assert.isString(process.env.PATH, 'env vars are strings (or undefined)');
      assert.isString(JSON.stringify({type:'object'}), 'a JSON is a string');
    });
    
    /** 14 - #include (on #notInclude ) works for strings too !! **/
    // It asserts that the actual string contains the expected substring
    test("String #include, #notInclude", function(){
      assert.include("Arrow", "row", "Arrow contains row...");
      assert.notInclude("dart", "queue", "But a dart doesn't contain a queue.");
    });
    
    /** 15 - #match Asserts that the actual value **/
    // matches the second argument regular expression.
    test("#match, #notMatch", function(){
      var regex = /^#\sname\:\s[\w\s]+,\sage\:\s\d+\s?$/;
      assert.match(formatPeople('John Doe', 35), regex);
      assert.notMatch(formatPeople('Paul Smith III', 'twenty-four'), regex);
    });
  });
  
  // -------------------------------------------------------------------
  
   // These variables are used in the tests. Don't Edit them.
  var Car = function() {
    this.model = 'cedan';
    this.engines = 1;
    this.wheels = 4;
  };

  var Plane = function() {
    this.model = '737';
    this.engines = ['left', 'right'];
    this.wheels = 6;
    this.wings = 2;
  };
  
  var myCar = new Car();
  var airlinePlane = new Plane();

  suite('Objects', function(){
    /** 16 - #property asserts that the actual object has a given property. **/
    // Use #property or #notProperty where appropriate
    test('#property, #notProperty', function() {
      assert.notProperty(myCar, 'wings', 'A car has not wings');
      assert.property(airlinePlane, 'engines', 'planes have engines');
      assert.property(myCar, 'wheels', 'Cars have wheels');
    });
    
    test('#typeOf, #notTypeOf', function() {
      
      /** 17 #typeOf asserts that value’s type is the given string, **/
      // as determined by Object.prototype.toString.
      // Use #typeOf or #notTypeOf where appropriate
      assert.typeOf(myCar, 'object');
      assert.typeOf(myCar.model, 'string');
      assert.notTypeOf(airlinePlane.wings, 'string');
      assert.typeOf(airlinePlane.engines, 'array');
      assert.typeOf(myCar.wheels, 'number');
    });
    
    test('#instanceOf, #notInstanceOf', function() {
      
      /** 18 #instanceOf asserts that an object is an instance of a constructor **/
      // Use #instanceOf or #notInstanceOf where appropriate
      assert.notInstanceOf(myCar, Plane);
      assert.instanceOf(airlinePlane, Plane);
      assert.instanceOf(airlinePlane, Object, 'everything is an Object');
      assert.notInstanceOf(myCar.wheels, String );
    });
  });
  /** 
 * Good Job, You are done here !!! 
 *  Please go to the file "2_functional_tests.js" ... 
 **/
});
```
### 19. Run Functional Tests on API Endpoints using Chai-HTTP
Replace assert.fail. Test the status and the text.response. Make the test pass.
Don't send a name in the query, the endpoint with responds with 'hello Guest'.
### 20 Run Functional Tests On API Endpoints using Chai-HTTP II
Replace assert.fail(). Test the status and the text.response. Make the test pass.
Send you name in the query query appending ?name=, the endpoint with responds with 'hello'.
### 21. Run Functional Tests on an API Response using Chai-HTTP III - PUT method.
In the next example we'll see how to send data in a request payload (body).
We are going to test a PUT request. The '/travellers' endpoint accepts.
a JSON object taking the structure: 
{surname: [last name of a traveller of the past]},
The route responds with: 
{name: [first name], surname: [last name], dates: [birth - death years]}.
see the server code for more details.
Send {surname: 'Colombo'}. Replace assert.fail() and make the test pass.
Check for 1) status, 2) type, 3)body.name, 4)body.surname

### 22. Run Functional Tests on an API Response using Chai-HTTP IV - PUT method.
This exercise is similar to the preceding. Look at it for the details.
Send {surname: 'da Verrazzano'}. Replace assert.fail() and make the test pass.
Check for 1) status, 2) type, 3) body.name, 4) body.surname
Follow the assertion order above, We rely on it.


```python
      // 19
      // If no name is passed, the endpoint responds with 'hello Guest'.
      test('Test GET /hello with no name',  function(done){ // Don't forget the callback...
         chai.request(server)             // 'server' is the Express App
          .get('/hello')                  // http_method(url). NO NAME in the query !
          .end(function(err, res){        // res is the response object
          
            // Test the status and the text response (see the example above). 
            // Please follow the order -status, -text. We rely on that in our tests.
            // It should respond 'Hello Guest'
            assert.equal(res.status, 200);
            assert.equal(res.text, 'hello Guest');
            done();   // Always call the 'done()' callback when finished.
          });
      });
      // 20
      /**  Another one... **/
      test('Test GET /hello with your name',  function(done){ // Don't forget the callback...
         chai.request(server)             // 'server' is the Express App
          .get('/hello?name=Minh Hai') /** <=== Put your name in the query **/ 
          .end(function(err, res){        // res is the response object
          
            // Your tests here.
            // Replace assert.fail(). Make the test pass.
            // Test the status and the text response. Follow the test order like above.
            assert.equal(res.status, 200);
             assert.equal(res.text, 'hello Minh Hai'/** <==  Put your name here **/);
            done();   // Always call the 'done()' callback when finished.
          });
      });
      
      // 21
      /** Now it's your turn. Make the test pass. **/
      // We expect the response to be
      // {name: 'Cristoforo', surname: 'Colombo', dates: '1451 - 1506'}
      // check the status, the type, name and surname.
      
      // !!!! Follow the order of the assertions in the preceding example!!!!, 
      // we rely on it in our tests.
      
      test('send {surname: "Colombo"}',  function(done){
       
       // we setup the request for you...
       chai.request(server)
        .put('/travellers')
        .send({surname: 'Colombo'})
        /** send {surname: 'Colombo'} here **/
        // .send({...})
        .end(function(err, res){
          
          /** your tests here **/
          assert.equal(res.status, 200, 'response status should be 200');
          assert.equal(res.type, 'application/json', "Response should be json");
            
          // res.body contains the response parsed as a JS object, when appropriate
          // (i.e the response type is JSON)
          assert.equal(res.body.name, 'Cristoforo', 'res.body.name should be "Cristoforo"');
          assert.equal(res.body.surname, 'Colombo', 'res.body.surname should be "Colombo"' );
          
          done(); // Never forget the 'done()' callback...
        });
      });
      
      // 22
      /** Repetition is the mother of learning. **/
      // Try it again. This time without help !!
      test('send {surname: "da Verrazzano"}', function(done) {
        /** place the chai-http request code here... **/
        chai.request(server)
        .put('/travellers')
        .send({surname: 'da Verrazzano'})
        /** send {surname: 'da Verrazzano'} here **/
        // .send({...})
        .end(function(err, res){
          
          /** your tests here **/
          assert.equal(res.status, 200, 'response status should be 200');
          assert.equal(res.type, 'application/json', "Response should be json");
            
          // res.body contains the response parsed as a JS object, when appropriate
          // (i.e the response type is JSON)
          assert.equal(res.body.name, 'Giovanni', 'res.body.name should be "Giovanni"');
          assert.equal(res.body.surname, 'da Verrazzano', 'res.body.surname should be "da Verrazzano"' );
          
          done(); // Never forget the 'done()' callback...
        });
      });
    });

```
