## নন স্ট্যাটিক কনটেক্সট 

আমরা আগের সেকশনে প্রোপার্টি দেখার সময় দেখেছি `$this` এর ব্যবহার । আমরা জেনেছি কোন ক্লাসের ভিতর যদি এই ভ্যারিয়েবলটি ব্যবহার করা হয় তাহলে ঐ ক্লাসের যতগুলো ইনস্ট্যান্স তৈরি করবো আমরা প্রতে্যকটির ভিতরে `$this` কিওয়ার্ড ঐ অবজেক্ট এ পয়েন্ট করবে । 

আগের উদাহরনটিই আরেকবার দেখে নেই: 

```php
<?php

class Person
{
    public $age;

    public function getAge()
    {
        return $this->age;
    }
}


$person = new Person();
$person->age = 32;

$anotherPerson = new Person();
$anotherPerson->age = 45;

var_dump($person->getAge());
var_dump($anotherPerson->getAge());
```

এখানে দেখুন, আমরা যখন `$person->getAge()` কল করছি তখন আমরা `$person` এর `age` প্রোপার্টি পাচ্ছি, আবার যখন `$anotherPerson->getAge()` কল করছি তখন পাচ্ছি `$anotherPerson` এর বয়স । অর্থাৎ, একই `$this` ভ্যারিয়েবলটি `$person` অবজেক্টের ভিতর `$person` কে এবং `$anotherPerson` ভিতরে `$anotherPerson` কে নির্দেশ করছে । 

এর ফলে, একটি ক্লাস থেকে তৈরি করা সব ইনস্ট্যান্সই তার নিজের প্রোপার্টি বা মেথড এ্যাক্সেস করতে পারে এই `$this` ভ্যারিয়েবল এর মাধ্যমে । তাই আলাদা আলাদা ইনস্ট্যান্সে একই প্রোপার্টির ভিন্ন ভিন্ন ভ্যালু থাকলেও আমরা এই ভ্যারিয়েবলটির মাধ্যমে ঐ ইনস্ট্যান্সের ভ্যালুটি জেনে নিতে পারছি খুব সহজেই! 

এই যে একই ক্লাস থেকে তৈরি করা অবজেক্ট ইনস্ট্যান্স গুলোর ভ্যালু আলাদা আলাদা হতে পারে এটাই হলো নন-স্ট্যাটিক কনটেক্সট । এই কনটেক্সট এ কোন প্রোপার্টি বা মেথড শুধু ঐ ইনস্ট্যান্স স্পেসিফিক হয় । 


## স্ট্যাটিক কনটেক্সট 

কখনো কখনো কিছু প্রোপার্টি বা মেথড আমাদের সব ইনস্ট্যান্সের জন্যই কমন হয় । এই প্রোপার্টি গুলো বা মেথড গুলো আলাদা আলাদা ইনস্ট্যান্স এর জন্য আলাদা হওয়ার দরকার নেই, বরং ঐ ক্লাসের সবার জন্যই একই । এই মেথড বা প্রোপার্টি তাই সবাই এক সাথে শেয়ার করতে পারে । যেমন ধরুন, আমি চাই একটি `$count` প্রোপার্টি যেটির ভ্যালু সব অবজেক্ট ইনস্ট্যান্স শেয়ার করুক । অর্থাৎ যে কোন ইনস্ট্যান্স থেকেই আমি এই প্রোপার্টির ভ্যালু একই পাই । এক্ষেত্রে আমাকে এই প্রোপার্টি-টিকে স্ট্যাটিক হিসেবে ডিক্লেয়ার করতে হবে । তখন আমার ঐ ক্লাস থেকেই আমি সরাসরি এটি এ্যাক্সেস করতে পারবো, আমার অবজেক্ট ইনস্ট্যান্স তৈরি না করলেও চলবে । এটাই হচ্ছে স্ট্যাটিক কনটেক্সট । একটি উদাহরন দেখলে আরো ভালো বোঝা যাবে --

```php
<?php

class Person
{
    public static $count;

    public static function getCount()
    {
        return self::$count;
    }
}


Person::$count = 34;
var_dump(Person::$count);

$person = new Person();
var_dump($person->getCount());

Person::$count = 23;
var_dump(Person::$count);

var_dump($person->getCount());


$anotherPerson = new Person();
var_dump($anotherPerson->getCount());

```

 উদাহরনটি একটু জটিল, তাই কয়েকবার ভালো করে পড়ুন । কোড রান করে আউটপুট ভালো করে মিলিয়ে নিন । 
 
দেখুন, এখানে `Person` ক্লাসে `$count` একটি স্ট্যাটিক প্রোপার্টি এবং `getCount()` একটি স্ট্যাটিক মেথড । এখান থেকে লক্ষ্যনীয়: 
 
 * স্ট্যাটিক মেথড বা প্রোপার্টি ডিফাইন করতে আমরা `static` কিওয়ার্ডটি ব্যবহার করি । 
 * `$this` এর মত `self` এর মাধ্যমে আমরা স্ট্যাটিক কনটেক্সট এ প্রোপার্টি বা মেথড এ্যাক্সেস করি । 
 * নন স্ট্যাটিক কনটেক্সট এ `->` ব্যবহার করা হয় এ্যাক্সেস করার জন্য । স্ট্যাটিক কনটেক্সট এ `::` । 
 * স্ট্যাটিক কনটেক্সট এ প্রোপার্টির নামের আগে ভ্যারিয়েবল সাইন থাকে । নন-স্ট্যাটিক কনটেক্সট এ থাকে না । স্ট্যাটিক কনটেক্সট এ তাই ভ্যারিয়েবল ভ্যারিয়েবল এর মত করে এ্যাক্সেস করতে চাইলে আরেকটি ভ্যারিয়েবল সাইন যোগ করতে হয় । 
 * স্ট্যাটিক মেথড কিংবা প্রোপার্টি কোন ইনস্ট্যান্স তৈরি না করেই সরাসরি ক্লাস এর নাম দিয়েই এ্যাক্সেস করা যায় । 
 * স্ট্যাটিক প্রোপার্টি বা মেথড ঐ ক্লাসের সব ইনস্ট্যান্সই এ্যাক্সেস করতে পারে । এর ভ্যালু সব ইনস্ট্যান্সেই একই থাকে । এটা নন-স্ট্যাটিক কনটেক্সট এ (যেমন ইনস্ট্যান্স এর ভিতর থেকে) পরিবর্তন করা যায় না । 


নন-স্ট্যাটিক কনটেক্সট থেকে স্ট্যাটিক কনটেক্সট এ্যাক্সেস করা যায় কারন স্ট্যাটিক কনটেক্সট সবার জন্য একই । কিন্তু স্বাভাবিকভাবেই এর উল্টোটা করা সম্ভব হয় না । 
 
 ## `$this` এবং `self` 
 
 এতক্ষনে আমরা বুঝে ফেলেছি এ দুটোর পার্থক্য । তবু বলি - `$this` নির্দেশ করে অবজেক্ট ইনস্ট্যান্স কে, `self` নির্দেশ করে ঐ ক্লাস কে । 