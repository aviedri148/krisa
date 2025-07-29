<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MATOK בגבעה - כל המחירונים</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        /* Custom font for a more appealing look */
        @import url('https://fonts.googleapis.com/css2?family=Heebo:wght@400;700;900&display=swap');
        body {
            font-family: 'Heebo', sans-serif;
            background-color: #f0fdf4; /* Light green background */
            display: flex;
            flex-direction: column; /* Arrange sections vertically */
            align-items: center;
            justify-content: flex-start; /* Align content to the top */
            min-height: 100vh;
            padding: 2rem;
        }
        .section-container {
            background-color: #fff;
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05); /* shadow-xl */
            border-radius: 1rem; /* rounded-2xl */
            padding: 1.5rem; /* p-6 */
            border: 4px solid #10b981; /* border-green-500 */
            margin-bottom: 2rem; /* Space between sections */
        }
        .price-item {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 0.75rem 0;
            border-bottom: 1px dashed #d1d5db; /* Dashed line for separation */
        }
        .price-item:last-child {
            border-bottom: none; /* No border for the last item */
        }

        /* Styles for individual price tags (squares) */
        .nut-tags-container {
            width: 100%;
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 1.5rem; /* Space between squares */
            padding: 2rem 0; /* Padding around the squares section */
            margin-top: 2rem; /* Space after other price lists */
        }
        .price-tag-square {
            width: 200px; /* Width of the square */
            height: 200px; /* Height of the square */
            border-radius: 0.5rem; /* Slightly rounded corners for a softer look */
            background-color: #ffffff;
            border: 4px solid #10b981; /* Green border */
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            align-items: center;
            text-align: center;
            padding: 1rem;
            position: relative;
            overflow: hidden; /* Ensure content stays within square */
        }
        .logo-small {
            line-height: 1; /* Adjust line height for compact logo */
            margin-bottom: 0.25rem; /* Small margin below logo */
        }
        .logo-small .m-text {
            color: #dc2626; /* red-600 */
            font-size: 1.5rem; /* Smaller M */
            font-weight: 900; /* font-extrabold */
        }
        .logo-small .matok-text {
            color: #047857; /* green-700 */
            font-size: 1rem; /* Smaller MATOK */
            font-weight: 900; /* font-extrabold */
        }
        .logo-small .bagivah-text {
            color: #4b5563; /* gray-700 */
            font-size: 0.75rem; /* Smaller בגבעה */
            font-weight: 600; /* font-semibold */
        }
        .product-name {
            font-size: 1.5rem; /* Smaller product name */
            font-weight: 700; /* font-bold */
            color: #1f2937; /* gray-900 */
            margin-bottom: 0.25rem;
            line-height: 1.2;
        }
        .price {
            font-size: 2.5rem; /* Very large price */
            font-weight: 900; /* font-extrabold */
            color: #047857; /* green-700 */
            line-height: 1;
        }
        .per-100g {
            font-size: 0.9rem; /* Smaller text for "ל-100 גרם" */
            font-weight: 600;
            color: #4b5563; /* gray-700 */
            margin-top: 0.25rem;
        }

        /* Print styles for better output */
        @media print {
            body {
                background-color: #fff !important; /* White background for printing */
                color: #000 !important; /* Black text for printing */
                padding: 0.5cm !important; /* Use cm for print consistency */
                margin: 0 !important; /* Remove body margins */
                width: 21cm; /* A4 width */
                height: 29.7cm; /* A4 height */
                box-sizing: border-box; /* Include padding in width/height */
            }
            .section-container {
                box-shadow: none !important; /* Remove shadows for printing */
                border: 1px solid #10b981 !important; /* Thinner border for print */
                margin-bottom: 0.8cm !important; /* Adjust margin for print */
                padding: 1cm !important; /* Adjust padding for print */
                max-width: 100% !important; /* Allow sections to take full print width */
                break-inside: avoid; /* Avoid breaking sections across pages */
            }
            .price-tag-square {
                box-shadow: none !important; /* Remove shadows for printing */
                border: 1px solid #10b981 !important; /* Thinner border for print */
                gap: 0.3cm !important; /* Smaller gap for printing squares */
                width: 6cm; /* Fixed width for print tags */
                height: 6cm; /* Fixed height for print tags */
                break-inside: avoid; /* Avoid breaking tags across pages */
            }
            .nut-tags-container {
                gap: 0.5cm !important; /* Smaller gap for printing squares container */
                padding: 1cm 0 !important; /* Adjust padding for print */
                margin-top: 1cm !important; /* Adjust margin for print */
                page-break-before: always; /* Start nuts tags on a new page */
            }
            h1, h2, h3, p, span {
                color: #000 !important; /* Ensure all text is black for printing */
            }
            /* Fine-tune font sizes for optimal print output on A4 */
            .text-4xl { font-size: 1.2rem !important; } /* Logo M */
            .text-2xl { font-size: 1rem !important; } /* Logo MATOK */
            .text-lg { font-size: 0.8rem !important; } /* Logo בגבעה */
            .text-base { font-size: 0.9rem !important; } /* Slogan */
            .text-sm { font-size: 0.7rem !important; } /* Phone number */
            .text-xs { font-size: 0.6rem !important; } /* מתוקים • מאפים • פינוקים */

            /* Specific adjustments for price lists */
            .section-container h3 { font-size: 1.5rem !important; } /* Section titles */
            .section-container .price-item span { font-size: 1rem !important; } /* Price list items */
            .section-container .price-item .font-bold { font-size: 1rem !important; } /* Price list prices */

            /* Specific adjustments for large price sections (chocolates, gummy, generic) */
            .section-container .text-5xl { font-size: 2.5rem !important; } /* Large price */
            .section-container .text-6xl { font-size: 3rem !important; } /* Largest price */
            .section-container .text-3xl { font-size: 1.2rem !important; } /* Per 100g / Kg */
            .section-container .text-4xl.font-bold { font-size: 1.5rem !important; } /* Hechsher text */

            /* Adjustments for nut tags */
            .price-tag-square .product-name { font-size: 1.1rem !important; } /* Product name in tag */
            .price-tag-square .price { font-size: 1.8rem !important; } /* Price in tag */
            .price-tag-square .per-100g { font-size: 0.7rem !important; } /* Per 100g in tag */
        }
    </style>
</head>
<body>

    <!-- Drinks Price List Section -->
    <div class="section-container max-w-md w-full">
        <!-- Logo Section (consistent across all) -->
        <div class="text-center mb-2">
            <div class="text-red-600 text-4xl font-bold leading-none mb-0">M</div>
            <h1 class="text-2xl font-extrabold text-green-700 mb-0">MATOK</h1>
            <h2 class="text-lg font-semibold text-gray-700 mb-0">בגבעה</h2>
            <p class="text-gray-500 text-xs mt-0">מתוקים • מאפים • פינוקים</p>
        </div>

        <!-- Price List Section -->
        <div class="mt-8">
            <h3 class="text-2xl font-bold text-center text-green-600 mb-6 pb-2 border-b-2 border-green-400">מחירון שתיה קלה</h3>

            <div class="space-y-4">
                <div class="price-item">
                    <span class="text-lg font-medium text-gray-800">קוקה קולה פחית</span>
                    <span class="text-lg font-bold text-green-700">8 ש"ח</span>
                </div>
                <div class="price-item">
                    <span class="text-lg font-medium text-gray-800">קוקה קולה בקבוק</span>
                    <span class="text-lg font-bold text-green-700">10 ש"ח</span>
                </div>
                <div class="price-item">
                    <span class="text-lg font-medium text-gray-800">ספרייט פחית</span>
                    <span class="text-lg font-bold text-green-700">8 ש"ח</span>
                </div>
                <div class="price-item">
                    <span class="text-lg font-medium text-gray-800">פאנטה בקבוק</span>
                    <span class="text-lg font-bold text-green-700">10 ש"ח</span>
                </div>
                <div class="price-item">
                    <span class="text-lg font-medium text-gray-800">נסטי אפרסק בקבוק</span>
                    <span class="text-lg font-bold text-green-700">9 ש"ח</span>
                </div>
                <div class="price-item">
                    <span class="text-lg font-medium text-gray-800">מים מינרליים קטן</span>
                    <span class="text-lg font-bold text-green-700">6 ש"ח</span>
                </div>
                <div class="price-item">
                    <span class="text-lg font-medium text-gray-800">מים מינרליים גדול</span>
                    <span class="text-lg font-bold text-green-700">8 ש"ח</span>
                </div>
                <div class="price-item">
                    <span class="text-lg font-medium text-gray-800">מיץ תפוזים סחוט</span>
                    <span class="text-lg font-bold text-green-700">12 ש"ח</span>
                </div>
                <div class="price-item">
                    <span class="text-lg font-medium text-gray-800">שוקו יוטבתה</span>
                    <span class="text-lg font-bold text-green-700">9 ש"ח</span>
                </div>
                <div class="price-item">
                    <span class="text-lg font-medium text-gray-800">בירה שחורה</span>
                    <span class="text-lg font-bold text-green-700">10 ש"ח</span>
                </div>
            </div>
        </div>

        <!-- Slogan -->
        <div class="text-center mt-8 pt-4 border-t-2 border-gray-200 text-gray-600 text-base font-bold">
            <p>תמיד טרי • תמיד מתוק</p>
        </div>
    </div>

    <!-- Chocolates & Candies Price List Section -->
    <div class="section-container max-w-xl w-full"> <!-- Wider for landscape feel -->
        <!-- Logo Section -->
        <div class="text-center mb-2">
            <div class="text-red-600 text-4xl font-bold leading-none mb-0">M</div>
            <h1 class="text-2xl font-extrabold text-green-700 mb-0">MATOK</h1>
            <h2 class="text-lg font-semibold text-gray-700 mb-0">בגבעה</h2>
            <p class="text-gray-500 text-xs mt-0">מתוקים • מאפים • פינוקים</p>
        </div>

        <!-- Price List Section for Chocolates/Candies -->
        <div class="flex-grow flex items-center justify-center text-center py-4">
            <div>
                <h3 class="text-4xl font-bold text-green-600 mb-6 pb-2 border-b-2 border-green-400 inline-block px-4">שוקולדים • סוכריות</h3>
                <p class="text-5xl font-extrabold text-gray-800 mt-4">
                    8.90 ש"ח
                </p>
                <p class="text-3xl font-semibold text-gray-700 mt-2">
                    ל-100 גרם
                </p>
                <p class="text-4xl font-bold text-gray-700 mt-4">
                    העדה החרדית
                </p>
            </div>
        </div>

        <!-- Slogan -->
        <div class="text-center mt-8 pt-4 border-t-2 border-gray-200 text-gray-600 text-base font-bold">
            <p>תמיד טרי • תמיד מתוק</p>
        </div>
    </div>

    <!-- Gummy Candies Price List Section -->
    <div class="section-container max-w-xl w-full"> <!-- Wider for landscape feel -->
        <!-- Logo Section -->
        <div class="text-center mb-2">
            <div class="text-red-600 text-4xl font-bold leading-none mb-0">M</div>
            <h1 class="text-2xl font-extrabold text-green-700 mb-0">MATOK</h1>
            <h2 class="text-lg font-semibold text-gray-700 mb-0">בגבעה</h2>
            <p class="text-gray-500 text-xs mt-0">מתוקים • מאפים • פינוקים</p>
        </div>

        <!-- Price List Section for Gummy Candies -->
        <div class="flex-grow flex items-center justify-center text-center py-4">
            <div>
                <div class="flex items-center justify-center mb-6 pb-2 border-b-2 border-green-400">
                    <h3 class="text-4xl font-bold text-green-600 inline-block px-4">ממתקי גומי</h3>
                </div>
                <p class="text-5xl font-extrabold text-gray-800 mt-4">
                    6.90 ש"ח
                </p>
                <p class="text-3xl font-semibold text-gray-700 mt-2">
                    ל-100 גרם
                </p>
                <p class="text-4xl font-bold text-gray-700 mt-4">
                    איגוד הרבנים
                </p>
                <div id="llmResponse" class="mt-8 p-4 bg-yellow-100 border border-yellow-300 rounded-lg text-gray-700 text-base hidden">
                    <p id="llmText"></p>
                    <div id="loadingIndicator" class="hidden text-center text-yellow-600 mt-2">
                        טוען...
                    </div>
                </div>
            </div>
        </div>

        <!-- Slogan -->
        <div class="text-center mt-8 pt-4 border-t-2 border-gray-200 text-gray-600 text-base font-bold">
            <p>תמיד טרי • תמיד מתוק</p>
        </div>
    </div>

    <!-- Baked Goods Price List Section -->
    <div class="section-container max-w-xl w-full">
        <!-- Logo Section -->
        <div class="text-center mb-2">
            <div class="text-red-600 text-4xl font-bold leading-none mb-0">M</div>
            <h1 class="text-2xl font-extrabold text-green-700 mb-0">MATOK</h1>
            <h2 class="text-lg font-semibold text-gray-700 mb-0">בגבעה</h2>
            <p class="text-gray-500 text-xs mt-0">מתוקים • מאפים • פינוקים</p>
        </div>

        <!-- Price List Section for Baked Goods -->
        <div class="flex-grow flex items-center justify-center text-center py-4">
            <div>
                <h3 class="text-4xl font-bold text-green-600 mb-6 pb-2 border-b-2 border-green-400 inline-block px-4">מאפים</h3>
                <p class="text-3xl font-semibold text-gray-700 mt-2">
                    (פרווה / חלבי)
                </p>
                <p class="text-5xl font-extrabold text-gray-800 mt-4">
                    49.90 ש"ח
                </p>
                <p class="text-3xl font-semibold text-gray-700 mt-2">
                    לקילוגרם
                </p>
            </div>
        </div>

        <!-- Slogan -->
        <div class="text-center mt-8 pt-4 border-t-2 border-gray-200 text-gray-600 text-base font-bold">
            <p>תמיד טרי • תמיד מתוק</p>
        </div>
    </div>

    <!-- Generic Price List Template - Small -->
    <div class="section-container max-w-xs w-full">
        <!-- Logo Section -->
        <div class="text-center mb-2">
            <div class="text-red-600 text-4xl font-bold leading-none mb-0">M</div>
            <h1 class="text-2xl font-extrabold text-green-700 mb-0">MATOK</h1>
            <h2 class="text-lg font-semibold text-gray-700 mb-0">בגבעה</h2>
            <p class="text-gray-500 text-xs mt-0">מתוקים • מאפים • פינוקים</p>
        </div>

        <!-- Generic Price List Section -->
        <div class="flex-grow flex items-center justify-center text-center py-4">
            <div>
                <h3 class="text-4xl font-bold text-green-600 inline-block px-4 mb-4">
                    <!-- Empty for manual input -->
                </h3>
                <p class="text-5xl font-extrabold text-gray-800 mt-4">
                    <!-- Empty for manual input -->
                </p>
                <p class="text-4xl font-bold text-gray-700 mt-4">
                    <!-- Empty for manual input -->
                </p>
                <!-- Green line moved here and made wider -->
                <div class="mt-6 pt-2 border-t-2 border-green-400 w-2/3 mx-auto"></div>
            </div>
        </div>

        <!-- Slogan -->
        <div class="text-center mt-8 pt-4 border-t-2 border-gray-200 text-gray-600 text-base font-bold">
            <p>תמיד טרי • תמיד מתוק</p>
        </div>
    </div>

    <!-- Generic Price List Template - Medium -->
    <div class="section-container max-w-sm w-full">
        <!-- Logo Section -->
        <div class="text-center mb-2">
            <div class="text-red-600 text-4xl font-bold leading-none mb-0">M</div>
            <h1 class="text-2xl font-extrabold text-green-700 mb-0">MATOK</h1>
            <h2 class="text-lg font-semibold text-gray-700 mb-0">בגבעה</h2>
            <p class="text-gray-500 text-xs mt-0">מתוקים • מאפים • פינוקים</p>
        </div>

        <!-- Generic Price List Section -->
        <div class="flex-grow flex items-center justify-center text-center py-4">
            <div>
                <h3 class="text-4xl font-bold text-green-600 inline-block px-4 mb-4">
                    <!-- Empty for manual input -->
                </h3>
                <p class="text-5xl font-extrabold text-gray-800 mt-4">
                    <!-- Empty for manual input -->
                </p>
                <p class="text-4xl font-bold text-gray-700 mt-4">
                    <!-- Empty for manual input -->
                </p>
                <!-- Green line moved here and made wider -->
                <div class="mt-6 pt-2 border-t-2 border-green-400 w-2/3 mx-auto"></div>
            </div>
        </div>

        <!-- Slogan -->
        <div class="text-center mt-8 pt-4 border-t-2 border-gray-200 text-gray-600 text-base font-bold">
            <p>תמיד טרי • תמיד מתוק</p>
        </div>
    </div>

    <!-- Generic Price List Template - Large -->
    <div class="section-container max-w-md w-full">
        <!-- Logo Section -->
        <div class="text-center mb-2">
            <div class="text-red-600 text-4xl font-bold leading-none mb-0">M</div>
            <h1 class="text-2xl font-extrabold text-green-700 mb-0">MATOK</h1>
            <h2 class="text-lg font-semibold text-gray-700 mb-0">בגבעה</h2>
            <p class="text-gray-500 text-xs mt-0">מתוקים • מאפים • פינוקים</p>
        </div>

        <!-- Generic Price List Section -->
        <div class="flex-grow flex items-center justify-center text-center py-4">
            <div>
                <h3 class="text-4xl font-bold text-green-600 inline-block px-4 mb-4">
                    <!-- Empty for manual input -->
                </h3>
                <p class="text-5xl font-extrabold text-gray-800 mt-4">
                    <!-- Empty for manual input -->
                </p>
                <p class="text-4xl font-bold text-gray-700 mt-4">
                    <!-- Empty for manual input -->
                </p>
                <!-- Green line moved here and made wider -->
                <div class="mt-6 pt-2 border-t-2 border-green-400 w-2/3 mx-auto"></div>
            </div>
        </div>

        <!-- Slogan -->
        <div class="text-center mt-8 pt-4 border-t-2 border-gray-200 text-gray-600 text-base font-bold">
            <p>תמיד טרי • תמיד מתוק</p>
        </div>
    </div>

    <!-- Generic Price List Template - Extra Large -->
    <div class="section-container max-w-lg w-full">
        <!-- Logo Section -->
        <div class="text-center mb-2">
            <div class="text-red-600 text-4xl font-bold leading-none mb-0">M</div>
            <h1 class="text-2xl font-extrabold text-green-700 mb-0">MATOK</h1>
            <h2 class="text-lg font-semibold text-gray-700 mb-0">בגבעה</h2>
            <p class="text-gray-500 text-xs mt-0">מתוקים • מאפים • פינוקים</p>
        </div>

        <!-- Generic Price List Section -->
        <div class="flex-grow flex items-center justify-center text-center py-4">
            <div>
                <h3 class="text-5xl font-bold text-green-600 inline-block px-4 mb-4">
                    <!-- Empty for manual input -->
                </h3>
                <p class="text-6xl font-extrabold text-gray-800 mt-4">
                    <!-- Empty for manual input -->
                </p>
                <p class="text-5xl font-bold text-gray-700 mt-4">
                    <!-- Empty for manual input -->
                </p>
                <!-- Green line moved here and made wider -->
                <div class="mt-6 pt-2 border-t-2 border-green-400 w-2/3 mx-auto"></div>
            </div>
        </div>

        <!-- Slogan -->
        <div class="text-center mt-8 pt-4 border-t-2 border-gray-200 text-gray-600 text-base font-bold">
            <p>תמיד טרי • תמיד מתוק</p>
        </div>
    </div>


    <!-- Nuts Price List Section (Two Columns) -->
    <div class="section-container max-w-4xl w-full">
        <!-- Logo Section -->
        <div class="text-center mb-2">
            <div class="text-red-600 text-4xl font-bold leading-none mb-0">M</div>
            <h1 class="text-2xl font-extrabold text-green-700 mb-0">MATOK</h1>
            <h2 class="text-lg font-semibold text-gray-700 mb-0">בגבעה</h2>
            <p class="text-gray-500 text-xs mt-0">מתוקים • מאפים • פינוקים</p>
        </div>

        <div class="mt-8">
            <h3 class="text-2xl font-bold text-center text-green-600 mb-6 pb-2 border-b-2 border-green-400">מחירון פיצוחים ופירות יבשים</h3>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-x-8 gap-y-2 text-lg">
                <!-- Column 1 -->
                <div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">שחורים</span>
                        <span class="font-bold text-green-700">4.50 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">אבטיח</span>
                        <span class="font-bold text-green-700">6.99 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">בוטן אמריקאי</span>
                        <span class="font-bold text-green-700">3.90 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">דלעת לבן</span>
                        <span class="font-bold text-green-700">6.20 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">צנובר</span>
                        <span class="font-bold text-green-700">19.90 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">חמוציות מסוכר</span>
                        <span class="font-bold text-green-700">4.40 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">ברזיל</span>
                        <span class="font-bold text-green-700">9.30 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">מקדמיה</span>
                        <span class="font-bold text-green-700">16.00 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">קשיו</span>
                        <span class="font-bold text-green-700">9.30 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">קבוקים</span>
                        <span class="font-bold text-green-700">4.50 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">פופקורן</span>
                        <span class="font-bold text-green-700">1.00 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">חמוציות</span>
                        <span class="font-bold text-green-700">5.50 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">שקד טבעי</span>
                        <span class="font-bold text-green-700">7.00 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">תמר</span>
                        <span class="font-bold text-green-700">8.00 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">שזיף / משמש</span>
                        <span class="font-bold text-green-700">7.70 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">פיסטוק</span>
                        <span class="font-bold text-green-700">9.30 ש"ח / 100 גרם</span>
                    </div>
                </div>
                <!-- Column 2 -->
                <div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">בוטנים</span>
                        <span class="font-bold text-green-700">5.49 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">פקאן סיני מתוק</span>
                        <span class="font-bold text-green-700">11.00 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">פקאן טבעי</span>
                        <span class="font-bold text-green-700">9.90 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">בונדוק לוז</span>
                        <span class="font-bold text-green-700">9.30 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">בננה צ'יפס</span>
                        <span class="font-bold text-green-700">6.50 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">שקד קליפה</span>
                        <span class="font-bold text-green-700">6.50 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">מעורב פינוקים כללי</span>
                        <span class="font-bold text-green-700">10.00 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">צימוק בהיר</span>
                        <span class="font-bold text-green-700">5.50 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">מנצ'ס</span>
                        <span class="font-bold text-green-700">6.49 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">שקדים</span>
                        <span class="font-bold text-green-700">9.30 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">פקאן קלוי</span>
                        <span class="font-bold text-green-700">10.50 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">קשיו טבעי</span>
                        <span class="font-bold text-green-700">8.00 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">אגוז מלך</span>
                        <span class="font-bold text-green-700">8.00 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">פקאן בחלבה</span>
                        <span class="font-bold text-green-700">11.00 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">בוטן מסוכר</span>
                        <span class="font-bold text-green-700">5.00 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">שקד מסוכר</span>
                        <span class="font-bold text-green-700">8.80 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">חומוס</span>
                        <span class="font-bold text-green-700">4.50 ש"ח / 100 גרם</span>
                    </div>
                    <div class="price-item">
                        <span class="font-medium text-gray-800">בוטן קליפה</span>
                        <span class="font-bold text-green-700">4.20 ש"ח / 100 גרם</span>
                    </div>
                </div>
            </div>
        </div>

        <!-- Slogan -->
        <div class="text-center mt-8 pt-4 border-t-2 border-gray-200 text-gray-600 text-base font-bold">
            <p>תמיד טרי • תמיד מתוק</p>
        </div>
    </div>

    <!-- Section for Individual Nut Price Tags -->
    <div class="nut-tags-container">
        <!-- Product 1 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">שחורים</span>
                <span class="price">4.50</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 2 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">אבטיח</span>
                <span class="price">6.99</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 3 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">בוטן אמריקאי</span>
                <span class="price">3.90</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 4 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">דלעת לבן</span>
                <span class="price">6.20</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 5 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">צנובר</span>
                <span class="price">19.90</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 6 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">חמוציות מסוכר</span>
                <span class="price">4.40</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 7 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">ברזיל</span>
                <span class="price">9.30</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 8 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">מקדמיה</span>
                <span class="price">16.00</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 9 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">קשיו</span>
                <span class="price">9.30</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 10 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">קבוקים</span>
                <span class="price">4.50</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 11 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">פופקורן</span>
                <span class="price">1.00</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 12 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">חמוציות</span>
                <span class="price">5.50</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 13 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">שקד טבעי</span>
                <span class="price">7.00</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 14 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">תמר</span>
                <span class="price">8.00</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 15 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">שזיף / משמש</span>
                <span class="price">7.70</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 16 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">פיסטוק</span>
                <span class="price">9.30</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 17 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">בוטנים</span>
                <span class="price">5.49</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 18 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">פקאן סיני מתוק</span>
                <span class="price">11.00</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 19 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">פקאן טבעי</span>
                <span class="price">9.90</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 20 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">בונדוק לוז</span>
                <span class="price">9.30</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 21 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">בננה צ'יפס</span>
                <span class="price">6.50</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 22 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">שקד קליפה</span>
                <span class="price">6.50</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 23 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">מעורב פינוקים כללי</span>
                <span class="price">10.00</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 24 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">צימוק בהיר</span>
                <span class="price">5.50</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 25 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">מנצ'ס</span>
                <span class="price">6.49</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 26 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">שקדים</span>
                <span class="price">9.30</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 27 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">פקאן קלוי</span>
                <span class="price">10.50</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 28 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">קשיו טבעי</span>
                <span class="price">8.00</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 29 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">אגוז מלך</span>
                <span class="price">8.00</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 30 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">פקאן בחלבה</span>
                <span class="price">11.00</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 31 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">בוטן מסוכר</span>
                <span class="price">5.00</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 32 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">שקד מסוכר</span>
                <span class="price">8.80</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 33 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">חומוס</span>
                <span class="price">4.50</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>

        <!-- Product 34 -->
        <div class="price-tag-square">
            <div class="logo-small">
                <div class="m-text">M</div>
                <div class="matok-text">MATOK</div>
                <div class="bagivah-text">בגבעה</div>
            </div>
            <div class="flex-grow flex flex-col justify-center items-center">
                <span class="product-name">בוטן קליפה</span>
                <span class="price">4.20</span>
                <span class="per-100g">ל-100 גרם</span>
            </div>
        </div>
    </div>

    <script>
        // No Gemini API integration for now, as the button was removed.
        // Script block is empty for future additions if needed.
    </script>
</body>
</html>

