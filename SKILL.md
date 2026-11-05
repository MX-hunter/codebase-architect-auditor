---
name: codebase-architect-auditor
description: Perform a comprehensive full-codebase review, architecture mapping, segmented path analysis, syntax and logic validation, cross-file compatibility checks, deep security auditing, automated unit test scaffolding, OpenAPI documentation generation, dependency vulnerability scanning, and Mermaid sequence diagram generation. Use when the user asks to map a codebase, audit code health, check cross-file dependencies, review security precautions, or generate a full project architecture and security report.
---

# Codebase Architect and Security Auditor

A comprehensive workflow for reading an entire codebase, generating a complete architectural map, analyzing segmented execution paths, verifying code health, enforcing strict security precautions, generating documentation, and scaffolding tests.

## إدارة الذاكرة واستهلاك التوكينز (Token Optimization & State Management)

لتجنب استهلاك التوكينز وإعادة قراءة المحادثة من البداية، اتبع القواعد التالية بدقة صارمة:

1. **الاعتماد المطلق على ملف الحالة الخارجي (State File Dependency):**
   - بمجرد أن تنشئ المهارة ملف التقرير أو خريطة الكود (مثل `architecture_map.md` أو تقارير التدقيق)، يُعتبر هذا الملف هو **مصدر الحقيقة الوحيد (Single Source of Truth)**.
   - في الطلبات اللاحقة، يُمنع منعاً باتاً طلب إعادة إرسال الكود الكامل أو قراءة الرسائل الأولى في المحادثة.

2. **استراتيجية التحديث التفاضلي (Delta Updates Only):**
   - عندما يطلب المستخدم تعديلاً أو فحصاً إضافياً:
     - لا تقرأ المشروع كاملاً. اقرأ فقط الملف المحدد أو الـ Diff المطلوب.
     - حدّث جزءاً محددصاً من الملف المرجعي الخارجي ولا تعيد توليد التقرير كاملاً من الصفر.

3. **نافذة السياق المضغوطة (Context Window Compression):**
   - عند الإجابة على أي استفسار تالي، أشر باختصار شديد إلى رقم القسم أو السطر في الملف المرجعي المنشأ مسبقاً بدلاً من نسخ محتوى الملف في الرد.

## Steps

### 1. التشريح الكامل والتشغيل الأولي (Initial Codebase Dissection)
- جرد وفهرسة الهيكل بالكامل واستخراج نقاط الدخول الأساسية (`bootstrap`, `index.php`, `config.php`).
- بناء قاعدة بيانات ذهنية متكاملة عن تدفق البيانات.

### 2. Segmented Path and Route Analysis (إنشاء مسارات مقسمة)
- تجميع مسارات الـ API و الـ Routes والتحقق من عزل المجلدات العامة عن النواة.

### 3. Code Health and Quality Validation (صحة الكود)
- فحص الأخطاء، مطابقة معايير النظافة المعمارية، ومعالجة الأخطاء والـ Logging.

### 4. Cross-File Compatibility and Integration (توافق أكواد الملفات)
- التحقق من الـ Namespaces، الـ Imports، وحساسية الأحرف (Case-Sensitivity) لبيئات Linux.

### 5. Comprehensive Security Audit (الاحتياطات الأمنية الشاملة)
- فحص ثغرات الحقن (PDO / SQLi)، المصادقة، التحقق من المدخلات، وتأمين الخوادم.

### 6. الميزات المتقدمة (Advanced Capabilities)
- **توليد خريطة تدفق البيانات (Mermaid Sequence Diagrams):** رسم مسار الطلب بصرياً عبر المخططات النصية.
- **توليد توثيق الـ API (OpenAPI / Swagger Scaffolding):** استخراج مسارات الـ Endpoints وتوثيقها بشكل قياسي.
- **فحص الثغرات والتبعيات (Dependency Scanning):** مراجعة حزم (`composer.json`, `package.json`, `requirements.txt`) لاكتشاف أي ثغرات معروفة.
- **توليد قوالب اختبارات الوحدات (Automated Unit Test Scaffolding):** إنشاء قوالب اختبار تلقائية للملفات الجديدة أو المعدلة.

## Output Report Format
1. الملخص التنفيذي والهندسي.
2. التشريح الأولي وخريطة المسارات المقسمة (مع مخططات Mermaid).
3. تقرير توافق الملفات وصحة الكود.
4. التدقيق الأمني الشامل والثغرات المرصودة مع الإصلاحات الجاهزة.
5. وثائق الـ API المقترحة وقوالب اختبارات الوحدات.
6. ### 5. High-Level Security Dissection & Vulnerability Triage (التشريح الأمني المتقدم والفرز)

عند فحص أي ملف أو كود برمجي، يجب تطبيق بروتوكول الفحص الأمني الصارم التالي:

1. **التمشيط الشامل لأنماط الثغرات (Comprehensive Threat Pattern Scanning):**
   تفلتر المهارة الكود بحثاً عن الفئات الأمنية الحرجة التالية:
   - **ثغرات الحقن (Injection Flaws):** استخدام استعلامات SQL غير مؤمنة (بدون PDO Prepared Statements)، أو حقن الأوامر (Command Injection)، أو تنفيذ التعليمات البرمجية ديناميكياً (`eval`).
   - **التحكم في الوصول والصلاحيات (Broken Access Control & IDOR):** غياب التحقق من الجلسات (Sessions) أو صلاحيات المستخدم (`Role-Based Access Control`) قبل تنفيذ العمليات الحساسة.
   - **إدارة الجلسات والمصادقة (Authentication & Session Management):** تخزين كلمات المرور بشكل مكشوف (بدون `password_hash`)، أو ضعف توليد الـ Tokens، أو غياب حماية الـ CSRF Tokens في النماذج (Forms).
   - **معالجة المدخلات والمخرجات (Insecure Data Handling & XSS):** غياب التطهير (`Sanitization`) والتحقق (`Validation`) للمدخلات القادمة من المستخدم، وغياب الترميز (`Output Encoding`) ضد ثغرات XSS.
   - **إعدادات الخادم والبيئة (Security Misconfigurations):** كشف تفاصيل الأخطاء الحساسة للمستخدم (`Display Errors Enabled`)، أو وجود مفاتيح ربط أو كلمات مرور صريحة داخل الكود (`Hardcoded Credentials`).

2. **تسلسل المشاكل في نقاط (Vulnerability Chain & Impact Analysis):**
   يتم سرد الأخطاء المكتشفة في تقرير منظم ومسلسل كالتالي:
   - **[VULN-ID]:** (مثلاً: `SQLI-01` أو `AUTH-02`).
   - **الموقع (Location):** اسم الملف ورقم السطر بدقة.
   - **نوع الثغرة (Threat Vector):** تصنيف الثغرة بناءً على معايير OWASP Top 10.
   - **سلسلة التأثير (Impact Chain):** كيف يمكن للمهاجم استغلال هذه الثغرة خطوة بخطوة للوصول إلى قاعدة البيانات أو تخريب النظام.

3. **اقتراح الإصلاحات الهندسية الجاهزة (Remediation & Secure Patching):**
   لكل ثغرة مرصودة، لا تكتفي المهارة بالتحذير، بل تقدم:
   - **الكود الحالي (Vulnerable Code):** توضيح الخطأ الموجود.
   - **الكود الآمن المقترح (Secure Patch):** كتابة الكود البديل المصحح بالكامل (جاهز للنسخ واللصق).
   - **شرح آلية الحماية (Defense Explanation):** شرح موجز لكيفية منع الثغرة بواسطة التعديل المقترح.
