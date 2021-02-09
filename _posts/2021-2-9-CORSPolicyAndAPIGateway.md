---
layout: post
title: طريقة عمل CORS مع Amazon API Gatway 
---

توفر منصة أمازون للخدمات السحابية عدة خدمات تسمح بإستضافة برامج الويب و صفحات الإنترنت لكن و عند بناء واجهة لبرمجة التطبيقات أو ال APIs تظهر مشكلة بسيطة في الإعدادات و  تواجه الكثير من المطورين و تحتاج إلى حل وهي توافق خدمة Amazon API Gateway مع CORS Policy و لذلك قبل البدء و التعمق في التفاصيل سنقوم بتعريف المصطلحات المستخدمة حتى تتضح الصورة بشكل أفضل:

## Amazon API Gateway
![Amazon API Gateway](https://i0.wp.com/oddblogger.com/wp-content/uploads/2019/08/Amazon-API-Gateway@4x.png?resize=225%2C225&ssl=1 "https://i0.wp.com/oddblogger.com/wp-content/uploads/2019/08/Amazon-API-Gateway@4x.png?resize=225%2C225&ssl=1")

هي إحدى خدمات منصة أمازون للخدمات السحابية التي تقوم بإدارة و متابعة جميع ال APIs كبوابة للحصول على
صلاحية استخدام البيانات و توفر عدة ميزات مثل رفع مستوى الحماية بشكل مرن على حسب المتطلبات و تخفيف التكاليف المالية  على  المطورين بالإضافة لسرعة التطوير و التعديل على الخدمة بطريقة سهلة و كذلك العديد من المميزات الأخرى التي  يمكن الإطلاع عليها [هنا](https://aws.amazon.com/api-gateway/)

## CORS Policy (Cross-Origin Resource Sharing)
![CORS](https://addons.cdn.mozilla.net/user-media/previews/full/227/227652.png?modified=1597135314 "https://addons.cdn.mozilla.net/user-media/previews/full/227/227652.png?modified=1597135314")

 هي نظام يستخدم HTTP Headers التي تحدد مصادر صفحات الويب و تساعد متصفحات الويب بحجب محتوى الصفحة بناء على معرفة المصادر المسموح بها. تعمل عن طريق إرسال طلب preflight قبل طلب محتويات صفحة الويب لتحديد صلاحيات الصفحة مسبقا عن طريق ال Headers فقط و بعدها يتم إرسال الطلب للصفحة بشكل كامل للمستخدم و يمكن الإطلاع أكثر على تفاصيلها بشكل أكبر [هنا](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) 

## المشكلة 

إذا ما المشكلة التي تسبب عدم التوافق ما بين التقنيات؟ بداية عند استخدام ال APIs في برامج الويب و صفحات الإنترنت نضطر إلى استخدام مصادر
مختلفة للمحتوى المستخدم في هذه الصفحات لنزيد من قوة حماية البرنامج و قوة هيكلته. بالإضافة، لقدرة إعادة استخدام عناصره في أماكن مختلفة مما يسهل للمطورين  تطوير المشاريع البرمجية الكبيرة و يزيد من سرعة  فاعلية الحلول الرقمية للمستخدمين.

و لذلك عند استخدام API Gateway نحتاج إلى إعدادات  معينة تسمح بإستخدامه من غير معارضة ال CORS Policy للسماح بالخدمات من عدة مصادر  بالعمل داخل الصفحة بدون حجبها.  لذا عندما يقوم API Gateway بإنتاج رابط و نريد إستعماله في إحدى الصفحات نقوم أولا بالتأكد من توافق ال CORS Policy مع التهيئة المناسبة للخدمة حتى لا تحجب الصفحة، علما أن ذلك قد يحدث مع أي نوع من الخدمات حتى استخدام الخطوط أو الصور من مصادر مختلفة.

  هنا مثال على أحد الأخطاء المنشرة التي تظهر عند عدم إتباع الخطوات أو التهيئة الصحيحة.


![CORS Error Example](https://miro.medium.com/max/3200/0*bI2yxKryqJzyUkud "https://miro.medium.com/max/3200/0*bI2yxKryqJzyUkud")


## التهيئة 

 الحل يكمن في جعل جميع ال Resources بداخل ال Methods المستخدمة في الخدمة تعتمد على خاصية  Enable CORS بكل بساطة و لكن قبل ذلك يجب إضافة ال Options Method لأن متصفحات الويب تقوم بإرسال Test Request حتى تتمكن من معرفة الخيارات المتوفرة لها  قبل تحميل الصفحة -كما قلنا سابقا- و تسمح بإستخدام ال APIs.

![Enable CORS](https://miro.medium.com/max/315/1*zhVcX8ekXYlcSbL4N4c6Yg.png "https://miro.medium.com/max/315/1*zhVcX8ekXYlcSbL4N4c6Yg.png")

و بعدها نتجه إلى إضافة أربعة ردود أساسية في ال Method responses إلى Header 200 status و هي:

* Access-Control-Allow-Headers

* Access-Control-Allow-Origin

* Access-Control-Allow-Credentials

* Access-Control-Allow-Methods

![Integration Response](https://s3.amazonaws.com/awscomputeblogmedia/11_API-gateway-navigate-to-integration-response.png "https://s3.amazonaws.com/awscomputeblogmedia/11_API-gateway-navigate-to-integration-response.png")

و بعد ذلك نستطيع إضافة القيم المناسبة لها في جزء ال Integration Response:

* Access-Control-Allow-Headers 

     'Content-Type,X-Amz-Date,Authorization,X-Api-Key,x-requested-with'

* Access-Control-Allow-Origin 

     '*' 
     
     (Note: * means for for all origins, however, you can specifiy certain ones)

* Access-Control-Allow-Credentials 

    'true'

* Access-Control-Allow-Methods  

    'GET' 
    
    (Note: in case you used a GET method)

## الخاتمة

يمكن أتمتة هذه العملية بالكامل بشكل سريع عند إتمام التهيئة لمرة واحدة. هذه الخطوات تعتبر مهمة عند استخدام الخدمة لفهم طريقة عملها بشكل أعمق و للعمل مع ال APIs و معرفة تفاصيلها من غير الحاجة لتعب بناءها من الصفر و الإستفادة من هذه الخدمة بأفضل شكل ممكن لإنتاج حلول رقمية بأعلى مستوى.

شكرا لوقتكم و في حال تواجد أي أسئلة أو تعليقات لا تتردوا في التواصل معي.

#### المصادر

MDN - CORS 

(<https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS>)

Amazon API Gateway 

(<https://aws.amazon.com/api-gateway/>)

Signing Requests 

(<https://docs.aws.amazon.com/apigateway/api-reference/signing-requests/>)

CORS for API Gateway and Lambda Functions 

(<https://chrislarson.me/blog/tutorial/lambda/2017/03/10/cors-api-gateway-lambda.html>)