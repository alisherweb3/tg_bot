# tg_bot
Ob havoni ko'rsatadigan telegram bot.


Bunaqa telegram bot yozish uchun bizga birinchi navbatda, ob havo ma'lumotlari kerak, ularni qayerdan olamiz? saytdan parsit qilish yoki API olish mumkin. 

Oxirida, Githubdagi alohida repositariylarni tashlab qo'yamiz.

Bu ishni qanday bajaramiz deysizmi? Internetda juda ham ko'plab ob havo API lari mavjud. masalan API Yandex Pogoda.

Chunki bu yerda test mode da bepul meteo data ni so'rash mumkin.

BU API faqat koordinatalarni qabul qiladi. Bizga esa shahar nomi kerak, raqamlar emas, shuning uchun, API yandex.geocoder dan foydalanamiz.

### API nima -- ( Application programming Interface ) - internetdan oson tarzda ma'lumotni yig'adigan dastur. hozircha shuni o'zini bilish kifoya, keyin yana to'xtalamiz.

API nima uchun mashhur va qulay?

API ni ishlatilishidan bir misol keltiramiz. Masalan: YouTube, Youtube da Frontend va BackEnd bor, va ularni API birlashtiradi. Chunki YouTubeda juda ko'p ma'lumot bor. va juda ko'pchilik foydalanadi, Shuning uchun serverlarni alohida ajratish, saytni tez ishlashiga olib keladi va har bir kishi uchun alohida Frontend ko'rsatadi. Har bir kishi uchun, xususiy YouTube bor. Hech kimniki bir biriga o'xshamaydi.

### GET -- Biror bir resursdan ma'lumotni chaqirib oladi. Masalan siz github saytini reload qilsangiz, sizning brauzeringiz github.com ga GET buyrug'ini beradi.

### POST -- Qaysidir ma'lumotlarni serverga yuborish, masalan saytga kirish uchun , login parolni yozgandan keyin, POST buyrug'i, sayt serveriga, siz kiritgan ma'lumotlarni yuboradi.

PUT -- POST ga o'xshab ketadi, lekin PUT, ma'lumotlarni yangilaydi.

DELETE -- qaysidir resursni o'chiradi.

Ko'pincha GET va POST ishlatiladi.


ENDI birinchi navbatda Yandex Pogoda ni kalitini olishimiz kerak. 

Bu uchun Yandex.ru dan ro'yxatdan o'tamiz.

Keyin esa developer.tech.yandex.ru - dasturchilar kabinetiga kiramiz va "API ni ulash" tugmasini bosamiz. Endi bizni JavaScript API , HTTP geocoder va API yandex pogoda qiziqtiradi. Test tarifini belgilaymiz. Ism familiyani, Kompaniya nomini (xoxlagan nom), bepul versiya, ochiq sistema, na karte ni belgilaymiz.

Ana endi sizga kalit berildi.

VA Nihoyat kod yozish vaqti yetib keldi.

Python IDE siga kiramiz. va ```requirements.txt``` va ```.gitignore``` fayllarini ochamiz.

Keyin esa Git da ```py -m venv myenv``` deb yozamiz  va ```source myenv/scripts/activate``` deb uni ishga tushiramiz.

endi ```config.py``` degan fayl ochamiz. bu fayl bizni API kalitlarimizni o'z ichida saqlaydi.

va oxirida, API yandex Pogoda ni qanday ishlayotganini tekshirish uchun ```request.py``` dagan fayl ochamiz.

Endi esa API ishlayotganini ko'rish uchun mana bu <a href="yandex.ru/dev/weather/doc/dg/concepts/forecast-info.html#forecast"> linkga </a> o'tamiz. 

Request format
```
GET https://api.weather.yandex.ru/v2/informers?
  lat=<kenglik>
  & lon=<uzunlik>
  & [lang=<javob tili>]

X-Yandex-API-Key: <kalitni yozamiz>
```

Aynan mana bu manzilga GET so'rovini (request) yuborish kerak.
```
https://api.weather.yandex.ru/v2/informers?
```

Hammasini yozib bo'lgandan keyin, keyingi qadamga o'tamiz.



so'rov formati
```
https://geocode-maps.yandex.ru/1.x
? geocode=<string>
& apikey=<string>
& [sco=<string>]
& [kind=<string>]
& [rspn=<boolean>]
& [ll=<number>, <number>]
& [spn=<number>, <number>]
& [bbox=<number>, <number>~<number>,<number>]
& [formar=<string>]
& [results]<integer>]
& [skip=<integer>]
& [lang=<string>]
& [callback=<string>]
```

bu yerdagi geocode* - geografik manzil, bu yerda koordinatlar yoki shahar nomi yozilishi mumkin.

*apikey - API kaliti

mana bu saytga GET request yuboriladi
```
https://geocode-maps.yandex.ru/1.x?
```

Keyinroq, PostgreSQL va Dockerni ulaymiz. Aiogram ni ishlatib ko'ramiz.
