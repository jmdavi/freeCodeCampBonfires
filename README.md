# freeCodeCampBonfires
Bonfires and other code I want to keep, especially as they get more complicated...

Don't worry, I'll get rid of the below at some point and separate them out into javascript files:

Roman Numeral Converter
convert(5) should return "V".
convert(9) should return "IX".
convert(12) should return "XII".
convert(16) should return "XVI".
convert(29) should return "XXIX".
convert(44) should return "XLIV".
convert(45) should return "XLV"
convert(68) should return "LXVIII"
convert(83) should return "LXXXIII"
convert(97) should return "XCVII"
convert(99) should return "XCIX"
convert(500) should return "D"
convert(501) should return "DI"
convert(649) should return "DCXLIX"
convert(798) should return "DCCXCVIII"
convert(891) should return "DCCCXCI"
convert(1000) should return "M"
convert(1004) should return "MIV"
convert(1006) should return "MVI"
convert(1023) should return "MXXIII"
convert(2014) should return "MMXIV"
convert(3999) should return "MMMCMXCIX"


function convert(num) {
 console.log(num);
  var numberArray = num.toString().split('');
  //console.log(numberArray);
  var romanArray = [];

  //looking to see if needs to convert any thousands = M
  if(typeof numberArray[numberArray.length-4] !== 'undefined') {
    // then thousands place does exist in number
    //var thousands=numberArray[numberArray.length-4];
    //console.log('thousands: '+thousands);
    for (i=0;i<numberArray[numberArray.length-4];i++) {
      //console.log('push M, please');
      romanArray.push('M');
      //console.log('romanArray: '+romanArray);
    }
}

    //hundreds = c; 500 = D; 900 = CM
  if(typeof numberArray[numberArray.length-3] !== 'undefined') {
    //need to think about this further...
      //this checks if 9 and returns 'CM' without going further
    var hundreds = numberArray[numberArray.length-3];  
    //console.log('hundreds= '+hundreds);
    if (hundreds == 9) {
        romanArray.push('CM');
      hundreds=0;
      //console.log('detected 900');
      }
    if (hundreds == 4) {
        romanArray.push('CD');
      hundreds=0;
      //console.log('detected 900');
      }
      if (hundreds >= 5 && hundreds < 9) {
      //  console.log('detected 500<x<900');
        romanArray.push('D');
        hundreds = hundreds - 5;
      }
    for (i=0;i<hundreds;i++) {
      romanArray.push('C');
    }
}

  //Tens place
    if(typeof numberArray[numberArray.length-2] !== 'undefined') {
    //need to think about this further...
      //this checks if 9 and returns 'CM' without going further
    var tens = numberArray[numberArray.length-2];  
    //console.log('tens= '+tens);
    if (tens == 9) {
        romanArray.push('XC');
      tens=0;
      //console.log('detected 90');
      }
      if (tens == 4) {
        romanArray.push('XL');
      tens=0;
      //console.log('detected 90');
      }
      if (tens >= 5 && tens < 9) {
      //  console.log('detected 50<x<90');
        romanArray.push('L');
        tens = tens - 5;
      }
    for (i=0;i<tens;i++) {
      romanArray.push('X');
    }
}

  
  //Ones
      if(typeof numberArray[numberArray.length-1] !== 'undefined') {
    //need to think about this further...
      //this checks if 9 and returns 'CM' without going further
    var ones = numberArray[numberArray.length-1];  
    //console.log('ones= '+ones);
    if (ones == 9) {
        romanArray.push('IX');
      ones=0;
      //console.log('detected 90');
      }
            if (ones == 4) {
        romanArray.push('IV');
      ones=0;
      //console.log('detected 90');
      }
      if (ones >= 5 && ones < 9) {
      //  console.log('detected 50<x<90');
        romanArray.push('V');
        ones = ones - 5;
      }
    for (i=0;i<ones;i++) {
      romanArray.push('I');
    }
}
  console.log(romanArray.join(''));
  return romanArray.join('');
}

convert(3936);

**********
Bonfire: Sum All Numbers in a Range
We'll pass you an array of two numbers. Return the sum of those two numbers and all numbers between them.

The lowest number will not always come first.

Remember to use Read-Search-Ask if you get stuck. Try to pair program. Write your own code.

Here are some helpful links:

Math.max()
Math.min()
Array.reduce()
  
sumAll([1, 4]) should return a number.
sumAll([1, 4]) should return 10.
sumAll([4, 1]) should return 10.
sumAll([5, 10]) should return 45.
sumAll([10, 5]) should return 45.

//THIS EXERCISE IS REALLY UGLY, so maybe think about recoding sometime.

function sumAll(arr) {
  var total = 0;
  var one = arr[0];
  //console.log('arr[0]'+arr[0]);
  var two = arr[1];
  //console.log('arr[1]'+arr[1]);
  if (one < two) {
    for (i=one;i<=two;i++) {
      total = total + i;
  //    console.log(total);
    } }
  else {
    for (i=two;i<=one;i++) {
      total = total + i;
      console.log(total);
    } }
  
  
  //console.log('Done: '+total);
  return total;
}

sumAll([10, 5]);


******
Bonfire: Pig Latin
Translate the provided string to pig latin.

Pig Latin takes the first consonant (or consonant cluster) of an English word, moves it to the end of the word and suffixes an "ay".

If a word begins with a vowel you just add "way" to the end.

Remember to use Read-Search-Ask if you get stuck. Try to pair program. Write your own code.

Here are some helpful links:

Array.indexOf()
Array.push()
Array.join()
String.substr()
String.split()

translate("california") should return "aliforniacay".
translate("paragraphs") should return "aragraphspay".
translate("glove") should return "oveglay".
translate("algorithm") should return "algorithmway".
translate("eight") should return "eightway".

function translate(str) {
  var arr =str.split('');
  //console.log(arr);
  var shifted = [];
  while (arr[0] !=='a' && arr[0] !=='e' && arr[0] !=='i' && arr[0] !=='o' && arr[0] !=='u' && arr[0] !== 'undefined') {
  shifted=shifted+arr.shift();}//need first "consonant cluster" not single letter...
console.log(shifted);
  //if (shifted == 'a'| shifted=='e'| shifted=='i'|shifted=='o'|shifted=='u') {
  if (shifted.length<1) {
   // console.log(shifted);
   // console.log(arr);
  //arr.unshift(shifted);
  arr.push('way');
}
  else {
    arr.push(shifted+'ay');
  }
  return arr.join('');
}

translate("eight");


***********
Bonfire: Where do I belong
Return the lowest index at which a value (second argument) should be inserted into an array (first argument) once it has been sorted.

For example, where([1,2,3,4], 1.5) should return 1 because it is greater than 1 (index 0), but less than 2 (index 1).

Likewise, where([20,3,5], 19) should return 2 because once the array has been sorted it will look like [3,5,20] and 19 is less than 20 (index 2) and greater than 5 (index 1).

Remember to use Read-Search-Ask if you get stuck. Write your own code.

Here are some helpful links:

Array.sort()

where([10, 20, 30, 40, 50], 35) should return 3.
where([10, 20, 30, 40, 50], 30) should return 2.
where([40, 60], 50) should return 1.
where([3, 10, 5], 3) should return 0.
where([5, 3, 20, 3], 5) should return 2.
where([2, 20, 10], 19) should return 2.
where([2, 5, 10], 15) should return 3.

function where(arr, num) {
  // Find my place in this sorted array.
  arr.sort();
  var answer = 0;
  for (i=0;i<arr.length;i++) {
    if (arr[i]<num) {answer++;}
  }
  return answer;
}

where([50, 20, 30, 40, 10], 35);


***********
Bonfire: Seek and Destroy
You will be provided with an initial array (the first argument in the destroyer function), followed by one or more arguments. Remove all elements from the initial array that are of the same value as these arguments.

Remember to use Read-Search-Ask if you get stuck. Write your own code.

Here are some helpful links:

Arguments object
Array.filter()
  Run tests (ctrl + enter)

destroyer([1, 2, 3, 1, 2, 3], 2, 3) should return [1, 1].
destroyer([1, 2, 3, 5, 1, 2, 3], 2, 3) should return [1, 5, 1].
destroyer([3, 5, 1, 2, 2], 2, 3, 5) should return [1].
destroyer([2, 3, 2, 3], 2, 3) should return [].
destroyer(["tree", "hamburger", 53], "tree", 53) should return ["hamburger"].

var asdf = 666;

function takeAway(valu) {
  //console.log(arrToWorkWith);
  //console.log("asdf in takeAway(): "+asdf);
  //console.log("valu: "+valu);
  //console.log(valu!==asdf);
  return valu !== asdf;
}

function destroyer(arr) {
  // Remove all the values
console.log("This is the original array: "+arguments[0]);
  qwer=arguments[0];
for(i = arguments.length-1;i>0; i--) {
  console.log("This is the argument to remove: "+arguments[i]);
  //console.log("Old asdf: "+asdf);
  asdf = arguments[i];
  //console.log("New asdf: "+asdf);
  //console.log(qwer);
  qwer=qwer.filter(takeAway);
  console.log(qwer);
  }
  
  return qwer;
}

destroyer([1, 2, 3, 1, 2, 3], 2, 3);



*******
Bonfire: Return Largest Numbers in Arrays
Return an array consisting of the largest number from each provided sub-array. For simplicity, the provided array will contain exactly 4 sub-arrays.

Remember, you can iterate through an array with a simple for loop, and access each member with array syntax arr[i] .

Remember to use Read-Search-Ask if you get stuck. Write your own code.

Here are some helpful links:

Comparison Operators
  Run tests (ctrl + enter)

largestOfFour([[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]]) should return an array.
largestOfFour([[13, 27, 18, 26], [4, 5, 1, 3], [32, 35, 37, 39], [1000, 1001, 857, 1]]) should return [27,5,39,1001].
largestOfFour([[4, 9, 1, 3], [13, 35, 18, 26], [32, 35, 97, 39], [1000000, 1001, 857, 1]]) should return [9, 35, 97, 1000000].

function largestOfFour(arr) {
  // You can do this!
  var maxArray = [];
  for (i=0;i<arr.length;i++) {
    //console.log(arr[i]);
    var maxi=0; //I think this is unused, per maxArray[i]=maxj
//    console.log(arr[i][1]);
      var maxj=0;

    for (j=0;j<arr[i].length;j++) {
      console.log(arr[i][j]);
      if (arr[i][j]>maxj) {maxj=arr[i][j];}
    }
    //if (arr[i][1]>maxi) {maxi=arr[i][1];}
    //console.log(maxi);
    maxArray[i]=maxj;
  }
  return maxArray;
}

largestOfFour([[4, 9, 1, 3], [13, 35, 18, 26], [32, 35, 97, 39], [1000000, 1001, 857, 1]]);



**************
Bonfire: Confirm the Ending
Check if a string (first argument) ends with the given target string (second argument).

Remember to use Read-Search-Ask if you get stuck. Write your own code.

Here are some helpful links:

String.substr()
  Run tests (ctrl + enter)

end("Bastian", "n") should return true.
end("Connor", "n") should return false.
end("Walking on water and developing software from a specification are easy if both are frozen", "specification") should return false.
end("He has to give me a new name", "name") should return true.
end("He has to give me a new name", "me") should return true.
end("He has to give me a new name", "na") should return false.
end("If you want to save our world, you must hurry. We dont know how much longer we can withstand the nothing", "mountain") should return false.

function end(str, target) {
  // "Never give up and good luck will find you."
  // -- Falcor
  var lastChar = str.substring(str.length-target.length,str.length);
console.log(lastChar);
  
  if (lastChar ==target)
    {return true;}
  else {return false;}
}

end("He has to give me a new name", "name") ;


**********
Bonfire: Slasher Flick
Return the remaining elements of an array after chopping off n elements from the head.

The head meaning the beginning of the array, or the zeroth index

Remember to use Read-Search-Ask if you get stuck. Write your own code.

Here are some helpful links:

Array.slice()
Array.splice()
  Run tests (ctrl + enter)

slasher([1, 2, 3], 2) should return [3].
slasher([1, 2, 3], 0) should return [1, 2, 3].
slasher([1, 2, 3], 9) should return [].
slasher([1, 2, 3], 4) should return [].

function slasher(arr, howMany) {
  // it doesn't always pay to be first
  for (i=0;i<howMany;i++)
  {arr.shift();}
  return arr;
}

slasher([1, 2, 3], 2);



********
Bonfire: Mutations
Return true if the string in the first element of the array contains all of the letters of the string in the second element of the array.

For example, ["hello", "Hello"], should return true because all of the letters in the second string are present in the first, ignoring case.

The arguments ["hello", "hey"] should return false because the string "hello" does not contain a "y".

Lastly, ["Alien", "line"], should return true because all of the letters in "line" are present in "Alien".

Remember to use Read-Search-Ask if you get stuck. Write your own code.

Here are some helpful links:

String.indexOf()
  Run tests (ctrl + enter)

mutation(["hello", "hey"]) should return false.
mutation(["hello", "Hello"]) should return true.
mutation(["zyxwvutsrqponmlkjihgfedcba", "qrstu"]) should return true.
mutation(["Mary", "Army"]) should return true.
mutation(["Mary", "Aarmy"]) should return true.
mutation(["Alien", "line"]) should return true.
mutation(["floor", "for"]) should return true.
mutation(["hello", "neo"]) should return false.

function mutation(arr) {
  //console.log(arr[1].toLowerCase().split('') );
  var lettersArr1 = arr[1].toLowerCase().split('');
  for (i=0;i<lettersArr1.length;i++) {
    console.log(arr[0].indexOf(lettersArr1[i]));
    if (arr[0].toLowerCase().indexOf(lettersArr1[i]) == -1) {return false;}
  }
  console.log("end of word");
  return true;
}

mutation(["hello", "ly"]);

/* Cheating, code found as way of checking in array

function isBiggerThan10(element, index, array) {
  return element > 10;
}
[12, 5, 8, 1, 4].some(isBiggerThan10);  // true
*/


*******
Bonfire: Falsy Bouncer
Remove all falsy values from an array.

Falsy values in javascript are false, null, 0, "", undefined, and NaN.

Remember to use Read-Search-Ask if you get stuck. Write your own code.

Here are some helpful links:

Boolean Objects
Array.filter()
  Run tests (ctrl + enter)

bouncer([7, "ate", "", false, 9]) should return [7, "ate", 9].
bouncer(["a", "b", "c"]) should return ["a", "b", "c"].
bouncer([false, null, 0, NaN, undefined, ""]) should return [].

function isFalsey(value) {
  return Boolean(value) === true ;
}

function bouncer(arr) {
  // Don't show a false ID to this bouncer.
  var filtered = arr.filter(isFalsey);
  return filtered;
}

console.log([false,0].filter(isFalsey));
bouncer([7, "ate", "", false, 9]);
//bouncer([false, null, 0, NaN, undefined, ""]);


********
