---
الملخص: اتبع هذا البرنامج التعليمي لإنشاء واختبار مثال لتطبيق جوال سريعًا لإدارة المهام.
tags: runtime-mobile; support-Mobile_Apps; support-Mobile_Apps-overview
---

# قم بإنشاء أول تطبيق جوال خاص بك 

يعد تطوير تطبيقات الأجهزة المحمولة باستخدام OutSystems أمرًا سهلاً. إذا كان لديك ملف Excel يحتوي على بياناتك ، فيمكنك استيراده إلى قاعدة بيانات وإنشاء تطبيق جوال سريعًا يمكّنك من التحقق من بياناتك وإدارتها أثناء التنقل.
لإنشاء تطبيق جوال ببيانات مستوردة من ملف Excel ، تحتاج إلى:

1. إنشاء نموذج قاعدة بيانات ، واستيراد البيانات من ملف Excel إلى قاعدة البيانات
2. قم بإنشاء شاشة تسرد البيانات من قاعدة البيانات
3. قم بإنشاء شاشة تمكنك من إنشاء سجلات جديدة وتحديث السجلات الموجودة
4. تنفيذ وظيفة لحذف السجلات من قاعدة البيانات
5. اختبر التطبيق على جهازك المحمول.
   هيا بنا نقوم بذلك! في هذا المثال ، سنستخدم نموذج ملف Excel مع معلومات مهمة المهام ، وسننشئ تطبيقًا بسيطًا لإدارة المهام على الأجهزة المحمولة.
## قم بإنشاء تطبيق جوال 

لنقم بإنشاء تطبيق جوال جديد لإدارة المهام. قم بما يلي في Service Studio:

1. يختار **New Application**.

    ![New app in Service Studio](images/new-app-ss.png)

1. يختار**From scratch** ثم اضغط  **NEXT**.

    ![New app in Service Studio](images/from-scratch-ss.png)

1. اختر ال **Phone App** النموذج واضغط **NEXT**.

    ![Mobile App template](images/phone-app-template-ss.png)

1. اسم التطبيق **To Do** and click **CREATE APP**. يفتح Service Studio تفاصيل التطبيق لك لإضافة الوحدة الأولى الخاصة بك.

    ![App name in the new app window](images/name-of-app-ss.png)

1. في شاشة تفاصيل التطبيق ، تأكد مما يلي وانقر على **CREATE MODULE**:
    
    * اسم الوحدة هو `ToDo`
    * نوع الوحدة هو **Phone App**.

    ![Create a Mobile Module](images/new-module-ss.png)

يحتوي التطبيق على وحدة نمطية واحدة أو أكثر ، ويمكن تغليف أجزاء مختلفة من التطبيق في وحدة نمطية. الوحدة النمطية هي المكان الذي تقوم فيه بتصميم نموذج البيانات وتنفيذ المنطق وتصميم واجهة المستخدم لتطبيقك.

## قم بإنشاء جدول قاعدة بيانات من ملف Excel

تقوم OutSystems بتخزين بيانات التطبيق الخاصة بك في قاعدة بيانات . هذا يعني أن الخطوة الأولى في إنشاء تطبيق هي تحديد نموذج البيانات.

للقيام بذلك ، سنستخدم ملف Excel يحتوي بالفعل على معلومات المهمة التالية:
* Description
* Due Date
* Is Active

في ال`ToDo` module, افتح ملف **Data** علامة التبويب في الزاوية العلوية اليمنى ، وانقر بزر الماوس الأيمن فوق **Entities** مجلد ، اختر **Import New Entities from Excel...**, وحدد ملف العينة`Tasks.xlsx` متاح بشكل افتراضي في الدليل `C:\Program Files\OutSystems\Development Environment 11\Service Studio\TutorialResources`.

![Create a Database Table from an Excel File](images/create-mobile-03.png)

عند استيراد ملف Excel ، تقوم OutSystems بإنشاء جدول قاعدة بيانات (يسمى كيان في أنظمة OutSystems) مع الأعمدة الضرورية (تسمى السمات في أنظمة OutSystems) لتخزين البيانات في قاعدة البيانات.
وراء الكواليس ، تنشئ OutSystems أيضًا منطقًا لاستيراد كل صف في ملف Excel إلى سجل قاعدة بيانات مطابق. بعد نشر التطبيق الخاص بك ، يقوم منطق الخلفية بملء قاعدة البيانات الخاصة بك بالبيانات من ملف Excel.

في هذا البرنامج التعليمي ، نقوم فقط بتخزين البيانات في قاعدة بيانات الخادم ، ولكن للاستخدام دون اتصال بالإنترنت ، من الممكن أيضًا تخزين البيانات محليًا في الأجهزة المحمولة باستخدام التخزين المحلي.
## قم بإنشاء شاشة لسرد المهام 

الآن يمكننا إنشاء شاشة تسرد جميع المهام.

افتح ال **Interface** علامة التبويب في الزاوية اليمنى العليا, وانقر نقرًا مزدوجًا**MainFlow** تحت **UI Flows**. ثم اسحب ملف **Screen** من Toolbox إلى منطقة فارغة في نافذة المحرر الرئيسي. اختر ال **Empty** النموذج ، قم بتسمية شاشتك `Tasks` ثم اضغط **Create Screen**.

![Create a new empty screen](images/create-mobile-04.png)

اسحب **Task** entity from the **Data** علامة التبويب إلى العنصر النائب للمحتوى لشاشة الجوال التي يتم عرضها في نافذة المحرر الرئيسي.

![Create a Screen to List Tasks](images/create-mobile-05.png)

يقوم هذا بتحديث ملف **Tasks** لتضمين قائمة تعرض في البداية 20 مهمة وتحميل المزيد من المهام تلقائيًا عندما يقوم المستخدم بالتمرير إلى نهاية القائمة.

![Tasks Screen](images/create-mobile-06.png)

## قم بإنشاء شاشة لتحرير المهام 

يعد إنشاء شاشة لتحرير السجلات بنفس سرعة إنشاء شاشة قائمة.
انقر بزر الماوس الأيمن فوق عنوان المهمة الأولى في القائمة ، وانقر فوق **Link to** > **(New Screen)**, اختر **Empty** النموذج ، قم بتسمية شاشتك `TaskDetail` and click **Create Screen**.

![Create a Screen to Edit Tasks](images/create-mobile-07.png)

يؤدي هذا إلى ربط عنوان المهام بشاشة تم إنشاؤها حديثًا. سنستخدم هذه الشاشة الجديدة لتعديل المهام ، ولكن من أجل ذلك سنحتاج إلى نموذج:

1. اسحب **Form** عنصر واجهة المستخدم من Toolbox إلى العنصر النائب للمحتوى في ملف **TaskDetail** mobile screen.

    ![Drag a Form](images/create-mobile-08.png)

1. اسحب **Task** entity من **Data** علامة التبويب إلى النموذج الذي تم إنشاؤه مسبقًا.

    ![Create a Screen to Edit Tasks](images/create-mobile-10.png)

سنحدد الآن المنطق الذي يتم تشغيله عندما يضغط المستخدمون النهائيون على زر حفظ:

1.انقر نقرًا مزدوجًا فوق منطقة فارغة من ملف **Save** زر لتعريف المنطق المرتبط بالزر. سيؤدي هذا إلى إنشاء إجراء شاشة جديد باسم **SaveOnClick**.

1. في ال **Data** علامة التبويب ، قم بتوسيع **Task** entity واسحب  **CreateOrUpdateTask** entity العمل ل **True** فرع من **If**. تعيين **Source** الملكية ل `GetTaskById.List.Current`.

1. اسحب الشاشة **Tasks** من **Interface** انقر فوق عقدة النهاية بحيث يتم إعادة توجيه المستخدم مرة أخرى إلى الشاشة الرئيسية بعد حفظ المهمة. 

    ![Create a Screen to Edit Tasks](images/create-mobile-11.png)

## السماح بإضافة المهام 

نريد تمكين المستخدمين النهائيين من إضافة مهام جديدة من شاشة القائمة عن طريق الارتباط بالشاشة المستخدمة بالفعل لتحرير المهام:
    
1. في  **Interface** علامة التبويب ، انقر نقرًا مزدوجًا فوق ملف **Tasks** لفتح شاشة القائمة.  
   اسحب ملف **Icon**عنصر واجهة مستخدم من Toolbox إلى العنصر النائب Actions في الزاوية العلوية اليمنى من الشاشة وحدد ملف **plus** icon.

    ![Add plus icon to Actions placeholder](images/create-mobile-12.png)

1.انقر بزر الماوس الأيمن فوق ملف **plus** أيقونة واختيار **Link** > **MainFlow\TaskDetail**.

    ![Allow Adding Tasks](images/create-mobile-13.png)

## السماح بإكمال المهام 

الآن دعنا نضيف الوظيفة لوضع علامة على المهام كمكتملة. دعنا ننفذ ذلك عن طريق حذف المهام المكتملة:

1. انقر فوق عنصر القائمة ، ثم على شريط الأدوات ، انقر فوق **Swipe Left Action**.

1. في "إجراء القائمة" الذي تم إنشاؤه حديثًا ، استبدل النص "Action" with "Done".

    ![Allow Completing Tasks](images/create-mobile-14.png)

1. انقر نقرًا مزدوجًا فوق منطقة فارغة من List Action لتحديد المنطق المرتبط بإجراء Swipe Left Action.

1. في ال **Data** علامة التبويب ، قم بتوسيع **Task** الكيان والسحب **DeleteTask** entity action ضمن مهمة الكيان في علامة تبويب البيانات لتدفق إجراء التمرير لليسار. اضبط خاصية ** Id ** على **Id**الملكية ل `GetTasks.List.Current.Task.Id`.

    ![Allow Completing Tasks](images/create-mobile-15.png)

1.اسحب  **Refresh Data** من Toolbox إلى تدفق الإجراء ، بعد ملف **DeleteTask** الإجراء ، وحدد التجميع **GetTasks** لتحديث المهام المتاحة في الشاشة.

    ![Allow Completing Tasks](images/create-mobile-16.png)

## اختبر تطبيق جوالك

في هذه المرحلة نقوم باختبار تطبيق الهاتف المحمول. انقر على **![1-Click Publish](../shared/icons-service-studio/publish.png) 1-Click Publish**زر لنشر التطبيق في بيئتك.

![Publish Your Mobile App](images/create-mobile-17.png)

عندما يتم نشر التطبيق ، انقر فوق**![Open in Browser](../shared/icons-service-studio/open-browser.png) Open in Browser** زر لاختبار التطبيق الخاص بك في متصفح (Chrome و Safari مدعومان).

![Test Your Mobile App](images/create-mobile-18.png)

لتجربة التطبيق على جهازك المحمول انظر [Distribute as a progressive web app (PWA)](../deliver-mobile/distribute-pwa/intro.md).
