# Lecture 6 - Array Operations - Imperative vs Declarative and Lecture 

এই দুই লেকচারে আমরা আজ অ্যারে এবং অবজেক্ট নিয়ে বিশদ আলোচনা করবো। যেহেতু এই দুই লেকচার একটার সাথে একটা রিলেটেড তাই আমার কাছে দুইটা লেকচারের ওভারভিউ একসাথে লেখাটা যুক্তিযুক্ত বলে মনে হয়েছে। আমাদের আজকের এজেন্ডা হলো-

## Table of Contents

- [Array Operations](#array-operations)

  - [Imperative traverse](#imperative-traverse)
  - [Declarative traverse](#declarative-traverse)
  - [Update](#update)
  - [Delete](#delete)
  - [Mutation](#mutation)
  - [Map](#map)
  - [Filter](#filter)
  - [Reduce](#reduce)

- [Object Deep Drive](#object-deep-dive)

  - [Object Operations](#object-operations)
  - [Function vs Method](#function-vs-method)

- [Object as a Data Structure](#object-as-a-data-structure)

  - [Array](#array)
  - [Object Over Array](#object-over-array)
  - [Comparison of object and array operation costs](#comparison-of-object-and-array-operation-costs)

## Array Operations

### Imperative Traverse

আমাদেরকে যদি বলা হয় একটা অ্যারে ট্রাভার্স করার জন্য, আমরা খুব সহজেই একটা লুপ চালিয়ে ট্রাভার্স করে ফেলতে পারি। এখন প্রশ্ন আসতে পারে ট্রাভার্স কি। ট্রাভার্স হলো ধরুন আমরা একটা অ্যারের প্রতিটা ইলেমেন্ট যেমন লুপ চালিয়ে টাচ করে যে অপারেশন করা দরকার করতে পারি এটাকেই বলে ট্রাভার্স। যেমনঃ

```js
const numbers = [2, 5, 6, 7, 89, 100];

for (let i = 0; i < numbers.length; i++) {
	console.log(numbers[i]);
}
```

আমরা সব ইলেমেন্ট প্রিন্ট করে ফেলতে পারি এভাবে `numbers` অ্যারের। আমরা যদি চাই প্রতিটা ইলেমেন্ট ২ দ্বারা গুণ করে সেই আউটপুট দেখাবো সেটাও পারবো।

```js
const numbers = [2, 5, 6, 7, 89, 100];

for (let i = 0; i < numbers.length; i++) {
	console.log(numbers[i] * 2);
}
```

এবার যদি আমরা চাই সব ইলেমেন্টের যোগফল বের করবো তাও পারবো।

```js
const numbers = [2, 5, 6, 7, 89, 100];

let sum = 0;
for (let i = 0; i < numbers.length; i++) {
	sum += numbers[i];
}

console.log(sum);
```

একে বলে Imperative Traversing। কারণ আমরা কোথা থেকে লুপ শুরু হবে তা বলে দিয়েছি, কোথায় গিয়ে থামবে তাও বলে দিয়েছি, এমনকি কিভাবে ইনক্রিমেন্ট হবে তাও বলে দিয়েছি। এরপর অপারেশন কি হবে সেটাও বলে দিয়েছি। তাই এটা একটা Imperative Traversing।

### Declarative Traverse

সাধারণত আমাদের ফর লুপ চালিয়ে জাভাস্ক্রিপ্টে কাজ করতে হয় না। যেহেতু জাভাস্ক্রিপ্ট একটা হাই লেভেল ল্যাঙ্গুয়েজ সেহেতু এর বিভিন্ন মেথড আছে, যেগুলো ব্যবহার করে আমরা ডিক্লারেটিভ ওয়েতে ট্রাভার্স করতে পারি। ফাংশন এবং মেথড কি এগুলো আমরা পরবর্তীতে জানবো। আমরা যেভাবে ইম্পারেটিভ ট্রাভার্স করেছিলাম সেভাবে যদি ডিক্লারেটিভ ওয়েতে করতে যায় তাহলে একটা সুন্দর মেথড আছে যার নাম `forEach`। আমরা একটু এই মেথড বুঝার চেষ্টা করি।

```js
const numbers = [2, 5, 6, 7, 89, 100];

numbers.forEach(function () {
	console.log('Hello World');
});
```

এখন এই প্রোগ্রাম রান করালে দেখা যাবে যে ছয়বার `Hello World` প্রিন্ট হবে। কেন ছয়বার কারণ `numbers` এর ইলেমেন্ট আছে ছয়টা। `forEach` এর কাজই হলো যতটা ইলেমেন্ট ততবার লুপ চলবে। `forEach` এর মধ্যে আর্গুমেন্ট আকারে একটা কলব্যাক ফাংশন পাস করবে। আমরা চাইলে ফাংশনটা `forEach` এর মধ্যে না লিখে বাইরে লিখে সেই ফাংশনের নামটাও পাস করে দিতে পারি। এখন ভিতরের ফাংশনটা কিন্তু আমরা কোথাও কল করিনি। তাহলে কিভাবে তা কল হলো? আমাদের জন্য `forEach` সেই ফাংশনটা কল করে রেখেছে কোনো না কোনোভাবে। এই কলব্যাক ফাংশনের মধ্যে প্যারামিটার আকারে কিছু না কিছু আছে। সেগুলো সব `arguments` নামক একটা ডাটা স্ট্রাকচারে স্টোর করা আছে। এটা অনেকটা অ্যারের মতো কাজ করে, কিন্তু অ্যারে না, এটা একটা ডিফারেন্ট টাইপের একটা ডাটা স্ট্রাকচার। একটা উদাহরণ দিলে সুন্দরভাবে বুঝা যাবে ব্যাপারটা।

```js
const numbers = [2, 5, 6, 7, 89, 100];

numbers.forEach(function () {
	console.log(arguments);
});

/* * Output
[Arguments] { '0': 2, '1': 0, '2': [ 2, 5, 6, 7, 89, 100 ] }
[Arguments] { '0': 5, '1': 1, '2': [ 2, 5, 6, 7, 89, 100 ] }
[Arguments] { '0': 6, '1': 2, '2': [ 2, 5, 6, 7, 89, 100 ] }
[Arguments] { '0': 7, '1': 3, '2': [ 2, 5, 6, 7, 89, 100 ] }
[Arguments] { '0': 89, '1': 4, '2': [ 2, 5, 6, 7, 89, 100 ] }
[Arguments] { '0': 100, '1': 5, '2': [ 2, 5, 6, 7, 89, 100 ] }
*/
```

আউটপুট থেকে দেখা যাচ্ছে অবজেক্টের মধ্যে '0' এর মধ্যে আছে আমাদের অ্যারের প্রতিটা ভ্যালু, '1' এর মধ্যে আছে সেই সংশ্লিষ্ট ভ্যালুর ইনডেক্স নাম্বার এবং '2' এর মধ্যে আছে পুরো অ্যারে। তাহলে আমরা বুঝতে পারলাম, `forEach` এর মধ্যে আর্গুমেন্ট আকারে যে ফাংশনটা আছে তার ভিতর তিনটা প্যারামিটার আছে। যদি একটু আমরা চেক করে দেখি,

```js
const numbers = [2, 5, 6, 7, 89, 100];

numbers.forEach(function (value, index, array) {
	console.log(value, index, array);
});

/* * Output
2 0 [ 2, 5, 6, 7, 89, 100 ]
5 1 [ 2, 5, 6, 7, 89, 100 ]
6 2 [ 2, 5, 6, 7, 89, 100 ]
7 3 [ 2, 5, 6, 7, 89, 100 ]
89 4 [ 2, 5, 6, 7, 89, 100 ]
100 5 [ 2, 5, 6, 7, 89, 100 ]
*/
```

দেখা যাচ্ছে আমরা যে আউটপুট পেয়েছিলাম আর্গুমেন্টস এর বেলায় ঠিক সেই আউটপুটই পেয়েছি। `arguments` অনেক কাজের। আপনি যখন কোনো লাইব্রেরি বা ফ্রেমওয়ার্ক নিয়ে কাজ করবেন তখন যদি কোনো মেথডের আর্গুমেন্ট জানার প্রয়োজন হয় সহজেই তা বের করে নিতে পারবেন।

এবার আসি আবার `forEach` এর কথায়। এটা দিয়ে ফর লুপের যাবতীয় যা যা কাজ আমরা করি সবই করতে পারি। এবার আমরা ফর লুপ দিয়ে যোগফলের যে কাজটি করেছিলাম সেটা একটু `forEach` দিয়ে করে দেখি।

```js
const numbers = [2, 5, 6, 7, 89, 100];

let sum = 0;
numbers.forEach(function (value) {
	sum += value;
});
console.log(sum); // 209
```

একই রেজাল্ট পাবো আমরা। এখানে একটা কথা বলে রাখা দরকার, যদি আমাদের `value` ছাড়া আর কিছু না লাগে তবে ফাংশন প্যারামিটার হিসেবে শুধু `value` নিলেই হবে। কিন্তু আমার যদি শুধু `array` দরকার হয় তবে অবশ্যই `value, index, array` এভাবে লিখতে হবে। নাহয় প্রোগ্রাম ভুল আউটপুট দেখাবে। এবার যদি চাই আমরা শুধু জোড় ইলেমেন্টগুলো প্রিন্ট করবো সেটাও পারবো।

```js
const numbers = [2, 5, 6, 7, 89, 100];

numbers.forEach(function (value) {
	if (value % 2 === 0) {
		console.log(value);
	}
});
```

এখানে `forEach` ফাংশন আমরা তৈরি করিনি। আমরা শুধু ব্যবহার করেছি। সুতরাং এটি একটি ডিক্লারেটিভ মেথড। এখন হয়তো অনেকেরই জানতে ইচ্ছা করছে `forEach` মেথডে কি এমন করা হয়েছে। যারা `forEach` সহ অ্যারে এবং অ্যারে মেথড সম্পর্কে জানতে আগ্রহী তারা স্ট্যাক লার্নারের এই [প্লেলিস্ট](https://youtube.com/playlist?list=PL_XxuZqN0xVDr08QgQHljCecWtA4jBLnS) দেখতে পারেন।

এখন আমি চাইছি যে শুধু প্রথম ৪টা ইলেমেন্টের যোগফল বের করবো। সেটার জন্য আমাদের কি করতে হবে তাহলে?

```js
const numbers = [2, 5, 6, 7, 89, 100];

let sum = 0;
numbers.forEach(function (value, index) {
	if (index <= 3) {
		sum += value;
	}
});
console.log(sum);
```

`forEach` মেথড মনে রাখার সহজ উপায় হলো, আমরা যে ফর লুপ লিখতাম সেটা আর লিখতে হবে না। সেটা `forEach` আমাদের জন্য করে দিয়েছে। শুধু আমাদের কাজ হচ্ছে যেটা আমরা লুপের বডিতে লিখতাম সেটা আমরা কলব্যাক ফাংশনের বডির মধ্যে লিখবো।

ধরি আমাদের একটা অ্যারে আছে নিচের মতো।

```js
const arr = [1, 2, 3, null, false, 4, 5, '', 'test', 6, 7];
```

এখন আমরা চাইছি এখান থেকে নাম্বার ছাড়া বাকি যা আছে সেগুলো বাদ দিয়ে শুধু নাম্বারগুলো ফিল্টার করে নিতে। সেটা আমরা ডিক্লারেটিভ ওয়েতে করতে চাইছি না। আমরা চাইছি ইম্পেরেটিভ ওয়েতে করতে। কিভাবে করতে পারি?

আমরা এভাবে শুরু করতে পারি।

```js
const arr = [1, 2, 3, null, false, 4, 5, '', 'test', 6, 7];

for (let i = 0; i < arr.length; i++) {
	if (typeof arr[i] !== 'number') {
		arr[i] = undefined;
	}
}

console.log(arr); // [1, 2, 3, undefined, undefined, 4, 5, undefined, undefined, 6, 7];
```

এখন এখানে সমস্যা হলো এই `undefined` গুলোকে কিভাবে আমরা বাদ দিবো। আমাদের অন্য ওয়েতে চিন্তা করতে হবে। আমরা এমন করতে পারি যে কোনো পজিশনে ইলেমেন্ট টাইপ যদি নাম্বার না হয় তাহলে আমরা পরবর্তী ভ্যালুকে অ্যাসাইন করে দিতে পারি। যদি আমরা স্টেপগুলো একটু দেখি তাহলে বোঝা যাবে।

```js
// step 1: [1, 2, 3, false, 4, 5, '', 'test', 6, 7, undefined]
// step 2: [1, 2, 3, 4, 5, '', 'test', 6, 7, undefined, undefined]
// step 3: [1, 2, 3, 4, 5, 'test', 6, 7, undefined, undefined, undefined]
// step 4: [1, 2, 3, 4, 5, 6, 7, undefined, undefined, undefined, undefined]
```

এবার আমাদের আইডিয়াকে আমরা একটু কোডে রূপান্তরিত করে দেখি।

```js
const arr = [1, 2, 3, null, false, 4, 5, '', 'test', 6, 7];

for (let i = 0; i < arr.length; i++) {
	for (let j = i; j < arr.length - 1; j++) {
		if (!arr[j] || typeof arr[j] !== 'number') {
			arr[j] = arr[j + 1];
			arr[j + 1] = undefined;
		}
	}
}

console.log(arr); // [1, 2, 3, 4, 5, 6, 7, undefined, undefined, undefined, undefined];
```

আমরা তাহলে আমাদের স্টেপ ৪ পেয়ে গেলাম। এবার এখান থেকে `undefined` বাদ দিয়ে দিতে হবে। সেটার জন্য আমরা একটা কাজ করতে পারি।

```js
const arr = [1, 2, 3, null, false, 4, 5, '', 'test', 6, 7];

count = 0;
for (let i = 0; i < arr.length; i++) {
	for (let j = i; j < arr.length - 1; j++) {
		if (!arr[j] || typeof arr[j] !== 'number') {
			arr[j] = arr[j + 1];
			arr[j + 1] = undefined;
		}
	}

	if (arr[i] == undefined) {
		count++;
	}
}
arr.length -= count;

console.log(arr); // [1, 2, 3, 4, 5, 6, 7];
```

আমরা করেছি কি? যদি ইলেমেন্ট আনডিফাইন্ড হয় তাহলে কাউন্ট করে সেটা `count` ভ্যারিয়েবলের মধ্যে রাখবে। শেষে আমরা `arr.length` থেকে `count` বিয়োগ করে অ্যারের সাইজ কমিয়ে দিলেই `undefined` সব বাদ পড়ে যাবে।

এবার একটু কোডটা এনালাইসিস করার চেষ্টা করি। আমরা ছোট একটা অ্যারে দিয়েই বুঝার চেষ্টা করি।

```txt
const arr = [1, false, true, '', 2, 3]
When i = 0:
  j = 0:
    arr[0] = 1, which is a number
  j = 1:
    arr[1] = false, which is not a number
    so, arr[1] = true
    arr[2] = undefined
  j = 2:
    arr[2] = undefined
    so arr[2] = ''
    arr[3] = undefined
  j = 3:
    arr[3] = undefined
    so arr[3] = 2
    arr[4] = undefined
  j = 4:
    arr[4] = undefined
    so arr[4] = 3
    arr[5] = undefined
  count = 1
After completion of first loop the array becomes like this [1, true, '', 2, 3, undefined]
After completion of loop the array looks like this [1, 2, 3, undefined, undefined, undefined] and count will be 3. After subtraction count from arr.length (6) we found 3. So the array of length 3 will become like this [1, 2, 3]
```

এখন যদি এই কাজটা ইম্পেরেটিভ ওয়েতে না করে ডিক্লারেটিভ ওয়েতে করতাম তাহলে অনেক সহজে করতে পারতাম।

```js
const arr = [1, 2, 3, null, false, 4, 5, '', 'test', 6, 7];

const filteredArray = arr.filter((val) => typeof val === 'number');
console.log(filteredArray);
```

কিন্তু এই জায়গায় একটা সমস্যা আছে। কারণ `filter` মেথড বিহাইন্ড দ্য সীন একটা এক্সট্রা মেমোরি ব্যবহার করে। আমরা যখন ফ্রন্টএন্ড ডেভেলপমেন্ট করি তখন সাধারণত এতো জটিল ইম্পেরেটিভ ওয়েতে করি না। আমরা যে বিল্ট-ইন মেথড আছে সেগুলো ব্যবহার করি। তাই দেখা যায় যে অনেক সময় ডাটা যখন অনেক বেশি হবে তখন অ্যাপ্লিকেশন হ্যাং হয়ে যায়। এখন আমরা কি সবসময় ইম্পেরেটিভ মেথডেই কাজ করবো? বা কখন বুঝবো আমাকে ইম্পেরেটিভ ওয়েতে করতে হবে, কখন ডিক্লারেটিভ ওয়েতে? প্রথম কথা হচ্ছে ৯০-৯৫% সময়ই আমাদের বিল্ট-ইন মেথড ইউজ করে কাজ হয়ে যাবে। কিন্তু কিছু কিছু ক্ষেত্রে আমাদের অ্যাপ্লিকেশনের কমপ্লেক্সিটি এতো বেশি হয় সেসব ক্ষেত্রে আমাদের বিল্ট-ইন মেথডের বাইরে গিয়ে কাজ করতে হতে পারে। ধরেন আমাদের অ্যারেতে এখন জাস্ট নাম্বার, স্ট্রিং এসব ডাটা আছে। কিন্তু যদি এমন হয় যে প্রতিটি ইলেমেন্ট এক একটা জায়ান্ট অবজেক্ট এবং প্রতিটা অবজেক্টের সাইজ প্রায় এক এমবি করে (যদিও এক এমবি ডাটা বানানো অনেক কঠিন, তাও বুঝার সুবিধার্থে উদাহরণ দিচ্ছি), এরকম যদি ১০০ টা অবজেক্ট থাকে তাহলে মোট অ্যারের সাইজ হবে ১০০ এমবি। এখন যদি এই ১০০ এমবি ডাটার অপারেশনের জন্য আমার আরো ১০০ এমবি মেমোরি খরচ হয় তাহলে সেটা অনেক সমস্যা। তাই এই ক্ষেত্রে আমাদের সম্পূর্ণ ইম্পেরেটিভ ওয়েতে গিয়ে কাজ করতে হবে। যদি আমাদের এখানে মেমোরি কনস্ট্রেইন না থাকতো তাহলে আমরা ইম্পেরেটিভ ওয়েতেও অনেক সহজে এই কাজটা করতে পারতাম।

```jsx
const arr = [1, 2, 3, null, false, 4, 5, '', 'test', 6, 7];

const newArr = [];
for (let i = 0; i < arr.length; i++) {
	if (typeof arr[i] === 'number') {
		newArr.push(arr[i]);
	}
}
console.log(newArr);
```

ফ্রন্টএন্ড অ্যাপ্লিকেশন বানানোর সময় আমাদের খেয়াল রাখতে হবে একজন ইউজার ৬৪ জিবি র‍্যামের পিসিও ইউজ করতে পারে, আবার ২ জিবি র‍্যামের পিসিও ইউজ করতে পারে। ব্যাকএন্ডে যতো ডাটা থাকবে তার জন্য সার্ভার কস্ট আমি বা আমার কোম্পানি বহন করছে। কিন্তু যখন ব্যাপার ফ্রন্টএন্ডের তখন সেটা পুরোপুরি ইউজার কেন্দ্রিক। আমি চাইবো আমার অ্যাপ্লিকেশন যেন ৬৪ জিবি র‍্যামের পিসি থেকেও ইউজ করার যায়, ২ জিবি র‍্যামের পিসি থেকেও ইউজ করা যায় আবার মোবাইল থেকেও যেন ইউজ করা যায়। তাই অনেক ছোট ছোট বিষয় খেয়াল রেখে ফ্রন্টএন্ড ডেভেলপমেন্ট করতে হয়। এখানেই ফ্রন্টএন্ড ডেভেলপমেন্টের চ্যালেঞ্জ।

### Update

আপডেটের ক্ষেত্রে ইম্পেরেটিভ ওয়েতে করার কোনো প্রয়োজন নেই। আপডেট অনেক সিম্পল। আমাদের যদি কোনো অ্যারের ইনডেক্স জানা থাকে তাহলে খুব সহজেই আমরা তার ডাটা আপডেট করে ফেলতে পারি। যেমন

```js
const arr = [1, 2, 3, 4, 5];

arr[3] = 300;

console.log(arr); // [1, 2, 3, 300, 5]
```

এখন যদি ইনডেক্স জানা না থাকে তাহলে প্রথমে আগে ইনডেক্স বের করে নিতে হবে। এরপর আপডেট করা যাবে। যেমন

```js
const arr = [
	{ id: 1, value: 10 },
	{ id: 2, value: 20 },
	{ id: 3, value: 30 },
	{ id: 4, value: 40 },
	{ id: 5, value: 50 },
];

const index = arr.findIndex((item) => item.id === 4);
arr[index].value = 400;

console.log(arr);

// [
//   { id: 1, value: 10 },
//   { id: 2, value: 20 },
//   { id: 3, value: 30 },
//   { id: 4, value: 400 },
//   { id: 5, value: 50 }
// ]
```

আবার ইনডেক্স বের না করেও আপডেট করা যায়। সেক্ষেত্রে আমাদের `find` মেথড ব্যবহার করতে হবে। যেমন

```js
const arr = [
	{ id: 1, value: 10 },
	{ id: 2, value: 20 },
	{ id: 3, value: 30 },
	{ id: 4, value: 40 },
	{ id: 5, value: 50 },
];

const obj = arr.find((val) => val.id === 4);
obj.value = 400;

console.log(obj); // { id: 4, value: 400 }
console.log(arr);

/* 
[
  { id: 1, value: 10 },
  { id: 2, value: 20 },
  { id: 3, value: 30 },
  { id: 4, value: 400 },
  { id: 5, value: 50 }
]
*/
```

এখানে দেখা যাচ্ছে আমি যদি `obj` এর ভ্যালু পরিবর্তন করি তাহলে `arr` এর ভ্যালুও পরিবর্তন হবে। কারণ হলো আমরা এখানে যেভাবে অ্যারে দেখতে পাচ্ছি আসলে তা সেরকম নাই। আমরা যতোই ডাটা রাখি অ্যারেতে জাস্ট অ্যারের মধ্যে কয়েকটা অ্যাড্রেস থাকে। ঐ ডাটাগুলোর অ্যড্রেস। মানে ঐ ডাটাগুলো যে অ্যাড্রেসে থাকে তা অ্যারে ভ্যারিয়েবলের মধ্যে জমা থাকে। আমরা যখন `obj` এর মধ্যে ফাইন্ড করছি তখন অ্যারের ঐ অ্যাড্রেসকে নিয়ে আসছি। তাই অ্যাড্রেস যেখানেই চেইঞ্জ করি না কেন তা অরিজিনাল অ্যারেতেও চেইঞ্জ হয়ে যাচ্ছে। এটা হচ্ছে মিউটেশন। আর `find` মেথড মিউটেবল।

এখন একটা উদাহরণ দেখি।

```js
const arr = [
	{ id: 1, value: 10 },
	{ id: 2, value: 20 },
	{ id: 3, value: 30 },
	{ id: 4, value: 40 },
	{ id: 5, value: 50 },
];

const obj = arr.find((val) => val.id === 4);
obj.value = 400;

console.log(arr[3] === obj); // true

const a = { a: 10 };
const b = { a: 10 };
const c = a;
console.log(a === c); // true
console.log(a === b); // false
```

যেকোনো বিগিনারের কাছে এটা পুরাই কনফিউশন সৃষ্টি করবে। যখন obj কিছু find করে নিয়ে আসে তখন আসলে অ্যারের রেফারেন্সটা নিয়ে আসে। তাই obj এবং `arr[3]` এর রেফারেন্স একই এজন্যই সেটা `true` আউটপুট দিয়েছে। একই ভাবে c আর a রেফারেন্স একই। তাই সেটা true দিয়েছে। কিন্তু a আর b এর রেফারেন্স সম্পূর্ণ আলাদা। দুইটা অবজেক্টে যতই সেইম ভ্যালু থাক, দুইটা অবেজক্টের রেফারেন্স কখনও এক হবে না। দুইটা বিল্ডিং দেখতে যতোই একই হোক, দুইটা বিল্ডিং এর অ্যাড্রেস কখনও একই হবে না। এক্ষেত্রেও তাই। এই কারণে শেষের কন্ডিশন false দিয়েছে।

### Delete

এবার আমরা অ্যারে থেকে কিভাবে কোনো ডাটা ডিলিট করতে হয় তা দেখবো। ইম্পেরেটিভ ওয়েতে কিভাবে ডাটা ডিলিট করতে হয় তা আমরা গেই দেখেছি অ্যারে ট্রাভার্সের উদাহরণে। এখানে আমরা দুইটা মেথড ইউজ করে ডিলিট করবো। `splice` and `filter`. এদের মধ্যে পার্থক্য হলো splice মেথড মিউটেবল এবং filter ইমমিউটেবল। কিভাবে আমরা একটু দেখি।

```js
const arr = [
	{ id: 1, value: 10 },
	{ id: 2, value: 20 },
	{ id: 3, value: 30 },
	{ id: 4, value: 40 },
	{ id: 5, value: 50 },
];

const index = arr.findIndex((item) => item.id === 4);
const arr1 = arr.splice(index, 1);

console.log(arr1); // [ { id: 4, value: 40 } ]
console.log(arr);
/* [
  { id: 1, value: 10 },
  { id: 2, value: 20 },
  { id: 3, value: 30 },
  { id: 5, value: 50 }
] */
```

এখানে দেখা যাচ্ছে splice মেথড সরাসরি অরিজিনাল অ্যারে থেকে ডাটা ডিলিট করে দিয়েছে। তার মানে এখানে মিউটেশন হয়েছে।

```js
const arr = [
	{ id: 1, value: 10 },
	{ id: 2, value: 20 },
	{ id: 3, value: 30 },
	{ id: 4, value: 40 },
	{ id: 5, value: 50 },
];

const arr2 = arr.filter((item) => item.id !== 4);

console.log(arr2);
/* 
[
  { id: 1, value: 10 },
  { id: 2, value: 20 },
  { id: 3, value: 30 },
  { id: 5, value: 50 }
]
*/
console.log(arr);
/* 
[
  { id: 1, value: 10 },
  { id: 2, value: 20 },
  { id: 3, value: 30 },
  { id: 4, value: 40 },
  { id: 5, value: 50 }
]
*/
```

এখানে অরিজিনাল অ্যারে যেমন ছিল তেমনই আছে। কিন্তু ফিল্টার করার পর ফিল্টার মেথড নতুন একটা অ্যারে দিয়েছে যেখানে যেটা ডিলিট করতে চেয়েছিলাম সেটা নেই। তার মানে দাঁড়ালো filter মেথড ইমমিউটেবল।

### Mutation

মিউটেশন নিয়ে অলরেডি আলোচনা হয়েছে। আশা করি ব্যাপারটা সবাই বুঝতে পেরেছেন।

### Map

ম্যাপ সাধারণত অরিজিনাল অ্যারের ক্লোন ভার্সন তৈরি করে। যদি অরিজিনাল অ্যারেতে ১০টা ডাটা থাকে তাহলে নতুন অ্যারেতেও ১০টা ডাটা থাকবে। এখন সে ডাটা একই হতে পারে বা ডিফারেন্ট হতে পারে। যেমন

```js
const numbers = [1, 2, 3, 4];
const strs = numbers.map((v) => v.toString());
console.log(strs);
```

সব নাম্বারের স্ট্রিং ভার্সন সে আউটপুট দিবে। একটা জিনিস মাথায় রাখতে হবে ম্যাপ করার পর অ্যারের লেংথের কোনো পরিবর্তন হবে না। শুধু ডাটা পরিবর্তন হবে। ডাটার সংখ্যা একই থাকবে।

### Filter

ফিল্টারের কাজ আমরা একটা অ্যারে থেকে যে যে ডাটা চাইছি তা ফিল্টার করে দেয়া। ধরেন আমাদের কাছে একটা অ্যারে আছে।

```js
const numbers = [1, 2, 3, 4, false, '', NaN, 5, 6];
```

আমরা চাইছি এখান থেকে সমস্ত falsy value বাদ দিয়ে শুধু truthy ভ্যালু নিবো। সেক্ষেত্রে ফিল্টার মেথড আমাদের ব্যবহার করতে হবে।

```js
const filteredArr = numbers.filter((v) => v);
console.log(filteredArr);
```

এক্ষেত্রে সকল truthy value রিটার্ন করে দিবে। কিন্তু এমন কিছু সিচুয়েশন আসবে যখন আমি truthy value চাইছি কিন্তু রিটার্ন করতে পারবো না সেক্ষেত্রে v এর আগে দুইটা !! বসিয়ে দিলেই truthy value পেয়ে যাবো।

### Reduce

আমরা একটু নিচের উদাহরণটা দেখি।

```js
const numbers = [1, 2, 3, 4, false, '', NaN, 5, 6];
const filteredArr = numbers.filter((v) => v);
const strs = filteredArr.map((v) => v.toString());
console.log(strs);
```

এক্ষেত্রে কিছু অসুবিধা আছে। যখন ফিল্টার হচ্ছে তখন n সংখ্যকবার সে ট্রাভার্স হচ্ছে। আবার যখন ম্যাপ হচ্ছে তখনও আবার ট্রাভার্স হচ্ছে। এতে করে টাইম কমপ্লেক্সিটি বেড়ে যাচ্ছে। এটা চেইন করেও করা যায়।

```js
const numbers = [1, 2, 3, 4, false, '', NaN, 5, 6];
const filteredArr = numbers.filter((v) => v).map((v) => v.toString());
console.log(strs);
```

এক্ষেত্রে টাইম কমপ্লেক্সিটি কিছুটা কমলেও পুরোপুরি এফিশিয়েন্ট না। সেজন্য আমাদের যেতে হবে reduce মেথডের কাছে।

ইউটিউবে আমরা যে সকল টিউটোরিয়াল দেখতে পাই তাতে reduce দিয়ে একটা কাজই ঘুরেফিরে করা হয়। সেটা হলো যোগ করা।

```jsx
const numbers = [1, 2, 3, 4, 5, 6];
const sum = numbers.reduce((a, b) => a + b);
console.log(sum);
```

কিন্তু reduce is way more powerful than summation. reduce এত পাওয়ারফুল যে তা কল্পনা করা যায় না। reduce ঠিকমতো বুঝলে ম্যাপ, ফিল্টার নিয়ে কাজ না করে reduce নিয়েই কাজ করে ফেলা যায়। ম্যাপ আমাদের রিটার্ন করে একই দৈর্ঘ্যের একটা নতুন অ্যারে। ফিল্টার ফিল্টারড ভ্যালুর অ্যারে রিটার্ন করে। এর দৈর্ঘ্য অরিজিনাল অ্যারের সমান হতেও পারে, নাও পারে। কিন্তু রিডিউস কি যে রিটার্ন করবে তা কেউ জানে না। শুধু আমরা জানবো। এখানে স্ট্রিং, নাম্বার, বুলিয়ান ইত্যাদি যেকোনো সম্ভাব্য ভ্যালুই এটা রিটার্ন করতে পারে।

আমরা একটু reduce এর স্ট্রাকচারটা দেখি

```js
numbers.reduce((acc, cur) => {
	return acc;
}, '');
```

প্রথম প্যারামিটার হিসেবে আমরা দিয়েছি acc (accumulator / previous value) এবং দ্বিতীয় ভ্যালু হিসেবে দিয়েছি cur (current value)। acc, cur এর পর আমরা চাইলে ইনডেক্স দিতে পারি, চাইলে পুরো অ্যারে দিতে পারি কিন্তু আমাদের সেটা দরকার নেই। reduce মেথডের সুবিধা হলো এখানে আমরা একটা ইনিশিয়াল ভ্যালু প্রোভাইড করতে পারি। '' এর জায়গায় খালি অবজেক্ট {}, খালি অ্যারে [], শূন্য যেকোনো কিছু বসাতে পারি। সেটা আমরা কি চাইছি তার উপর নির্ভর করবে। এর মানে হলো বর্তমানে acc এর ভ্যালু ঐ ইনিশিয়ালাইজার হিসেবে যেটা দিবো সেটা। দিন শেষে আমরা আমাদের acc কে রিটার্ন করবো। যাই করি না কেন আমরা reduce মেথডে acc কেই রিটার্ন করবো। এখন আমরা চাইছি `const numbers = [1, 2, 3, 4, false, '', NaN, 5, 6];` এটা থেকে আমরা `1234falseNaN56` রিটার্ন করতে। সেটা করতে আমরা reduce মেথডের সাহায্য নিবো।

```js
const numbers = [1, 2, 3, 4, false, '', NaN, 5, 6];
const result = numbers.reduce((acc, cur) => {
	acc += cur.toString();
	return acc;
}, '');

console.log(result); // 1234falseNaN56
```

আমরা করেছি কি এখানে? acc এর ভ্যালু আমরা ধরে নিয়েছি ''। এরপর ওটার সাথে cur এর toString যোগ করে দিয়েছি। এবং আমাদের রেজাল্টটাকে আমরা একটা ভ্যারিয়েবলের মধ্যে রেখেছি। এরপর যখন আউটপুট দিলো দেখা গেলো আমরা যেটা চাইছি সেটাই পেয়ে গেছি।

এখন আমরা চাইছি এই অ্যারে থেকে শুধু truthy values নিবো। কোনো falsy ভ্যালু নিবো না। সেক্ষেত্রে আমরা একটা কন্ডিশন বসিয়ে দিতে পারি।

```js
const numbers = [1, 2, 3, 4, false, '', NaN, 5, 6];
const result = numbers.reduce((acc, cur) => {
	if (cur) {
		acc += cur.toString();
	}
	return acc;
}, '');

console.log(result); // 123456
```

আমরা যদি চাই প্রতিটার শেষে কমা (,) যোগ করবো সেটাও করতে পারি।

```js
const numbers = [1, 2, 3, 4, false, '', NaN, 5, 6];
const result = numbers.reduce((acc, cur, index) => {
	if (cur) {
		acc += cur.toString() + (index < numbers.length - 1 ? ', ' : '');
	}
	return acc;
}, '');

console.log(result); // 1, 2, 3, 4, 5, 6
```

আমরা চাইলে অ্যারের একটা শেইপও দিতে পারি। যেমন

```js
const numbers = [1, 2, 3, 4, false, '', NaN, 5, 6];
const result = numbers.reduce((acc, cur, i) => {
	if (i === 0) {
		acc += '[';
	}
	if (cur) {
		acc += cur.toString() + (i < numbers.length - 1 ? ', ' : '');
	}
	if (i === numbers.length - 1) {
		acc += ']';
	}
	return acc;
}, '');
console.log(result); // [1, 2, 3, 4, 5, 6]
```

তাহলে আমরা reduce এর পাওয়ারটা বুঝতে পারছি কিছুটা। এটা গেলো এক ধরণের পাওয়ার। আরো অনেক পাওয়ার আছে reduce মেথডের। যেমন এখন আমরা acc স্ট্রিং হিসেবে চাইছি না। আমরা চাইছি সকল truthy ভ্যালুর একটা অ্যারে। সেটাও reduce দিয়ে করা যায়।

```js
const numbers = [1, 2, 3, 4, false, '', NaN, 5, 6];
const result = numbers.reduce((acc, cur) => {
	if (cur) {
		acc.push(cur.toString());
	}
	return acc;
}, []);
console.log(result); // [ '1', '2', '3', '4', '5', '6' ]
```

এখানে আমরা acc হিসেবে একটা ফাঁকা অ্যারে নিয়েছি। এরপর একটা কন্ডিশন লিখেছি truthy ভ্যালু পাওয়ার জন্য। তারপর সেই কন্ডিশন যে সকল ভ্যালুর পূরণ করবে তাদের toString ভার্সন আমরা acc এর মধ্যে push করে দিবো যেহেতু acc একটা অ্যারে। আমরা একই রেজাল্ট পাচ্ছি আরো বেটার সল্যুশনের মাধ্যমে।

আমরা একটু map/filter অপারেশনের সাথে reduce অপারেশনের টাইম কমপ্লেক্সিটি তুলনা করে দেখি।

```js
const arr = [];
for (let i = 1; i < 5000000; i++) {
	arr.push(i);
}

console.time('not-optimized');
arr.filter((item) => item % 2 === 0).map((item) => item * 2);
console.timeEnd('not-optimized'); // not-optimized: 325.853ms

console.time('optimized');
arr.reduce((acc, cur) => {
	if (cur % 2 === 0) {
		acc.push(cur * 2);
	}
	return acc;
}, []);
console.timeEnd('optimized'); // optimized: 198.256ms
```

তাহলে দেখা যাচ্ছে reduce method অনেক অপটিমাইজড। এবার আমরা একটু reduce মেথডের ইমপ্লিমেন্টেশনটা দেখি। আমরা আমদের reduce ফুঞ্চতিওন বানিয়ে ফেলতে পারি। যেহেতু আমরা প্রোটোটাইপ নিয়ে আলোচনা করিনি তাই মেথড বানাবো না। আমরা জাস্ট একটা ফাংশন বানাবো।

```js
// implement 1
function myReduce(arr, cb, init) {
  let acc = init;
  for (let i = 0; i < arr.length; i++) {
    acc = cb(acc, arr[i], i, arr);
  }
  return acc
} 
```

এটাই আমাদের reduce ফাংশন। এখানে কি করেছি একটু ব্যাখ্যা করা যাক। আমরা তিনটা প্যারামিটার নিয়েছি। প্রথম প্যারামিটার হিসেবে থাকবে একটা অ্যারে। দ্বিতীয় প্যারামিটার হিসেবে থাকবে একটা কলব্যাক ফাংশন। আর তৃতীয় প্যারামিটার হিসেবে থাকবে আমাদের ইনিশিয়ালাজার। আমরা যে ইনিশিয়ালাইজার ব্যবহার করেছিলাম reduce মেথডে সেটা। এখন আমরা আমাদের acc হিসেবে init নিয়ে নিলাম। এরপর লুপ চালালাম। লুপের মধ্যে acc আপডেট হচ্ছে কলব্যাক ফাংশন অনুযায়ী। সেই কলব্যাক ফাংশনের প্যারামিটার হিসেবে থাকছে acc, অ্যারের ইলেমেন্ট, ইনডেক্স আর আমাদের অ্যারে। আর এই ফাংশন রিটার্ন করবে আমাদের acc। এবার একটু আমাদের ফাংশনটা টেস্ট করে দেখি।

```js
const sum = myReduce(
  nums,
  (acc, cur) => {
    return acc + cur;
  }, 0);
console.log(res);

const arr = [1, 2, '', false, 3, NaN, false, 4, 5, NaN, 6];
const result = myReduce(
	arr,
	(acc, cur) => {
		if (cur) {
			acc.push(cur ** 2);
		}
		return acc;
	},
	[]
);
console.log(result); // [1, 4, 9, 16, 25, 36]
```

How amazing is this! জাভাস্ক্রিপ্টের যতোই গভীরে যাবেন এর মজাটা ততোই পাবেন। আমরা আমাদের reduce ফাংশন বানিয়ে সেটা নিয়ে কাজও করে ফেললাম। আর এটাও জানলাম behind the scene reduce মেথড কিভাবে কাজ করে।

implementation 2

```js
const box = {
  reduce(callback, init) {
    let arr = Object.entries(box);
    arr = arr[arr.length - 1][1];

    let acc = init;
    for (let i = 0; i < arr.length; i++) {
      acc = callback(acc, arr[i], i, arr);
    }
    return acc;
  },
};

box.nums = [1, 2, 3, 4, 5, 6];
const sum = box.reduce((acc, cur) => acc + cur, 0);
console.log(sum); // 21

box.list = [1, 2, "", false, 3, NaN, false, 4, 5, NaN, 6];;
const res = box.reduce((acc, cur) => {
  if (cur) {
    acc.push(cur);
  }
  return acc;
}, []);

console.log(res); // [1, 2, 3, 4, 5, 6]
```

আমরা আরেকটা উদাহরণ দেখি reduce এর। তার জন্য আমাদের axios প্যাকেজটা ইনস্টল করে নেয়া লাগবে। আমরা ইনস্টল করে নিলাম। এখন আমরা [json placeholder](https://jsonplaceholder.typicode.com/posts) এই সাইটে ঢুকলে কিছু ডামী ডাটা পাবো পোস্টের। খেয়াল করলে দেখবো এই ডাটা দেয়া আছে অ্যারে হিসেবে। কিন্তু আমার ট্রাভার্সের চেয়ে গুরুত্বপূর্ণ হলো আপডেট ও ডিলিট করা। ব্যাকএন্ড ডেভেলপার তার সুবিধামতো অ্যারেতে দিয়ে দিলেও আমাদের নিজেদের প্রয়োজনে তা অবজেক্টে রূপান্তরিত করে নেয়া লাগবে। এখানে আমাদের body প্রোপার্টিজ প্রয়োজন নেই। আমাদের দরকার userId, id ও title। আর আমার এতো ডাটার প্রয়োজন নেই আমাদের প্রথম ১০টা ডাটা হলেই হয়ে যাবে। চলুন দেখি।

```js
const axios = require('axios').default;
const url = 'https://jsonplaceholder.typicode.com/posts';

async function getData() {
	const { data } = await axios.get(url);
	const result = data.slice(0, 10).map((item) => {
		return {
			userId: item.userId,
			id: item.id,
			title: item.title,
		};
	});
	return result;
}

getData()
	.then((data) => console.log(data))
	.catch((e) => console.log(e));

/* 
[
	{
		userId: 1,
		id: 1,
		title:
			'sunt aut facere repellat provident occaecati excepturi optio reprehenderit',
	},
	{ userId: 1, id: 2, title: 'qui est esse' },
	{
		userId: 1,
		id: 3,
		title: 'ea molestias quasi exercitationem repellat qui ipsa sit aut',
	},
	{ userId: 1, id: 4, title: 'eum et est occaecati' },
	{ userId: 1, id: 5, title: 'nesciunt quas odio' },
	{ userId: 1, id: 6, title: 'dolorem eum magni eos aperiam quia' },
	{ userId: 1, id: 7, title: 'magnam facilis autem' },
	{ userId: 1, id: 8, title: 'dolorem dolore est ipsam' },
	{
		userId: 1,
		id: 9,
		title: 'nesciunt iure omnis dolorem tempora et accusantium',
	},
	{ userId: 1, id: 10, title: 'optio molestias id quia eum' },
];
*/
```

আমরা map ব্যবহার করে প্রথম ১০টি ডাটা পেয়ে গেলাম। এবং বডিও আমরা বাদ দিয়ে দিলাম। কিন্তু এখনও এটা অ্যারে রিটার্ন করছে। map করলে কখনও আমরা অবজেক্ট রিটার্ন করতে পারবো না। কারণ map সবসময় অ্যারেই রিটার্ন করে। এবার আমরা একটু reduce নিয়ে কাজ করি। কারণ reduce এ আমরা কি টাইপের ডাটা চাই তা ইনিশিয়ালাইজের মাধ্যমে দিয়ে দিতে পারি।

```js
const axios = require('axios').default;
const url = 'https://jsonplaceholder.typicode.com/posts';

async function getData() {
	const { data } = await axios.get(url);
	const result = data.slice(0, 10).reduce((acc, cur) => {
		acc[cur.id] = {
			...cur,
		};
		delete acc[cur.id].body;
		return acc;
	}, {});
	return result;
}

getData()
	.then((data) => console.log(data))
	.catch((e) => console.log(e));

/* 
{
  '1': {
    userId: 1,
    id: 1,
    title: 'sunt aut facere repellat provident occaecati excepturi optio reprehenderit'
  },
  '2': { userId: 1, id: 2, title: 'qui est esse' },
  '3': {
    userId: 1,
    id: 3,
    title: 'ea molestias quasi exercitationem repellat qui ipsa sit aut'
  },
  '4': { userId: 1, id: 4, title: 'eum et est occaecati' },
  '5': { userId: 1, id: 5, title: 'nesciunt quas odio' },
  '6': { userId: 1, id: 6, title: 'dolorem eum magni eos aperiam quia' },
  '7': { userId: 1, id: 7, title: 'magnam facilis autem' },
  '8': { userId: 1, id: 8, title: 'dolorem dolore est ipsam' },
  '9': {
    userId: 1,
    id: 9,
    title: 'nesciunt iure omnis dolorem tempora et accusantium'
  },
  '10': { userId: 1, id: 10, title: 'optio molestias id quia eum' }
}
*/
```

আমরা এখানে acc হিসেবে নিয়েছি একটা ফাঁকা অবজেক্ট ({})। সেই অবজেক্টের কী হিসেবে থাকবে current ভ্যালুর আইডি। আমরা সেই আইডি ধরে সব current ভ্যালু অবজেক্টে স্টোর করে দিলাম। এখন আমরা তো বডি চাই না। তাই পরের লাইনে সিমপ্লি delete এর মাধ্যমে বডি ডিলিট করে দিলাম। আর দিনশেষে তো acc ই রিটার্ন করবে। সব শেষে যখন রান করালাম, ওয়াও, আমাদের অবজেক্ট আমরা পেয়ে গেলাম। reduce এর পাওয়ার অন্য লেভেলের। এর পাওয়ার বলে শেষ করা যায় না।

লাস্ট আরেকটা এক্সাম্পল আমরা দেখি এই reduce মেথডের। ধরুন আমাদের কাছে একটা অ্যারে আছে নামের।

```js
const names = [
	'Ayman',
	'Abu Rayhan',
	'Anik',
	'Elias Emon',
	'Engr. Sabbir',
	'Fahim Faisal',
	'Feroz Khan',
	'Habib',
	'HM Azizul',
	'Hridoy Saha',
	'Jahid Hassan',
	'Johir',
	'Md Al-Amin',
	'Md Arafatul',
	'Md Ashraful',
	'Parvez',
];
```

আমরা এটাকে নিচের মতো করে আউটপুট পেতে চাইছি।

```txt
----------- A -----------
Ayman
Abu Rayhan
Anik

----------- E -----------
Elias Emon
Engr. Sabbir

----------- F -----------
Fahim Faisal
Feroz Khan

----------- H -----------
Habib
HM Azizul
Hridoy Saha

----------- J -----------
Jahid Hassan
Johir

----------- M -----------
Md Al-Amin
Md Arafatul
Md Ashraful

----------- P -----------
Parvez
```

এটা আমরা কিভাবে পেতে পারি। আমাদের আছে অ্যারে। আমরা যদি এই কাজটাকে নিচের স্ট্রাকচার হিসেবে কল্পনা করি তাহলে অনেক সহজ হয়ে যাবে।

```js
const namesGroup = {
	A: ['Ayman', 'Abu Rayhan', 'Anik'],
	E: ['Elias Emon', 'Engr. Sabbir'],
	F: ['Fahim Faisal', 'Feroz Khan'],
};
```

এখন অ্যারে থেকে আমাদের এভাবে অবজেক্টে পরিণত করতে হবে। আর এই কাজটা করতে পারে reduce. তাহলে চলুন করা যাক।

```js
const namesGrouped = names.reduce((acc, cur) => {
	const firstLetter = cur[0].toUpperCase();
	if (firstLetter in acc) {
		acc[firstLetter].push(cur);
	} else {
		acc[firstLetter] = [cur];
	}
	return acc;
}, {});
console.log(namesGrouped);

/* 
{
  A: [ 'Ayman', 'Abu Rayhan', 'Anik' ],
  E: [ 'Elias Emon', 'Engr. Sabbir' ],
  F: [ 'Fahim Faisal', 'Feroz Khan' ],
  H: [ 'Habib', 'HM Azizul', 'Hridoy Saha' ],
  J: [ 'Jahid Hassan', 'Johir' ],
  M: [ 'Md Al-Amin', 'Md Arafatul', 'Md Ashraful' ],
  P: [ 'Parvez' ]
}
*/
```

আমরা প্রথমে আমাদের acc কে একটা ফাঁকা অবজেক্ট হিসেবে নিয়ে নিলাম। এরপর আমরা প্রথম লেটার ধরে চেক করবো তা acc তে আছে কিনা। যদি থাকে কি করবো আর না থাকলে কি করবো। তাহলে প্রথমে আমরা current ভ্যালুর প্রথম লেটারের আপারকেইস নিয়ে একটা ভ্যারিয়েবলে স্টোর করে রাখলাম। এবার একটা কন্ডিশন লিখলাম। যদি firstLetter acc এর মধ্যে না থাকে firstLetter দিয়ে একটা কী তৈরি করবে এবং ঐ কী এর মধ্যে current ভ্যালুর একটা অ্যারে নিবে। যদি firstLetter acc এর মধ্যে থাকে তাহলে জাস্ট কারেন্ট ভ্যালুর যে অ্যারে তাতে push করে দিবে। এবার যদি আমরা একটু আউটপুট দেখি তাহলে দেখবো আমরা যে স্ট্রাকচারটা কল্পনা করেছিলাম সেটা পেয়ে গেছি। এবার এখান থেকে আমাদের রিকোয়ার্ড আউটপুট কিভাবে প্রিন্ট করবো, যেটা শুরুতে দেখিয়েছিলাম, তা একটু দেখি।

```js
Object.keys(namesGrouped).forEach((groupKey) => {
	console.log('-----------', groupKey, '-----------');
	namesGrouped[groupKey].forEach((name) => console.log(name));
	console.log();
});
```

এটা আশা করি বুঝানোর কিছু নেই। সিম্পল forEach মেথড যা আগে দেখেছিলাম। রান করলে দেখবেন আমাদের ডিজায়ার্ড আউটপুট আমরা পেয়ে গেছি।

যদি আমাদের filter, map, reduce জানা থাকে ভালভাবে তাহলে অন্যান্য ডাটা স্ট্রাকচার এবং অ্যালগরিদম ব্যবহার না করেও আমরা কিছু কিছু ক্ষেত্রে অপটিমাইজড অ্যাপ্লিকেশন বানিয়ে ফেলতে পারবো।