# Lecture 04 - Programming Fundamentals using JavaScript

লাস্ট ক্লাসে আমরা প্রোগ্রামিং ল্যাঙ্গুয়েজের যে ফান্ডামেন্টাল বিষয়গুলো নিয়ে আলোচনা করেছিলাম আজ সেগুলোর অরিজিন সম্পর্কে জানবো। অরিজিন সম্পর্কে জানলে আমাদের আর এসব বিষয় নিয়ে চিন্তা করতে হবে না। প্রোগ্রামিং ল্যাঙ্গুয়েজের যে ফান্ডামেন্টালস আছে তা হলোঃ

- Variables
- Operators
- Conditions
- Loops
- Arrays
- Objects
- Functions
- Expression vs Statement

## Variables

আমরা জানি ভ্যারিয়েবল মানে চলক। বিগিনারদের একটা সমস্যা হয় যে কোন জায়গায় ভ্যারিয়েবল নিতে হবে আর কোন জায়গায় নিতে হবে না। এর জন্য কিছু ট্রিকস আছে। তার আগে আমাদের জানা দরকার ভ্যারিয়েবলের কাজটা কি? সহজ ভাষায় বলতে গেলে ভ্যারিয়েবল আমাদের যেকোনো কিছু ডায়নামিক করতে সাহায্য করে। এটাই একমাত্র কাজ। এটা ছাড়া ভ্যারিয়েবলের আর কোনো কাজ নেই। এটা অনেকটা পাত্রের মতো। পাত্র যতো বেশি লাগবে জায়গা ততো বেশি লাগবে। মানে বেশি মেমোরি লাগবে। তাহলে এক্সট্রা মেমোরির দরকার কি? ভ্যারিয়েবল কম নিলেই তো হয়। তাহলে আমাদের অ্যাপ্লিকেশন অনেক হালকা হবে। কিন্তু তা সত্ত্বেও আমাদের ভ্যারিয়েবল নিতে হয়। যেমন ধরেন আমরা পানি খাবো। এই পানি কিভাবে আমাদের কাছে আসবে? প্রথমে মাটির নিচ থেকে পানি পাইপ এবং পাম্পের মাধ্যমে বাসার নিচে একটা ট্যাংকে জমা হয়। এরপর আরেকটা পাম্পের মাধ্যমে তা ছাদের উপর গিয়ে আরেকটা ট্যাংকে জমা হয়। ওখানে থেকে পাইপিং এর মাধ্যমে বাসায় বাসায় ডিস্ট্রিবিউট করা হয়। বাসায় ট্যাপের মাধ্যমে সেই পানি আমরা ফিল্টারের মধ্যে জমা করি। ফিল্টার হওয়ার পর সেই পানি আমরা জগ বা বোতলে নিয়ে রাখি। এরপর যখন পানি খাওয়ার প্রয়োজন হয় তখন আমরা জগ বা বোতল থেকে গ্লাসে ঢেলে পানি খাই। আমাদের উদ্দেশ্য কিন্তু পানি খাওয়া তাহলে মাঝখানে এত জায়গায় পানি জমা করে রাখার প্রয়োজন কি? যদি ট্যাংকে জমা রাখতে না পারতাম তাহলে সবার ঘরে ঘরে ডিস্ট্রিবিউট করা সম্ভব হতো না। যদি ফিল্টারে না রাখতাম তাহলে পানি বিশুদ্ধ করতে পারতাম না। সুতরাং ভ্যারিয়েবলও এরকম। এরা ডাটা স্টোর করে রাখে। ভ্যারিয়েবল যদি আমরা না নিই তাহলে আমরা ডাটা দ্বিতীয়বার ইউজ করতে পারতাম না।

```js
console.log('Abu Rayhan', 'Abu Rayhan'.length); // Abu Rayhan 10
```

উপরের উদাহরণে যদি আমরা অন্য কোনো নাম দিয়ে করতে চাই তাহলে সেটা সম্ভব না। সেটা করতে গেলে বর্তমান নামকে বাদ দিতে হবে। কারণ স্ট্যাটিক কোডের ক্ষেত্রে রানটাইমে কোনো কিছু চেইঞ্জ করা যায় না। এখন প্রশ্ন আসতে পারে রানটাইম আর কম্পাইল টাইম কি?

```js
console.log('Abu Rayhan', 'Abu Rayhan'.length); // Abu Rayhan 10
throw new Error('Something wrong'); // Error
```

এখানে প্রোগ্রামে কোনো ভুল নেই। কিন্তু প্রোগ্রাম রান করতে গিয়ে দেখা যাচ্ছে একটা এরর আছে। একে বলে রানটাইম এরর। প্রোগ্রাম রান করার সময়কে বলা হচ্ছে রানটাইম।

```js
console.log('Abu Rayhan', 'Abu Rayhan'.length);
121354644dsfsdf
```

এক্ষেত্রে প্রথম কোড এক্সিকিউট হবে না। সরাসরি এরর দেখাবে। মানে কম্পাইল করার সময় সে কোডে ভুল পেয়েছে। একে বলে কম্পাইল টাইম এরর।

এখন রানটাইমে আমরা ডায়নামিক্যালি অনেক কিছু চেইঞ্জ করতে পারি। যেমন কিছু ইনপুট দিতে পারি, ইন্টারনেট থেকে কিছু নিয়ে আসতে পারি, মাউস দিয়ে ক্লিক করতে পারি। এসব কিছুই রানটাইমে হয়। কিন্তু যখন আমরা প্রথম উদাহরণের মতো স্ট্যাটিক ডাটা নিয়ে কাজ করবো তখন আমরা কোনোভাবেই লগের ভিতরে থাকা ডাটা চেইঞ্জ করতে পারবো না। এজন্য আমাদের ভ্যারিয়েবল নিতে হবে। যখনই আমরা দেখবো ডাটা তখনই আমরা একটা ভ্যারিয়েবল নিয়ে নিবো।

```js
let name = 'Abu Rayhan';
console.log(name, name.length); // Abu Rayhan 10
```

ভ্যারিয়েবলে নেয়ার কিছু উপকার আছে। প্রথম উপকার হলো এই ডাটাটা আমরা আবু রায়হানের জন্য নিয়েছি। এখন আমি চাইছি জাহিদ হাসানের জন্য নিবো, বা এইচ এম নাঈমের জন্য নিবো। সেক্ষেত্রে শুধু `name` এর মধ্যে থাকা ডাটা চেইঞ্জ করে দিলেই হচ্ছে। আরো একটা উপকার হলো এখানে `name` শুধু দুই জায়গাতে ব্যবহার হয়েছে। এটা দুই জায়গায় না হয় দুইহাজার হতে পারতো, দুই লক্ষ হতে পারতো। এখন কোনো কারণে ডাটা চেইঞ্জ করতে হলে আমার পক্ষে দুই লক্ষ জায়গায় চেইঞ্জ করা কি সম্ভব? সেক্ষেত্রে ভ্যারিয়েবল নিয়ে নিলে আমরা শুধু এক জায়গাতেই চেইঞ্জ করবো। বাকি দুই লক্ষ জায়গায় আর দৌঁড়াতে হলো না।

আরেকটা উদাহরণ দিলে ডায়নামিক্যালি কিভাবে রানটাইমে ডাটা পরিবর্তন করা যায় ভ্যারিয়েবলের মাধ্যমে তা স্পষ্ট হয়ে যাবে।

```js
const names = [
	'HM Nayeem',
	'Aditya Chakraborty',
	'Abu Rayhan',
	'Shaker Hossain',
	'Akib Ahmad',
	'Alvi Chowdhury',
];
let index = -1;
let person = names[++index];

setInterval(() => {
	person = names[index++];
	console.log(person, person.length);

	if (index === names.length) {
		index = 0;
	}
}, 1000);
```

এখন প্রোগ্রামটি রান করলে দেখা যাবে ১ সেকেন্ড পরপর নামগুলো পরিবর্তন হয়ে একটার পর একটা আসতে থাকবে। শেষ হয়ে গেলে আবার প্রথম থেকে শুরু করবে। এর কোনো শেষ থাকবে। এখন যদি আমরা ভ্যারিয়েবল ব্যবহার না করে জাস্ট একটা নাম বসিয়ে দিই, তাহলে শুধুমাত্র সেই নামটাই প্রিন্ট হবে বারবার। ডায়ামিক ব্যাপারটা আর থাকলো না। আর আমরা প্রোগ্রামিং করিই সবকিছু ডায়নামিক করার জন্য। তাই যেখানেই দেখবো ডাটা সেখানেই আমরা ভ্যারিয়েবল ধরে নিবো। এক্সট্রা মেমোরি যায় যাক।

এবার আসি দুইটা গুরুত্বপূর্ণ টার্ম `let` এবং `const` নিয়ে। কখন `let` আর কখন `const` ব্যবহার করবো। যখন দেখবো কোনো ডাটা আমার আর পরবর্তীতে আপডেট হচ্ছে না সেক্ষেত্রে আমরা `const` ব্যবহার করবো। তাহলে আমরা চাইলেও বা ভুল করেও সেই ডাটা আপডেট করতে পারবো না। করতে গেলে এরর চলে আসবে। আর যেসব ডাটা পরবর্তীতে আপডেট হওয়ার চান্স থাকে সেসব ডাটার ক্ষেত্রে আমরা `let` ব্যবহার করবো। উপরের উদাহরণে `names` কোথাও আপডেট হচ্ছে না। তাই আমরা `const` ব্যবহার করেছি। কিন্ত `index` এবং `person` আমরা আপডেট করেছি পরবর্তীতে। তাই আমরা সেখানে `let` ব্যবহার করেছি। নিয়ম হলো সবকিছু প্রথমে আমরা `const` ধরে নিবো। এরপর যদি কোনো ডাটা আপডেট হচ্ছে দেখা যায় সেটাকে আমরা পরে `let` করে দিবো। এভাবে করলে আমাদের ভুল করার চান্স অনেক কম থাকবে।

**তাহলে দেখা যাচ্ছে ভ্যারিয়েবল ব্যবহার করা হয় রানটাইমে ডাটা ডায়নামিক্যালি আপডেট করার জন্য।**

## Operators

অপারেটরের সাথে আমরা সবাই পরিচিত। ছোটবেলা থেকে আমরা যোগ, বিয়োগ, গুণ, ভাগ করি। ওখানে আমরা কিছু ম্যাথমেটিকাল অপারেটর ব্যবহার করতাম। প্রোগ্রামিং এর অপারেটরসও একই। প্রোগ্রামিং ল্যাঙ্গুয়েজে অপারেটরস ব্যবহার করা হয় গাণিতিক হিসাবনিকাশের জন্য। আর কোনো কাজ নেই এর। অপারেটরস হলো মূলত ফাংশনস। যেসব ল্যাঙ্গুয়েজে অপারেটর ওভারলোডিং আছে সেখানে আমরা ফাংশন তৈরি করে অপারেটরের কাজকর্মগুলো করি। যেমন

```js
add();

mod();

lessThan();
```

আমরা যোগ করার জন্য `add` ফাংশন বানিয়ে ব্যবহার করতে পারি। `mod` ফাংশন ইউজ করে আমরা মডুলাস অপারেশন করতে পারি, `lessThan` ব্যবহার করে আমরা আমাদের ভ্যালু ছোট কিনা তা চেক করতে পারি। কিন্তু জাভাস্ক্রিপ্টে অপারেটর ওভারলোড হয় না। তাই আমাদের ফাংশন বানানোর দরকার পড়ে না। জাভাস্ক্রিপ্ট আগে থেকেই কিছু সিম্বলিক রিপ্রেজেন্টশনের মাধ্যমে এসব ফাংশন তৈরি করে রেখেছে, যাতে আমাদের কাজ অনেক সহজ হয়। `add()` এর পরিবর্তে আমরা `+` ব্যবহার করি, `mod()` এর পরিবর্তে `%`, `lessThan` এর পরিবর্তে আমরা `<` ব্যবহার করি। অপারেটরস নিয়ে আসলে আর ডিটেইলস তেমন কিছু বলার নেই।

## Conditions

কন্ডিশনকে বলা হয় কম্পিউটারের ব্রেইন। এই কন্ডিশনের উপর ভিত্তি করেই কম্পিউটার সিদ্ধান্ত নেয় কোন কাজটা সে করবে। যদিও কম্পিউটারের ডিসিশন নেয়ার কোনো ক্ষমতা নেই। আমরাই বিভিন্ন লজিক লিখে কম্পিউটারকে একটা সিদ্ধান্ত নেয়ার রাস্তা করে দিই। এখন লজিক লিখতে গেলে আমাদের কন্ডিশন প্রয়োজন। আমরা প্রতিনিয়ত আমাদের প্রাত্যহিক জীবনে কন্ডিশন ব্যবহার করে যাচ্ছি। যেমন যদি আকাশ মেঘলা থাকে তাহলে আমি ছাতা নিয়ে বের হবো, নাহয় ছাতা নিয়ে বের হবো না। এটা একটা কন্ডিশন। আবার ধরুন আমার অফিস ৯টায়। এখন যদি আমি ৮টার মধ্যে ঘর থেকে বের হতে পারি তাহলে বাসে যাবো, নাহয় সিএনজি নিয়ে যাবো। এটাও এক ধরণের কন্ডিশন। আবার যেমন আজকের ক্লাসে যেহেতু বেসিক পড়ানো হবে সেহেতু আমি আজকের ক্লাসে জয়েন করবো না, যদি অ্যাডভান্স পড়ানো হয় তাহলে জয়েন করবো। এখন এই কন্ডিশনকে কিভাবে আমরা কোডে রূপান্তর করতে পারি সেটা দেখা যাক।

```js
if (studyBasic) {
	wontJoin();
}

if (studyAdvanced) {
	join();
}

if (teacherSpeaks) {
	silent();
}

if (!teacherSpeaks) {
	shout();
}
```

এটা একটু আমরা বুঝার চেষ্টা করি। যদি বেসিক পড়ানো হয় তাহলে আজকের ক্লাসে আমি জয়েন করবো না। যদি অ্যাডভান্স পড়ানো হয় তাহলে জয়েন করবো। যদি টিচার কথা বলেন আমরা সবাই চুপ থাকবো। যদি তিনি কথা না বলেন আমরা সবাই একসাথে কথা বলবো। এরকম আমরা আমাদের প্রাত্যহিক কর্মকান্ডের মধ্যে কন্ডিশন খুঁজে পাবো। কন্ডিশন ছাড়া সব অচল। প্রোগ্রামিং ল্যাঙ্গুয়েজের ৫০% হলো কন্ডিশন, আর ৫০% হলো লুপ।

এখন কন্ডিশন ৩ ভাবে লেখা যায়। অর্থাৎ এর ৩টা সিনারিও আছে। আমরা একটু আগে নিচের কোড দেখি। এরপর ব্যাখ্যা করবো।

```js
// Scenario 1 - Single branch
// if condition
if (hasMoney) {
	buyPhone();
}

// Scenario 2 - Two branches
// if else condition
if (toss === 'head') {
	win();
} else {
	loss();
}

// Scenario 3 - Multiple branches
// else if
let a = 1,
	b = 2;
if (a > b) {
	big();
} else if (a < b) {
	small();
} else {
	same();
}
```

- Scenario - 1: এটা সিঙ্গেল ব্রাঞ্চ। এখানে একটার বেশি কেইস হওয়া সম্ভব না। সেক্ষেত্রে আমরা এই সিনারিও ব্যবহার করবো। একে বলা হয় `if condition`। এখানে বলা হয়েছে টাকা থাকলে ফোন কিনবো। না থাকলে যেমন যাচ্ছে যাবে। একটার বেশি কেইস এখানে দরকার নেই। তাই এখানে আমরা শুধু `if condition` ব্যবহার করবো।

- Scenario - 2: এটা মূলত দুইটা ব্রাঞ্চের উপর নির্ভর করে, অর্থাৎ এর সর্বোচ্চ দুইটা আউটকাম থাকবে। একে বলা হয় `if else condition`। এ ধরণের সিনারিওতে দুইটার বেশি কন্ডিশন কখনই সম্ভব হবে না। যেমন যদি টসে হেড আসে তাহলে আমি টস জিতবো, নাহয় হারবো। এই দুইটার বেশি রেজাল্ট আসার সম্ভাবনা নেই।

- Scenario - 3: এটা মাল্টিপল ব্রাঞ্চ। যদি দুইয়ের অধিক আউটকাম আসার সম্ভাবনা থাকে তাহলে আমরা এটা ব্যবহার করবো। এই ধরণের সিনারিওকে বলে `else if condition`। যেমন যদি `a > b` হয় তাহলে a, b এর চেয়ে বড় হবে। যদি `a < b` হয় তাহলে a, b এর চেয়ে ছোট হবে। নাহয় দুইটাই সমান হবে। এখানে দুইয়ের অধিক আউটকাম এসেছে। তাই এখানে আমরা মাল্টিপল ব্রাঞ্চ ব্যবহার করেছি।

কন্ডিশন নির্ভর করে মূলত আউটকামের উপর। আমার কয়টা আউটকাম আসতে পারে, সেভাবে কন্ডিশন লিখতে হবে।

## Loop

লুপের একটাই কাজ। একই কাজ বারবার করা। যেমন আমাদের একজন ক্লায়েন্ট এসে বললেন বাংলাদেশ তো এবার ৫১ বছরে পা দিলো। আমরা আমাদের অ্যাপ্লিকেশনে এমন কিছু করবো যেন ৫১ বার 'We love Bangladesh' লেখা আসে। আমরা অনেক বুদ্ধিমান আমরা ১ ঘন্টা ধরে গুণে গুণে ৫১ বার `console.log('We love Bangladesh')` লিখে ক্লায়েন্টকে দেখালাম। ক্লায়েন্ট বললো না ভাই ৫১ বার না। যেহেতু ১৯৭১ সালে বাংলাদেশ স্বাধীন হয়েছিল আমরা ১৯৭১ বার চাইছি। এবার আমি ৩ দিন ধরে গুণে গুণে সেই একই কোড লিখে বিধ্বস্ত অবস্থায় ক্লায়েন্টের কাছে নিয়ে দেখালাম। ক্লায়েন্ট বললো, নাহ্‌। এভাবে না। আমরা ৩০ লাখ শহীদকে সম্মান দেখিয়ে ৩০ লক্ষ বার এটা প্রিন্ট করবো এবার আমি বেহুঁশ। আমি গিয়ে রিসার্চ করে দেখলাম জাভাস্ক্রিপ্টে `repeat()` নামক একটি ফাংশন আছে। এবার তো ইজি। ক্লায়েন্ট যতবার চায় ততবার লিখে দিতে পারবো জাস্ট এক লাইন কোড লিখে। আমিও নিচের কোড লিখে ক্লায়েন্টের কাছে খুব গর্ব নিয়ে গেলাম জাস্ট ১০ মিনিটের মধ্যে।

```js
console.log('We love Bangladesh\n'.repeat(3000000));
```

আমি তো আকাশে উড়ছি। মনে মনে জাভাস্ক্রিপ্টকে ধন্যবাদ দিচ্ছি এই ফাংশনের জন্য। এবার ক্লায়েন্ট দেখে খুব খুশি হলেন। কিন্তু কিছুক্ষণ পরে বললেন, আচ্ছা ৩০ লক্ষ বার তো প্রিন্ট হলো। ইউজার কিভাবে বুঝবে এটা ৩০ লক্ষ বার হয়েছে। প্রতিটার আগে একটা নাম্বার দিয়ে দিলে বিষয়টা আরো ভাল হয়। এবার তো মাথায় হাত। ডায়নামিক্যালি এত নাম্বার কিভাবে করবো? তার জন্য সহজ সমাধান নিয়ে এসেছে প্রোগ্রামিং ল্যাঙ্গুয়েজ। সেটা হলো লুপ। লুপের মাধ্যমে আমরা সহজেই একই কাজ বারবার করাতে পারি যতবার খুশি।

```js
for (let i = 1; i <= 3000000; i++) {
	console.log(i, 'We love Bangladesh');
}
```

এবার সব সমস্যার সমাধান হয়ে গেলো। লুপ আমাদের রিপিটেশনের কাজকে অনেক সহজ করে দিয়েছে। ধরে নেন লুপের মধ্যে কার্লি ব্যাকেটের ব্লকটা একটা নতুন js ফাইল। আমরা এখানে যেকোনো ভ্যালিড js কোড লিখতে পারি। কিন্তু মনে রাখতে হবে এই ব্লকের মধ্যে যা কোড থাকবে তা মাল্টিপল টাইম এক্সিকিউট হবে।

প্রধাণত ৩ ধরণের লুপ আছে জাভাস্ক্রিপ্টে। এরপর বিভিন্ন কাজের সুবিধার্থে লুপের সংখ্যা বৃদ্ধি পেয়েছে। মাল্টিপল আইপের লুপ থাকলেও যেকোনো একটা লুপ ব্যবহার করেই প্রব্লেম সলভ করার যাবে।

- for loop
  - range
  - for in
  - for of
- while loop
- do while loop

### For Loop

For লুপ দিয়ে আমরা while, do while দুই ধরণের কাজই করা যায়। এখন for loop কেন আসলো, এর কাজটা কি? আমরা আমাদের আগের উদাহরণটাই নিই। এখানে ক্লায়েন্ট বলে দিয়েছেন ৩০ লক্ষ বার প্রিন্ট করার জন্য। তার মানে আমার রেঞ্জ জানা আছে। আমার স্টার্টিং পয়েন্টও জানা আছে, আবার কোথায় গিয়ে থামতে হবে তাও জানা আছে। এক্ষেত্রে আমরা সবসময় ফর লুপ ব্যবহার করবো। তার মানে হলো যেসব ক্ষেত্রে আমাদের স্টার্টিং পয়েন্ট এবং এন্ডিং পয়েন্ট জানা থাকবে সেসব ক্ষেত্রে আমরা ফর লুপ ব্যবহার করবো। ফর লুপের মধ্যে আবার ৩ ধরণের লুপ রয়েছে। একটা হলো রেঞ্জ রিলেটেড যেটা দেখলাম। আরেকটা for in যেটা আমরা অ্যারে বা অবজেক্টের ক্ষেত্রে ব্যবহার করতে পারি। যেটাতে রেঞ্জ দিতে হয় না in ব্যবহার করে আমরা কাজ করতে পারি। সেটা আমরা পরে দেখবো। আরেকটা হল for of loop। এটা ইটারেটর আসার পর সহজে কাজ করার জন্য এসেছে। এটাও অ্যারে নিয়ে কাজ করতে ব্যবহৃত হয় বা যেকোনো ইটারেটরের ক্ষেত্রে এটা ব্যবহৃত হয়, সেটাও আমরা পরে আলোচনা করবো। এটা খুব কাজে লাগবে যখন আমরা asynchronous data নিয়ে কাজ করবো তখন।

### While Loop

While loop দিয়েও আমরা for, do while এর কাজ করতে পারি। এখন এটা কেন আসলো, এর কাজ কি? ধরেন ক্লায়েন্ট আমাদের বললো আমরা লুপটা র‍্যান্ডমলি চালাবো। ১ থেকে চালাতে হবে সেরকম কথা নেই। জাস্ট একটা র‍্যান্ডম নাম্বার থাকবে আর পাশে 'We love Bangladesh' কথাটা থাকবে। কতক্ষণ চালাতে হবে তার কোনো বর্ণনা নেই। আবার ইনফিনিট লুপও চালানো যাবে না। ক্লায়েন্ট বললো তুমি একটা কাজ করো। যখনই নাম্বার চলতে চলতে ৭১ এ আসবে তখনই আমার প্রিন্টিং বন্ধ হয়ে যাবে। নিচের উদাহরণ দেখলে আরো স্পষ্ট হবে আপনাদের কাছেঃ

```js
while (true) {
	let num = Math.ceil(Math.random() * 100);
	console.log(num, 'We love Bangladesh');
	if (num === 71) break;
}
```

ফর লুপের সাথে এর পার্থক্য হলো ফর লুপের ৩টা পার্ট ছিল। ইনিশিয়ালাইজ, কন্ডিশন, ইনক্রিমেন্ট/ডিক্রিমেন্ট। কিন্তু হোয়াইল লুপে আছে শুধু একটা পার্ট, সেটা হলো কন্ডিশন। আর কন্ডিশন মানেই হলো হয় সত্য হবে নাহয় মিথ্যা। তার মানে যখন আমার কোনো রেঞ্জ জানা থাকবে না, শুধু কন্ডিশন জানা থাকবে তখনই আমরা হোয়াইল লুপ ব্যবহার করবো।

### Do While Loop

Do While দিয়ে আমরা কিন্তু for বা do while এর কাজ করতে পারি না। এটা একটা স্পেশাল টাইপের লুপ। এটা কেন ব্যবহার করা হয়। ধরেন হোয়াইল লুপের উদাহরণে কন্ডিশন সত্য না হয়ে মিথ্যা হলো। তাহলে সে একবারও আউটপুট শো করবে না। আমি চাইছি সত্য হোক বা মিথ্যা হোক আউটপুট অন্তত একবার হলেও শো করবে। সেক্ষেত্রে আমরা do while loop ব্যবহার করবো। এটা হোয়াইল লুপ দিয়েও সম্ভব। কিন্তু ডু হোয়াইল দিয়ে আরেকটু বেটার কাজ করা যায়। একটি উদাহরণ দেখি আমরা।

```js
do {
	console.log('It will run at least once');
} while (false);
```

যদিও এর কন্ডিশন মিথ্যা কিন্তু তাও অন্তত একবার এটি আউটপুট দেখাবে। এটাই হলো এই লুপের কনসেপ্ট।

## Array

সবচেয়ে অবহেলিত ডাটা স্ট্রাকচার এবং সবচেয়ে শক্তিশালী ডাটা স্ট্রাকচারের মধ্যে অন্যতম। অ্যারে ব্যবহার করে আমরা অনেক কমপ্লেক্স ডাটা স্ট্রাকচার তৈরি করে ফেলতে পারি। যেমন গ্রাফ, হীপ, স্ট্যাক, কিউ। ২/৩ লক্ষ ডাটা নিয়ে কাজ করার জন্য অ্যারে অনেক পাওয়ারফুল এবং পারফেক্ট ডাটা স্ট্রাকচার। প্রশ্ন হলো অ্যারে কেন আসছে আর অ্যারের কাজ কি? আমরা কয়েকজন মানুষের নাম স্টোর করে রাখতে চাইছি। সেটা আমরা ভ্যারিয়েবল দিয়ে করতে পারি।

```js
const name1 = 'Rayhan';
const name2 = 'Alvi';
const name3 = 'Anik';
const name4 = 'Arjun';
const name5 = 'Ayman';
```

এখন আমি চাইছি এই নামগুলোকে লোয়ারকেসে কনভার্ট করবো। সেটার জন্য আমাদের প্রত্যেকটা ধরে ধরে কনভার্ট করতে হবে।

```js
console.log(name1, name1.toLowerCase());
console.log(name2, name2.toLowerCase());
console.log(name3, name3.toLowerCase());
console.log(name4, name4.toLowerCase());
console.log(name5, name5.toLowerCase());
```

এখন এখানে তো ৫টা নাম না থেকে তো ৫ লক্ষ নাম থাকতে পারতো। সেগুলোকে যদি প্রত্যেকটা ধরে ধরে কনভার্ট করতে হয় তাহলে সেটা তো একটা অসম্ভব ব্যাপার। তার জন্য আমাদের এমন একটা উপায় দরকার যাতে করে আমরা সব নামকে একটা ভ্যারিয়েবলের মধ্যে রাখতে পারি। এখন একটা ভ্যারিয়েবলের মধ্যে রেখে দেখি।

```js
const persons = 'Rayhan, Alvi, Anik, Arjun, Ayman';
```

এখন এখানে প্রব্লেম হলো এগুলো সব মিলে একটা বড় স্ট্রিং এ পরিণত হয়ে গেছে। এখানে থেকে আলাদা করবো কিভাবে? আলাদা আলাদা ভাবে স্টোর করে দেখা যাক।

```js
const persons = 'Rayhan', 'Alvi', 'Anik', 'Arjun', 'Ayman';
```

কিন্তু এখন প্রোগ্রাম রান করাতে গেলে অনেক বড়সড় একটা এরর খেয়ে বসে থাকবো আমরা। এই সমস্যা সমাধানের জন্য আমাদের কাছে একটা ডাটা স্ট্রাকচার আছে যার নামে অ্যারে। কিছু না জাস্ট উপরের উদাহরণের আগে আর পরে `[]` বসিয়ে দিলেই অ্যারে হয়ে যাবে।

```js
const persons = ['Rayhan', 'Alvi', 'Anik', 'Arjun', 'Ayman'];
```

এবার এখান থেকে ডাটা কিভাবে বের করা যায়? প্রতিটা অ্যারে এলিমেন্টের পজিশনের একটা নাম্বার আছে। একে বলে ইনডেক্স। ইনডেক্স শুরু হয় ০ থেকে। তাহলে ১ম পজিশনের ইনডেক্স ০, ২য় পজিশনের ইনডেক্স ১, ৩য় পজিশনের ইনডেক্স ২ এভাবে করে ইনডেক্সিং করা যায়। তাহলে আমরা অ্যারের একটা নাম পেলাম আর নাম্বার পেলাম। নাম্বার পাওয়ার কারণে সুবিধা হলো আমরা এখানে সহজেই ক্যালকুলেশন করতে পারবো। আর এটাই অ্যারের পাওয়ার। এখন কিভাবে অ্যারে থেকে ডাটা বের করা যায় সেটা দেখি।

```js
const persons = ['Rayhan', 'Alvi', 'Anik', 'Arjun', 'Ayman'];
console.log(persons[0]);
console.log(persons[1]);
console.log(persons[2]);
console.log(persons[3]);
console.log(persons[4]);
```

এভাবে আমরা সব নাম বের করে আনতে পারি। এখন এখানে দেখা যাচ্ছে সব একই শুধু ইনডেক্সটা ভিন্ন। মানে একই কাজ বারবার চলছে। তাহলে এখানে আমরা একটা লুপ চালাতে পারি।

```js
const persons = ['Rayhan', 'Alvi', 'Anik', 'Arjun', 'Ayman'];

for (let i = 0; i < 5; i++) {
	console.log(persons[i]);
}
```

এবার যদি প্রোগ্রাম রান করা হয় তাহলে দেখা যাবে সব নাম সুন্দর করে প্রিন্ট হয়ে যাবে। এখানে একটা প্রব্লেম আছে। প্রব্লেমটা বুঝার জন্য আমরা আরো দুইটা নাম অ্যাড করি।

```js
const persons = ['Rayhan', 'Alvi', 'Anik', 'Arjun', 'Ayman', 'Ayuub', 'Bidyut'];

for (let i = 0; i < 5; i++) {
	console.log(persons[i]);
}
```

এখন যদি প্রোগ্রাম চালাই দেখা যাবে `Ayman` পর্যন্ত এসেই লুপ থেমে যাবে। কারণ আমার লুপের রেঞ্জে দেয়া আছে ইনডেক্স ৫ এর কম হতে হবে। এই সমস্যা সমাধানের জন্য আমরা ৫ এর জায়গায় ডায়নামিক্যালি `persons.length` বসিয়ে দিলেই হয়ে যাবে। তাহলে অ্যারের লেংথ যতোই বাড়ুক সে ডায়নামিক্যালি আপডেট হয়ে যাবে। এবার প্রথম উদাহরণটা যদি আমরা অ্যারে এবং লুপ দিয়ে করি তাহলে কেমন দেখাবে?

```js
const persons = ['Rayhan', 'Alvi', 'Anik', 'Arjun', 'Ayman', 'Ayuub', 'Bidyut'];

for (let i = 0; i < 5; i++) {
	console.log(students[i], students[i].toLowerCase());
}
```

তাহলে বুঝতেই পারছেন অ্যারে কতটা শক্তিশালী। অ্যারের সাথে ওতপ্রোতভাবে জড়িয়ে আছে লুপ। এই অ্যারে এবং লুপ দিয়ে আমরা অনেক কাজ সহজে এবং কম সময়ে করে ফেলতে পারি।

অ্যারেতে আমরা কি কি ধরণের ডাটা স্টোর করতে পারি। প্রায় সব প্রোগ্রামিং ল্যাঙ্গুয়েজে অ্যারেতে ডাটা স্টোর করার কিছু লিমিটেশন আছে। আর একটা অ্যারেতে এক ডাটা টাইপেরই ডাটা স্টোর করা যায়। এদিক থেকে জাভাস্ক্রিপ্ট পূর্ণ স্বাধীনতা দিয়েছে। জাভাস্ক্রিপ্টে যেকোনো ডাটা টাইপের ডাটা স্টোর করা যায়। এমনকি একটা অ্যারেতে ভিন্ন ভিন্ন ডাটা টাইপের ডাটাও স্টোর করে রাখা যায়। আমরা একটু নিচের দিকে তাকালে বুঝতে পারবো।

```js
const nums = [1, 2, 3, 4, 5, 6];
const bools = [true, true, false, false];
const nulls = [null, null, null];
const undefineds = [undefined, undefined, undefined];
const arrayOfArray = [
	[1, 2, 3],
	[4, 5, 6],
	[7, 8, 9],
];
const mixed = [true, null, 'Str', 5, [12, 2, 4]];
```

এছাড়াও অ্যারেতে অবজেক্ট এবং ফাংশনও স্টোর করা যায়। যেহেতু আমরা এখনও অবজেক্ট ও ফাংশন নিয়ে আলোচনা করিনি তাই আমরা এখানে সেটা দেখালাম না। একটা অ্যারেতে ভিন্ন ডাটা টাইপের ডাটা স্টোর করা গেলেও আমরা একটা অ্যারেতে শুধু একই ডাটা টাইপের ডাটা স্টোর করবো। কারণ হলো ধরেন আপনি ছাত্রছাত্রীর নামের একটা অ্যারে বানালেন। এখন সেখানে যদি আপনি তাদের ঠিকানা, ফোন নাম্বার সব দিয়ে রাখেন তাহলে নাম খুঁজে বের করতে কষ্ট হয়ে যাবে। তাই একটা অ্যারেতে একই টাইপের ডাটা স্টোর করে রাখা উচিৎ।

অ্যারের কিছু ফাংশনালিটিজ আছে। অ্যারেকে আমরা একটা ডাটাবেজ হিসেবে কল্পনা করতে পারি। ইন মেমোরি ডাটাবেজ। যেখানে আমরা ডাটা ক্রিয়েট করতে পারবো, রীড করতে পারবো, প্রয়োজনে আপডেট করতে পারবো এবং চাইলে ডাটা ডিলিটও করতে পারবো। এই পুরো অপারেশনকে বলা হয় **CRUD - Create, Read, Update, Delete** অপারেশন। দুনিয়াতে যত যত ডাটা স্ট্রাকচার আছে সবকিছুর কাজ এই ঘুরেফিরে CRUD। অ্যারে নিয়ে আরো কিছু আলোচনা আছে। তবে অ্যারে নিয়ে আলোচনা করতে গেলে আমাদের অবজেক্ট সম্পর্কে একটু আলোচনা আগে করা দরকার।

## Object

অ্যারেতে আমরা কিছু ছাত্রের নাম লিখলাম। কিন্তু এখন যদি আমরা তাদের ইমেইল, বয়স এবং সে কি বর্তমান ক্লাসে উপস্থিত আছে কিনা সে ইনফরমেশন স্টোর করতে চাই তাহলে অ্যারে দিয়ে করলে একটা প্রব্লেম আছে। কি প্রব্লেম সেটা আমরা একটু দেখার চেষ্টা করি।

```js
const student = ['Abu', 'Rayhan', 'rayhan@example.com', 25, true];
sendEMail(students[0]);

function sendEmail(email) {
	console.log('Sending Email to ', email);
}
```

এখন আমরা দেখি এখানে কি কি প্রব্লেম হতে পারে। প্রথমে এটা দেখে বুঝার কোনো উপায় নেই কোনটা কি ধরণের ইনফরমেশন। মানে রিডেবিলিটি নেই কোডটার। আমরা যখন কাউকে ইমেইল করতে যাবো তখন কত নাম্বার ইনডেক্সে সেই ইনফরমেশনটা আছে সেটা আমাদের মনে রাখতে হবে। এখন এখানে ৫টা ডাটা বলে নাহয় কোনোরকমে মনে রাখা গেলো। যদি ৫০০০ হয় তখন মনে রাখাটা অনেক দুষ্কর হয়ে যাবে। এই সমস্যার উত্তোরণের জন্য আমরা এটাকে অন্যভাবে লেখার চেষ্টা করি।

```js
const student = {
	firstName: 'Abu',
	secondName: 'Rayhan',
	email: 'rayhan@example.com',
	age: 25,
	attend: true,
};

sendEMail(students.email);

function sendEmail(email) {
	console.log('Sending Email to ', email);
}
```

কিছু লেখা বেশি লিখতে হলেও কোডটা সহজে পড়েই বুঝা যাচ্ছে কোনটা কি ইনফরমেশন। এখন আর আমাকে ইনডেক্স মনে রাখার দরকার নেই। জাস্ট ভ্যারিয়েবলের নামের শেষে একটা ডট (.) বসিয়ে নামটা দিলেই হয়ে যাবে। এটা আগেরটার চেয়ে অনেক বেশি রিডেবল, অনেক বেশি ইনফরমেটিভ।

এখন আমরা চাইলে অনেকগুলো ছাত্রের ইনফরমেশন একটা অ্যারেতে স্টোর করে রাখতে পারি। কিভাবে পারি? চলুন দেখি

```js
const student1 = {
	firstName: 'Abu',
	secondName: 'Rayhan',
	email: 'rayhan@example.com',
	age: 25,
	attend: true,
};

const student2 = {
	firstName: 'Alvi',
	secondName: 'Chowdhury',
	email: 'alvi@example.com',
	age: 25,
	attend: true,
};

const student3 = {
	firstName: 'Akib',
	secondName: 'Ahmad',
	email: 'akib@example.com',
	age: 25,
	attend: true,
};

const allStudents = [student1, student2, student3];
```

আমরা প্রতিটা ছাত্রের জন্য আলাদা আলাদা অবজেক্ট তৈরি করবো। এরপর প্রতিটা অবজেক্টকে আমরা একটা অ্যারের মধ্যে স্টোর করে রাকবো। অ্যারেতে যে অবজেক্টও স্টোর করে রাখা যায় এই উদাহরণের মাধ্যমে তারও প্রমাণ আপনারা পেয়ে গেলেন। এখন আমি চাইছি সব ছাত্রকে একসাথে একই ইমেইল পাঠাবো। সেক্ষেত্রে আমাদের অ্যারের উপর লুপ চালিয়ে আমরা সহজেই উপরের কোড অনুসারে একসাথে সবাইকে ইমেইল পাঠিয়ে দিতে পারি। লুপ চালিয়ে প্রথমে আমাদের অ্যারের ইনডেক্স নাম্বার দিয়ে ঐ ডাটাকে ধরতে হবে। এরপর অবজক্টের নিয়ম অনুসারে (.) বসিয়ে এরপর প্রোপার্টি নাম দিয়ে দিলেই কাজ শেষ। অ্যারে এবং অবজেক্টের সমন্বয়ে আমরা প্রোগ্রামকে কিভাবে ডায়নামিক করতে পারি তার ছোট একটি উদাহরণ আপনারা দেখলেন। আপনি যতো বড় অ্যাপ্লিকেশনই বানান ঘুরেফিরে এই কাজটাই করবেন।

javascript er object ke arektu bhalo bhabe bujha jabe jodi etake java or c# er shathe compare kora jaay. java te amra object create korte pari ekta `class` theke. and `new` keyword use kore object literal define korte pari. niche c# code er example dewa holo. which is just basically a curbon copy of java. 😂

```c#
class Student { // blue print
  String name;
  int age;

  public Student(String name, int age) { // constructor
    this.name = name;
    this.age = age;
  }

  public void doSomething() { // method
    Console.WriteLine(name + " doing something");
  }
}

Student student = new Student("john doe", 20);
student.doSomething() // -> john doe doing something
```

ei similar object ta javascript e lekha jaay ebhabe-
```js
const student = {
  name: 'jack marston',
  age: 20,
  doSomething: function() {
    console.log(this.name, 'doing something')
  }
}

student.doSomething()
```

```
## Functions

ফাংশন আমরা বানাই অনেকটা লুপের মতো কাজ করার জন্য। লুপ আমরা ব্যবহার করি একই কাজ বারবার করার জন্য। ফাংশনও আমরা ব্যবহার করবো একই কাজ বারবার করার জন্য। তাহলে লুপ থাকতে কেন আমরা ফাংশন ব্যবহার করবো?

ফাংশন আমরা বিভিন্ন জায়গায় আমাদের মতো করে ব্যবহার করতে পারবো। আমি আমার মতো করে ফাংশনকে কল করতে পারবো। ফাংশনকে আমরা রিইউজ করতে পারি, কারণ ফাংশনের একটা নাম আছে। কিন্তু লুপের কোনো নাম নেই। সুতরাং লুপকে চাইলে আমি যেখানে সেখানে ইউজ করতে পারবো না। আবার লুপ চালু হলে তাকে আমার হয় ব্রেক করে দিতে হবে, নাহয় লুপ শেষ না হওয়া পর্যন্ত চলতে দিতে হবে। লুপের উপর আমাদের কন্ট্রোল নাই। কিন্তু ফাংশনকে আমরা বিভিন্ন জায়গায় আমাদের প্রয়োজন অনুসারে ব্যবহার করতে পারবো। আমাদের প্রয়োজন অনুসারে কন্ট্রোল করতে পারবো। আগের উদাহরণ থেকে যদি আমি কয়েকটা লাইন নিই


for (let i = 0; i < allStudents.length; i++) {
 sendEmail(allStudents[i].email);
 console.log('Sending email to', allStudents[i].email);
}

function sendEmail(email) {
  console.log('Sending email to', email);
}

আমরা ফাংশন না লিখেও সেইম কাজ করতে পারতাম। কিন্তু লুপের ভিতরের লাইনটা লুপের বাইরে অন্য কোথাও কাজ করবে না। কিন্তু ফাংশন যেকোনো জায়গায় কল করা যাবে। আবার ধরেন আমার অন্য জায়গায় দরকার পুরো নাম সেটা কি আবার সেই লুপ চালিয়ে করবো। না, আমরা ফাংশন দিয়ে করবো। এক্ষেত্রে আমরা একটা বিল্ড ইন ফাংশন ব্যবহার করে দেখি।


allStudents.forEach((item) => console.log('Email ', item.email));
allStudents.forEach((item) =>
	console.log('Full Name ', item.firstName, item.secondName)
);

এক্ষেত্রে আমরা বারবার লুপ না চালিয়ে `forEach` ফাংশনটা ব্যবহার করলাম। ফাংশনের সবচেয়ে বড় সুবিধা এটাকে মাল্টিপল টাইম ব্যবহার করা যায় যেকোনো জায়গায়।

ফাংশন কখন ব্যবহার করবো আর লুপ কখন? যখন একই কাজ আমরা দুইটা ভিন্ন ভিন্ন জায়গায় করবো সেক্ষেত্রে ফাংশন। আর যদি এক জায়গাতেই হয় তাহলে লুপ। যেমন যদি আমরা ইমেইল পাঠাই, আর ইমেইলে পুরো নামের দরকার হয় সেক্ষেত্রে আমরা লুপ দিয়ে কাজ সেরে ফেলতে পারি। কিন্তু যদি আমরা এক জায়গায় ইমেইল পাঠাই, আর অন্য জায়গায় ছাত্র তালিকা তৈরির জন্য পুরো নাম দরকার হয় সেক্ষেত্রে লুপ দিয়ে কাজ হবে না। আমাদের ফাংশন ব্যবহার করতে হবে। এটা প্রাথমিক অবস্থায় বুঝানো অনেক কঠিন হবে। আস্তে আস্তে প্র্যাকটিস করতে থাকলে এটা একসময় মাথায় গেঁথে যাবে।

ফাংশন লেখার নিয়ম নিচে দেয়া হলোঃ

```js
function nameOfFunction() {
	console.log('Hello', 'Elias');
}

nameOfFunction(); // Hello Elias
nameOfFunction(); // Hello Elias
nameOfFunction(); // Hello Elias
```

এখন এখানে যতোবারই আমি কল করছি ততোবারই একই আউটপুট দিচ্ছে। বিভিন্ন জায়গায় যদি এই একই আউটপুট দরকার হয় তখন আমরা এভাবে ফাংশন তৈরি করবো। এখন আমি চাইছি ডায়নামিক্যালি নাম বসাবো। যেই নাম আমি ইনপুট দিবো সেটাই বসবে। এর জন্য আমাদের প্যারেন্থেসিসের ভেতর একটা ভ্যারিয়েবল নিতে হবে। একে বলে প্যারামিটার। আমরা একটু দেখি সেটা।

```js
function nameOfFunction(name) {
	console.log('Hello', name);
}

nameOfFunction('Murshed'); // Hello Murshed
nameOfFunction('Fahim'); // Hello Fahim
nameOfFunction(); // Hello undefined
```

আমরা যখন ফাংশন কল করবো তখন আমাদের নামটা আর্গুমেন্ট আকারে সেই প্যারামিটারের জায়গায় বসিয়ে দিবো। প্যারামিটার হলো আপনি ফাংশন লেখার সময় যে ভ্যারিয়েবলটা দিবেন। আর আর্গুমেন্ট হলো ফাংশন কল করার সময় আপনি ভ্যালু আকারে যেটা পাস করবেন। এখন যদি না বসাই তাহলে `undefined` দেখাবে। এখানে আমরা একটা সহজবোধ্য কাজ করে দিতে পারি যদি ইউজার নাম না দেয় তাহলে আমরা তাকে নাম দেয়ার জন্য একটা ম্যাসেজ দেখাতে পারি। মানে একটা এরর হ্যান্ডেল করতে পারি।

```js
function nameOfFunction(name) {
	if (!name) {
		console.log('Please provide your name');
	} else {
		console.log('Hello', name);
	}
}

nameOfFunction('Murshed'); // Hello Murshed
nameOfFunction('Fahim'); // Hello Fahim
nameOfFunction(); // Please provide your name
```

আশা করি এই উদাহরণটা সবাই বুঝতে পারি। আরেকটা উদাহরণ দেখুন কেন ফাংশন আমাদের দরকার। ধরেন আমরা ১ থেকে ১০ এর মধ্যে কোনো র‍্যানডম নাম্বার জেনারেট করতে চাইছি। তাহলে র‍্যান্ডম নাম্বার জেনারেট করার জন্য একটা ফরমুলা লিখে ফেলি।

```js
const randomNumber = Math.floor(Math.random() * 10);
```

এখন যদি ১ থেকে ১০০ এর মধ্যে চাই

```js
const randomNumber = Math.floor(Math.random() * 100);
```

এভাবে লিখতে হবে। যদি এখন ১ থেকে ১০০০ এর মধ্যে চাই

```js
const randomNumber = Math.floor(Math.random() * 1000);
```

এভাবে লিখতে হবে। এখন এতবার না লিখে আমরা এটাকে একটা ফাংশন বানিয়ে ফেলি।

```js
function generateRandomNumber(max) {
	const randomNumber = Math.floor(Math.random() * max);
	return randomNumber;
}

console.log(generateRandomNumber(10));
console.log(generateRandomNumber(100));
console.log(generateRandomNumber(1000));
```

এখন আমি যত চাই ততবার র‍্যান্ডম নাম্বার জেনারেট করতে পারবো। এখন আমি চাইছি দুইটা নাম্বারের মধ্যে একটা র‍্যান্ডম নাম্বার জেনারেট করতে।

```js
function generateRandomNumber(min, max) {
	const randomNumber = Math.floor(Math.random() * min + (max - min));
	return randomNumber;
}

console.log(generateRandomNumber(5, 10));
console.log(generateRandomNumber(85, 100));
```

তাহলে বুঝুন ফাংশন আমাদের কাজকে কতটা সহজ করে দেয়।

ekhon emon ekta example jodi chinta kori jekhane amader back to back 2 ta loop proyojon tokhon amra chaile ekta function er moddhe ekta loop e niye oi function ta ke 2 bar othoba jotobar iccha call korte pari
```js
function myLoop(arr) {
  for (let i = 0; i < arr.length; i++) {
    console.log(arr[i]);
  }
}

let arr1 = [1, 2, 3, 4, 5];
let arr2 = ["a", "b", "c", "d", "e", "f"];

myLoop(arr1); 
myLoop(arr2);
```

uporer code tay loop er bhitorer operation kintu amra ekbar e define kore diyechi. jotobar e `myLoop` function ta call hobe totobari `argument` e jei array dewa hoyeche tar item gula eke eke print korbe. But, amra jodi chai je, loop er bhitorer operation pre-defined thakbe na. tahole bhinno dhoroner operation perform korar jonne alda ekta function create korte pari.
```js
const arr = [10, 11, 12, 13, 14, 15, 16]

function customLoop(arr, callBack) {
  for (let i = 0; i < arr.length; i++) {
    callBack(arr[i]);
  }
}

function callBack(item) {
  console.log(item * 2);
}

customLoop(arr, callBack);
```

ekhane `callBack` function dara amra item gulake 2 diye multiply kore print korchi. tar mane ekhane different operation perform kora hocche. ei `callBack` function ke amra `customLoop` function er parameter e argument hishebe pass kore dicchi. then ei `callBack` ta `customLoop` function er bhitor `for` loop er moddhe call hocche. ar eta call howar somoy parameter e argument hishebe array er element gula pass kora hocche. ei callback function ke generally aladabhabe na likhe shorasori parameter er bhitorei likha jaay -

```js
const arr = [10, 11, 12, 13, 14, 15, 16]

function customLoop(arr, callBack) {
  for (let i = 0; i < arr.length; i++) {
    callBack(arr[i]);
  }
}

customLoop(arr, function (item) {
  if (item % 2 == 0) {
    console.log(item);
  }
});

// arrow function and cool syntax use koreo likha jaay
customLoop(arr, (item) => {
  item % 2 == 0 && console.log(item)
})
```

ekhane koyekta interger er ekta array and ekta callback function pass korchi. and function tar moddhe shudhu even integer gulai print hobar operation define kore diyechi.
similar statement ta js er built in method diyeo kora jaay. jemon `forEach` method use kore -

```js
const arr = [10, 11, 12, 13, 14, 15, 16]
arr.forEach((item) => item % 2 == 0 && console.log(item))
```

for each ke amra function bolchi na. instead etake `method` bolchi. karon ekta function ke method tokhon e bolbo jokhon sheta kono object ke belong kore. `forEach` function ta js er `array` object ke belong kore. ekta example diye bisoy ta bujha jaak -
```js
function doSomething() {
  console.log('a random function')
}

const student = {
  name: 'jack',
  age: 20,
  doSomething: function() {
    console.log('a random function')
  }
}
student.doSomething()
```
uporer code tay prothom `doSomething` holo function. ar sudent object er bhitorer `doSomething` ke function na bole `method` bolbo. etake key value hishebe na likhe direct value hishebe lekha jaay. for example -
```js
const obj = {
  name: 'john doe',
  myFunc() {
    console.log(this.name)
  }
}
obj.myFunc()
```

## Expression vs Statement

এই বিষয় বুঝার আগে আমরা একটু কিছু উদাহরণ দেখি

```js
const name1 = 'Rayhan'; // Statement
const name2 = 'Alvi'; // Statement

const students = [
	'Rayhan',
	'Alvi',
	'Anik',
	'Arjun',
	'Ayman',
	'Ayuub',
	'Bidyut',
]; // Statement

console.log(students[0]); // Expression
console.log(students[1]); // Expression

for (let i = 0; i < students.length; i++) {
	console.log(students[i], students[i].toLowerCase()); // Expression
} // Statement

name1.sendEmail(); // Expression
name2.sendEmail(); // Expression

const nums = [1, 2, 3, 4, 5, 6]; // Statement
const mixed = [true, null, 'Str', 5, [12, 2, 4]]; // Statement

const student1 = {
	firstName: 'Abu',
	secondName: 'Rayhan',
	email: 'rayhan@example.com',
	age: 25,
	attend: true,
}; // Statement

const student2 = {
	firstName: 'Alvi',
	secondName: 'Chowdhury',
	email: 'alvi@example.com',
	age: 25,
	attend: true,
}; // Statement

const student3 = {
	firstName: 'Akib',
	secondName: 'Ahmad',
	email: 'akib@example.com',
	age: 25,
	attend: true,
}; // Statement

const allStudents = [student1, student2, student3]; // Statement

for (let i = 0; i < allStudents.length; i++) {
	sendMail(allStudents[i].email); // Expression
} // Statement

function sendMail(email) {
	console.log('Sending email to', email);
} // Statement

allStudents.forEach((item) => console.log('Email ', item.email)); // Expression
allStudents.forEach((item) =>
	console.log('Full Name ', item.firstName, item.secondName)
); // Expression

function nameOfFunction(name) {
	if (!name) {
		console.log('Please provide your name');
	} else {
		console.log('Hello', name);
	}
} // Statement

nameOfFunction('Murshed'); // Expression
nameOfFunction('Fahim'); // Expression
nameOfFunction(); // Expression

function generateRandomNumber(min = 1, max) {
	const randomNumber = Math.floor(Math.random() * min + (max - min)); // Statement
	return randomNumber; // Expression
} // Statement

console.log(generateRandomNumber(5, 10)); // Expression
```

Expression and Statement এর মধ্যে বেসিক যে পার্থক্য সেটা হলো এক্সপ্রেশন দিন শেষে কিছু না কিছু রিটার্ন করে, ডাটা প্রোডিউস করে, এবং একে কোনো এক জায়গায় স্টোর করে রাখা যায়। সেই হিসেবে ফাংশন কল এক ধরণের এক্সপ্রেশন। আর স্টেটমেন্ট কোনো ডাটা প্রোডিউস করেনা, কোথাও স্টোর করে রাখা যায় না, কিছু রিটার্ন করে না। ফাংশন লেখা হচ্ছে স্টেটমেন্ট, আর ফাংশন কল হচ্ছে এক্সপ্রেশন। কারণ ফাংশন লিখলে তা কিছু রিটার্ন করে না যতক্ষণ পর্যন্ত কল করা না হচ্ছে। আবার যদি অ্যারো ফাংশন লেখা হয় সেটা এক্সপ্রেশন কারণ সেটাকে একটা ভ্যারিয়েবলে স্টোর করে রাখা হচ্ছে।

### function expression
```js
function myFunc() {}
```
eta function statement er ekta example. jodi etake expression akare likhte chai tahole function ta kono ekta variable e assign korte hobe.
```js
const myFunc = function () {};
```
es6 er syntax use kore-

```js
const myFunc = () => {};
```
ekhane, 1st way ke function `declaration` or `statement` bole. ar 2nd way ke bole function `expression`. ei bisoy ta hoisting er shathe jorito. ja next kono ek lecture e alochona kora hobe.

function declaration vs expression somporke details e bujhte chaile ei link ta recommended. [function statement vs expression](https://www.geeksforgeeks.org/difference-between-function-declaration-and-function-expression-in-javascript/)

javascript er statement vs expression bhujhte ei video [statement vs expression in js](https://www.youtube.com/watch?v=WVyCrI1cHi8)

## কোথায় অ্যারে ব্যবহার করবো আর কোথায় অবজেক্ট?

যে টার্মগুলো Singular সেখানে আমরা ব্যবহার করবো অবজেক্ট। যেখানে Plural সেখানে আমরা ব্যবহার করবো অ্যারে। যেমন একটা ফোন - অবজেক্ট, অনেকগুলো ফোন - অ্যারে, person - object, people - array, member - object, members - array। যেখানে একজন বা একটা কিছুর ইনফরমেশন সেখানে অবজেক্ট। যেখানে একের অধিক লোক বা একের অধিক অবজেক্ট বা বস্তু আসবে সেখানেই আমরা অ্যারে ব্যবহার করবো। জাস্ট এই কথাটা মাথায় রাখবেন। জীবনে আর অ্যারে আর অবজেক্ট নিয়ে গুলিয়ে ফেলবেন না।

## জাভাস্ক্রিপ্টে ভাল দখল আনার জন্য কোন কোন বিষয়ের উপর জোর দিতে হবে?

- Arrays
- Objects
- Functions and Functional Programming
- Basic OOP
