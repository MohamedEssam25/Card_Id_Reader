!المتطلبات!
1-تاكد من تثبيت برنامج pytessract
2-تاكد من تثبيت جميع المكتبات الموجوده ف الكود
3-قم بنقل ملف ال ara_number_id الي ملف C:\Program Files\Tesseract-OCR\tessdata
-------------------
**شرح الكود**
ملاحظات:-
1-في السطر رقم 28 تاكد من اضافه المسار الصحيح للملف الكود الذي قمت بتنزيله
2-في السطر رقم 173 تاكد من تصحيح المسار اذا كان خاطئا
3- في خاصيه ال train يقول لك ان تختار الملف الذي يحتوي علي الداتا يجب ان تكون هكذا:
مقسمه الي ملفين اسمهما test,val
بداخل ملف ال test مثلا موجود ملفين
card,nocard
وكذلك ملف ال val يحتوي علي ملفين 
card,nocard
و سيقوم البرنامج تلقائيا بعمل train 
وستكون 10epoches
و سيقوم بحفظ الموديل الناتج تلقائيا ب اسم card_classifier_new.pth
------------------------------------
الشرح
هذا الموديل المتواضع يعمل بطريقه ان تعطيه موديل التدريب و الصوره المراده و سيقوم بتطبيق الموديل عليها و اذا كانت بطاقه 
سيقوم بتطبيق الخوارزميه الثانيه و يقوم بانتاج الرقم القومي
واذا لم يكن معك موديل تدريبي و كان معك داتا ف يمكنك تدريبها و عمل موديل منها
------------------------
فكره العمل
لشرح فكره العمل يجب ان تكون ناتجه من حل مشكلات فقط للمشروع
ف اول مشكله لماذا ف الاول عملناه oop 
لانها عند عمل browse واختيارها تحفظ القيمه ولا تنساها
ثم عند اختيار الصوره و تطبيق عليها الموديل الاول و يقول فعلا انها بطاقه
ياتي الموديل الثاني ل يقوم باستخراج الرقم القومي
يقوم الموديل الاخر والذي هو عباره عن 2 موديل
الاول يقوم باكتشاف وجه الشخص الي ف البطاقه و علي حسب المربع بتاع الوجه
يقوم بعمل طريقه نسبيه يستخرج بقها حجم البطاقه من الصوره
ف هنا قمنا باقتصاص صوره البطاقه فقط من الصوره بناءا علي وجه الشخص
وبعد ان اقتصصنا صوره البطاقه فقط من الصوره ياتي دور قص الصوره الناتجه 75% من الاعلي
ليتبقي الجزء الخاص  ب الرقم القومي فقط و قصه من اليسار %30
ثم ياتي الي الموديل الثاني و هو التعرف علي الارقام باستخدام pytessract
لقد قمنا بجمه مجموعه من الارقام العربيه في صور البطاقات
وعمل موديل تدريبي cluster باستخدام pytessract وهو ال ara_num_id.traineddata
هو موديل لي موجود في موديلات pytessract بل نحن من انشاناه باستخدام اداه jTessBoxEditor
وقمنا بالتحديد حول كل حرف و الابعاد ثم طبقنا ال cluster وانشانا الخوارزميه 
ثم بعد ذلك ياتي بالصوره و يحولها الي رمادي ثم يطبق عليها فلاتر خاصه ب الصور لتوضيحها
ومن استناجتنا وجدنا ان فلتر ال trunced هو افضل فلتر لانه يقوم بتوضيح الصوره
ثم ياتي دور ال gui و قد قمنا باستخدام موقع figma لعمل التصميم ثم تحويله الي كود باستخدام Tkinter-Designer-master
ثم جئنا الي كل زر و قد قمنا بوضع الداله الخاصه به في مكانه
مع بعض التعديلات في ال gui و الاماكن انتهينا من المشروع 🤩


