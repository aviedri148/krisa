<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ניתוח משבר הנסיעות לאומן</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Assistant:wght@300;400;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutrals & Slate Blue -->
    <!-- Application Structure Plan: The SPA is designed as a thematic, single-page dashboard. This structure allows users to explore the complex issue from multiple angles—the core problems, the underlying causes, attempted solutions, key data, and future lessons—in a non-linear, intuitive way. The navigation bar provides quick access to each theme, facilitating understanding of the multifaceted crisis better than a linear report. Key interactions include tabbed content for dissecting causes and interactive charts for data visualization, all aimed at making the dense information digestible and engaging. -->
    <!-- Visualization & Content Choices: 
        - Goal: Inform (Core Problems) -> Presentation: Icon-based cards -> Interaction: Quick visual summary -> Justification: Easily conveys the main pain points.
        - Goal: Organize/Analyze (Causes) -> Presentation: Tabbed interface, HTML/CSS flow diagram -> Interaction: Click to switch between logistical, political, and public factors -> Justification: Breaks down a complex web of causes into focused, manageable sections. The diagram visually explains the political tangle without complex graphics.
        - Goal: Compare/Quantify (Key Data) -> Presentation: Donut & Bar Charts (Chart.js), Stat Cards -> Interaction: Hover for tooltips, visual comparison -> Justification: Charts provide an immediate quantitative perspective on the scale of the issues (cancellations, financial disputes, capacity gaps).
        - Goal: Outline Process (Solutions/Lessons) -> Presentation: Styled lists -> Interaction: Clear, readable content -> Justification: Presents actionable takeaways and historical attempts in a straightforward format.
        - Library/Method: Chart.js for all charts on Canvas, Tailwind CSS for layout and styling. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Assistant', sans-serif;
            scroll-behavior: smooth;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 450px;
            margin-left: auto;
            margin-right: auto;
            height: 350px;
            max-height: 400px;
        }
        @media (max-width: 768px) {
            .chart-container {
                height: 300px;
            }
        }
        .tab-button.active {
            border-color: #3b82f6;
            background-color: #eff6ff;
            color: #3b82f6;
        }
    </style>
</head>
<body class="bg-[#F8F5F2] text-slate-800">

    <header class="bg-[#2C3E50] text-white shadow-md sticky top-0 z-50">
        <nav class="container mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <h1 class="text-xl md:text-2xl font-bold">משבר אומן</h1>
                <div class="hidden md:flex items-center space-x-8 space-x-reverse">
                    <a href="#problem" class="hover:text-blue-300 transition">הבעיה</a>
                    <a href="#causes" class="hover:text-blue-300 transition">הסיבות</a>
                    <a href="#data" class="hover:text-blue-300 transition">נתונים</a>
                    <a href="#solutions" class="hover:text-blue-300 transition">פתרונות</a>
                    <a href="#lessons" class="hover:text-blue-300 transition">לקחים</a>
                </div>
                <div class="md:hidden">
                    <select onchange="window.location.href = this.value;" class="bg-[#2C3E50] border-0 text-white rounded-md">
                        <option value="#_">ניווט</option>
                        <option value="#problem">הבעיה</option>
                        <option value="#causes">הסיבות</option>
                        <option value="#data">נתונים</option>
                        <option value="#solutions">פתרונות</option>
                        <option value="#lessons">לקחים</option>
                    </select>
                </div>
            </div>
        </nav>
    </header>

    <main class="container mx-auto p-4 sm:p-6 lg:p-8">

        <section id="hero" class="text-center py-16">
            <h2 class="text-4xl md:text-5xl font-bold text-[#2C3E50] mb-4">מסע התלאות לאומן: ניתוח המשבר</h2>
            <p class="text-lg md:text-xl text-slate-600 max-w-3xl mx-auto">
                המסע השנתי לאומן לראש השנה נתקל בקשיים חסרי תקדים, והותיר אלפי חסידים במצוקה. יישום זה מנתח את הגורמים המרכזיים למשבר, הפתרונות שנוסו, והלקחים החשובים לעתיד, על בסיס המידע והתובנות שעלו מהשטח.
            </p>
        </section>

        <section id="problem" class="py-16">
            <h3 class="text-3xl font-bold text-center mb-2 text-[#2C3E50]">מהות הבעיה: חווית הנוסעים</h3>
            <p class="text-center text-slate-600 mb-12 max-w-2xl mx-auto">המשבר לא היה רק לוגיסטי, אלא חוויה אנושית קשה עבור אלפי אנשים. אלו היו האתגרים המרכזיים איתם התמודדו הנוסעים בשטח.</p>
            <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
                <div class="bg-white p-6 rounded-lg shadow-lg text-center transform hover:scale-105 transition-transform duration-300">
                    <div class="text-5xl mb-4">🚌</div>
                    <h4 class="text-xl font-semibold mb-2">תקיעות בגבולות</h4>
                    <p class="text-slate-600">המתנות של 14 עד 24 שעות ואף יותר בגבולות, בעיקר במעבר לרומניה. אנשים נתקעו בקור, ללא תנאים בסיסיים, במצב של חוסר ודאות מוחלט.</p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-lg text-center transform hover:scale-105 transition-transform duration-300">
                    <div class="text-5xl mb-4">✈️</div>
                    <h4 class="text-xl font-semibold mb-2">ביטולי טיסות המוניים</h4>
                    <p class="text-slate-600">אלפי כרטיסי טיסה חזור בוטלו במפתיע, לעיתים במהלך החג עצמו. הדבר יצר כאוס וחרדה, כאשר נוסעים רבים הגיעו לשדות התעופה ללא כרטיס בתוקף.</p>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-lg text-center transform hover:scale-105 transition-transform duration-300">
                    <div class="text-5xl mb-4">ℹ️</div>
                    <h4 class="text-xl font-semibold mb-2">חוסר מידע ותיאום</h4>
                    <p class="text-slate-600">הציבור הרגיש חוסר אונים עקב מיעוט נציגים בשטח, קושי בקבלת מידע אמין, והיעדר תוכנית מסודרת לניהול הכאוס שנוצר בשדות התעופה ובגבולות.</p>
                </div>
            </div>
        </section>

        <section id="causes" class="py-16 bg-slate-50 rounded-lg">
            <h3 class="text-3xl font-bold text-center mb-2 text-[#2C3E50]">הסיבות שהובילו לכאוס</h3>
            <p class="text-center text-slate-600 mb-12 max-w-2xl mx-auto">המשבר נבע משילוב קטלני של מספר גורמים. חלקם היו צפויים, אחרים הפתיעו בעוצמתם. כאן נפרט את הגורמים המרכזיים שהצטברו יחד ויצרו "סופה מושלמת".</p>
            
            <div class="mb-8 border-b-2 border-slate-200 flex justify-center">
                <button class="tab-button active text-lg font-semibold py-2 px-6 border-b-2" data-tab="logistics">כשל לוגיסטי</button>
                <button class="tab-button text-lg font-semibold py-2 px-6 border-b-2 border-transparent" data-tab="politics">סבך פוליטי</button>
                <button class="tab-button text-lg font-semibold py-2 px-6 border-b-2 border-transparent" data-tab="public">התנהלות הציבור</button>
            </div>

            <div class="tab-content" id="logistics">
                <div class="bg-white p-8 rounded-lg shadow-inner">
                    <h4 class="text-2xl font-bold mb-4">קריסת המערך הלוגיסטי</h4>
                    <p class="mb-4">הבחירה בשדה התעופה הקטן בבקאו, רומניה, לא התאימה להיקף של 65 טיסות ואלפי נוסעים. למרות שהוצגה תכנית עבודה מפורטת (הכנסת קבוצות של 100 איש, 50 לצ'ק-אין ו-50 להמתנה), היא קרסה תחת העומס. המשטרה השתלטה על האירוע, הוציאה את הסוכנים מהתמונה, ואף אילצה להעלות נוסעים עם טיסות מאוחרות יותר, בעוד שאנשים עם טיסות קרובות נתקעו בחוץ. בנוסף, ההחלטה להמשיך לשלוח אוטובוסים מאומן לגבולות שכבר היו פקוקים החמירה את המצב, מתוך תקווה שהבעיה תיפתר "כל רגע".</p>
                </div>
            </div>

            <div class="tab-content hidden" id="politics">
                 <div class="bg-white p-8 rounded-lg shadow-inner">
                    <h4 class="text-2xl font-bold mb-4">השפעת היחסים בין המדינות</h4>
                    <p class="mb-6">המשבר הלוגיסטי הוצת והוחמר עקב מתיחויות פוליטיות. חסידי ברסלב מצאו את עצמם ככלי משחק ביחסים הדיפלומטיים בין ישראל, מולדובה ואוקראינה. האירועים לא היו מקריים אלא תוצאה של לחצים ואינטרסים פוליטיים.</p>
                    <div class="flex flex-col md:flex-row justify-around items-center text-center gap-4">
                        <div class="flex-1 p-4 border rounded-lg">
                             <h5 class="font-bold text-lg text-red-600">מולדובה</h5>
                             <p>מנעה כניסת ישראלים בתירוץ של חוב נטען של כ-200 אלף דולר ורשימה ארוכה של עניינים בלתי פתורים בין המדינות. ההחלטה סגרה נתיב מרכזי והפנתה את כל העומס לרומניה.</p>
                        </div>
                        <div class="text-4xl text-slate-400 font-light mx-4">&harr;</div>
                        <div class="flex-1 p-4 border rounded-lg bg-blue-50">
                             <h5 class="font-bold text-lg text-blue-700">ישראל</h5>
                             <p>התנהלות בירוקרטית איטית בעיכוב תשלומים (כמו 40 מיליון ש"ח לאוקראינה בעבר) וחוסר מעורבות מוקדמת תרמו להסלמת המצב מול מולדובה ואוקראינה. המלחמה בישראל הגבילה אף היא את יכולת התגובה.</p>
                        </div>
                         <div class="text-4xl text-slate-400 font-light mx-4">&harr;</div>
                        <div class="flex-1 p-4 border rounded-lg">
                             <h5 class="font-bold text-lg text-yellow-600">אוקראינה</h5>
                             <p>אינה מעוניינת במיוחד בהגעת חסידים בזמן מלחמה. המצב מראה דפוס חוזר של שימוש בקיבוץ באומן כמנוף לחץ לדרישות שונות.</p>
                        </div>
                    </div>
                </div>
            </div>
            
            <div class="tab-content hidden" id="public">
                <div class="bg-white p-8 rounded-lg shadow-inner">
                    <h4 class="text-2xl font-bold mb-4">הגורם האנושי והתנהגות הקהל</h4>
                    <p class="mb-4">גורם משמעותי שהוסיף שמן למדורה היה הגעתם של אלפי אנשים לשדות התעופה ללא כרטיס טיסה חזור בתוקף. חלקם איבדו את טיסתם עקב ביטולים, ואחרים הגיעו בתקווה "להסתדר". בנוסף, הלחץ והשמועות על סגירת שמי ישראל (בעקבות חיסול נסראללה) גרמו לאנשים עם טיסות מאוחרות יותר להגיע מוקדם, מה שיצר עומס בלתי נשלט שהוביל להתערבות המשטרה המקומית ולקריסת התכנון המקורי.</p>
                </div>
            </div>
        </section>


        <section id="data" class="py-16">
            <h3 class="text-3xl font-bold text-center mb-2 text-[#2C3E50]">המשבר במספרים: נתוני מפתח</h3>
            <p class="text-center text-slate-600 mb-12 max-w-2xl mx-auto">המספרים שמאחורי הכאוס ממחישים את היקף המשבר ואת האתגרים הלוגיסטיים והפיננסיים שעמדו בבסיסו.</p>
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-2 gap-8 items-center">
                <div>
                    <div class="grid grid-cols-2 gap-4 text-center">
                       <div class="bg-white p-4 rounded-lg shadow-lg">
                            <p class="text-3xl font-bold text-blue-600">16,000+</p>
                            <p class="text-slate-600">נוסעים בביטול ראשוני (מולדובה)</p>
                        </div>
                         <div class="bg-white p-4 rounded-lg shadow-lg">
                            <p class="text-3xl font-bold text-blue-600">~30</p>
                            <p class="text-slate-600">טיסות שבוטלו (גלים שונים)</p>
                        </div>
                        <div class="bg-white p-4 rounded-lg shadow-lg">
                            <p class="text-3xl font-bold text-blue-600">$200,000</p>
                            <p class="text-slate-600">חוב נטען למולדובה</p>
                        </div>
                         <div class="bg-white p-4 rounded-lg shadow-lg">
                            <p class="text-3xl font-bold text-blue-600">95%+</p>
                            <p class="text-slate-600">הגיעו לאומן (במאמץ רב)</p>
                        </div>
                    </div>
                </div>
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h4 class="text-xl font-semibold text-center mb-4">חלוקת הבעיות המרכזיות</h4>
                    <div class="chart-container">
                        <canvas id="issuesChart"></canvas>
                    </div>
                     <p class="text-xs text-center text-slate-500 mt-2">הערכה המבוססת על דגשים בשיח ובמסמך</p>
                </div>
                 <div class="bg-white p-6 rounded-lg shadow-lg col-span-1 md:col-span-2">
                    <h4 class="text-xl font-semibold text-center mb-4">פער קיבולת הרכבות</h4>
                    <div class="chart-container h-64 md:h-80 max-w-4xl">
                        <canvas id="trainsChart"></canvas>
                    </div>
                    <p class="text-center text-slate-600 mt-4">הניסיון להשתמש ברכבות כפתרון נתקל בפער עצום: הביקוש עומד על עשרות אלפים, בעוד שהקיבולת המקסימלית ברכבות מאוקראינה היא כ-1,500-2,500 איש ביום במקרה הטוב, מה שהופך את הפתרון לבלתי ריאלי להיקף הנוסעים.</p>
                </div>
            </div>
        </section>
        
        <section id="solutions" class="py-16 bg-slate-50 rounded-lg">
            <h3 class="text-3xl font-bold text-center mb-2 text-[#2C3E50]">ניסיונות לפתרון בזמן אמת</h3>
            <p class="text-center text-slate-600 mb-12 max-w-2xl mx-auto">למרות הכאוס, נעשו מאמצים רבים בשטח כדי להקל על המצוקה ולמצוא פתרונות, גם אם חלקיים.</p>
            <ul class="space-y-4 max-w-2xl mx-auto">
                <li class="bg-white p-4 rounded-lg shadow-sm flex items-start space-x-4 space-x-reverse">
                    <span class="text-blue-500 text-2xl font-bold">🚄</span>
                    <div>
                        <h4 class="font-semibold">בחינת חלופת הרכבות</h4>
                        <p class="text-slate-600">הושקעו זמן וכסף רבים בבחינת הפעלת רכבות ייעודיות מפולין. היוזמה נכשלה עקב בירוקרטיה, עלויות גבוהות וקיבולת נמוכה מדי (כאמור, כ-2,500 איש ביום לכל היותר).</p>
                    </div>
                </li>
                 <li class="bg-white p-4 rounded-lg shadow-sm flex items-start space-x-4 space-x-reverse">
                    <span class="text-blue-500 text-2xl font-bold">🗣️</span>
                    <div>
                        <h4 class="font-semibold">התערבות מול הרשויות</h4>
                        <p class="text-slate-600">ניסיונות הידברות עם המשטרה והרשויות ברומניה ובגבולות כדי לשחרר את הפקקים, לרוב ללא הצלחה משמעותית, כאשר המשטרה אף השתלטה על ניהול שדה התעופה בבקאו.</p>
                    </div>
                </li>
                <li class="bg-white p-4 rounded-lg shadow-sm flex items-start space-x-4 space-x-reverse">
                    <span class="text-blue-500 text-2xl font-bold">🎫</span>
                    <div>
                        <h4 class="font-semibold">שיבוץ מחדש של נוסעים</h4>
                        <p class="text-slate-600">הסוכנים עבדו מסביב לשעון כדי למצוא מקומות חלופיים לאלפי הנוסעים שטיסותיהם בוטלו (כולל יצירת 8 טיסות חילוץ נוספות), ולשבץ אותם בטיסות קיימות, לעיתים בפעם השלישית.</p>
                    </div>
                </li>
                 <li class="bg-white p-4 rounded-lg shadow-sm flex items-start space-x-4 space-x-reverse">
                    <span class="text-blue-500 text-2xl font-bold">💰</span>
                    <div>
                        <h4 class="font-semibold">התחייבויות כספיות עתק</h4>
                        <p class="text-slate-600">הסוכנים ספגו עלויות מטורפות (עשרות אלפי דולרים על נסיעות פנים, תוספות לחברות תעופה, ביטוחים), והתחייבו על טיסות גם אם לא יצאו, מבלי לבקש סנט נוסף מהלקוחות.</p>
                    </div>
                </li>
            </ul>
        </section>

        <section id="lessons" class="py-16">
            <h3 class="text-3xl font-bold text-center mb-2 text-[#2C3E50]">לקחים והמלצות לעתיד</h3>
             <p class="text-center text-slate-600 mb-12 max-w-2xl mx-auto">כדי למנוע הישנות של משבר כזה, יש להפיק לקחים ולהיערך אחרת. אלו הן המסקנות המרכזיות שעולות מהניתוח.</p>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 max-w-4xl mx-auto">
                <div class="bg-blue-50 p-6 rounded-lg border-r-4 border-blue-500">
                    <h4 class="font-bold text-lg mb-2">הפרדת הדת מהפוליטיקה</h4>
                    <p>יש לפעול כדי שהקיבוץ באומן לא יהפוך לקלף מיקוח פוליטי בין מדינות. יש צורך בניתוק האירוע מהדיפלומטיה, שכן חסידי ברסלב משמשים "בני ערובה" ביחסים אלו.</p>
                </div>
                <div class="bg-blue-50 p-6 rounded-lg border-r-4 border-blue-500">
                    <h4 class="font-bold text-lg mb-2">היערכות מוקדמת וריאלית</h4>
                    <p>התכנון לשנים הבאות חייב להתחיל מוקדם הרבה יותר (כמעט שנה מראש), תוך בחינת כל התרחישים ובחירת נתיבים ושדות תעופה שיכולים לעמוד בעומס, והבנה שאין זמן להתארגנות של הרגע האחרון.</p>
                </div>
                 <div class="bg-blue-50 p-6 rounded-lg border-r-4 border-blue-500">
                    <h4 class="font-bold text-lg mb-2">ניהול מרכזי ותקשורת</h4>
                    <p>יש לשקול הקמת גוף ניהול מתכלל שיוכל לספק מידע אמין לציבור ולתאם בין כל הגורמים בשטח בזמן אמת, במיוחד במצבי לחץ ואי-ודאות.</p>
                </div>
                <div class="bg-blue-50 p-6 rounded-lg border-r-4 border-blue-500">
                    <h4 class="font-bold text-lg mb-2">הדילמה המרכזית: הגעה מול סבל</h4>
                    <p>הלקח המרכזי הוא ההתמודדות עם הדילמה: האם המטרה העיקרית היא להביא כל יהודי לאומן, גם במחיר סבל רב, או לבטל טיסות כדי למנוע סבל? שאלה זו מלווה את המארגנים כל העת.</p>
                </div>
            </div>
        </section>
    </main>

    <footer class="bg-[#2C3E50] text-white text-center p-4 mt-8">
        <p>&copy; 2024 ניתוח משבר הנסיעות לאומן. נוצר להמחשה בלבד.</p>
    </footer>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            
            const tabButtons = document.querySelectorAll('.tab-button');
            const tabContents = document.querySelectorAll('.tab-content');

            tabButtons.forEach(button => {
                button.addEventListener('click', () => {
                    tabButtons.forEach(btn => btn.classList.remove('active'));
                    button.classList.add('active');
                    
                    const tabId = button.dataset.tab;
                    tabContents.forEach(content => {
                        if (content.id === tabId) {
                            content.classList.remove('hidden');
                        } else {
                            content.classList.add('hidden');
                        }
                    });
                });
            });

            const issuesCtx = document.getElementById('issuesChart').getContext('2d');
            new Chart(issuesCtx, {
                type: 'doughnut',
                data: {
                    labels: ['ביטולי טיסות/גבולות', 'סבך פוליטי', 'כשל לוגיסטי', 'התנהלות הקהל'],
                    datasets: [{
                        label: 'חלוקת הבעיות',
                        data: [40, 25, 20, 15], /* Updated data based on new document emphasis */
                        backgroundColor: [
                            '#ef4444', // red-500
                            '#f97316', // orange-500
                            '#3b82f6', // blue-500
                            '#84cc16'  // lime-500
                        ],
                        borderColor: '#F8F5F2',
                        borderWidth: 4
                    }]
                },
                options: {
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            position: 'bottom',
                            labels: {
                                font: {
                                    family: "'Assistant', sans-serif"
                                }
                            }
                        },
                        tooltip: {
                            bodyFont: {
                                family: "'Assistant', sans-serif"
                            },
                            titleFont: {
                                family: "'Assistant', sans-serif"
                            }
                        }
                    }
                }
            });

            const trainsCtx = document.getElementById('trainsChart').getContext('2d');
            new Chart(trainsCtx, {
                type: 'bar',
                data: {
                    labels: ['הביקוש לנסיעה (עשרות אלפים)', 'קיבולת יומית מרבית ברכבות'],
                    datasets: [{
                        label: 'מספר נוסעים',
                        data: [35000, 2500], /* Updated data based on new document for train capacity */
                         backgroundColor: [
                            'rgba(239, 68, 68, 0.6)',
                            'rgba(59, 130, 246, 0.6)'
                        ],
                        borderColor: [
                            'rgba(239, 68, 68, 1)',
                            'rgba(59, 130, 246, 1)'
                        ],
                        borderWidth: 1
                    }]
                },
                options: {
                    indexAxis: 'y',
                    responsive: true,
                    maintainAspectRatio: false,
                    plugins: {
                        legend: {
                            display: false
                        }
                    },
                    scales: {
                        x: {
                            beginAtZero: true,
                            ticks: {
                                callback: function(value) {
                                    return value.toLocaleString('he-IL');
                                }
                            }
                        }
                    }
                }
            });

        });
    </script>

</body>
</html>
# krisa
