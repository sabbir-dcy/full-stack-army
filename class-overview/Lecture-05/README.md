# Lecture 5 - JavaScript Array and Object Deep Dive

### Object Operations

আমাদের চারপাশে আমরা যা দেখি তাই অবজেক্ট। ধরে আমাদের সামনে একটি মাইক্রোফোন আছে। এটাও একটা অবজেক্ট। কিভাবে চলুন একটু দেখি।

```js
const microphone = {
	brand: 'Fifine',
	indictor: true,
	price: 8000,
	color: 'Black',
	startRecording() {
		console.log('recording started');
	},
	stopRecording() {
		console.log('recording stopped');
	},
};
```

যখন আমাদের কোনো একটা বিষয় বা বস্তুকে রিপ্রেজেন্ট করার জন্য একাধিক ইনফরমেশন দরকার, তখনই আমাদের প্রয়োজন অবজেক্ট। একটা ইনফরমেশন হলে আমরা ভ্যারিয়েবল নিয়ে কাজ সেরে ফেলতে পারতাম। কিন্তু যেহেতু একের অধিক তাই আমাকে ঐ বিষয় বা বস্তু রিপ্রেজেন্ট করার জন্য প্রয়োজন অবজেক্ট। সেইম জিনিস জাভাতে বলে ক্লাস, পাইথনে বলে ডিকশনারি, সি তে সেটা হলো স্ট্রাকচার। এখন অবজেক্ট মানেই অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং না। অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং হলো এই অবজেক্টকেই কিভাবে সুন্দর করে অর্গানাইজড ওয়েতে রিপ্রেজেন্ট করা যায় সেটার থিওরাম হচ্ছে অবজেক্ট অরিয়েন্টেড প্রোগ্রামিং। এই টার্মটা আমাদের এখন প্রয়োজন নেই। আমরা বেসিক অবজেক্ট নিয়ে কথা বলছি, তাই ফোকাসটা আপাতত অবজেক্টের দিকেই দিই।

আমরা জানি যে, অবজেক্টের মধ্যে এর অনেকগুলো প্রোপার্টি রাখতে পারি। অবজেক্টের প্রোপার্টিজকে দুই ভাগে ভাগ করা যায়। যথাঃ

1. Noun / Adjective (State/data/property/field) - যে প্রোপার্টি দ্বারা আমাদের ডাটা রিপ্রেজেন্ট করতে পারি সেগুলোই এর আলোচ্য বিষয়। উপরের উদাহরণে brand, indicator, price, color এগুলো সবই প্রোপার্টি। কারণ এগুলো ডাটা রিপ্রেজেন্ট করছে। এই ডাটাগুলো স্ট্রিং, নাম্বার, বুলিয়ান যেকোনো ডাটা টাইপের হতে পারে।
2. Verb (functionalities -> start, stop) - যেমন আমাদের মাইক্রোফোনে কিছু ফাংশনালিটিজ থাকে। যেমন, start button, stop button, recording button etc. যেমন উপরের উদাহরণে startRecording, stopRecording।

তাহলে অবজেক্টের দুইটা অংশের একটা আমাদের ডাটাকে রিপ্রেজেন্ট করবে, আরেকটা অংশ ডাটার সাথে রিলেটেড কাজগুলো করবে। এই দুইটা অংশ মিলেই আমাদের একটা অবজেক্ট তৈরি হয়।

এখন এখানে যেসব প্রোপার্টি আমরা লিখলাম এর বাইরেও অনেক প্রোপার্টি আছে যেগুলো হিডেন আছে। যেমন আমরা যদি লিখি `microphone.toString()` তাহলে আউটপুট আসবে `[object Object]`। কিন্তু `toString` মেথড তো আমরা এখানে কোথাও লিখিনি। তাহলে এটা আসলো কোথা থেকে। এটা এসেছে `Object` থেকে। এই `Object` কে বলা হয় অবজক্ট কন্সট্রাকটর।

আমরা যেভাবে অবজেক্ট তৈরি করেছিলাম সেটা ছাড়াও অন্যভাবে অবজেক্ট তৈরি করা যায়। আমরা একটু সেই প্রসেসটাও দেখি।

```js
const testObj = new Object();
testObj.name = 'Test Object';
testObj.time = new Date();
console.log(testObj); // { name: 'Test Object', time: 2022-06-16T07:09:01.373Z }
```

আউটপুটে আমরা দেখতে পাচ্ছি একটা অবজেক্ট ক্রিয়েট হয়ে গিয়েছে। তার মানে আমরা দুইভাবেই অবজেক্ট ক্রিয়েট করতে পারি। প্রথমে যেভাবে তৈরি করেছি সেটাকে বলে `Object Literal` এবং পরে যেভাবে তৈরি করেছি সেটাকে বলে `Constructor Function`। আমরা যেভাবেই তৈরি করি না কেন সবকিছুর পিছনে ঐ `Object` কনস্ট্রাক্টরই কাজ করছে। এই `Object` এর মধ্যে কিছু ্ প্রোপার্টিজ আছে যা আমরা দুনিয়ায় যতো অবজেক্টই বানাবো সবকিছুতে ইনহেরিট হয়ে যাবে। আমরা একটু সেসব প্রোপার্টিজ দেখার চেষ্টা করি। এর জন্য আমাদের একটু ব্রাউজারের কনসোলে যেতে হবে। নিচের স্ক্রিনশটটি একটু খেয়াল করুন আপনারা।

![Object methods](class-overview/Lecture-05/Screenshot_1.png)

প্রথমে আছে কনস্ট্রাকটর। আমরা `Object` এর আগে `new` লাগিয়ে যে অবজেক্ট তৈরি করেছিলাম সেটাকে সেজন্য কন্সট্রাক্টর বলে। এরপর আছে `hasOwnProperty` এটা দিয়ে আমরা কোনো প্রোপার্টি ঐ অবজেক্টের নিজস্ব প্রোপার্টি কিনা তা চেক করতে পারবো। এছাড়াও `toString`, `valueOf`, `toLocaleString` ইত্যাদি প্রোপার্টিজ আছে। যেগুলো আমরা অবজেক্টে ডিফাইন না করলেও তারা প্রয়োজনে সেই মেথডগুলো ব্যবহার করতে পারবে। এগুলো মূলত আমরা যখন অবজেক্ট ওরিয়েন্টেড প্রোগ্রামিং করতে যাবো তখন এসব দরকার পড়বে। এখন অবশ্য ES6 আসার পরে অতো ডিপলি অবজেক্ট অরিয়েন্টেড প্রোগ্রামিং করার দরকার পড়ে না। তারপরও যতটুকু দরকার আমরা শিখে নিবো।এই মুহূর্তে সেটা নিয়ে মাথা না ঘামালেও চলবে। আমরা যদি `Oboject` লিখে একটা ডট (.) দিই তাহলে অনেক প্রোপার্টিজ আসবে। এখন এদের মধ্যে কোন কোন প্রোপার্টিজ ইনহেরিট হবে বা এক্সটেন্ডেড হবে এবং কোন কোন প্রোপার্টিজ হবে না। উপরের ছবিটি খেয়াল করুন। প্রোটটাইপের মধ্যে যে সকল প্রোপার্টিজ আছে সেগুলো ইনহেরিট বা এক্সটেন্ডেড হবে। আর যেগুলো নেই সেগুলো হবে না।

এই প্রোপার্টিজগুলোর মধ্যে আমরা একটু `freeze` প্রোপার্টিটা দেখি। ধরেন আমরা আমাদের microphone অবজেক্টে নতুন একটা প্রোপার্টি অ্যাড করতে চাইছি। তাহলে আমাদের নিচের কোডটা লিখতে হবে।]

```js
const microphone = {
	brand: 'Fifine',
	indictor: true,
	price: 8000,
	color: 'Black',
	startRecording() {
		console.log('recording started');
	},
	stopRecording() {
		console.log('recording stopped');
	},
};

microphone.newProperty = 'New Property';
console.log(microphone);
/* {
  brand: 'Fifine',
  indictor: true,
  price: 8000,
  color: 'Black',
  startRecording: [Function: startRecording],
  stopRecording: [Function: stopRecording],
  newProperty: 'New Property'
} */
```

কিন্তু অনেক সময় এমন অবজেক্ট নিয়ে আমরা কাজ করতে পারি যেখানে আমরা ডাটা এন্ট্রি রেস্ট্রিক্ট করে দিতে চাইছি। সোজা কথায় আমরা এখানে ডাটা ইনপুট দিতে দিবো না। সেই ক্ষেত্রে `freeze` মেথডটা অনেক কাজে আসে।

```js
const microphone = {
	brand: 'Fifine',
	indictor: true,
	price: 8000,
	color: 'Black',
	startRecording() {
		console.log('recording started');
	},
	stopRecording() {
		console.log('recording stopped');
	},
};

Object.freeze(microphone);
microphone.newProperty = 'New Property';
console.log(microphone);
/* {
  brand: 'Fifine',
  indictor: true,
  price: 8000,
  color: 'Black',
  startRecording: [Function: startRecording],
  stopRecording: [Function: stopRecording],
} */
```

খেয়াল করুন এখানে আমাদের অবজেক্ট কিন্তু আপডেট হয়নি। এই মেথড ব্যবহার করে আমরা অবজেক্টকে লক করে দিতে পারি। আরো দুইটা মেথড দেখি আমরা। একটা `keys` এবং অন্যটা `values`।

```js
console.log(Object.keys(microphone)); // ['brand', 'indictor', 'price', 'color', 'startRecording', 'stopRecording'];
console.log(Object.values(microphone));

/* 
[
  'Fifine',
  true,
  8000,
  'Black',
  [Function: startRecording],
  [Function: stopRecording]
]
*/
```

`Object.keys()` অবজেক্টের সব keys অ্যারে আকারে রিটার্ন করবে এবং `Object.values()` অবজেক্টের সব values অ্যারে আকারে রিটার্ন করবে। এখন এগুলো আমাদের কি দরকার? আমরা তো এগুলো ছাড়াও লুপ চালিয়ে কী এবং ভ্যালু বের করে আনতে পারি এভাবে-

```js
for (let k in microphone) {
	console.log(k, microphone[k]);
}

/* 
brand Fifine
indictor true
price 8000
color Black
startRecording [Function: startRecording]
stopRecording [Function: stopRecording]
*/
```

এখানে ভ্যালু বের করার জন্য যে অবজেক্ট নোটেশন ব্যবহার করা হয়েছে তাকে বলে অ্যারে নোটেশন। অবজেক্ট থেকে ভ্যালু দুইটা নোটেশন ইউজ করে বের করা যায়।

- Dot notation (microphone.brand)
- Array notation (microphone['brand])

যখন আমরা ডায়নামিক্যালি কোনো কী নিবো তখন আমরা জানি না সেটা কিরকম। তাই আমরা এক্ষেত্রে সবসময় অ্যারে নোটেশন ইউজ করবো। এবার মূলকথায় ফিরে যায়। আমরা তো এভাবেও কী আর ভ্যালু পাচ্ছি। তাহলে ঐ দুইটা মেথডের কাজ কি? আমরা একটু দেখি।

```js
const empty = {};
console.log(empty); // {}
console.log(Boolean(empty)); // true
```

আমরা যদি জানতে চাই আমাদের অবজেক্টটা সত্যিই ফাঁকা কিনা তাহলে এভাবে পারবো না। কারণ ফাঁকা অবজেক্ট, ফাঁকা অ্যারে সবসময় true রিটার্ন করবে। সেক্ষেত্রে আমরা `Object.keys()` এর সাহায্য নিবো।

```js
const empty = {};
console.log(Object.keys(empty)); // []
```

এখন ফাঁকা অ্যারেও তো true রিটার্ন করবে কারণ ফাঁকা অ্যারেও একটা truthy value. আমাদের অবজেক্ট প্রোপারলি ফাঁকা কিনা তা জানার জন্য আমাদেরকে নিচের কাজটা করতে হবে।

```js
const empty = {};
console.log(Object.keys(empty).length === 0); // true
```

তার মানে যদি লেংথ ০ হয় তাহলে আমাদের অবজেক্টটা ফাঁকা বলে ধরে নিতে পারি।

এছাড়াও আছে `Object.entries()` মেথড। এটার কাজটা আমরা দেখি একটু।

```js
console.log(Object.entries(microphone));
/*
[
  [ 'brand', 'Fifine' ],
  [ 'indictor', true ],
  [ 'price', 8000 ],
  [ 'color', 'Black' ],
  [ 'startRecording', [Function: startRecording] ],
  [ 'stopRecording', [Function: stopRecording] ]
]
*/
```

ছিল অবজেক্ট। হয়ে গেলো কী আর ভ্যালু এর জন্য আলাদা আলাদা অ্যারে। এটা আমাদের ভবিষ্যতে অনেক কাজে লাগবে।

এখন ধরেন আমাদের কাছে একটা অ্যারে আছে। আমরা চাইছি সেটা থেকে অবজেক্ট বানাতে। তা জন্য আমাদের ব্যবহার করতে হবে `fromEntries` মেথডটি।

```js
const arr = [
	['brand', 'Fifine'],
	['indictor', true],
	['price', 8000],
	['color', 'Black'],
];

console.log(Object.fromEntries(arr)); // { brand: 'Fifine', indictor: true, price: 8000, color: 'Black' }
```

### Function vs Method

যখন একটা ফাংশন একটা অবজেক্টের মধ্যে থাকে তখন আমরা সেটাকে বলি মেথড। তাহলে আমরা যে array.filter(), array.push(), array.map(), array.splice() ব্যবহার করেছি এগুলো সবগুলোই হচ্ছে মেথড। এরা ফাংশন না। ফাংশন আর মেথডের মধ্যে একটাই পার্থক্য। ফাংশন স্বাধীনভাবে যেকোনো জায়গায় কল করা যায় কিন্তু মেথড পারা যায় না। একটা উদাহরণ দিলে আমরা ভালভাবে বুঝতে পারবো।

```js
const microphone = {
	brand: 'Fifine',
	indictor: true,
	price: 8000,
	color: 'Black',
	startRecording() {
		console.log('recording started');
	},
	stopRecording() {
		console.log('recording stopped');
	},
};

function startRecording() {
	console.log('recording started');
}

startRecording();

microphone.startRecording();
```

এখানে `startRecording` ফাংশনটা অবজেক্টের ভিতরেও আছে, আবার বাইরেও আছে। এখন বাইরের ফাংশনকে চাইলে আমরা এমনিই কল করতে পারবো। কিছু ছাড়াই। কিন্তু অবজেক্টের ফাংশনকে যদি কল করতে চাই তাহলে অবশ্যই `microphone.startRecording()` লিখতে হবে। এটাই বেসিক পার্থক্য। তাহলে আমরা কোনোকিছুর পর ডট দিয়ে যাই লিখবো অর্থাৎ অবজেক্টের মধ্যে কোনো ফাংশন থাকলে সেগুলো সবগুলো হলো মেথড। আর ইন্ডিপেন্ডেন্টলি যা লিখবো সেগুলো হচ্ছে ফাংশন।

## Object as a Data Structure

আমরা চাইছি কয়েকজন ছাত্রের ইনফরমেশন স্টোর করতে। সেখানে থাকবে একজন ছাত্রের একটা ইউনিক আইডি, তার নাম এবং তার ইমেইল। এখন আমরা প্রথমে একটা ইউনিক আইডি জেনারেট করার ফাংশন তৈরি করে ফেলি।

```js
function uuidv4() {
	return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, (c) => {
		const r = (Math.random() * 16) | 0;
		const v = c == 'x' ? r : (r & 0x3) | 0x8;
		return v.toString(16);
	});
}
```

এই ফাংশনটা গুগল থেকে নেয়া। এখন আমরা এই ছাত্রদের ইনফরমেশন অ্যারে দিয়েও স্টোর করতে পারি আবার অবজেক্ট দিয়েও পারি। প্রথমেই বলে রাখি সব কাজের জন্য অ্যারে ভাল না আবার সব কাজের জন্য অবজেক্টও ভাল না। আমাদেরকে আমাদের কাজের উপর ভিত্তি করে সিদ্ধান্ত নিতে হবে কখন আমরা অ্যারে ইউজ করবো আর কখন অবজেক্ট। প্রথমে আমরা একটু অ্যারে নিয়ে কাজ করে দেখি। এরপর অবজেক্ট নিয়ে করবো।

### Array

আমাদের সমস্ত ছাত্রের ইনফরমেশন আমরা অ্যারেতে স্টোর করে রাখি এখন।

```js
const students = [
	{
		id: uuidv4(),
		name: 'Md Al-Amin',
		email: 'alamin@test.com',
	},
	{
		id: uuidv4(),
		name: 'Akib Ahmed',
		email: 'akib@test.com',
	},
	{
		id: uuidv4(),
		name: 'Elias Emon',
		email: 'elias@test.com',
	},
];
```

যেহেতু আমরা UI নিয়ে কাজ করছি না তাই আমরা চাইবো না বারবার আইডি চেইঞ্জ হোক। আমরা একবার প্রোগ্রাম রান করে যে আউটপুট জেনারেট হবে সেটাকেই স্টোর করে রাখবো। বারবার আইডি চেইঞ্জ হলে আমরা আমাদের যে অপারেশন তা ঠিকভাবে করতে পারবো না। সুতরাং আমরা প্রথমবার রান করার পর সেই আউটপুটকে স্টোর করে নিই আগে।

```js
const students = [
	{
		id: '67de71e5-0eac-474f-ab51-850ba9b31ed5',
		name: 'Md Al-Amin',
		email: 'alamin@test.com',
	},
	{
		id: 'ebdf6b78-c32b-4b1d-8574-e8c655b05c1e',
		name: 'Akib Ahmed',
		email: 'akib@test.com',
	},
	{
		id: 'ee729e84-a84e-4adf-b32c-4647a7114d5b',
		name: 'Elias Emon',
		email: 'elias@test.com',
	},
];
```

অ্যারেতে স্টোর করে রাখলে আমরা কিছু সুবিধা পাবো। সেগুলো হলোঃ

1. Create a new one
2. Update
3. Delete
4. Filter
5. Easily Traverse

এবার আমরা এক এক করে এই কাজগুলো দেখি।

- Create a new one

এটা সবচেয়ে সহজ কাজ। আমরা জানি আমরা যখন অ্যারেতে একটা ডাটা ইনসার্ট করতে চাই দুইটা মেথড আমরা ইউজ করতে পারি। যদি সবার শেষে ইনসার্ট করতে চাই তাহলে `push` মেথড ব্যবহার করবো, আর যদি সবার প্রথমে ইনসার্ট করতে চাই তাহলে `unshift` মেথড ব্যবহার করবো। কিন্তু `unshift` অনেক এক্সপেন্সিভ। কেন এক্সপেন্সিভ? কারণ আমাকে প্রতিটা ইলেমেন্ট এক ঘর করে ডান পাশে শিফট করতে হচ্ছে। যার কারনে অনেক বেশি অপারেশন ঘটাতে হচ্ছে। অর্থাৎ এর কমপ্লেক্সিটি O(n)। অন্যদিকে `push` মেথডে আমার কাউকে সরাতে হচ্ছে না। শুধু শেষে ডাটাটা বসিয়ে দিলেই হলো। অর্থাৎ এর কমপ্লেক্সিটি O(1)। O(n) হলো ডাটা সাইজের উপর এর এক্সিকিউশন টাইম নির্ভর করে। সাইজ ছোট হলে কম সময় আর সাইজ বড় হলে বেশি সময়। এটার সমস্যা হলো আমরা এখানে বিগ অ্যামাউন্টের ডাটা স্টোর করে রাখতে পারবো না। আর O(1) হলো ডাটার সাইজ কতো বড় বা ছোট সেটা বিবেচ্য না। সেটা একটা নির্দিষ্ট সময়েই এক্সিকিউট হবে তা বড় সাইজের ডাটা হোক বা ছোট সাইজের। তার এক্সিকিউশন টাইম কন্সট্যান্ট। এক্ষেত্রে ডাটা ইনসার্টের জন্য আমরা `push` মেথড ব্যবহার করবো।

```js
students.push({
	id: '0a2c956c-a9f4-48b9-83fa-551b432dfb2b',
	name: 'Fahim Faisal',
	email: 'fahim@test.com',
});
```

এখন আমাদের প্রোগ্রাম রান করালে দেখা যাবে আমাদের অ্যারেতে নতুন ডাটা ক্রিয়েট হয়ে গেছে।

- Update

আমরা দুইভাবে আপডেট করতে পারি। একটা হচ্ছে যাকে আপডেট করতে হবে find মেথডের মাধ্যমে সেই অবজেক্টকে বের করে তাকে আপডেট করা। আরেকটা হলো ঐ অবজেক্টের ইনডেক্সকে findIndex মেথডের মাধ্যমে বের করে সেটা ধরে আপডেট করা। অবজেক্ট ধরে যদি আপডেট করতে চাই সেক্ষেত্রে একটা সমস্যা আছে। সেটা একটু আমরা দেখি।

```js
const idToUpdate = 'ee729e84-a84e-4adf-b32c-4647a7114d5b';
const updatedData = {
	name: 'Habiba Akhtar',
	email: 'habiba@test.com',
};

let updatedObj = students.find((item) => item.id === idToUpdate);
updatedObj = {
	id: idToUpdate,
	...updatedData,
};
console.log('Updated', students);
```

```bash
[
  {
    id: '67de71e5-0eac-474f-ab51-850ba9b31ed5',
    name: 'Md Al-Amin',
    email: 'alamin@test.com'
  },
  {
    id: 'ebdf6b78-c32b-4b1d-8574-e8c655b05c1e',
    name: 'Akib Ahmed',
    email: 'akib@test.com'
  },
  {
    id: 'ee729e84-a84e-4adf-b32c-4647a7114d5b',
    name: 'Elias Emon',
    email: 'elias@test.com'
  },
  {
    id: '0a2c956c-a9f4-48b9-83fa-551b432dfb2b',
    name: 'Fahim Faisal',
    email: 'fahim@test.com'
  }
]
```

কিছুই আপডেট হলো না। কারণ আমরা অবজেক্ট অ্যাসাইন করছি। আর যেহেতু অ্যাসাইন করছি সেহেতু এর রেফারেন্সও আলাদা হয়ে গেছে। আলাদা রেফারেন্সের কারণে আমার আপডেট কাজ করছে না। ei bisoy tar ekta example dekhi-

suppose, `project_alpha` and `project_beta` name e duita project start kora holo. dui ta tei 100 million invest kora holo. so amra likhte pari `project_beta = project_alpha`

```js
let project_alpha = {
  invest: 100,
};

let project_beta = project_alpha
console.log(project_alpha === project_beta) // true
```

duita project e memory address same. ekhon jodi `project_beta` te kono changes kora hoy tahole `project_alpha` o affect hobe and vice versa. 
`note: (.) operator use kore`

```js
project_beta.invest += 50;
console.log(project_alpha === project_beta); // true
```
abar, jekono ekta te jodi kono kichu re-assign kori tahole mem address change hoye jabe. `project_alpha` te 50 million add kori tahole `project_alpha` ar `project_beta` same thakbe na.

```js
project_alpha = {
  invest: project_alpha['invest'] + 50
}

console.log(project_alpha) // {invest: 200}
console.log(project_alpha === project_beta); // false
```

so, jodi `updatedObj.email` ebhabe (.) operator diye `key` dhore dhore update korte chai tahole kora jabe. kintu eta kono efficient way na. ekhane 3 ta na hoye 1000 ta properties hote parto. eto properties er key toh mone rakha somvob na. jodi amader ke ekta raw file dewa hoy shekhetre pura file ta insert/re-assign kora tulana mulok easier. sheta kibhabe `findIndex` use kore kora jaay dekha jaak-

```js
const idToUpdate = 'ee729e84-a84e-4adf-b32c-4647a7114d5b';
const updatedData = {
	name: 'Habiba Akhtar',
	email: 'habiba@test.com',
};

const updatedIndex = students.findIndex((item) => item.id === idToUpdate);
students[updatedIndex] = {
	...students[updatedIndex],
	...updatedData,
};
console.log('Updated', students);
```

তিনটা ডট দেয়াকে জাভাস্ক্রিপ্টে বলে স্প্রেড অপারেটর। এর মানে হলো অরিজিনাল অবজেক্টে যা যা আছে সবই থাকবে। আর নতুন ডাটা অনুযায়ী সেটা আপডেট হবে। যখন কোনো কিছু রিঅ্যাসাইনের কাজ আসবে তখন আমরা find ব্যবহার না করে findIndex ব্যবহার করবো। 
ekhon kotha holo `index` keno khuje ber korchi? javascript e array o special type er object. index ke amra `key` assume korte pari. ar jodi `key` amader kache thake tahole `value` obosshoi update korte parbo.

```js
const arr = ['alpha', 'beta', 'gama', 'sigma']
console.log(Object.keys(arr))
```

```bash
[
    "0",
    "1",
    "2",
    "3",
]
```
এই আপডেট করা মোটামুটি রকমের কমপ্লেক্স। তাই এর কমপ্লেক্সিটি আমরা O(n) হিসেবে ধরতে পারি।

- Delete

ডিলিট করাটা তুলনামূলক সহজ। কিন্তু আমরা ডিলিটের জন্য দুইটা মেথড ইউজ করতে পারি `splice` এবং `filter`। এই দুইটা মেথডের কমপ্লেক্সিটি O(n)। এখানে আমরা splice নিয়ে কাজ করছি। পরের ধাপে আমরা filter অপারেশন দেখাবো। আমরা যদি আমাদের upodatedIndex ডিলিট করতে চাই তাহলে এভাবে লিখতে হবে।

```js
students.splice(updatedIndex, 1);
```

- Filter

```js
const filteredStudents = students.filter((item) => item.id !== idToUpdate);
console.log(filteredStudents);
```

- Easily Traverse

অ্যারের ক্ষেত্রে ট্রাভার্স করা অনেক সহজ। ধরি আমরা ছাত্রদের নাম জানতে চাইছি। তিনভাবে আমরা অ্যারে ট্রাভার্সের মাধ্যমে নাম বের করে আনতে পারি। এগুলো হলো। `for` loop, `for in` loop, `for of` loop। নিচে তিনটারই উদাহরণ দেয়া হলো।

```js
for (let i = 0; i < students.length; i++) {
	console.log(students[i].name);
}

for (let i in students) {
	console.log(students[i].name);
}

for (let student of students) {
	console.log(student.name);
}
```

এছাড়াই কিছু বিল্ট-ইন মেথড রয়েছে অ্যারে ট্রাভার্সের জন্য। যেমন `forEach`, `map`, `filter`, `every`, `reduce`, `some`, `find`, `findIndex` ইত্যাদি। তাহলে আমরা বুঝলাম যে অ্যারে অনেক সহজে ট্রাভার্স করা যায়। এটার কমপ্লেক্সিটি O(n)।

### Object Over Array

এবার আমরা আমাদের ছাত্রদের অ্যারেকে একটা অবজেক্টে রূপান্তরিত করি এবং একে একে অ্যারের ক্ষেত্রে যে যে অপারেশন করেছি সেই সেই অপারেশন করার চেষ্টা করি।

```js
const students = {
	'67de71e5-0eac-474f-ab51-850ba9b31ed5': {
		id: '67de71e5-0eac-474f-ab51-850ba9b31ed5',
		name: 'Md Al-Amin',
		email: 'alamin@test.com',
	},
	'ebdf6b78-c32b-4b1d-8574-e8c655b05c1e': {
		id: 'ebdf6b78-c32b-4b1d-8574-e8c655b05c1e',
		name: 'Akib Ahmed',
		email: 'akib@test.com',
	},
	'ee729e84-a84e-4adf-b32c-4647a7114d5b': {
		id: 'ee729e84-a84e-4adf-b32c-4647a7114d5b',
		name: 'Elias Emon',
		email: 'elias@test.com',
	},
};
```

আমাদের অবজেক্ট রেডি। এবার আমরা অপারেশনগুলো দেখি এক এক করে।

- Create a new one

অ্যারেতে আমরা সহজেই push মেথড ইউজ করে ডাটা ইনসার্ট করেছিলাম। কিন্তু অবজেক্টে তো এরকম কিছু নেই। তাহলে আমরা কিভাবে এই অপারেশন চালাবো। দেখি একটু কিভাবে করা যায়।

```js
const std = {
	id: uuidv4(),
	name: 'Feroz Khan',
	email: 'feroz@test.com',
};

students[std.id] = std;
```

একটাই উপায়। এবং সবচেয়ে সহজ উপায়। এই উপায়ে আপনি যতো চান ততো ডাটা ক্রিয়েট করতে পারবেন। খুব সহজ। আর এর কমপ্লেক্সিটি হলো O(1)।

- Update

যেহেতু এটা অ্যারে না সেহেতু এখানে find বা findIndex কিছুই কাজ করবে না। তাহলে কিভাবে আপডেট করবো। খুব সহজ। চলুন দেখা যাক।

```js
const idToBeUpdated = 'ee729e84-a84e-4adf-b32c-4647a7114d5b';
const updatedData = {
	name: 'HM Azizul',
	email: 'azizul@test.com',
};
students[idToBeUpdated] = {
	...students[idToBeUpdated],
	...updatedData,
};
```

এখন যদি আপনি প্রোগ্রাম রান করান দেখবেন আপনার ডাটা আপডেট হয়ে গেছে। কিন্তু যেহেতু এখানে কোনো ধরণের বিল্ট-ইন মেথড লাগেনি তাই এর কমপ্লেক্সিটি হবে O(1)।

- Delete

অবজেক্ট থেকে ডিলিট করা খুব সহজ।মানে এত সহজ হওয়া সম্ভব না। জাস্ট একটা কীওয়ার্ড ব্যবহার করলে ডিলিট হয়ে যাবে।

```js
delete students[idToBeUpdated];
```

কাজ শেষ। কমপ্লেক্সিটি O(1)।

- Get anything if you have the key

যদি আমাদের কোনো অবজেক্টের কী জানা থাকে তাহলে ১ সেকেন্ডের মধ্যে আমরা সেই অবজেক্টকে পেয়ে যাবো। কিভাবে> দেখুন তাহলে-

```js
console.log(students['67de71e5-0eac-474f-ab51-850ba9b31ed5']);
```

জাস্ট এটুকুই। আর এটার কমপ্লেক্সিটিও O(1)।

- Traverse

আমরা for in লুপ ব্যবহার করে খুব সহজেই অবজেক্ট ট্রাভার্স করতে পারি। যেমন যদি আমরা অবজেক্টে থাকা সবার নাম বের করে আনতে চাই তাহলে কিভাবে করবো?

```js
for (let key in students) {
	console.log(students[key].name);
}
```

কিন্তু এটা একটা ইম্পেরেটিভ ওয়ে। আমরা যখন রিয়্যাক্ট নিয়ে কাজ করবো তখন jsx এ কিন্তু for in ব্যবহার করতে পারবো না। আমাদের দরকার একটা ডিক্লারেটিভ ওয়ে। সেটার জন্য আমরা অবজেক্টের আলোচনায় দুইটা মেথডের কথা বলেছিলাম। একটা ছিল `Object.keys()` এবং অন্যটা হলো `Object.values()`। চলুন দেখি এগুলো কিভাবে অ্যাপ্লাই করতে পারি।

```js
Object.keys(students).forEach((key) => {
	const student = students[key];
	console.log(student.name);
});
```

এখানে key না নিয়েও আমরা সরাসরি value নিয়ে কাজ করতে পারতাম। যেমন

```js
Object.values(students).forEach((student) => {
	console.log(student.name);
});
```

এটার মাধ্যমে আমরা অবজেক্ট থেকে অ্যারে বানিয়ে অ্যারের সমস্ত কাজ আমরা করতে পারি। এতে কিন্তু আমাদের কোনো এক্সট্রা মেমোরি লাগছে না। কারণ আমরা এটাকে কোথাও স্টোর করে রাখছি না। এটা তার কাজ শেষ করে গার্বেজ কালেক্ট করে ক্লিয়ার করে ফেলবে।

তাহলে দেখা যাচ্ছে যে যে কাজ আমরা অ্যারে দিয়ে করতে পারতাম সেগুলো আমরা অবজেক্ট দিয়েও করতে পারি। এবং অনেক ক্ষেত্রে অনেক সহজেই করতে পারি।

## Comparison of object and array operation costs

```js
const arr = [];
const arrToObj = {};
for (let i = 0; i < 5000000; i++) {
	const o = {
		id: i,
		value: i,
	};
	arr.push(o);
	arrToObj[i] = o;
}

console.time('array');
let id = 4999999;
const obj = arr.find((item) => item.id === id);
obj.value = 555;
console.timeEnd('array'); // 104.901ms

console.time('obj');
arrToObj[id].value = 999;
console.timeEnd('obj'); // 0.019ms
```

অ্যারের অপারেশনে সময় লেগেছে ১০৪.৯০১ মিলিসেকেন্ড আর অবজেক্টের অপারেশনে লেগেছে ০.০১৯ মিলিসেকেন্ড।

```js
console.time('array');
arr.unshift({
	id: 5000000,
	value: 5000000,
});
console.timeEnd('array'); // 15.084ms

console.time('obj');
arrToObj[5000000] = {
	id: 5000000,
	value: 5000000,
};
console.timeEnd('obj'); // 0.018ms
```

অ্যারের জন্য লেগেছে ১৫.০৮৪ মিলিসেকেন্ড আর অবজেক্টের ক্ষেত্রে লেগেছে ০.০১৮ মিলিসেকেন্ড।

```js
console.time('array');
const index = arr.findIndex((item) => item.id === 4000000);
arr.splice(index, 1);
console.timeEnd('array'); // 93.135ms

console.time('obj');
delete arrToObj[4000000];
console.timeEnd('obj'); // 0.015ms
```

অ্যারের ক্ষেত্রে লেগেছে ৯৩.১৩৫ মিলিসেকেন্ড আর অবজেক্টের ক্ষেত্রে লেগেছে ০.০১৫ মিলিসেকেন্ড।

সবক্ষেত্রে দেখা যাচ্ছে তাহলে অবজেক্ট বিজয়ী। তবে কিছু কিছু ক্ষেত্রে অ্যারে নিয়ে কাজ করা লাগে। যেমন যখন আমার অর্ডারড ডাটা লাগবে, অর্থাৎ সিকোয়েন্স মেইনটেইন করতে হবে তখন অ্যারে মাস্ট। object a sequence random hoye jaay.