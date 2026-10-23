# Free Fire Esports Manager — Localhost MVP

এটি একটি প্রাথমিক, লোকাল-কম্পিউটারে চালানো যায় এমন Flask + SQLite ওয়েব অ্যাপ।

## ফিচার
- Admin ও Player login
- Player account তৈরি (Admin)
- BR ও CS ম্যাচের ফলাফল সংরক্ষণ
- Daily training task assign/complete
- Player ranking: kills, average damage, BR average placement, CS round totals
- Player match history ও coach review
- Dark professional esports UI
- SQLite ডেটাবেস (`team.db`) স্বয়ংক্রিয়ভাবে তৈরি হয়

## চালাতে যা লাগবে
- Windows 10/11 হলে Python 3.10 বা নতুন সংস্করণ
- ইন্টারনেট শুধু প্রথমবার Flask প্যাকেজ ইনস্টল করতে লাগবে; এরপর লোকালি চলবে।

## Windows-এ চালানো
1. ZIP ফাইল Extract করুন।
2. `run_windows.bat`-এ ডাবল-ক্লিক করুন। অথবা Command Prompt-এ ফোল্ডারে গিয়ে চালান:
   ```bat
   py -m venv .venv
   .venv\Scripts\activate
   pip install -r requirements.txt
   python app.py
   ```
3. ব্রাউজারে খুলুন: http://127.0.0.1:5000

## Demo login (প্রথম চালু করার পর)
- Admin: `admin` / `Admin123!`
- Player: `player1` / `Player123!`

**গুরুত্বপূর্ণ:** এগুলো demo password। নিজের কম্পিউটারে ব্যবহারের আগে `app.py`-তে seed password পরিবর্তন করুন অথবা অ্যাপ চালু করে admin থেকে player account তৈরি করুন। MVP-তে password পরিবর্তনের পেজ নেই, তাই বাস্তব/পাবলিক সার্ভারে সরাসরি ব্যবহার করবেন না।

## প্রথমবার ব্যবহার
1. Admin হিসেবে লগইন করুন।
2. `Players` থেকে ৫–৭ জনের account তৈরি করুন (প্রতিটি password কমপক্ষে ৮ অক্ষর)।
3. `Training` থেকে প্রতিদিনের কাজ দিন: Aim, Gloo Wall, Movement, Close-range, BR Rotation, CS Entry/Trade ইত্যাদি।
4. `Matches` থেকে BR/CS ম্যাচের stats যোগ করুন। BR-এর ক্ষেত্রে placement দিন; CS-এর ক্ষেত্রে rounds won/lost দিন।
5. `Coach Reviews` থেকে strength, improvement area ও next goal লিখুন।
6. `Ranking` ও প্রতিটি player-এর `History` দেখে সাপ্তাহিক পর্যালোচনা করুন।

## ম্যাচ ডেটা কীভাবে নেবেন
- Manual entry: ম্যাচ শেষে player/admin form পূরণ করবে।
- Screenshot: এই MVP-তে screenshot file upload বা OCR এখনো নেই। স্ক্রিনশট দেখে stats form-এ হাতে লিখুন। পরের সংস্করণে image upload/OCR যোগ করা যাবে।

## ডেটা কোথায় থাকে?
`team.db` ফাইলে। ব্যাকআপের জন্য অ্যাপ বন্ধ করে ফাইলটি কপি করুন।

## নিরাপত্তা ও সীমাবদ্ধতা
- এটি localhost MVP, production deployment নয়।
- `debug=True` শুধু লোকাল ডেভেলপমেন্টের জন্য।
- Localhost-এ নিজের কম্পিউটারেই ব্যবহার করুন; port forwarding করে ইন্টারনেটে প্রকাশ করবেন না।
- Ranking সহজ পরিসংখ্যানভিত্তিক; এটি skill-এর সম্পূর্ণ মূল্যায়ন নয়। Teamplay, survival, utility, decision-making ও coach review-ও দেখুন।
- Demo version-এ account deletion, password reset, CSV export, file upload/OCR এবং automated Free Fire API integration নেই।
