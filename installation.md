# ইনস্টলেশন

আর দশটা প্রোগ্রামিং ল্যাঙ্গুয়েজের মত পিএইচপিও কমান্ড লাইন থেকে চালানো সম্ভব । কিন্তু পিএইচপির জন্ম হয়েছিলো ওয়েব অটোমেশনের জন্য, পিএইচপির ব্যবহারও তাই মূলত সার্ভার কেন্দ্রিক । পিএইচপি ভালো করে শিখতে হলে সার্ভার এনভায়রনমেন্ট সম্পর্কে ভালো ধারণা থাকাটা জরুরী । নবীনদের জন্য পিএইচপির সাথে এ্যাপাচি হবে সার্ভার হিসেবে ভালো চয়েস । একই সাথে আমাদের আরও শিখে রাখা দরকার একটি ডাটাবেইজ সিস্টেম । অন্যান্য অধিকাংশ ডাটাবেইজ সিস্টেমের জন্য সাপোর্ট থাকলেও, পিএইচপির সাথে মাইসিকুয়েল (MySQL) এর প্রবল জনপ্রিয়তা চোখে পড়ার মত । তাই আমাদের ইন্সটলেশন সেকশনে আমরা দেখবো কিভাবে পিএইচপি, এ্যাপাচি এবং মাইসিকুয়েল ইন্সটল করা যায় । 

### উইন্ডোজ 

আমি ব্যক্তিগতভাবে বিশ্বাস করি মাইক্রোসফটের নিজেদের ডেভেলপমেন্ট প্ল্যাটফর্ম ডট নেট ছাড়া বাকি যে কোন ধরনের প্রোগ্রামিং এর জন্যই উইন্ডোজ একটি বাজে চয়েস । লিনাক্স বা ইউনিক্স এনভায়রনমেন্ট পিএইচপি ডেভেলপমেন্ট এর জন্য উৎকৃষ্ট । ইন ফ্যাক্ট, আপনি উইন্ডোজে পিএইচপির সব ফিচার পাবেন ও না । তাই আমি রিকমেন্ড করি পিএইচপির জন্য উবুন্টু বা ম্যাক ওস এক্স ব্যবহার করার জন্য । সেটা সম্ভব না হলে ভার্চুয়াল বক্সে লিনাক্স চালানোর জন্য । একেবারে নিরুপায় হলেই উইন্ডোজে পিএইচপি চালানো উচিৎ । উইন্ডোজে হয়তো আপনার কাজ চলে যাবে কিন্তু পিএইচপি ট্র্যাকে ক্যারিয়ারে উপরে উঠতে গেলে আপনাকে আজ হোক কাল হোক উইন্ডোজ ছাড়তেই হবে । বলাই বাহূল্য, আপনার ডেভেলপ করা এ্যাপ্লিকেশন ৯৯% ক্ষেত্রেই লিনাক্স হোস্টিং এ চলবে । সুতরাং, এগিয়ে থাকতে চাইলে এখনই সময় পিএইচপির জন্য অন্য কোন অপারেটিং সিস্টেম ব্যবহার করা । 

উইন্ডোজে পিএইচপি, এ্যাপাচি এবং মাইসিকুয়েল সেটাপ করার জন্য <a href="https://www.apachefriends.org/index.html">XAMPP</a> জনপ্রিয় । এটি ডাউনলোড করে ইন্সটল করে নিলেই পেয়ে যাবেন আপনার ডেভেলপমেন্ট এনভায়রনমেন্ট । 

### লিনাক্স 

পিএইচপি ডেভেলপমেন্টের আসল মজাটা পাওয়া যায় লিনাক্সে । পিএইচপি, এ্যাপাচি এবং মাইসিকুয়েল সেটাপ করার জন্য আপনার লিনাক্স ডিস্ট্রোর প্যাকেজ ম্যানেজার ব্যবহার করুন । যারা উবুন্টু কিংবা উবুন্টু এর কোন ভ্যারিয়ান্ট ব্যবহার করছেন, তাদের জন্য এই ছোট্ট কমান্ডটি টার্মিনালে টাইপ করে এন্টার চাপলেই হবে: 

```bash
sudo apt-get install lamp-server^
```

লিনাক্সের জন্যও XAMPP এর একটি ভার্সন আছে । কিন্তু সবকিছু রিপোজিটরি থেকে সেটাপ করে নেওয়াটাই বুদ্ধিমানের কাজ । এত ঝামেলা কম হয়, পরে প্রয়োজন হলে ট্রাবলশুটিং এও সমস্যা কম হবে । এছাড়া পিএইচপি রিলেটেড প্রচুর প্যাকেজ পাওয়া যাবে উবুন্টু সফটওয়্যার রিপোজিটরি থেকে যেগুলোও খুব সহজে ইনস্টল করে নিতে পারবেন । 

### ম্যাক ওএস এক্স

ওসএক্স এ বাই ডিফল্ট এ্যাপাচি থাকে । পিএইচপি এবং মাইসিকুয়েল টা <a href="http://brew.sh">হোমব্রু</a> এর মাধ্যমে ইনস্টল করে নেওয়া ভালো । বিস্তারিত ইন্সট্রাকশন পাওয়া যাবে এখানে - <a href="https://github.com/Homebrew/homebrew-php">https://github.com/Homebrew/homebrew-php</a> । 

এছাড়াও উইন্ডোজের মতই সবকিছু একই প্যাকেজে পাওয়া যাবে <a href="http://www.mamp.info/en/">MAMP</a> এর মাধ্যমে । তবে হোমব্রু এর মাধ্যমে সেটাপ করাটাই আমি রিকমেন্ড করি । প্রথমে একটু ঝামেলা মনে হলেও পরবর্তীতে এক্সটেনশন ইন্সটল করা কিংবা কমান্ড লাইন থেকে পিএইচপি রান করার জন্য হোমব্রু পিএইচপিই বেটার অপশন । সেই তুলনায় MAMP ব্যবহার করা সহজ কিন্তু কাস্টোমাইজেশন এর জন্য বেশ রেস্ট্রিক্টিভ । 