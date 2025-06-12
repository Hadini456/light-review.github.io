---
layout: default # هذا يخبر Jekyll أن يستخدم تخطيط default.html
title: "بوابة الألعاب - الرئيسية" # عنوان الصفحة الرئيسية
permalink: / # هذا يجعلها الصفحة الرئيسية لموقعك (على سبيل المثال: yourwebsite.com/)
---

<!-- Hero Section -->
<section id="hero" class="relative min-h-screen flex items-end bg-cover bg-center bg-no-repeat" style="background-image: url('https://placehold.co/1920x1080/111827/DC2626?text=Cyberpunk+Saga');">
    <div class="absolute inset-0 hero-gradient"></div>
    <div class="relative container mx-auto px-6 py-16 text-center text-white z-10">
        <h1 class="text-5xl md:text-7xl font-black mb-4 animate-fade-in-down red-text-glow">Cyberpunk Saga: مراجعة شاملة</h1>
        <p class="text-lg md:text-xl max-w-3xl mx-auto mb-8 animate-fade-in-up">
            انغمس في عالم المستقبل المظلم، هل تستحق هذه المغامرة وقتك وأموالك؟ اكتشف في مراجعتنا الكاملة.
        </p>
        <!-- الرابط ليقود إلى مراجعة سايبربانك كـ "post" (صفحة تم إنشاؤها بواسطة Jekyll) -->
        <!-- يتطلب هذا استخدام link tag الخاص بـ Jekyll مع مسار ملف الـ Markdown -->
        <a href="{{ site.baseurl }}{% link _posts/2025-06-12-cyberpunk-saga-review.md %}" class="bg-red-600 hover:bg-red-700 text-white font-bold py-3 px-8 rounded-lg text-lg transition-all duration-300 ease-in-out transform hover:scale-105 red-glow">
            اقرأ المراجعة <i class="fas fa-arrow-left mr-2"></i>
        </a>
    </div>
</section>

<!-- Game Reviews Section -->
<section id="reviews" class="py-20 bg-gray-900">
    <div class="container mx-auto px-6">
        <h2 class="text-4xl font-black text-center mb-12 text-white">أحدث <span class="text-red-600">المراجعات</span></h2>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
            <!-- حلقة Jekyll لجلب أحدث المراجعات تلقائياً من مجلد _posts -->
            {% assign posts_limit = 3 %} {# يمكنك تحديد عدد المراجعات المراد عرضها هنا #}
            {% for post in site.posts limit: posts_limit %}
            <div class="bg-gray-800 rounded-xl overflow-hidden shadow-lg transform transition-all duration-500 hover:scale-105 hover:shadow-2xl hover:shadow-red-800/40 group">
                <div class="relative">
                    <!-- استخدام post.image لجلب الصورة من Front Matter للمراجعة -->
                    <img src="{{ post.image | default: 'https://placehold.co/600x400/1F2937/FFFFFF?text=Game+Image' }}" alt="{{ post.title }}" class="w-full h-56 object-cover">
                    <div class="absolute inset-0 card-gradient"></div>
                    <!-- تحديد لون منصة اللعبة ديناميكياً بناءً على post.platform -->
                    <div class="absolute top-4 right-4 {% if post.platform contains 'PS' %}bg-red-600{% elsif post.platform contains 'XBOX' %}bg-green-500{% elsif post.platform contains 'PC' %}bg-blue-500{% else %}bg-gray-500{% endif %} text-white text-sm font-bold py-1 px-3 rounded-md">{{ post.platform }}</div>
                    <!-- عرض عنوان اللعبة من post.game_title -->
                    <div class="absolute bottom-4 right-4 text-white font-black text-2xl">{{ post.game_title }}</div>
                </div>
                <div class="p-6">
                    <!-- عرض مقتطف المراجعة من post.excerpt -->
                    <p class="text-gray-400 mb-4 h-24 overflow-hidden">{{ post.excerpt }}</p>
                    <div class="flex justify-between items-center mb-4">
                        <!-- عرض تاريخ النشر من post.date -->
                        <span class="text-sm text-gray-500">تاريخ النشر: {{ post.date | date: "%-d %B %Y" }}</span>
                        <div class="text-yellow-400">
                            <!-- عرض النجوم والتقييم من post.score. قد تحتاج لتعديل هذا الجزء ليكون أكثر دقة حسب التقييم -->
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            <i class="fas fa-star"></i>
                            {% if post.score == "9.5" %}<i class="fas fa-star"></i>{% elsif post.score contains ".5" %}<i class="fas fa-star-half-alt"></i>{% else %}<i class="far fa-star"></i>{% endif %}
                            <span class="text-white font-bold ml-1">{{ post.score }}</span>
                        </div>
                    </div>
                    <!-- هذا الرابط سيقود إلى صفحة المراجعة الفردية التي تم إنشاؤها بواسطة Jekyll -->
                    <a href="{{ site.baseurl }}{{ post.url }}" class="block w-full text-center bg-gray-700 text-white font-bold py-2 rounded-lg transition-colors duration-300 group-hover:bg-red-600">اقرأ المزيد</a>
                </div>
            </div>
            {% endfor %}

            <!-- إذا كان لديك مراجعات أخرى، قم بتحويلها إلى ملفات Markdown في مجلد _posts. -->
            <!-- ستظهر تلقائياً في الحلقة أعلاه بمجرد إضافتها وتضمين بياناتها في Front Matter. -->
        </div>
    </div>
</section>

<!-- News Section -->
<section id="news" class="py-20 bg-gray-800/50">
    <div class="container mx-auto px-6">
        <h2 class="text-4xl font-black text-center mb-12 text-white">آخر <span class="text-red-600">الأخبار</span></h2>
        <div class="max-w-4xl mx-auto">
            <div class="space-y-6">
                <!-- News Item 1 -->
                <a href="#" class="flex items-center bg-gray-800 p-4 rounded-lg transition-transform duration-300 hover:bg-gray-700 hover:scale-102">
                    <img src="https://placehold.co/150x100/DC2626/FFFFFF?text=E3+2025" alt="خبر" class="w-32 h-20 object-cover rounded-md">
                    <div class="mr-6 rtl:mr-0 rtl:ml-6">
                        <h3 class="text-xl font-bold text-white">تسريبات حصرية من معرض E3 2025 القادم</h3>
                        <p class="text-gray-400">الكشف عن قائمة الألعاب المتوقعة وأبرز المفاجآت.</p>
                    </div>
                </a>
                <!-- News Item 2 -->
                <a href="#" class="flex items-center bg-gray-800 p-4 rounded-lg transition-transform duration-300 hover:bg-gray-700 hover:scale-102">
                    <img src="https://placehold.co/150x100/DC2626/FFFFFF?text=Update" alt="خبر" class="w-32 h-20 object-cover rounded-md">
                    <div class="mr-6 rtl:mr-0 rtl:ml-6">
                        <h3 class="text-xl font-bold text-white">تحديث ضخم للعبة "Valiant Warriors V" يضيف طور لعب جديد</h3>
                        <p class="text-gray-400">المطورون يستجيبون لطلبات اللاعبين بمحتوى إضافي مجاني.</p>
                    </div>
                </a>
            </div>
        </div>
    </div>
</section>