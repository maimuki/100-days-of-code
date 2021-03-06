# 100 Days Of Code - Log

********Gavin's Day 1: 2/26/2018********

Today's Progress: 
Worked on the "Factorialize a Number" FCC Algorithm Challenge.  Ended up needing to see the answer.  There are two interesting ways to solve the challenge.  
  1) function factorialize(num) {
      if (num===0){return 1;}
        return num * factorialize (num-1);
      }
    factorialize(5);
  2) function factorialize(num) {
      for (a = 1; num >=1; num --){a= num * a;}
      return a;
      }
    factorialize(5);
    
Next I studied the Udacity Intro to AJAX course.  I'm finding it very helpful.  AJAX is a way to get information for a page without refreshing.  XML and HTMl can be used, but JSON is more common.  JSON is a way to intereact with data and javascript. In the class we scrolled to the bottom of a Facebook page and recorded the Network in the inspect area to watch as an AJAX call was made.
 

Thoughts: So I can call factorialize within my factorialize function?  I want to better understand how that works with Global and Local scope.  The 2nd way to solve the problem used a for loop.  They set a to 1, but then used num for the other 2 perameters.  I didn't know I could do this.  I'm still trying to wrap my head around the rules here.  

********Day 2: 2/27/2018********

I worked on the Into to AJAX class today.  Watching the videos has been helpful in getting an idea of how it all works together.  I'm trying to use JQUERY to display coordinates in Google Maps at the moment.

********Day 44: 4/11/2018********

It's been a long time since I've updated this.  I've been posting to Twitter everyday, but neglected this journal.  I worked through the Free Code Camp Intermediate Algorithm DNA PAIRING.  
function pairElement(str) {
  var newPair=[];
  for(var x=0; x<str.length; x++){
    if(str[x]==='G'){
      newPair.push((str[x] + 'C').split(''));    
    } else if (str[x]==='C'){
      newPair.push((str[x] + 'G').split(''));
    }
    else if (str[x]==='T'){
      newPair.push((str[x] + 'A').split(''));
    }
    else if (str[x]==='A'){
      newPair.push((str[x] + 'T').split(''));
    }
  }
   return newPair;
}

pairElement("GCG");

I'm also playing around with portfolio templates on Github Pages.

********Day 45: 4/12/18********
Got my portfolio up on Github https://gavinsimon1.github.io  I'm stoked because this was a goal of mine.  I still need to improve the design and add projects.  But I'm excited that everything I build will be displayed.  

Missing Letters Solution:
function fearNotLetter(str) {

   for(var x=0; x < str.length - 1; x++){
     if (str.charCodeAt(x+1)- str.charCodeAt(x) != 1){
       return String.fromCharCode(str.charCodeAt(x) + 1);
     }
   }
}

fearNotLetter("abce");

Explanation:
The for loop give the index of the string.  If the next index number less the index number is not equal to 1, then return the index number plus 1. So a has an index of 97, b is 98, c is 99, e is 101.  101 less 99 is not 1, so it returns the missing index number of 100.  I use String.fromCharCode to change the index number back to an alphabet letter.  Cool beans.

********Day 46 4/13/2018 Friday the 13th AKA "Lucky Friday"********
Solved Boo who Challenge

function booWho(bool) {
  // What is the new fad diet for ghost developers? The Boolean.
 var cool = typeof(bool) === "boolean";
  return cool;
}

booWho(null);

Explanation:
I found the initial explanation confusing.  The different types are:
1) Primative value booleans: The most common way is to set a variable to true or false. 
       var cat = true; console.log(cat); // returns true
       var dog = false;  console.log(dog); // returns false
2) Boolean functions: 
       Boolean(2>1) returns true and Boolean(1>2) returns false. 
3) Boolean functions can be used as a constructor by adding New
4) Use var x = new Boolean().  I tried using new Boolean as a constructor but JS Bin didn't like that
It was helpful to get an overview of the complex world of booleans, but turned out to be more of a detour. 

It turns out that typeof() is the key to this challenge. 
    console.log(typeof(bool)); //returns boolean, object, number, string, or undefined.
So if the variable is true or false it will return "boolean" which will return true in the solution above.  If it doesn't equal "boolean" it will return false.
********Day 47 4/14/2018 Saturday******
Sorted Union Algorithm Challenge

function uniteUnique(arr) {
  var args = [];
  for(var x=0; x<arguments.length; x++){
    var blue = arguments[x];
    for(var y=0; y<blue.length; y++){
      var balls = blue[y];
      if(args.indexOf(balls)<0){
        args.push(balls);
      }
    }
  }
  return args;
}

uniteUnique([1, 3, 2], [5, 2, 1, 4], [2, 1]);

********Day 48 4/15/2018 Sunday******
Explanation:
When I console logged arr, I only got the first object in the array.  I wasn't sure how to access the other parts of the array.  But using the arguments object worked. Free Code Camp provides a great overview of arguments: https://forum.freecodecamp.org/t/javascript-arguments/14283 
console.log(arguments); //returns all the objects in the array. 
[object Arguments] {
  0: [1, 3, 2],
  1: [5, 2, 1, 4],
  2: [2, 1]
}
I can access specific parts of the arry with console.log(arguments[x]);
However, arguments is not an array.  The same link also explains that the best way to convert arguments into an array is:  
var args = []; // Empty array, at first.
for (var i = 0; i < arguments.length; i++) {
    args.push(arguments[i])
} 
This will return all of the arguments as an array: [[1, 3, 2], [5, 2, 1, 4], [2, 1]]
Now we have all of the arguments as an array, but we still need to combine them.  Removing push and setting arguments[x] equal to a variable returns:
[1, 3, 2]
[5, 2, 1, 4]
[2, 1]
A second loop through returns all of the elements of the arrays as:
1
3
2
5
2
1
4
2
1
console.log(args.indexOf(balls)) returns:
-1
-1
-1
-1
2
0
-1
2
0
So 1,3,2,5 are not found in args. But 2 and 1 are.  4 is not, but 2 and 1 are again.  So if it's less than 0, we push it to args.


**Day 49 4/16/2018 Monday**
Diving into regular expressions today
I found out there are two ways to write regular expressions.  The longway:
regexp = new RegExp("pattern", "flags");
And the short way:
regexp = /pattern/; // no flags
regexp = /pattern/gmi; // with flags g,m and i 
I like this example of a simple regular expression:

let str = "I love JavaScript!"; 
let regexp = /love/;
alert( str.search(regexp) ); // 2
alert( str.search(/LOVE/i) ); // 2

**Day 50 4/17/2018 Tuesday**
Convert HTML Entities Challenge
function convertHTML(str) {
 var object = {
   '&': '&amp;',
   '<': '&lt;',
   '>': '&gt;',
   '"': '&quot;',
   "'": '&apos;',
 };
  for (var x in object){
    var before = x;
    var after = object[x];
    var pattern = new RegExp(before, 'g');
    str = str.replace(pattern, after);
   
  }
   return str;
}

convertHTML("Dolce & Gabbana");

Explanation: for(variable in object) can be used with an object.  When I console.log(before); I get:
"&"
"<"
">"
"\""
"'"
console.log(after); results in:
"&amp;"
"&lt;"
"&gt;"
"&quot;"
"&apos;"

So this part of the code is giving me the two pieces I need.  
for (x in object){
var before = x;
var after = object[x];

Now, to put them together.
The new RegExp constructor creates a regular expression object for matching text with a pattern.  "Use the constructor function when you know the regular expression pattern will be changing, or you don't know the pattern and are getting it from another source, such as user input."

Finally replace allows me to change the regular expression to after. 

Spinal Tap Case
str=str.toLowerCase().split(" ").join('-'); works for some of the cases but not all of them.  

**Day 51 4/18/2018 Wednesday**
function spinalCase(str) {
 var blue = str.replace(/_/g, '');
   var balls = blue.replace(/([A-Z])/g, ' $1');
   var dog = balls.replace(/\s+/g, '-').toLowerCase();
   var hairy = dog.replace(/^-/, '');

   return hairy;
}

spinalCase('thisIsSpinalTap');

Explanation:
This one took a lot of tinkering.  First I replace all of the underscores with spaces.  I found this great article https://codeburst.io/javascript-learn-regular-expressions-for-beginners-bb6107015d91 explaining regular expressions.  He specifically explains how to replace camel case with spaces.  He shows how to use capturing parenthesis to remember the matched capital letters which are accessed with $1.  So now we have spaces between words.  Next I remove the spaces and add a dash.  I thought I was done, but there are dashes at the beginning of some of the cases.  The final line uses ^- to remove the first dash while keeping the rest.  

**Day 52 4/19/2018 Thursday**
Sum All Odd Fibonacci Numbers
function sumFibs(num) {
  var num1 = 0;
  var num2 = 1;
  var result =1;
  var odd =[];
  
  for(var i=0; i <= num; i++){
    next = num1 + num2;
    num1 = num2;
    num2 = result;
   
     if(num1%2==1 && num1<=num){
     odd.push(num1);
   } 

  } 
 console.log(odd);
  var sum = odd.reduce(add, 0);

      function add(a, b) {
              return a + b;
     }

   return (sum);
      
}

sumFibs(4);

Explanation:
Fibonacci sequence: every number after the first two is the sum of the two preceding ones. The sequence is: 1,1,2,3,5,8,13,21,34,55,89,144,... 
Within the loop for loop 
//num1 returns 1,1,2,3,5
//num2 returns 1,2,3,5,8
//result returns 1,2,3,5,8
//num remains 4
Then I needed to check if the number was odd and less than or equal to the number.  Numbers that pass that test get pushed into the odd array.  I used another function to add the numbers together.  

**Day 53 4/20/2018 Friday**
Worked on Sum All Primes.  Got the first solution quickly.  It identified all of the prime numbers in 10.  But 977 is itself Prime.  To find all of the prime numbers in a prime number, I need to go back to the drawing board.
function sumPrimes(num) {
for(var x = 2; x <= num; x++){
    if(num % x === 0){
     keep.push(x);
      console.log(keep);  
    } 
  }
  }

sumPrimes(10);


**Day 53 4/21/2018 Saturday**
Solved Sum All Primes
Even sad panda smiles!

function sumPrimes(num) {
  
  var blank = [];
  var array = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97, 101, 103, 107, 109, 113, 127, 131, 137, 139, 149, 151, 157, 163, 167, 173, 179, 181, 191, 193, 197, 199, 211, 223, 227, 229, 233, 239, 241, 251, 257, 263, 269, 271, 277, 281, 283, 293, 307, 311, 313, 317, 331, 337, 347, 349, 353, 359, 367, 373, 379, 383, 389, 397, 401, 409, 419, 421, 431, 433, 439, 443, 449, 457, 461, 463, 467, 479, 487, 491, 499, 503, 509, 521, 523, 541, 547, 557, 563, 569, 571, 577, 587, 593, 599, 601, 607, 613, 617, 619, 631, 641, 643, 647, 653, 659, 661, 673, 677, 683, 691, 701, 709, 719, 727, 733, 739, 743, 751, 757, 761, 769, 773, 787, 797, 809, 811, 821, 823, 827, 829, 839, 853, 857, 859, 863, 877, 881, 883, 887, 907, 911, 919, 929, 937, 941, 947, 953, 967, 971, 977, 983, 991, 997];
  
for (var x=0; x < array.length; x++){
    if(array[x]<= num){
    blank.push(array[x]);
     
    } 
     
  }
 
 function add(a,b){
       return a + b;
   }
  
  return blank.reduce(add);
}

sumPrimes(10);

Explanation: I used an array of all the prime numbers up to 1000.  First a for loop cycles through the array and returns all of the numbers less than or equal to the num variable.  Those get pushed to a blank array.  I initially tried to create the adding function within the for loop, but JS Bin wasn't having that.  It was a good thing to learn.  Stringing together functions.  The add function adds two numbers, then blank.reduce(add) takes out the garbage.  

**Day 54 4/22/2018 Sunday**
Worked on Smallest Common Multiple.  Got all of the primes in each mulitple, but I don't think that will work.
Spent time investigating career paths in web development.  I looked at the next steps for Javascript, and if I should learn PHP to be able to do Wordpress development.  Still not sure, but definately continuing with the FCC Front End Cert.

**Day 55 4/23/2018 Monday**
Still working on Smallest Common Multiple.
**Day 57 4/25/2018 Wedesday**
Tried a bunch of code, which I should have recorded.  I finally found that the code below will return the greatest common denominator.

function gcd(a, b){
  
  if(b === 0 || a === b)
    return a;
  else if(a > b)
    return gcd(a-b,b);
  else if(b > a)
     return gcd(a,b-a);
}

For gcd(5,4) this returns 1.  Reversing the numbers returns the same result. 

**Day 59 4/27/2018 Friday**
I passed all of the tests except the last one.  I was getting a Stack Overflow with the final test smallestCommons([23, 18]). Changing the Greatest Common Denominator function to the code below solved the problem.
function gcd(a, b) {
  if (!b) {
    return a;
  }
  return gcd(b, a % b);
}
Now I have to figure out why.  The full solution is:
function smallestCommons(arr) {
  var list = [];
  var a = arr[0];
  var b = arr[1];
 
  var max = arr.reduce(function(a,b){
      return Math.max(a,b);
  });
  
 //  console.log(max);
  var min = arr.reduce(function(a,b){
    return Math.min(a,b);
  });
  
   //console.log(min);
  
   for(var x=min; x<=max; x++){
        list.push(x);  
  }
  
 //console.log(list);
 
 function gcd(a, b) {
  if (b===0) {
    return a;
  }
  return gcd(b, a % b);
}

   // console.log(gcd(a,b));
  function lcm(a,b){
    return (a * b) / gcd(a, b);
  }
   //console.log(lcm(4,5));
 
  var balls = list.reduce(function(a,b){
   return lcm(a,b);
  });
  return balls;
 
}   
smallestCommons([23, 18]);

Explanation:
Find the highest and lowest numbers.  Then find all of the numbers in between.  Find the Greatest Common Denominator.  Use that to return the Lowest Common Multiple.  Reduce the range of numbers and find the LCM of all of them. 

**Day 60 4/28/2018 Saturday**
Finders Keepers

function findElement(arr, func) {
 var newArr = arr.filter(function(num){ return num % 2 === 0; });
  
 return newArr[0];

}

findElement([1, 3, 5, 8, 9, 10], function(num){ return num % 2 === 0; });

Explanation:
This next one was pretty easy.  I was a little unsure how to handle the test at the bottom.  But it turns out that arr.filter takes care of it.  I just need to repeat the test within the filter.  I set that to a variable called newArr.  It checks each element in the array and returns the result of the test.  We only need the first element in the array that passes the test, so newArr[0] does the trick.  

**Day 61 4/29/2018 Sunday**
Drop It Challenge
Exploring the "arguments object" today on Code Train.  Javascript is such a mind binder sometimes.  
function dropElements(arr, func) { 
console.log(arguments);
 }
dropElements([1, 2, 3], function(n) {return n < 3; });

//[object Arguments] { 0: [1, 2, 3], 1: function (n) {return n < 3; }}
**Day 62 4/30/2018 Monday**
After spending a bunch of time exploring object arguments, shift, and slice I ended up going with a for loop.  I tried out shift earlier, which returned the first false number, but I couldn't figure out how to loop through all of the numbers.  arr.shift(func[0]); 
The filter function passed 3 of the 5 tests. arr.filter(func)  It actually worked too well!  It didn't stop after the first true.  So in the end, the for loop below works:

function dropElements(arr,func) {
for (var i =0; i<arr.length+i; i++) {
if(func(arr[0]) === false ) {
arr.shift();
} else {
return arr;
}
}
return arr;
}

dropElements([1, 2, 3], function(n) {return n < 3; });

Steamroller
This function returns //[1, 2, 3, [[4]]] which is close, but not quite it.  
function steamrollArray(arr) {
 var flattened = [].concat.apply([], arr);
  console.log(flattened);

I'm not sure hwo to cycle through it, but running this multiple times solved the problem!
function steamrollArray(arr) {
    var flattened = [].concat.apply([], arr);
    var moreFlat = [].concat.apply([], flattened);
    var flattest =[].concat.apply([], moreFlat);
  return flattest;
}

steamrollArray([1, [2], [3, [[4]]]]);

}

I hope I'll be able to refactor this soon, but it works.

steamrollArray([1, [2], [3, [[4]]]]);

**Day 63 5/1/2018 Tuesday**
function binaryAgent(str) {
  var binaryCode  = str.split(" ");
  var biWords= [];
  

  for(var x=0; x<binaryCode.length; x++){
    biWords.push(String.fromCharCode(parseInt(binaryCode[x], 2)));
       
  }
  
 return biWords.join("");
 
}

binaryAgent("01000001 01110010 01100101 01101110 00100111 01110100 00100000 01100010 01101111 01101110 01100110 01101001 01110010 01100101 01110011 00100000 01100110 01110101 01101110 00100001 00111111");

**Day 64 5/2/2018 Wednesday**
Everything Be True Challenge
function truthCheck(collection, pre) {
  // Is everyone being true?
  var arr=[];
for (var x=0; x<collection.length; x++){
  if(!collection[x][pre]){
      arr.push(collection[x]);
  } 
}
  if(arr.length === 0){
    return true;
  } else {return false;}
}
truthCheck([{"user": "Tinky-Winky", "sex": "male"}, {"user": "Dipsy", "sex": "male"}, {"user": "Laa-Laa", "sex": "female"}, {"user": "Po", "sex": "female"}], "sex");

Explanation: 
First we need a for loop to cycle through the collection array. collection[x][pre] will return the sex of each of the parts of the array.  If there is no sex, it gets pushed to an empty array.  If there is nothing in the array, then everything returned as true and it gives us the final true statement.  If there is something in the array, the final statement will be false.  

Arguments Optional Challenge
function addTogether() {
 if (arguments.length === 1 && typeof arguments[0] === 'number'){
   var x = arguments[0];
   return function(y){
     if(typeof y === 'number'){
       return x + y;
     }    
   };   
 } else if (typeof arguments[0] === 'number' && typeof arguments[1] === 'number'){
   return arguments[0] + arguments[1];    
 }
}
addTogether(2,3);

Explanation:  This was a brain twister, but the solution makes sense.  First we check to see if there are two varibles being passed into the function.  If there is only one variable, and it is a number then we do something.  If there are two variables, and they are both numbers, we add them together.  If there is only one variable, we create a function to add them. We don't know what the first variable will be, so we set it to x.  Then we use a function y to add the two.  It looks very simple in retrospect.  


**Day 65 5/3/2018 Thursday**
Starting the Advanced Algorithm Challanges!  First up is Validate US Telephone Numbers Challenge.
I did it with the following code:
function telephoneCheck(str) {
  // Good luck!
// var phoneRegEx = /\d$ \(\d\d\d\) \d\d\d \d\d\d\d$/;
   var phoneRegEx = /^1? \(\d\d\d\) \d\d\d-\d\d\d\d$/;
   var phoneRegEx1 = /^1? \d\d\d-\d\d\d-\d\d\d\d$/;
   var phoneRegEx2 = /^1?\d\d\d\d\d\d\d\d\d\d$/;
   var phoneRegEx3 = /^1?\d\d\d-\d\d\d-\d\d\d\d$/;
   var phoneRegEx4 = /^1?\d\d\d-\d\d\d-\d\d\d\d$/;
   var phoneRegEx5 = /^1?\(\d\d\d\)\d\d\d-\d\d\d\d$/;
   var phoneRegEx6 = /^1? \d\d\d \d\d\d \d\d\d\d$/;
  
  if(str.match(phoneRegEx)){
    return true;
  } 
  else if (str.match(phoneRegEx1)){
            return true;
            } 
  else if (str.match(phoneRegEx2)){
            return true;
            }
  else if (str.match(phoneRegEx3)){
            return true;
            }
  else if (str.match(phoneRegEx4)){
            return true;
            }
  else if (str.match(phoneRegEx5)){
            return true;
            }
  else if (str.match(phoneRegEx6)){
            return true;
            }
  
  else {return false;}
}
telephoneCheck("555-555-5555");

Then I learned that I could do it in a single line!  Much better.
var phoneRegEx = /^1? ?(\d{3}|\(\d{3}\))[ -]?\d{3}[ -]?\d{4}$/; 


**Day 66 5/4/2018 Friday**
I was really stumped on this one.  Thankfully, I found a good discussion in the forum.  Here is the final code:

function updateRecords(id, prop, value) {
  if(prop !== "tracks" && value !== ""){
    collection[id][prop] = value;   
  } else if (prop === "tracks" && value !== ""){
    var check = collection[id].hasOwnProperty('tracks');
    if (check === false) {
      collection[id].tracks = [];
      collection[id][prop].push(value);
    }
    else if (check === true) {
      collection[id][prop].push(value);
    }
  } else {delete collection[id][prop];}
  
  return collection;
}

Explanation: If the prop is not tracks and value is not empty, set the property of the ID to the new value.  If the property is tracks and the vale is not blank, check to see if the ID has a track property.  If it does, push the value to that property.  If not, create an empty array and push the value to the empty array.  If there is no tracks then delete the property altogether.   

**Day 67 5/5/2018 Saturday**
Symmetric Difference Challenge

I spent a while yesterday trying to figure out how to access the second part of sym.  This morning I found that Array.protype.slice.call(arguments) does the trick!  

function sym(args) {

var yoMaMa = Array.prototype.slice.call(arguments);
console.log(yoMaMa);
  
}

sym([1, 2, 3], [5, 2, 1, 4]);

Now I can access all prarts of the array.  The next issue is that I don't know how many arrays will be used in sym. 

function sym() {
var args = [];
for(var x=0; x<arguments.length; x++){
  args.push(arguments[x]);
   
}
 
//console.log(args);
  
   
function difference(arr1, arr2){
  var result = [];
  arr1.forEach(function(balls){
    if(arr2.indexOf(balls) < 0 && result.indexOf(balls) < 0){
      result.push(balls);
  
  arr2.forEach(function(balls){
    if(arr1.indexOf(balls)<0 && result.indexOf(balls)<0){
      result.push(balls);
     
    }
    
  });
             
    }
    
  });
  return result;
    
  }
  return args.reduce(difference);
}   

sym([1, 2, 3], [5, 2, 1, 4]);

**Day 68 5/6/2018 Sunday**

Explanation:  I spent some time going over this again.  I really like the simplicity, but I'm still struggling to wrap my mind around all of the concepts.  We start with creating an empty array for arr.  Then we use arguements.  We loop through arguments and push the results to our empty arr.  Next we create a function called difference to compare arr1 and arr2.  First we create a new empty array called results.  We loop through arr1 to see if there is an indexOf -1 for both arr2 and results.  If both return a -1, we know the number is not in arr2 and results.  So we push it to the results array.  We used arr1.forEach(function(balls){if... in the example above.  I used a for loop this morning for (var x=0; x<arr1.length; x++){if... The only difference is the for loop is a bit more combersome with arr1[x] and arr2[y], but it comes more intuitively to me than forEach(function(balls).  The real mind bender comes at the end with args.reduce(difference).   

**Day 69 5/7/2018 Monday**
Started the Exact Change problem.  Only got a for loop to give me the contents of the array.  A good start, but now comes the harder part.

function checkCashRegister(price, cash, cid) {
  var change =  cash - price;
   //console.log(cid[1]);
  
  //console.log(change);
  for(x=0; x<cid.length; x++){
    console.log(cid[x][1]);
  }
  return change;
}

checkCashRegister(19.50, 20.00, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.10], ["QUARTER", 4.25], ["ONE", 90.00], ["FIVE", 55.00], ["TEN", 20.00], ["TWENTY", 60.00], ["ONE HUNDRED", 100.00]]);


**Day 71 5/9/2018 Wednesday**
Back to the drawing board on the Exact Change Challenge.
I'm using this code to loop backwards through my for loop:
for(var i = cid.length -1; i>=0; i-- ){
    console.log(cid[i]);
  }
function checkCashRegister(price, cash, cid) {
  var change = (cash - price) * 10;
  var result = [];
   
  
  for(var i = cid.length -1; i>=0; i-- ){
    var names = cid[i][0];
    var money = cid[i][1];
    var test = money - change;
    //console.log(money);
    //console.log(change);
   if(test>0){result.push(test);} 
    
  }
      
  // if(change>0){
   // money--;
   // change--;
   // result.push(money - change);
      
  // }
  console.log(result); //[95, 55, 15, 50, 85]  
  
}


**Day 72 5/10/2018 Thursday**

I found a tutorial on creating custom Wordpress themes yesterday.  I'm excited to give it a try soon: https://www.taniarascia.com/developing-a-wordpress-theme-from-scratch/ and this one looks helpful too http://webdesignerwall.com/tutorials/building-custom-wordpress-theme

**Day 73 5/11/2018 Friday**
I'm using the map function to provide all of the money in cid.  Then the reduce functions to total all of the cash in drawer.
var cidMoney = cid.map(function(balls){
    //console.log(balls[1]);
     return balls[1];
  });
  
  var totalMoney = money.reduce(function(a,b){
    return a+b;
  })
  console.log(totalMoney.toFixed(2));
  
  **Day 74 5/12/2018 Saturday**
  
  Getting close but hit some large snags.  It almost returns the correct amount, but the pennies aren't included.  Also, it's not passing the test case for 0.50.  It returns ("QUARTERS, .5) or ("QUARTERS, "0.50") which is not passing.  Here is what I have so far: 
  
  function checkCashRegister(price, cash, cid) {
  var change = (cash - price).toFixed(2);
  var result = [];
  var cashToPay = [];
  
  var cidMoney = cid.map(function(balls){
    //console.log(balls[1]);
    return balls[1];
    
  });
  
  var allMoney = cidMoney.reduce(function(a,b){
    return a+b;
  });
   
   totalMoney = allMoney.toFixed(2);
   
  
  var totalChange = totalMoney - change; 
  if (totalChange < 0){
    return "Insufficient Funds";
  } else if(totalChange === 0){
    return "Closed";
  }


 for(var x = cid.length - 1; x > 0; x--){
   var coinNames = cid[x][0];
   var totalCoins = cid[x][1];
   var nameValue = findValue(coinNames);
   var coinAmount = totalCoins/nameValue;
   var toReturn = 0;
   
 while (change >= nameValue && coinAmount > 0){
   change -= nameValue;
   coinAmount--;
   toReturn++;
 }
   
 
 if(toReturn > 0){
    var myNumber = toReturn * nameValue;
 
   result.push(coinNames, parseFloat(myNumber.toFixed(2)));
 }  
 
 }
   
      return result;
 }


function findValue(names){
  
  switch (names){
    case "PENNY":
      return 0.01;
    case "NICKEL":
      return 0.05;
    case "DIME":
      return 0.10;
    case "QUARTER":
      return 0.25;
    case "ONE": 
      return 1;
    case "FIVE":
      return 5;
    case "TEN":
      return 10;
    case "TWENTY": 
      return 20;
    case "ONE HUNDRED":
      return 100;
    
}    
}

checkCashRegister(3.26, 100.00, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.10], ["QUARTER", 4.25], ["ONE", 90.00], ["FIVE", 55.00], ["TEN", 20.00], ["TWENTY", 60.00], ["ONE HUNDRED", 100.00]]);

  **Day 75 5/13/2018 Sunday**
  Exact Change Challenge Solution:
  
var denominations = [
  {name: "HUNDRED" , value: 100},
   {name: "TWENTY" , value: 20},
  {name: "TEN" , value: 10},
  {name: "FIVE" , value: 5},
  {name: "ONE" , value: 1},
   {name: "QUARTER" , value: 0.25},
    {name: "DIME" , value: 0.10},
   {name: "NICKEL"  , value: 0.05},
  {name: "PENNY" , value: 0.01}, 
     
   ];
    
function checkCashRegister(price, cash, cid) {
  var change = cash - price;
  var totalCid = cid.reduce (function (acc, next){
    //console.log(acc);
  // console.log(next);
    //console.log(acc+next[1]);
    return acc + next[1]; 
  },0.0);
  
 
  if(totalCid < change){
    return "Insufficient Funds";
  } else if(totalCid === change){
    return "Closed";
  }
  
  cid = cid.reverse();
  //console.log(cid);
  
 var result = denominations.reduce (function(acc,next,index){
  
   if(change>=next.value){
     var currentValue = 0.0;
     while(change>=next.value && cid[index][1] >= next.value){
       currentValue += next.value;
       change -= next.value;
       change = Math.round(change * 100)/100;
       cid[index][1] -= next.value;
       
     } 
     acc.push([next.name, currentValue]);
       
       return acc;
   } else {
     return acc;
   }
 },[]);
  
  return result.length > 0 && change === 0 ? result: "Insufficient Funds";
  
  **Day 76 5/14/2018 Monday**
  Reviewed and reworked through Exact Change today.  First we create an object called money, which is outside of the checkCashRegister function.  An object has key value pairs, which can be accessed using money.name and money.value.  Cid is a 2D Array which can be accessed with Cid[0] to get the name and cid[1] to get the value.  We get the change owed by subtracting the price from the cash.  We use the reduce method on cid to get the total value of the money in the cash register.  We add the next value in cid, which is b[1], to the accumulator.  We need to give the accumulator a starting value of 0.0.  If the total in the register is less than the change due, we return "Insufficient Funds".  If the two are equal, we return "Closed". We reverse the cid array so it aligns with the decending order we have in our money object, (100 lines up with 100, 20 lines up with 20, etc.). Now we get to the meat of our function.  We use reduce on the money object.  We use the accumulator, next, and the index.  We also need to add an empty array at the end.  This is to return a 2D array instead of a 1D array.  Next.value is the value in the money object (100, 20, 10, etc.).  If change is greater than this value, so if 50 cents is greater than 25 cents, we use our while loop.  We set a current value equal to 0.00.  We also look at the value in the cash in drawer 2D array with cid[index][1].  cid[index][1] will be 100, than 60, than 20, than 55, etc. While change is greater than the object's current value and cid[index][1] is greater than or equal to the current value, we do math.  If it's .25 cents in our next.value then we add that .25 to the current value, we subtract change, and we subtract from the cash register.  We use Math.round to make sure the decimals are correct. The final part is if we owe .50 cents but we only have a $10 bill, we can't return change.  So the last line says to return insufficient funds if the result greater than 0 and change is equal to zero.
 
  var money = [
  {name: "HUNDRED" , value: 100},
   {name: "TWENTY" , value: 20},
  {name: "TEN" , value: 10},
  {name: "FIVE" , value: 5},
  {name: "ONE" , value: 1},
   {name: "QUARTER" , value: 0.25},
    {name: "DIME" , value: 0.10},
   {name: "NICKEL"  , value: 0.05},
  {name: "PENNY" , value: 0.01}, 
     
   ];

function checkCashRegister(price, cash, cid) {
  var change = cash - price;
 var register =  cid.reduce(function (a,b){
    return a + b[1];
  }, 0.0);
  
 if(register < change){
   return "Insufficient Funds";
 } else if (register === change){
   return "Closed";
 }
  
  cid = cid.reverse();
  
 var result = money.reduce(function(acc, next, index){
   if(change >= next.value){
     var currentValue = 0.00;
     while(change >= next.value && cid[index][1] >= next.value){
       currentValue += next.value;
       change -= next.value;
       change = Math.round(change*100)/100;
       cid[index][1] -= next.value;
     }
      acc.push([next.name, currentValue]);
      return acc;
   } else {
     return acc;
   } 
 },[]);
  
  return result.length > 0 && change === 0 ? result: "Insufficient Funds";
}

checkCashRegister(19.50, 20.00, [["PENNY", 1.01], ["NICKEL", 2.05], ["DIME", 3.10], ["QUARTER", 4.25], ["ONE", 90.00], ["FIVE", 55.00], ["TEN", 20.00], ["TWENTY", 60.00], ["ONE HUNDRED", 100.00]]);

 **Day 77 5/15/2018 Tuesday**
 
 Starting on Inventory Update challenge.  I can push the items into a new array.  But it's more complex than that.  Need to comapre and update the 2d array.  Reading about the sort method now.
 
 **Day 79 5/17/2018 Thursday**
 Still trying to combine these 2D arrays. 
 
 function updateInventory(arr1, arr2) {
  var newArr = [];
   //console.log(arr1[2][0]);
  //console.log(arr1[0][1]);
  for(var x=0; x < arr1.length; x++){
    //console.log(arr1[x][1]);
    //console.log(arr1[x][0]); returns number
   for(var y=0; y < arr2.length; y++){
      
     if(arr1[x][1] === arr2[y][1]){
       //console.log(arr1[x]);
        
        newArr.push(arr1[x][0] + arr2[y][0], arr1[x][1]);
        
       }
     }
   
  }
  
    console.log(newArr);
  
  }



// Example inventory lists
var curInv = [
    [21, "Bowling Ball"],
    [2, "Dirty Sock"],
    [1, "Hair Pin"],
    [5, "Microphone"]
];

var newInv = [
    [2, "Hair Pin"],
    [3, "Half-Eaten Apple"],
    [67, "Bowling Ball"],
    [7, "Toothpaste"]
];

updateInventory(curInv, newInv);

**Day 80 5/18/2018 Friday**
Still basically where I started with this problem a few days ago.  I'm ablt to return an array with the duplicate elements added together.  But I'm not sure how to add the rest of the elements that are not duplicated.  The result of my current code is [[88, "Bowling Ball"], [3, "Hair Pin"]].  I'm using 2 for loops and pushing the results to a new array.  But I need to add the other arrays and then alphabatize it.  It doesn't seem like it should be hard, but I keep running into obstacles.  

**Day 83 5/21/2018 Monday**
Finally got through the Exact Change Challenge!
function updateInventory(arr1, arr2) {
    // All inventory must be accounted for or you're fired!
    var newArr = [];
    for(var x = 0; x < arr1.length; x++){
      for(var y = 0; y < arr2.length; y++){
        if(arr1[x][1] === arr2[y][1]){
          arr1[x][0] = arr1[x][0] + arr2[y][0];
          newArr.push([arr1[x][0], arr1[x][1]]);
          arr1.splice(x,1);
          arr2.splice(y,1);
        }
      }
    }
  newArr = newArr.concat(arr1);
  newArr = newArr.concat(arr2);
  function balls(a,b){
    if(a[1] < b[1]) return -1;
    if(a[1] > b[1]) return 1;
    return 0;
  }
  newArr.sort(balls); 
  return newArr;
}

 

// Example inventory lists
var curInv = [
    [21, "Bowling Ball"],
    [2, "Dirty Sock"],
    [1, "Hair Pin"],
    [5, "Microphone"]
];

**Day 84 5/22/2018 Tuesday**

Starting to work on No Repeats challenge.  Taking a look at Heap’s Permutation Algorithm

var swap = function (array, pos1, pos2) {
  var temp = array[pos1];
  array[pos1] = array[pos2];
  array[pos2] = temp;
};

var heapsPermute = function (array, output, n) {
  n = n || array.length; // set n default to array.length
  if (n === 1) {
    output(array);
  } else {
    for (var i = 1; i <= n; i += 1) {
      heapsPermute(array, output, n - 1);
      if (n % 2) {
        var j = 1;
      } else {
        var j = i;
      }
      swap(array, j - 1, n - 1); // -1 to account for javascript zero-indexing
    }
  }
};


// For testing:
var print = function(input){
  console.log(input);
}

heapsPermute(['a', 'b', 'c', 'd'], print);
// heapsPermute([1, 2, 3], print)
var newInv = [
    [2, "Hair Pin"],
    [3, "Half-Eaten Apple"],
    [67, "Bowling Ball"],
    [7, "Toothpaste"]
];

updateInventory(curInv, newInv);

**Day 85 5/23/2018 Wednesday**
Working on the No Repeats Please problem. 

function permAlone(str) {
  
  var consec = /(.)\1/;
  
  return heap(str).filter(function(balls){
    return !consec.test(balls);
  }).length;
  
  function heap(str){
    var arr = string.split('');
    var perm = [];
    
    function swap(a,b){
      var temp = arr[a];
      arr[a] = arr[b];
      arr[b] = temp;
    }
    
    function gen(n){
      if(n === 1){
        perm.push(arr.join(''));
      } else {
        for (var i = 0; i != n; i++){
          gen(n-1);
          swap(n % 2 ? 0 : i, n - 1);
        }
      }
    }
    gen(arr.length);
    return perm;
    
  }
  
  **Day 91 5/29/2018 Tuesday **
  
  Make a Person Challenge
  
  var Person = function(firstAndLast) {
    // Complete the method below and implement the others similarly
   
  var firstName;
  var lastName;
  
  this.getFirstName = function (){
    return firstName;
  };
  
  this.getLastName = function (){
    return lastName;
  };
  
  this.getFullName = function() {
      return firstName + ' ' + lastName;
    };
 
  this.setFirstName = function(first){
      firstName = first;
  };
  
  this.setLastName = function(last){
    lastName = last;
  };
  
  this.setFullName = function(firstAndLast){
    firstAndLast = firstAndLast.split(' ');
    firstName = firstAndLast[0];
    lastName = firstAndLast[1];
  };
  
  this.setFullName(firstAndLast);
  
};

var bob = new Person('Bob Ross');
bob.getFullName();

  **Day 100 6/8/2018 Friday**
  In 100 days of Code I:
  * Started waking up at 5am to code
  * Got my portfolio online
  * Built 2 websites
  * Worked through most of the Free Code Camp advanced algorithms
  * Learned a ton
  
 
