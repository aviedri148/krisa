<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>אומן תשפ"ד – איך קרס המסע הגדול בעולם?</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Assistant:wght@300;400;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutrals & Slate Blue, with dynamic slide colors (Blue, Neutral, Red, Green) -->
    <!-- Application Structure Plan: The SPA is designed as a linear, slide-based presentation, allowing users to progress through the narrative of the Uman crisis step-by-step. This structure was chosen to tell a cohesive story, moving from a general overview to specific causes, human impact, solutions, and lessons learned, culminating in a powerful quote. Navigation is controlled by "Next" and "Previous" buttons, providing a clear user flow. Each slide has a distinct thematic background color to visually reinforce the content's tone. Charts are integrated into relevant slides to provide quantitative context. -->
    <!-- Visualization & Content Choices: 
        - Goal: Inform (Overview, Human Cost, Solutions, Lessons, Quote) -> Presentation: Text blocks, icon-based cards, styled lists -> Interaction: Slide navigation -> Justification: Delivers narrative and key takeaways clearly.
        - Goal: Organize/Analyze (Timeline, Causes) -> Presentation: HTML/CSS timeline, Doughnut Chart -> Interaction: Slide navigation, chart tooltips -> Justification: Visualizes chronological events and breaks down complex causes into digestible proportions.
        - Goal: Compare/Quantify (Overview - Train Capacity) -> Presentation: Bar Chart -> Interaction: Slide navigation, chart tooltips -> Justification: Highlights the scale of the challenge and the unsuitability of alternative transport.
        - Library/Method: Chart.js for all charts on Canvas, Tailwind CSS for layout and styling. Unicode emojis for icons. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Assistant', sans-serif;
            scroll-behavior: smooth;
        }
        .slide-container {
            min-height: calc(100vh - 128px); /* Full height minus header/footer */
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            opacity: 0;
            transition: opacity 0.5s ease-in-out, background-color 0.5s ease-in-out;
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            padding: 2rem;
            box-sizing: border-box;
        }
        .slide-container.active {
            opacity: 1;
            position: relative;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 450px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 350px;
        }
        @media (max-width: 768px) {
            .chart-container {
                height: 250px;
                max-height: 300px;
            }
        }
    </style>
</head>
<body class="bg-[#F8F5F2] text-slate-800">

    <header class="bg-[#2C3E50] text-white shadow-md sticky top-0 z-50">
        <nav class="container mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex items-center justify-between h-16">
                <h1 class="text-xl md:text-2xl font-bold">אומן תשפ"ד – איך קרס המסע הגדול בעולם?</h1>
                <div class="flex items-center space-x-4 space-x-reverse">
                    <span id="slide-counter" class="text-lg"></span>
                    <button id="prev-slide" class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full transition-colors duration-200 disabled:opacity-50 disabled:cursor-not-allowed">
                        &larr; קודם
                    </button>
                    <button id="next-slide" class="bg-blue-600 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded-full transition-colors duration-200 disabled:opacity-50 disabled:cursor-not-allowed">
                        הבא &rarr;
                    </button>
                </div>
            </div>
        </nav>
    </header>

    <main class="relative overflow-hidden min-h-[calc(100vh-64px)]">
        <!-- Slide 1: מבט כללי -->
        <section id="slide-1" class="slide-container active bg-blue-100">
            <div class="text-center max-w-4xl mx-auto p-4 rounded-lg">
                <h2 class="text-4xl md:text-5xl font-bold text-[#2C3E50] mb-6">מסע שאין כמוהו בעולם</h2>
                <div class="flex flex-col md:flex-row items-center justify-center gap-6 mb-8">
                    <div class="text-6xl">🇮🇱</div>
                    <div class="text-4xl">✈️</div>
                    <div class="text-4xl">➡️</div>
                    <div class="text-6xl">🇲🇩 / 🇷🇴</div>
                    <div class="text-4xl">➡️</div>
                    <div class="text-4xl">🚌</div>
                    <div class="text-6xl">🇺🇦</div>
                </div>
                <p class="text-lg md:text-xl text-slate-700 mb-8">
                    מסע רב-יבשתי, בשיא מלחמה באוקראינה וישראל, דרך מדינות שלא רוצות שנעבור בהן. פרויקט בסדר גודל שאין לו אח ורע בעולם, שנעשה בתנאים כמעט בלתי אפשריים.
                </p>
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h4 class="text-xl font-semibold text-center mb-4">פער קיבולת הרכבות</h4>
                    <div class="chart-container">
                        <canvas id="trainsChart"></canvas>
                    </div>
                    <p class="text-center text-slate-600 mt-4 text-sm">
                        הניסיון להשתמש ברכבות כפתרון נתקל בפער עצום: הביקוש עומד על עשרות אלפים, בעוד שהקיבולת המקסימלית ברכבות מאוקראינה היא כ-1,500-2,500 איש ביום במקרה הטוב, מה שהופך את הפתרון לבלתי ריאלי להיקף הנוסעים.
                    </p>
                </div>
            </div>
        </section>

        <!-- Slide 2: השתלשלות האירועים בקצרה -->
        <section id="slide-2" class="slide-container hidden bg-slate-50">
            <div class="text-center max-w-4xl mx-auto p-4 rounded-lg">
                <h2 class="text-4xl md:text-5xl font-bold text-[#2C3E50] mb-6">השתלשלות האירועים בקצרה</h2>
                <div class="relative py-8">
                    <div class="absolute inset-x-0 top-1/2 h-1 bg-slate-300 transform -translate-y-1/2"></div>
                    <div class="flex justify-between items-start text-sm md:text-base">
                        <div class="flex-1 text-center relative px-2">
                            <div class="w-4 h-4 bg-blue-500 rounded-full absolute -top-2 left-1/2 -translate-x-1/2"></div>
                            <p class="mt-4 font-semibold">חשוון תשפ"ד</p>
                            <p class="text-slate-600">התחלת הכנות</p>
                        </div>
                        <div class="flex-1 text-center relative px-2">
                            <div class="w-4 h-4 bg-blue-500 rounded-full absolute -top-2 left-1/2 -translate-x-1/2"></div>
                            <p class="mt-4 font-semibold">אלול</p>
                            <p class="text-slate-600">ביטולי מולדובה</p>
                        </div>
                        <div class="flex-1 text-center relative px-2">
                            <div class="w-4 h-4 bg-blue-500 rounded-full absolute -top-2 left-1/2 -translate-x-1/2"></div>
                            <p class="mt-4 font-semibold">כ"ה אלול</p>
                            <p class="text-slate-600">מלחמה בישראל, איסור טיסות</p>
                        </div>
                        <div class="flex-1 text-center relative px-2">
                            <div class="w-4 h-4 bg-blue-500 rounded-full absolute -top-2 left-1/2 -translate-x-1/2"></div>
                            <p class="mt-4 font-semibold">א' תשרי</p>
                            <p class="text-slate-600">הגעה לאומן (בקושי)</p>
                        </div>
                        <div class="flex-1 text-center relative px-2">
                            <div class="w-4 h-4 bg-blue-500 rounded-full absolute -top-2 left-1/2 -translate-x-1/2"></div>
                            <p class="mt-4 font-semibold">אחרי החג</p>
                            <p class="text-slate-600">קריסת חזרה (בקאו)</p>
                        </div>
                    </div>
                </div>
                <p class="text-lg text-slate-700 mt-8">
                    ההכנות החלו כמעט שנה מראש, אך שרשרת אירועים בלתי צפויים וביטולים דרמטיים הובילו לכאוס מוחלט, במיוחד בימים שלפני ראש השנה ובחזרה ממנו.
                </p>
            </div>
        </section>

        <!-- Slide 3: סיבת הקריסה -->
        <section id="slide-3" class="slide-container hidden bg-red-50">
            <div class="text-center max-w-4xl mx-auto p-4 rounded-lg">
                <h2 class="text-4xl md:text-5xl font-bold text-[#2C3E50] mb-6">סיבת הקריסה: שילוב גורמים קטלני</h2>
                <p class="text-lg text-slate-700 mb-8">
                    המשבר נבע משילוב של כשלים לוגיסטיים, סבך פוליטי, וגורמים אנושיים שהצטברו יחד ויצרו "סופה מושלמת".
                </p>
                <div class="bg-white p-6 rounded-lg shadow-lg">
                    <h4 class="text-xl font-semibold text-center mb-4">חלוקת הבעיות המרכזיות</h4>
                    <div class="chart-container">
                        <canvas id="issuesChart"></canvas>
                    </div>
                    <p class="text-xs text-center text-slate-500 mt-2">הערכה המבוססת על דגשים בשיח ובמסמך</p>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-4 mt-8 text-left">
                    <div class="bg-white p-4 rounded-lg shadow-sm">
                        <h4 class="font-bold text-lg mb-1">חוב של ישראל למולדובה</h4>
                        <p class="text-slate-600 text-sm">חוב נטען של כ-200 אלף דולר, ששימש כקלף מיקוח וגרם לביטול אישורי טיסות.</p>
                    </div>
                    <div class="bg-white p-4 rounded-lg shadow-sm">
                        <h4 class="font-bold text-lg mb-1">מלחמות בירוקרטיות</h4>
                        <p class="text-slate-600 text-sm">איחורים באישורים, חוסר גמישות והתעלמות של הרשויות מהמציאות בשטח.</p>
                    </div>
                    <div class="bg-white p-4 rounded-lg shadow-sm">
                        <h4 class="font-bold text-lg mb-1">שדות תעופה לא ערוכים</h4>
                        <p class="text-slate-600 text-sm">שדות קטנים כמו בקאו לא היו מסוגלים להכיל את עשרות אלפי הנוסעים.</p>
                    </div>
                    <div class="bg-white p-4 rounded-lg shadow-sm">
                        <h4 class="font-bold text-lg mb-1">התערבות המשטרה</h4>
                        <p class="text-slate-600 text-sm">השתלטות המשטרה על ניהול שדה התעופה בבקאו הוציאה את הסוכנים מהתמונה וגרמה לכאוס.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Slide 4: המחיר האנושי -->
        <section id="slide-4" class="slide-container hidden bg-slate-50">
            <div class="text-center max-w-4xl mx-auto p-4 rounded-lg">
                <h2 class="text-4xl md:text-5xl font-bold text-[#2C3E50] mb-6">הסבל שלא רואים בחדשות</h2>
                <p class="text-lg text-slate-700 mb-8">
                    המחיר האנושי של הכאוס היה כבד מנשוא, והותיר אלפי חסידים עם חוויה קשה וכואבת.
                </p>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="bg-white p-6 rounded-lg shadow-lg">
                        <div class="text-5xl mb-4">👶😭</div>
                        <p class="text-slate-700">"המתנות של 15 שעות בקור, ילדים בוכים, ללא תנאים בסיסיים."</p>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-lg">
                        <div class="text-5xl mb-4">🧳🚶‍♂️</div>
                        <p class="text-slate-700">"שדות תעופה מלאים ללא סדר, אנשים עם מזוודות תקועים שעות ארוכות."</p>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-lg">
                        <div class="text-5xl mb-4">👴 collapses</div>
                        <p class="text-slate-700">"חוסר שליטה מוחלט – גם מי שהיה לו כרטיס – לא עלה לטיסה."</p>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-lg">
                        <div class="text-5xl mb-4">👮‍♂️🚫</div>
                        <p class="text-slate-700">"המשטרה הוציאה את הסוכנים מחוץ לתמונה, והחליטה מי נכנס לשדה התעופה."</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Slide 5: נקודת האור -->
        <section id="slide-5" class="slide-container hidden bg-green-50">
            <div class="text-center max-w-4xl mx-auto p-4 rounded-lg">
                <h2 class="text-4xl md:text-5xl font-bold text-[#2C3E50] mb-6">למרות הכל – נקודת האור</h2>
                <p class="text-lg md:text-xl text-slate-700 mb-8">
                    בתוך הכאוס והסבל, בלטו מסירות הנפש והמאמצים העילאיים שאפשרו את קיום המסע.
                </p>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                    <div class="bg-white p-6 rounded-lg shadow-lg">
                        <div class="text-5xl mb-4">🙏</div>
                        <h4 class="text-xl font-semibold mb-2">מסירות נפש</h4>
                        <p class="text-slate-700">"למרות כל הקשיים והמניעות – למעלה מ-95% מהלקוחות הגיעו לרבינו באומן!"</p>
                    </div>
                    <div class="bg-white p-6 rounded-lg shadow-lg">
                        <div class="text-5xl mb-4">💸</div>
                        <h4 class="text-xl font-semibold mb-2">מחיר כבד לסוכנים</h4>
                        <p class="text-slate-700">"לא דרשנו שקל נוסף מהנוסעים – למרות הפסדים של מאות אלפי דולרים."</p>
                    </div>
                </div>
                <p class="text-lg text-slate-700 mt-8">
                    הסוכנים נלחמו על כל טיסה, ספגו עלויות מטורפות, והתחייבו על טיסות גם בסיכון, הכל כדי להבטיח את הגעת החסידים.
                </p>
            </div>
        </section>

        <!-- Slide 6: מסקנות לעתיד -->
        <section id="slide-6" class="slide-container hidden bg-blue-100">
            <div class="text-center max-w-4xl mx-auto p-4 rounded-lg">
                <h2 class="text-4xl md:text-5xl font-bold text-[#2C3E50] mb-6">לקחים שחייבים ללמוד</h2>
                <p class="text-lg text-slate-700 mb-8">
                    כדי למנוע הישנות של משבר כזה, יש להפיק לקחים עמוקים ולבנות תוכנית עבודה חדשה.
                </p>
                <ul class="space-y-4 max-w-2xl mx-auto text-left">
                    <li class="bg-white p-4 rounded-lg shadow-sm flex items-start space-x-4 space-x-reverse">
                        <span class="text-blue-500 text-2xl font-bold">🏛️</span>
                        <div>
                            <h4 class="font-semibold">קשרים ברורים עם ממשלות</h4>
                            <p class="text-slate-600">הפרדת הדת מהפוליטיקה ויצירת ערוצי תקשורת רשמיים ויציבים עם מדינות המעבר.</p>
                        </div>
                    </li>
                    <li class="bg-white p-4 rounded-lg shadow-sm flex items-start space-x-4 space-x-reverse">
                        <span class="text-blue-500 text-2xl font-bold">🎯</span>
                        <div>
                            <h4 class="font-semibold">מוקד תיאום מרכזי</h4>
                            <p class="text-slate-600">גוף אחד שיתכלל את כל הלוגיסטיקה, התקשורת והטיפול במשברים בזמן אמת.</p>
                        </div>
                    </li>
                    <li class="bg-white p-4 rounded-lg shadow-sm flex items-start space-x-4 space-x-reverse">
                        <span class="text-blue-500 text-2xl font-bold">🔄</span>
                        <div>
                            <h4 class="font-semibold">תכנית גיבוי מקיפה</h4>
                            <p class="text-slate-600">הכנות לוגיסטיות לשני תרחישים (הלוך וחזור), כולל שדות תעופה חלופיים, רכבות ואוטובוסים.</p>
                        </div>
                    </li>
                    <li class="bg-white p-4 rounded-lg shadow-sm flex items-start space-x-4 space-x-reverse">
                        <span class="text-blue-500 text-2xl font-bold">💬</span>
                        <div>
                            <h4 class="font-semibold">תקשורת רציפה עם הנוסעים</h4>
                            <p class="text-slate-600">עדכון שוטף ואמין של הציבור, גם במצבי אי-ודאות, כדי למנוע בהלה ועומס מיותר.</p>
                        </div>
                    </li>
                </ul>
            </div>
        </section>

        <!-- Slide 7: ציטוט מרגש לסיום -->
        <section id="slide-7" class="slide-container hidden bg-slate-50">
            <div class="text-center max-w-4xl mx-auto p-4 rounded-lg">
                <h2 class="text-4xl md:text-5xl font-bold text-[#2C3E50] mb-6">מסר לסיום</h2>
                <p class="text-3xl md:text-4xl font-semibold text-slate-700 italic leading-snug mb-8">
                    "עשינו הכול כדי להביא יהודים לרבינו – גם אם נשרטנו בדרך."
                </p>
                <p class="text-lg text-slate-600">- מתוך מכתבי הסיכום של הסוכנים</p>
            </div>
        </section>
    </main>

    <footer class="bg-[#2C3E50] text-white text-center p-4 mt-8">
        <p>&copy; 2024 ניתוח משבר הנסיעות לאומן. נוצר להמחשה בלבד.</p>
    </footer>

    <script>
        let currentSlideIndex = 0;
        const slides = document.querySelectorAll('.slide-container');
        const slideCounter = document.getElementById('slide-counter');
        const prevButton = document.getElementById('prev-slide');
        const nextButton = document.getElementById('next-slide');

        const slideBackgrounds = [
            'bg-blue-100',    // Slide 1
            'bg-slate-50',    // Slide 2
            'bg-red-50',      // Slide 3
            'bg-slate-50',    // Slide 4
            'bg-green-50',    // Slide 5
            'bg-blue-100',    // Slide 6
            'bg-slate-50'     // Slide 7
        ];

        function updateSlideDisplay() {
            slides.forEach((slide, index) => {
                if (index === currentSlideIndex) {
                    slide.classList.add('active');
                    slide.classList.remove('hidden');
                    // Remove all existing background classes
                    slideBackgrounds.forEach(bg => slide.classList.remove(bg));
                    // Add the correct background for the current slide
                    slide.classList.add(slideBackgrounds[index]);
                } else {
                    slide.classList.remove('active');
                    slide.classList.add('hidden');
                }
            });
            slideCounter.textContent = `${currentSlideIndex + 1} / ${slides.length}`;
            prevButton.disabled = currentSlideIndex === 0;
            nextButton.disabled = currentSlideIndex === slides.length - 1;
        }

        prevButton.addEventListener('click', () => {
            if (currentSlideIndex > 0) {
                currentSlideIndex--;
                updateSlideDisplay();
            }
        });

        nextButton.addEventListener('click', () => {
            if (currentSlideIndex < slides.length - 1) {
                currentSlideIndex++;
                updateSlideDisplay();
            }
        });

        document.addEventListener('DOMContentLoaded', function () {
            updateSlideDisplay(); // Initialize first slide

            const issuesCtx = document.getElementById('issuesChart').getContext('2d');
            new Chart(issuesCtx, {
                type: 'doughnut',
                data: {
                    labels: ['ביטולי טיסות גורפים', 'סגירת מולדובה/רומניה', 'כשל ניהולי בשטח', 'התנהלות הציבור'],
                    datasets: [{
                        label: 'חלוקת הבעיות',
                        data: [35, 30, 20, 15],
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
                        data: [35000, 2500],
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

                }
            });

        });
    </script>

</body>
</html>
# krisa
