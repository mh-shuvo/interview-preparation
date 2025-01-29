# Laravel Advanced Interview Questions & Answers

## 1. Laravel Middleware কী এবং এটি কীভাবে কাজ করে?
Middleware হল HTTP অনুরোধের (Request) এবং প্রতিক্রিয়ার (Response) মধ্যে একটি ফিল্টার হিসেবে কাজ করা একটি কম্পোনেন্ট। এটি authentication, logging, এবং CORS চেকের মতো কাজ সম্পাদন করতে ব্যবহৃত হয়।

### Middleware কীভাবে request lifecycle এ কাজ করে?
- যখন কোনো request Laravel-এর কাছে আসে, তা প্রথমে Middleware-এর মধ্য দিয়ে যায়।
- Middleware নির্দিষ্ট শর্ত অনুযায়ী request অনুমোদন বা বাতিল করতে পারে।
- অনুমোদিত request Routing Layer-এ যায় এবং Controller-এ পৌঁছে।
- Response ফেরত আসার আগেও Middleware সেটিকে প্রসেস করতে পারে।

**Middleware তৈরি করার কমান্ড:**
```bash
php artisan make:middleware CheckUserRole
```

Middleware রেজিস্টার করা হয় `app/Http/Kernel.php` ফাইলে।

---

## 2. Laravel-এর Facade কী? এটি কীভাবে কাজ করে?
Facade হল একটি স্ট্যাটিক ইন্টারফেস যা Laravel-এর Service Container-এ থাকা ক্লাসের অ্যাক্সেস সহজ করে। এটি মূলত `Proxy` ডিজাইন প্যাটার্ন অনুসরণ করে।

### Facade-এর উপকারিতা:
- সহজ ও স্বল্প কোডে কমপ্লেক্স ফাংশনালিটি ব্যবহার করা যায়।
- সার্ভিস কন্টেইনারের সরাসরি ডিপেন্ডেন্সি না থাকায় টেস্টিং সহজ হয়।

**উদাহরণ:**
```php
use Illuminate\Support\Facades\Cache;

Cache::put('key', 'value', 600);
$value = Cache::get('key');
```

---

## 3. Laravel Query Builder ও Eloquent ORM-এর পার্থক্য কী?
| বিষয় | Query Builder | Eloquent ORM |
|--------|---------------|---------------|
| পারফরম্যান্স | বেশি পারফরম্যান্ট | তুলনামূলক ধীর |
| কোডিং স্টাইল | SQL-এর কাছাকাছি | OOP-based |
| সম্পর্ক | সম্পর্ক ম্যানেজ করতে পারে না | Model Relationships ব্যবহার করা যায় |

**যখন Query Builder ব্যবহার করবেন:**
- যদি খুব বড় ও জটিল কাস্টম SQL কোয়েরি দরকার হয়।
- যখন পারফরম্যান্স অপটিমাইজেশনের দরকার হয়।

**যখন Eloquent ORM ব্যবহার করবেন:**
- যখন কোডিং স্টাইল ক্লিন এবং মডেল-ভিত্তিক হতে হবে।
- যখন `hasMany`, `belongsTo` এর মতো রিলেশন দরকার।

---

## 4. Laravel Job এবং Queue কীভাবে কাজ করে?
Laravel Queue ব্যবহার করে ব্যাকগ্রাউন্ড প্রসেসিং করা যায়। Queue সার্ভার যেমন Redis, Beanstalk, অথবা Database ব্যবহার করা হয়।

**ইমেইল পাঠানো ব্যাকগ্রাউন্ডে প্রসেস করানোর উপায়:**
```php
use App\Jobs\SendEmailJob;

dispatch(new SendEmailJob($user));
```

Queue চালু করার জন্য:
```bash
php artisan queue:work
```

---

## 5. Laravel-এর Event Listener কী এবং এটি কোথায় ব্যবহার করা হয়?
Laravel Event Listener ব্যবহার করা হয় asynchronous কার্যকলাপ পরিচালনার জন্য। এটি মূলত Observer প্যাটার্ন অনুসরণ করে।

**Observer vs Event-Listener পার্থক্য:**
| বিষয় | Observer | Event-Listener |
|--------|------------|----------------|
| কী ট্রিগার করে | মডেল ইভেন্ট (create, update) | কাস্টম ইভেন্ট |
| কোডিং স্টাইল | নির্দিষ্ট মডেল নির্ভর | কাস্টম হ্যান্ডলিং |

**Event তৈরি করা:**
```bash
php artisan make:event UserRegistered
php artisan make:listener SendWelcomeEmail --event=UserRegistered
```

---

## 6. Laravel-এ Singleton প্যাটার্ন কোথায় ব্যবহার করা হয়?
Singleton প্যাটার্ন ব্যবহার করা হয় সার্ভিস কন্টেইনারে এমন কিছু ক্লাস একবার instantiate করতে যেগুলোর একাধিক instance দরকার হয় না।

**উদাহরণ:**
```php
app()->singleton('App\Services\PaymentService', function () {
    return new PaymentService();
});
```

---

## 7. Laravel Service Container কীভাবে Dependency Injection পরিচালনা করে?
Service Container Dependency Injection পরিচালনা করে bind এবং singleton পদ্ধতির মাধ্যমে।

**Dependency Injection ও Service Container-এর সম্পর্ক:**
- Dependency Injection ক্লাসগুলোর উপর সরাসরি নির্ভরশীলতা কমিয়ে দেয়।
- Service Container ব্যবহার করে ডিপেন্ডেন্সি রেজলভ করা যায়।

**Binding Service Container:**
```php
app()->bind('App\Contracts\UserRepository', 'App\Repositories\EloquentUserRepository');
```

---

## 8. Laravel-এ Cache কীভাবে কাজ করে এবং কোন কোন ক্যাশিং ড্রাইভার রয়েছে?
Laravel বিভিন্ন ক্যাশিং ড্রাইভার সাপোর্ট করে, যেমন **file, database, redis, memcached**।

**Query Cache, View Cache, এবং Config Cache-এর মধ্যে পার্থক্য:**
| ক্যাশিং | কাজ | কমান্ড |
|------------|---------------|------------------|
| Query Cache | ডাটাবেজ কোয়েরির রেজাল্ট সংরক্ষণ করে | `Cache::remember('users', 60, function () { return User::all(); });` |
| View Cache | Blade টেমপ্লেট কম্পাইল করে সংরক্ষণ করে | `php artisan view:cache` |
| Config Cache | Config ফাইলগুলোর ভ্যালু ক্যাশে রাখে | `php artisan config:cache` |

---

## উপসংহার
Laravel-এর এই বিষয়গুলো ভালোভাবে বুঝতে পারলে আপনার ইন্টারভিউ প্রস্তুতি অনেক বেশি শক্তিশালী হবে। আরও ভালো বোঝার জন্য অফিসিয়াল ডকুমেন্টেশন পড়ুন এবং প্রকল্পে প্রয়োগ করুন। 🚀
