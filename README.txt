AMAR BAZAR — FIREBASE STARTER (মোবাইল-ফ্রেন্ডলি)

এই প্যাকেজে:
- index.html: কাস্টমারদের দোকান; Firebase সেটআপের পর Firestore-এ অর্ডার জমা দেয়।
- admin.html: অ্যাডমিন লগইন করে অর্ডার দেখতে ও স্ট্যাটাস আপডেট করতে পারেন।
- firestore.rules: অর্ডারের জন্য প্রাথমিক নিরাপত্তা নিয়ম।

গুরুত্বপূর্ণ:
এটি প্রস্তুত প্যাকেজ/স্টার্টার কোড, এখনো লাইভ স্টোর বা ইনস্টল করার Android APK নয়।
Firebase config এবং Admin UID না বসালে অর্ডার জমা/অ্যাডমিন লগইন কাজ করবে না।
পণ্যের দামগুলো নমুনা। এই ডেমোতে পণ্যের তালিকা HTML-এ আছে; অ্যাডমিন থেকে পণ্য যোগ/দাম পরিবর্তনের সুবিধা এখনো নেই।
অর্ডারের তথ্য ব্যক্তিগত—কখনো Firestore-এ read: if true; allow all ধরনের উন্মুক্ত নিয়ম ব্যবহার করবেন না।

মোবাইল দিয়ে Firebase সেটআপের ধাপ:
1. মোবাইল ব্রাউজারে https://console.firebase.google.com খুলুন এবং Google অ্যাকাউন্ট দিয়ে সাইন ইন করুন।
2. Add project চাপুন; নাম দিন amar-bazar (অথবা উপলভ্য অন্য project ID)।
3. Project তৈরি হলে Build → Firestore Database → Create database নির্বাচন করুন। শুরুতে production mode বেছে নিন।
4. Project settings → General → Your apps → Web app (</>) যোগ করুন। অ্যাপের নাম Amar Bazar দিন। Firebase config দেখাবে।
5. index.html এবং admin.html-এর মধ্যে firebaseConfig অবজেক্টে PASTE_ দিয়ে শুরু হওয়া মানগুলোর বদলে নিজের config-এর মান বসান।
   Firebase config সাধারণত ওয়েব অ্যাপে ব্যবহারের জন্য তৈরি; তবে নিরাপত্তা Firestore Rules ও Authentication দিয়ে নিয়ন্ত্রণ করতে হবে।
6. Build → Authentication → Get started → Sign-in method-এ Email/Password চালু করুন।
7. Authentication → Users-এ আপনার নিজের অ্যাডমিন ইমেইল দিয়ে Add user করুন। তৈরি হওয়া UID কপি করুন।
8. firestore.rules ফাইলের PASTE_ADMIN_UID_HERE-এ ওই UID বসান।
9. Firestore Database → Rules-এ firestore.rules-এর সম্পূর্ণ নিয়ম পেস্ট করে Publish করুন।
10. index.html ও admin.html-কে HTTPS-এ হোস্ট করতে হবে (যেমন Firebase Hosting বা অন্য স্থির হোস্টিং)। ফোনে ফাইল সরাসরি খুললে module/Firebase কাজ নাও করতে পারে।
11. Admin পেজে নিজের ইমেইল ও পাসওয়ার্ড দিয়ে লগইন করুন। প্রথমে একটি পরীক্ষামূলক অর্ডার করে যাচাই করুন।

অর্ডার ও নিরাপত্তা:
- গ্রাহকের অর্ডার Firestore-এ যাবে; শুধু Admin UID-র অ্যাকাউন্ট অর্ডার পড়তে/পরিবর্তন করতে পারবে।
- Admin UID ভুল বসালে অ্যাডমিন অর্ডার দেখতে পারবেন না।
- বাস্তব ব্যবসায় চালুর আগে নিয়ম, অর্ডার যাচাই, স্প্যাম/ভুয়া অর্ডার প্রতিরোধ, গোপনীয়তা নীতি এবং ব্যাকআপ পরীক্ষা করান।
- গ্রাহক ডেটা অপ্রয়োজনীয়ভাবে শেয়ার করবেন না।
