---
layout: post
title: إدارة البيانات و هيكلتها مع AWS Glue
---

الكثير من الشركات و المنظمات تقوم بالإعتماد على البيانات و إدارتها في تطوير منتجاتها و تقديم خدماتها. و عند بناء البرمجيات و محاولة تحليل البيانات توجد الحاجة لإدارة البيانات بشكل أساسي و خاصة مع نمو نسبة التحول الرقمي في العالم في عام 2020 بنسية مقدرة بحوالي 20 بالمئة. سنقوم أولا بفهم طريقة التعامل المشهورة مع البيانات في إدارتها و هيكلتها و ثانيا لخدمة تقدمها AWS Glue لإدارة البيانات بشكل ميسر و منظم مما يسمح بأتمتة العملية بنسبة عالية. لنبدأ بالمفاهيم الأساسية:


## ETL Pipeline
![AWS Glue](https://i0.wp.com/oddblogger.com/wp-content/uploads/2019/08/Amazon-API-Gateway@4x.png?resize=225%2C225&ssl=1 "https://i0.wp.com/oddblogger.com/wp-content/uploads/2019/08/Amazon-API-Gateway@4x.png?resize=225%2C225&ssl=1")

هي عملية إدارة و هيكلة البيانات الغير منتظمة مكونة من ثلاثة خطوات رئيسية (إستخراج-تحويل-تحميل) و هذه العملية تعمل في مسار واحد لإنتاج بيانات منظمة تساعد على جمع البيانات الغير منظمة من مصادرها و تحولها إلى بيانات تفي بالمتطلبات التشغيلية و التحليلية بالشركات.

## إستخراج البيانات
![CORS](https://addons.cdn.mozilla.net/user-media/previews/full/227/227652.png?modified=1597135314 "https://addons.cdn.mozilla.net/user-media/previews/full/227/227652.png?modified=1597135314")

أولا، إستخراج البيانات من مصادرها يعتمد بشكل كبير على 

## تحويل البيانات

ثانيا، تحويل البيانات يعني أن نقوم بتحويل البيانات إلى صيغ متناسقة نستطيع 


![CORS Error Example](https://miro.medium.com/max/3200/0*bI2yxKryqJzyUkud "https://miro.medium.com/max/3200/0*bI2yxKryqJzyUkud")


## تحميل البيانات

ثالثا، تحميل البيانات هو جزء أساسي من اكتمال عملية هيكلة البيانات لتصبح جاهزة للتحليل، لكن ماذا نعني بتحميل البيانات؟ تحميل البيانات بشكل مبسط تعني 

## AWS Glue

هي خدمة تقدم من منصة أمازون للخدمات السحابية للمساعدة في إدارة ال etl و تقوم بشكل مبسط بإطلاق Crawlers بداخل قواعد البيانات، مستودعات البيانات، و غيرها من لفهم هيكلة البيانات و استخراجها و تحميلها لقاعدة بيانات لتحليلها بطريقة منتظمة.

## الخاتمة

تنظيف البيانات لجعلها أكثر موثوقية و أقل في الأخطاء

القدرة على عرض البيانات بشكل سلس في أدوات عرض البيانات

عملية لتبسيط دمج تنسيقات ملفات البيانات مثل JSON و XML في البيئة السحابية

تحديد واضح لنطاق المشروع و متطلباته و بالتالي تخفيض قيمة العمل في التركيز على البيانات المهمة في صناعة القرار و بطريقة مؤتمتة. 



شكرا لوقتكم و في حال تواجد أي أسئلة أو تعليقات لا تتردوا في التواصل معي.

#### المصادر

MDN - CORS 

(<https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS>)

AWS Glue

(<https://aws.amazon.com/glue/?whats-new-cards.sort-by=item.additionalFields.postDateTime&whats-new-cards.sort-order=desc>)

Signing Requests 

(<https://docs.aws.amazon.com/apigateway/api-reference/signing-requests/>)

CORS for API Gateway and Lambda Functions 

(<https://chrislarson.me/blog/tutorial/lambda/2017/03/10/cors-api-gateway-lambda.html>)