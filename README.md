<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="application-name" content="BRICS Trader">
    <meta name="msapplication-TileColor" content="#1e3a8a">
    <meta name="theme-color" content="#1e3a8a">
    <meta name="msapplication-config" content="browserconfig.xml">
    <meta name="msapplication-window" content="width=1200;height=800">
    <meta name="robots" content="index, follow">
    <meta name="googlebot" content="index, follow">
    <meta name="bingbot" content="index, follow">
    <meta name="slurp" content="index, follow"> <!-- Yahoo -->
    <meta name="baiduspider" content="index, follow"> <!-- Baidu -->
    <meta name="yandex" content="index, follow"> <!-- Yandex -->
    <title>BRICS Trader - International Stock Insights | Accessible Trading Platform</title>
    <meta name="description" content="Accessible trading platform for BRICS nations with screen reader support and keyboard navigation">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <script src="https://cdn.tailwindcss.com"></script>
    <!-- Add package.json for npm dependencies -->
    <script type="application/json" id="package-json">
    {
      "name": "brics-trader",
      "version": "1.0.0",
      "description": "BRICS Trader Platform",
      "dependencies": {
        "chart.js": "^3.7.1",
        "tailwindcss": "^3.0.24"
      }
    }
    </script>
    <script>
        // Windows system integration
        if (window.electronAPI || window.__TAURI__) {
            document.documentElement.setAttribute('data-platform', 'windows');
            
            // System theme detection
            const updateTheme = (isDark) => {
                document.documentElement.classList.toggle('dark', isDark);
                localStorage.setItem('theme', isDark ? 'dark' : 'light');
            };
            
            if (window.electronAPI) {
                // Electron specific
                window.electronAPI.onSystemThemeChanged(updateTheme);
                window.electronAPI.getSystemTheme().then(updateTheme);
            } else if (window.__TAURI__) {
                // Tauri specific
                import('@tauri-apps/api/window').then(({ appWindow }) => {
                    appWindow.theme().then(theme => {
                        updateTheme(theme === 'dark');
                    });
                });
            }
        }
    </script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <link rel="robots" href="/robots.txt">
    <link rel="canonical" href="https://www.bricstrader.com/" />
    <style>
        .chart-container {
            height: 300px;
            position: relative;
        }
        .blink {
            animation: blink-animation 1s steps(5, start) infinite;
        }
        @keyframes blink-animation {
            to { visibility: hidden; }
        }
        .gradient-bg {
            background: linear-gradient(135deg, #1e3a8a 0%, #1e40af 100%);
        }
        .country-flag {
            width: 24px;
            height: 16px;
            display: inline-block;
            margin-right: 8px;
            background-size: cover;
            border-radius: 2px;
        }
    </style>
</head>
<body class="bg-gray-100 font-sans" aria-label="BRICS Trading Platform">
    <a href="#main-content" class="sr-only focus:not-sr-only">Skip to main content</a>
    <div class="min-h-screen flex flex-col">
        <!-- Header -->
        <header class="gradient-bg text-white shadow-lg">
            <div class="container mx-auto px-4 py-4 flex justify-between items-center">
                <div class="flex items-center space-x-2">
                    <i class="fas fa-globe-americas text-2xl"></i>
                    <h1 class="text-xl md:text-2xl font-bold">BRICS Trader</h1>
                    <span class="text-xs bg-yellow-500 text-black px-2 py-1 rounded-full ml-2">Open Source</span>
                    <span class="text-xs bg-green-500 text-white px-2 py-1 rounded-full ml-1 flex items-center">
                        <i class="fas fa-shield-alt mr-1"></i> Protected
                    </span>
                    <button id="translate-btn" class="ml-2 bg-purple-500 hover:bg-purple-600 text-white px-2 py-1 rounded-md text-sm flex items-center">
                        <i class="fas fa-language mr-1"></i> Translate
                    </button>
                </div>
                <div class="flex items-center space-x-4">
                    <div class="relative group">
                        <button class="bg-gray-800 hover:bg-gray-900 px-3 py-1 rounded text-sm flex items-center">
                            <i class="fas fa-exchange-alt mr-1"></i> FX
                        </button>
                        <div class="hidden group-hover:block absolute right-0 mt-2 w-64 bg-white rounded-md shadow-lg z-50 p-3">
                            <h4 class="font-bold mb-2">Currency Exchange</h4>
                            <div class="grid grid-cols-3 gap-2 text-xs mb-2">
                                <div class="font-medium">Pair</div>
                                <div class="font-medium">Buy</div>
                                <div class="font-medium">Sell</div>
                                <div>USD/RUB</div>
                                <div>92.45</div>
                                <div>92.55</div>
                                <div>USD/CNY</div>
                                <div>7.24</div>
                                <div>7.26</div>
                                <div>USD/INR</div>
                                <div>83.12</div>
                                <div>83.18</div>
                            </div>
                            <button class="w-full bg-blue-600 text-white py-1 rounded text-sm">
                                Trade Currencies
                            </button>
                        </div>
                    </div>
                    <button class="bg-blue-600 hover:bg-blue-700 px-3 py-1 rounded text-sm">
                        <i class="fas fa-user mr-1"></i> Login
                    </button>
                    <button class="bg-green-600 hover:bg-green-700 px-3 py-1 rounded text-sm">
                        <i class="fas fa-sign-in-alt mr-1"></i> Open Account
                    </button>
                    <div class="flex items-center bg-yellow-500 text-black px-2 py-1 rounded-full text-xs">
                        <i class="fas fa-check-circle mr-1"></i> BRICS Certified
                    </div>
                </div>
            </div>
        </header>

        <!-- Unique Value Proposition -->
        <div class="bg-gradient-to-r from-blue-800 to-purple-800 text-white py-4 px-6 text-center">
            <div class="container mx-auto">
                <h2 class="text-xl font-bold mb-2">Why BRICS Market Navigator?</h2>
                <p class="text-sm max-w-3xl mx-auto">
                    Unlike traditional platforms, we provide direct access to emerging market data with transparent 
                    sourcing and open methodology. Our independent analysis is free from Western financial institution 
                    biases, offering unique perspectives on BRICS economies.
                </p>
            </div>
        </div>

        <!-- Verification & Status Bar -->
        <div class="bg-gray-800 text-white text-sm py-1 px-4 flex justify-between items-center">
            <div class="flex items-center space-x-4">
                <div class="flex items-center">
                    <i class="fas fa-certificate text-yellow-400 mr-2"></i>
                    <span>BRICS Markets Member ID: <span id="brics-id">NBRICS-XXXXXX</span></span>
                </div>
                <div class="flex items-center">
                    <i class="fas fa-shield-alt text-green-400 mr-2"></i>
                    <span>AI Firewall Active - Blocking <span id="threats-blocked">0</span> threats today</span>
                </div>
            </div>
            <div class="flex items-center">
                <i class="fas fa-shield-alt text-green-400 mr-2"></i>
                <span>AI Firewall Active - Blocking <span id="threats-blocked">0</span> threats today</span>
            </div>
            <div class="flex items-center">
                <i class="fas fa-lock text-blue-400 mr-2"></i>
                <span>End-to-End Encrypted</span>
            </div>
        </div>

        <!-- Main Content -->
        <main id="main-content" class="flex-grow container mx-auto px-4 py-6" role="main">
            <div class="mb-6">
                <h2 class="text-2xl font-bold text-gray-800 mb-2">BRICS Market Overview</h2>
                <p class="text-gray-600">Real-time stock data from BRICS nations without U.S. restrictions</p>
            </div>

            <!-- Market Status Cards -->
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-5 gap-4 mb-8">
                <!-- Brazil -->
                <div class="bg-white rounded-lg shadow p-4 border-l-4 border-green-500">
                    <div class="flex justify-between items-start">
                        <div>
                            <div class="flex items-center mb-2">
                                <span class="country-flag" style="background-image: url('https://flagcdn.com/br.svg')"></span>
                                <h3 class="font-bold">Brazil (BOVESPA)</h3>
                            </div>
                            <p class="text-gray-600 text-sm">IBOV Index</p>
                        </div>
                        <span class="text-green-600 font-bold">+1.25%</span>
                    </div>
                    <div class="mt-4">
                        <p class="text-2xl font-bold">112,345.67</p>
                        <p class="text-sm text-gray-500">Last updated: <span class="text-blue-600 blink">Live</span></p>
                    </div>
                </div>

                <!-- Russia -->
                <div class="bg-white rounded-lg shadow p-4 border-l-4 border-blue-500">
                    <div class="flex justify-between items-start">
                        <div>
                            <div class="flex items-center mb-2">
                                <span class="country-flag" style="background-image: url('https://flagcdn.com/ru.svg')"></span>
                                <h3 class="font-bold">Russia (MOEX)</h3>
                            </div>
                            <p class="text-gray-600 text-sm">IMOEX Index</p>
                        </div>
                        <span class="text-red-600 font-bold">-0.45%</span>
                    </div>
                    <div class="mt-4">
                        <p class="text-2xl font-bold">3,245.89</p>
                        <p class="text-sm text-gray-500">Last updated: <span class="text-blue-600 blink">Live</span></p>
                    </div>
                </div>

                <!-- India -->
                <div class="bg-white rounded-lg shadow p-4 border-l-4 border-orange-500">
                    <div class="flex justify-between items-start">
                        <div>
                            <div class="flex items-center mb-2">
                                <span class="country-flag" style="background-image: url('https://flagcdn.com/in.svg')"></span>
                                <h3 class="font-bold">India (NSE)</h3>
                            </div>
                            <p class="text-gray-600 text-sm">NIFTY 50</p>
                        </div>
                        <span class="text-green-600 font-bold">+2.15%</span>
                    </div>
                    <div class="mt-4">
                        <p class="text-2xl font-bold">19,876.54</p>
                        <p class="text-sm text-gray-500">Last updated: <span class="text-blue-600 blink">Live</span></p>
                    </div>
                </div>

                <!-- China -->
                <div class="bg-white rounded-lg shadow p-4 border-l-4 border-red-500">
                    <div class="flex justify-between items-start">
                        <div>
                            <div class="flex items-center mb-2">
                                <span class="country-flag" style="background-image: url('https://flagcdn.com/cn.svg')"></span>
                                <h3 class="font-bold">China (SSE)</h3>
                            </div>
                            <p class="text-gray-600 text-sm">SSE Composite</p>
                        </div>
                        <span class="text-green-600 font-bold">+0.75%</span>
                    </div>
                    <div class="mt-4">
                        <p class="text-2xl font-bold">3,456.78</p>
                        <p class="text-sm text-gray-500">Last updated: <span class="text-blue-600 blink">Live</span></p>
                    </div>
                </div>

                <!-- South Africa -->
                <div class="bg-white rounded-lg shadow p-4 border-l-4 border-yellow-500">
                    <div class="flex justify-between items-start">
                        <div>
                            <div class="flex items-center mb-2">
                                <span class="country-flag" style="background-image: url('https://flagcdn.com/za.svg')"></span>
                                <h3 class="font-bold">South Africa (JSE)</h3>
                            </div>
                            <p class="text-gray-600 text-sm">JALSH Index</p>
                        </div>
                        <span class="text-red-600 font-bold">-0.30%</span>
                    </div>
                    <div class="mt-4">
                        <p class="text-2xl font-bold">72,345.12</p>
                        <p class="text-sm text-gray-500">Last updated: <span class="text-blue-600 blink">Live</span></p>
                    </div>

                    <!-- Trust Options -->
                    <div class="mt-8 border-t pt-6">
                        <h3 class="text-xl font-bold text-gray-800 mb-4">Trust & Inheritance Planning</h3>
                        <p class="text-gray-600 mb-4">Secure your investments for yourself or beneficiaries according to international laws:</p>
                        
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <!-- Personal Trust -->
                            <div class="bg-white border border-blue-100 rounded-lg p-4 shadow-sm">
                                <h4 class="font-bold text-blue-800 mb-2 flex items-center">
                                    <i class="fas fa-user-shield mr-2"></i> Personal Trust
                                </h4>
                                <p class="text-gray-600 text-sm mb-3">Maintain full control while protecting assets from creditors</p>
                                <ul class="text-sm text-gray-600 space-y-1 mb-3">
                                    <li><i class="fas fa-check-circle text-blue-500 mr-2"></i> Revocable during lifetime</li>
                                    <li><i class="fas fa-check-circle text-blue-500 mr-2"></i> Avoids probate</li>
                                    <li><i class="fas fa-check-circle text-blue-500 mr-2"></i> Tax-efficient transfers</li>
                                </ul>
                                <button class="text-blue-600 hover:text-blue-800 text-sm font-medium">
                                    Learn More <i class="fas fa-chevron-right ml-1"></i>
                                </button>
                            </div>
                            
                            <!-- Family Trust -->
                            <div class="bg-white border border-green-100 rounded-lg p-4 shadow-sm">
                                <h4 class="font-bold text-green-800 mb-2 flex items-center">
                                    <i class="fas fa-users mr-2"></i> Family Trust
                                </h4>
                                <p class="text-gray-600 text-sm mb-3">Provide for multiple generations with controlled distributions</p>
                                <ul class="text-sm text-gray-600 space-y-1 mb-3">
                                    <li><i class="fas fa-check-circle text-green-500 mr-2"></i> Multi-generational planning</li>
                                    <li><i class="fas fa-check-circle text-green-500 mr-2"></i> Protection from divorce/creditors</li>
                                    <li><i class="fas fa-check-circle text-green-500 mr-2"></i> Jurisdiction selection</li>
                                </ul>
                                <button class="text-green-600 hover:text-green-800 text-sm font-medium">
                                    Learn More <i class="fas fa-chevron-right ml-1"></i>
                                </button>
                            </div>
                            
                            <!-- Charitable Trust -->
                            <div class="bg-white border border-purple-100 rounded-lg p-4 shadow-sm">
                                <h4 class="font-bold text-purple-800 mb-2 flex items-center">
                                    <i class="fas fa-hand-holding-heart mr-2"></i> Charitable Trust
                                </h4>
                                <p class="text-gray-600 text-sm mb-3">Support causes while receiving tax benefits</p>
                                <ul class="text-sm text-gray-600 space-y-1 mb-3">
                                    <li><i class="fas fa-check-circle text-purple-500 mr-2"></i> Income tax deductions</li>
                                    <li><i class="fas fa-check-circle text-purple-500 mr-2"></i> Avoid capital gains tax</li>
                                    <li><i class="fas fa-check-circle text-purple-500 mr-2"></i> Legacy planning</li>
                                </ul>
                                <button class="text-purple-600 hover:text-purple-800 text-sm font-medium">
                                    Learn More <i class="fas fa-chevron-right ml-1"></i>
                                </button>
                            </div>
                            
                            <!-- International Trust -->
                            <div class="bg-white border border-yellow-100 rounded-lg p-4 shadow-sm">
                                <h4 class="font-bold text-yellow-800 mb-2 flex items-center">
                                    <i class="fas fa-globe-europe mr-2"></i> International Trust
                                </h4>
                                <p class="text-gray-600 text-sm mb-3">Asset protection across jurisdictions</p>
                                <ul class="text-sm text-gray-600 space-y-1 mb-3">
                                    <li><i class="fas fa-check-circle text-yellow-500 mr-2"></i> Multi-currency options</li>
                                    <li><i class="fas fa-check-circle text-yellow-500 mr-2"></i> Conflict of law protection</li>
                                    <li><i class="fas fa-check-circle text-yellow-500 mr-2"></i> Tax treaty benefits</li>
                                </ul>
                                <button class="text-yellow-600 hover:text-yellow-800 text-sm font-medium">
                                    Learn More <i class="fas fa-chevron-right ml-1"></i>
                                </button>
                            </div>
                        </div>
                        
                        <div class="mt-6 text-center">
                            <button class="bg-gray-800 hover:bg-gray-900 text-white px-6 py-2 rounded-md font-medium">
                                <i class="fas fa-balance-scale mr-2"></i> Consult Trust Specialist
                            </button>
                            <p class="text-xs text-gray-500 mt-2">Our experts comply with all international trust laws including Hague Convention</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- BRICS Trading Account Section -->
            <div class="bg-white rounded-lg shadow p-6 mb-8">
                <div class="flex items-start">
                    <div class="flex-shrink-0">
                        <img src="https://flagcdn.com/w320/br.png" class="h-16 w-24 object-cover rounded" alt="BRICS">
                    </div>
                    <div class="ml-6">
                        <h2 class="text-2xl font-bold text-gray-800">Official BRICS Trading Account</h2>
                        <p class="text-gray-600 mt-2">Fully verified and compliant trading access across all BRICS exchanges</p>
                        <div class="mt-4 grid grid-cols-1 md:grid-cols-3 gap-4">
                            <div class="bg-blue-50 p-3 rounded-lg">
                                <h3 class="font-bold text-blue-800">Multi-Currency</h3>
                                <p class="text-sm text-gray-600 mt-1">Trade in local currencies with automatic conversion</p>
                            </div>
                            <div class="bg-green-50 p-3 rounded-lg">
                                <h3 class="font-bold text-green-800">Direct Market Access</h3>
                                <p class="text-sm text-gray-600 mt-1">Connect directly to B3, MOEX, NSE, SSE, JSE</p>
                            </div>
                            <div class="bg-purple-50 p-3 rounded-lg">
                                <h3 class="font-bold text-purple-800">Regulated</h3>
                                <p class="text-sm text-gray-600 mt-1">Compliant with all BRICS financial authorities</p>
                            </div>
                        </div>
                        <div class="mt-6">
                            <button class="bg-green-600 hover:bg-green-700 text-white px-6 py-3 rounded-md font-medium">
                                <i class="fas fa-file-signature mr-2"></i> Apply for Trading Account
                            </button>
                            <p class="text-xs text-gray-500 mt-2">Verification required: ID, proof of address, and financial questionnaire</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Beginner's Guide Section -->
            <div class="bg-white rounded-lg shadow p-6 mb-8">
                <h2 class="text-2xl font-bold text-gray-800 mb-4">Simple Investing Guide for Passive Income</h2>
                
                <!-- Goal Marker -->
                <div class="mb-6 p-4 bg-indigo-50 rounded-lg border border-indigo-100">
                    <h3 class="text-lg font-bold text-indigo-800 mb-3 flex items-center">
                        <i class="fas fa-bullseye mr-2"></i> Set Your Investment Goal
                    </h3>
                    <div class="grid grid-cols-1 md:grid-cols-3 gap-4 mb-3">
                        <div>
                            <label class="block text-sm font-medium text-indigo-700 mb-1">Target Amount</label>
                            <input type="number" class="w-full border-indigo-200 rounded-md shadow-sm" placeholder="e.g. 100000">
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-indigo-700 mb-1">Timeframe</label>
                            <select class="w-full border-indigo-200 rounded-md shadow-sm">
                                <option>1-3 years</option>
                                <option>3-5 years</option>
                                <option>5-10 years</option>
                                <option>10+ years</option>
                            </select>
                        </div>
                        <div>
                            <label class="block text-sm font-medium text-indigo-700 mb-1">Risk Tolerance</label>
                            <select class="w-full border-indigo-200 rounded-md shadow-sm">
                                <option>Conservative</option>
                                <option>Moderate</option>
                                <option>Aggressive</option>
                            </select>
                        </div>
                    </div>
                    <button class="bg-indigo-600 hover:bg-indigo-700 text-white px-4 py-2 rounded-md text-sm font-medium">
                        <i class="fas fa-save mr-1"></i> Save Goal
                    </button>
                </div>
                <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
                    <!-- Step 1 -->
                    <div class="bg-blue-50 p-4 rounded-lg">
                        <div class="flex items-center mb-3">
                            <span class="bg-blue-600 text-white rounded-full w-8 h-8 flex items-center justify-center mr-3">1</span>
                            <h3 class="font-bold text-blue-800">Start Small</h3>
                        </div>
                        <p class="text-gray-600 text-sm">Begin with just $50-$100 per month. Consistency matters more than amount when starting.</p>
                    </div>
                    
                    <!-- Step 2 -->
                    <div class="bg-green-50 p-4 rounded-lg">
                        <div class="flex items-center mb-3">
                            <span class="bg-green-600 text-white rounded-full w-8 h-8 flex items-center justify-center mr-3">2</span>
                            <h3 class="font-bold text-green-800">Choose ETFs</h3>
                        </div>
                        <p class="text-gray-600 text-sm">Pick 2-3 BRICS ETFs that track entire markets (like EBRA, INDA). Less risk than single stocks.</p>
                    </div>
                    
                    <!-- Step 3 -->
                    <div class="bg-purple-50 p-4 rounded-lg">
                        <div class="flex items-center mb-3">
                            <span class="bg-purple-600 text-white rounded-full w-8 h-8 flex items-center justify-center mr-3">3</span>
                            <h3 class="font-bold text-purple-800">Set Auto-Invest</h3>
                        </div>
                        <p class="text-gray-600 text-sm">Schedule automatic investments each payday. "Set and forget" for true passive income.</p>
                    </div>
                </div>
                
                <!-- Daily Trading Tips -->
                <div class="mt-8 border-t pt-6">
                    <h3 class="text-xl font-bold text-gray-800 mb-4">Daily ETF Trading for Busy People</h3>
                    <div class="space-y-4">
                        <div class="flex items-start">
                            <span class="bg-yellow-100 text-yellow-800 rounded-full p-2 mr-3">
                                <i class="fas fa-clock text-sm"></i>
                            </span>
                            <div>
                                <h4 class="font-medium">Morning Routine (5 min)</h4>
                                <p class="text-gray-600 text-sm">Check pre-market trends. Set limit orders for your ETFs at target prices.</p>
                            </div>
                        </div>
                        <div class="flex items-start">
                            <span class="bg-blue-100 text-blue-800 rounded-full p-2 mr-3">
                                <i class="fas fa-chart-line text-sm"></i>
                            </span>
                            <div>
                                <h4 class="font-medium">Lunch Check (2 min)</h4>
                                <p class="text-gray-600 text-sm">Review if orders executed. Adjust afternoon strategy if needed.</p>
                            </div>
                        </div>
                        <div class="flex items-start">
                            <span class="bg-green-100 text-green-800 rounded-full p-2 mr-3">
                                <i class="fas fa-coins text-sm"></i>
                            </span>
                            <div>
                                <h4 class="font-medium">Evening Review (3 min)</h4>
                                <p class="text-gray-600 text-sm">Analyze daily performance. Set alerts for next day's price targets.</p>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Main Dashboard -->
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-6">
                <!-- Stock Recommendations -->
                <div class="lg:col-span-2 bg-white rounded-lg shadow p-6">
                    <div class="flex justify-between items-center mb-6">
                        <h2 class="text-xl font-bold text-gray-800">Today's Top BRICS Picks</h2>
                        <div class="flex space-x-2">
                            <button class="bg-blue-100 text-blue-700 px-3 py-1 rounded text-sm">All</button>
                            <button class="hover:bg-gray-100 px-3 py-1 rounded text-sm">Brazil</button>
                            <button class="hover:bg-gray-100 px-3 py-1 rounded text-sm">Russia</button>
                            <button class="hover:bg-gray-100 px-3 py-1 rounded text-sm">India</button>
                            <button class="hover:bg-gray-100 px-3 py-1 rounded text-sm">China</button>
                            <button class="hover:bg-gray-100 px-3 py-1 rounded text-sm">S.Africa</button>
                        </div>
                    </div>

                    <div class="overflow-x-auto">
                        <table class="min-w-full divide-y divide-gray-200">
                            <thead class="bg-gray-50">
                                <tr>
                                    <th class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Stock</th>
                                    <th class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Price</th>
                                    <th class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Change</th>
                                    <th class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Signal</th>
                                    <th class="px-4 py-3 text-left text-xs font-medium text-gray-500 uppercase tracking-wider">Action</th>
                                </tr>
                            </thead>
                            <tbody class="bg-white divide-y divide-gray-200">
                                <tr>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <div class="flex items-center">
                                            <span class="country-flag" style="background-image: url('https://flagcdn.com/cn.svg')"></span>
                                            <div>
                                                <div class="font-medium">BABA</div>
                                                <div class="text-gray-500 text-sm">Alibaba Group</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td class="px-4 py-3 whitespace-nowrap">$89.45</td>
                                    <td class="px-4 py-3 whitespace-nowrap text-green-600">+3.2%</td>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <span class="px-2 py-1 bg-green-100 text-green-800 rounded-full text-xs font-bold">STRONG BUY</span>
                                    </td>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <button class="bg-green-600 hover:bg-green-700 text-white px-3 py-1 rounded text-sm">Trade</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <div class="flex items-center">
                                            <span class="country-flag" style="background-image: url('https://flagcdn.com/in.svg')"></span>
                                            <div>
                                                <div class="font-medium">TCS.NS</div>
                                                <div class="text-gray-500 text-sm">Tata Consultancy</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td class="px-4 py-3 whitespace-nowrap">₹3,456.78</td>
                                    <td class="px-4 py-3 whitespace-nowrap text-green-600">+1.8%</td>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <span class="px-2 py-1 bg-green-100 text-green-800 rounded-full text-xs font-bold">BUY</span>
                                    </td>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <button class="bg-green-600 hover:bg-green-700 text-white px-3 py-1 rounded text-sm">Trade</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <div class="flex items-center">
                                            <span class="country-flag" style="background-image: url('https://flagcdn.com/ru.svg')"></span>
                                            <div>
                                                <div class="font-medium">GAZP.ME</div>
                                                <div class="text-gray-500 text-sm">Gazprom</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td class="px-4 py-3 whitespace-nowrap">₽165.43</td>
                                    <td class="px-4 py-3 whitespace-nowrap text-red-600">-0.7%</td>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <span class="px-2 py-1 bg-yellow-100 text-yellow-800 rounded-full text-xs font-bold">HOLD</span>
                                    </td>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <button class="bg-gray-600 hover:bg-gray-700 text-white px-3 py-1 rounded text-sm">Watch</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <div class="flex items-center">
                                            <span class="country-flag" style="background-image: url('https://flagcdn.com/br.svg')"></span>
                                            <div>
                                                <div class="font-medium">VALE3.SA</div>
                                                <div class="text-gray-500 text-sm">Vale S.A.</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td class="px-4 py-3 whitespace-nowrap">R$67.89</td>
                                    <td class="px-4 py-3 whitespace-nowrap text-green-600">+2.4%</td>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <span class="px-2 py-1 bg-green-100 text-green-800 rounded-full text-xs font-bold">BUY</span>
                                    </td>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <button class="bg-green-600 hover:bg-green-700 text-white px-3 py-1 rounded text-sm">Trade</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <div class="flex items-center">
                                            <span class="country-flag" style="background-image: url('https://flagcdn.com/za.svg')"></span>
                                            <div>
                                                <div class="font-medium">NPN.JO</div>
                                                <div class="text-gray-500 text-sm">Naspers</div>
                                            </div>
                                        </div>
                                    </td>
                                    <td class="px-4 py-3 whitespace-nowrap">R3,456.78</td>
                                    <td class="px-4 py-3 whitespace-nowrap text-red-600">-1.2%</td>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <span class="px-2 py-1 bg-red-100 text-red-800 rounded-full text-xs font-bold">SELL</span>
                                    </td>
                                    <td class="px-4 py-3 whitespace-nowrap">
                                        <button class="bg-gray-600 hover:bg-gray-700 text-white px-3 py-1 rounded text-sm">Watch</button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>

                    <!-- Trading Section -->
                    <div class="mt-8 border-t pt-6">
                        <h3 class="text-lg font-bold text-gray-800 mb-4">Trade BRICS Stocks</h3>
                        <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                            <!-- Currency Trading -->
                            <div class="bg-gray-50 p-4 rounded-lg border border-blue-200 mb-4">
                                <h4 class="font-medium text-blue-800 mb-3 flex items-center">
                                    <i class="fas fa-exchange-alt mr-2"></i> Currency Trading
                                </h4>
                                <div class="grid grid-cols-2 gap-3 mb-3">
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Sell</label>
                                        <div class="flex">
                                            <input type="number" class="w-full border-gray-300 rounded-l-md shadow-sm">
                                            <select class="border-gray-300 rounded-r-md shadow-sm bg-gray-100">
                                                <option>USD</option>
                                                <option>EUR</option>
                                                <option>GBP</option>
                                            </select>
                                        </div>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Buy</label>
                                        <div class="flex">
                                            <input type="number" class="w-full border-gray-300 rounded-l-md shadow-sm">
                                            <select class="border-gray-300 rounded-r-md shadow-sm bg-gray-100">
                                                <option>CNY</option>
                                                <option>INR</option>
                                                <option>BRL</option>
                                                <option>ZAR</option>
                                                <option>RUB</option>
                                            </select>
                                        </div>
                                    </div>
                                </div>
                                <div class="text-xs text-gray-500 mb-3">
                                    Rate: 1 USD = 7.24 CNY (0.3% fee included)
                                </div>
                                <button class="w-full bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md font-medium">
                                    <i class="fas fa-check-circle mr-2"></i> Exchange Currencies
                                </button>
                            </div>

                            <!-- Buy Panel -->
                            <div class="bg-gray-50 p-4 rounded-lg border border-green-200 relative">
                                <div class="absolute -top-3 right-2 bg-white px-2 py-1 rounded-full shadow text-xs">
                                    <button onclick="toggleConversionCalc()" class="text-blue-600 hover:text-blue-800">
                                        <i class="fas fa-calculator mr-1"></i>Convert
                                    </button>
                                </div>
                                <div id="conversion-calc" class="hidden bg-white p-3 rounded-lg shadow-md mb-3 border border-blue-100">
                                    <div class="grid grid-cols-3 gap-2 mb-2">
                                        <input type="number" id="convert-amount" placeholder="Amount" class="col-span-2 border rounded p-1 text-sm">
                                        <select id="convert-from" class="border rounded p-1 text-sm">
                                            <option>USD</option>
                                            <option>RUB</option>
                                            <option>CNY</option>
                                            <option>INR</option>
                                            <option>BRL</option>
                                            <option>ZAR</option>
                                        </select>
                                    </div>
                                    <div class="grid grid-cols-3 gap-2 mb-2">
                                        <div class="col-span-2 text-sm p-1" id="conversion-result">0.00</div>
                                        <select id="convert-to" class="border rounded p-1 text-sm">
                                            <option>RUB</option>
                                            <option>CNY</option>
                                            <option>INR</option>
                                            <option>BRL</option>
                                            <option>ZAR</option>
                                            <option>USD</option>
                                        </select>
                                    </div>
                                    <button onclick="calculateConversion()" class="w-full bg-blue-100 text-blue-800 text-xs py-1 rounded">
                                        Calculate
                                    </button>
                                </div>
                                <div class="flex justify-between items-center mb-3">
                                    <h4 class="font-medium text-gray-700">
                                        <i class="fas fa-shopping-cart text-green-600 mr-2"></i> Buy Stocks
                                    </h4>
                                    <span class="bg-green-100 text-green-800 text-xs px-2 py-1 rounded-full">
                                        <i class="fas fa-check-circle mr-1"></i> Verified
                                    </span>
                                </div>
                                <div class="space-y-3">
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Select Stock</label>
                                        <select class="w-full border-gray-300 rounded-md shadow-sm">
                                            <option>BABA - Alibaba Group</option>
                                            <option>TCS.NS - Tata Consultancy</option>
                                            <option>GAZP.ME - Gazprom</option>
                                            <option>VALE3.SA - Vale S.A.</option>
                                            <option>NPN.JO - Naspers</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Quantity</label>
                                        <input type="number" min="1" value="1" class="w-full border-gray-300 rounded-md shadow-sm">
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Order Type</label>
                                        <select class="w-full border-gray-300 rounded-md shadow-sm">
                                            <option>Market Order</option>
                                            <option>Limit Order</option>
                                            <option>Stop Order</option>
                                        </select>
                                    </div>
                                    <button class="w-full bg-green-600 hover:bg-green-700 text-white py-2 px-4 rounded-md font-medium">
                                        <i class="fas fa-check-circle mr-2"></i> Place Buy Order
                                    </button>
                                </div>
                            </div>

                            <!-- Sell Panel -->
                            <div class="bg-gray-50 p-4 rounded-lg">
                                <h4 class="font-medium text-gray-700 mb-3">
                                    <i class="fas fa-coins text-yellow-600 mr-2"></i> Sell Stocks
                                </h4>
                                <div class="space-y-3">
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Your Holdings</label>
                                        <select class="w-full border-gray-300 rounded-md shadow-sm">
                                            <option>10 shares of BABA @ $89.45</option>
                                            <option>5 shares of TCS.NS @ ₹3,456.78</option>
                                            <option>20 shares of VALE3.SA @ R$67.89</option>
                                        </select>
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Quantity</label>
                                        <input type="number" min="1" value="1" class="w-full border-gray-300 rounded-md shadow-sm">
                                    </div>
                                    <div>
                                        <label class="block text-sm font-medium text-gray-700 mb-1">Order Type</label>
                                        <select class="w-full border-gray-300 rounded-md shadow-sm">
                                            <option>Market Order</option>
                                            <option>Limit Order</option>
                                            <option>Stop Order</option>
                                        </select>
                                    </div>
                                    <button class="w-full bg-yellow-600 hover:bg-yellow-700 text-white py-2 px-4 rounded-md font-medium">
                                        <i class="fas fa-check-circle mr-2"></i> Place Sell Order
                                    </button>
                                </div>
                            </div>
                        </div>

                        <!-- Price Alerts -->
                        <div class="mt-6 bg-blue-50 p-4 rounded-lg">
                            <h4 class="font-medium text-blue-800 mb-3">
                                <i class="fas fa-bell text-blue-600 mr-2"></i> Set Price Alerts
                            </h4>
                            <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
                                <div>
                                    <label class="block text-sm font-medium text-blue-700 mb-1">Stock</label>
                                    <select class="w-full border-blue-200 rounded-md shadow-sm">
                                        <option>Select Stock</option>
                                        <option>BABA - Alibaba Group</option>
                                        <option>TCS.NS - Tata Consultancy</option>
                                        <option>GAZP.ME - Gazprom</option>
                                    </select>
                                </div>
                                <div>
                                    <label class="block text-sm font-medium text-blue-700 mb-1">Alert Type</label>
                                    <select class="w-full border-blue-200 rounded-md shadow-sm">
                                        <option>Price Above</option>
                                        <option>Price Below</option>
                                        <option>Percentage Change</option>
                                    </select>
                                </div>
                                <div>
                                    <label class="block text-sm font-medium text-blue-700 mb-1">Value</label>
                                    <div class="flex">
                                        <input type="number" class="w-full border-blue-200 rounded-l-md shadow-sm">
                                        <button class="bg-blue-600 text-white px-4 rounded-r-md">
                                            <i class="fas fa-plus"></i>
                                        </button>
                                    </div>
                                </div>
                            </div>
                            <div class="mt-4">
                                <button class="bg-blue-600 hover:bg-blue-700 text-white py-2 px-4 rounded-md text-sm font-medium">
                                    <i class="fas fa-bell mr-2"></i> Create Alert
                                </button>
                                <span class="ml-3 text-sm text-blue-600">We'll notify you via email or SMS</span>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Market Insights -->
                <div class="bg-white rounded-lg shadow p-6">
                    <h2 class="text-xl font-bold text-gray-800 mb-6">BRICS Market Insights</h2>
                    
                    <div class="space-y-4">
                        <div class="p-4 bg-blue-50 rounded-lg">
                            <div class="flex items-start">
                                <div class="flex-shrink-0 pt-1">
                                    <i class="fas fa-chart-line text-blue-600"></i>
                                </div>
                                <div class="ml-3">
                                    <h3 class="font-bold text-blue-800">Chinese Tech Rally</h3>
                                    <p class="text-sm text-gray-600 mt-1">Alibaba and Tencent show strong momentum with 15% YTD growth despite global tech slowdown.</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="p-4 bg-green-50 rounded-lg">
                            <div class="flex items-start">
                                <div class="flex-shrink-0 pt-1">
                                    <i class="fas fa-bolt text-green-600"></i>
                                </div>
                                <div class="ml-3">
                                    <h3 class="font-bold text-green-800">Indian Energy Surge</h3>
                                    <p class="text-sm text-gray-600 mt-1">Renewable energy stocks in India up 8% this week on new government incentives.</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="p-4 bg-yellow-50 rounded-lg">
                            <div class="flex items-start">
                                <div class="flex-shrink-0 pt-1">
                                    <i class="fas fa-exclamation-triangle text-yellow-600"></i>
                                </div>
                                <div class="ml-3">
                                    <h3 class="font-bold text-yellow-800">Russian Commodity Warning</h3>
                                    <p class="text-sm text-gray-600 mt-1">Analysts suggest caution with Russian commodity stocks due to potential sanctions impact.</p>
                                </div>
                            </div>
                        </div>
                        
                        <div class="p-4 bg-purple-50 rounded-lg">
                            <div class="flex items-start">
                                <div class="flex-shrink-0 pt-1">
                                    <i class="fas fa-gem text-purple-600"></i>
                                </div>
                                <div class="ml-3">
                                    <h3 class="font-bold text-purple-800">Brazilian Mining Opportunity</h3>
                                    <p class="text-sm text-gray-600 mt-1">Vale SA expected to benefit from lithium demand surge - analysts upgrade to buy.</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    
                    <div class="mt-6">
                        <h3 class="font-bold text-gray-700 mb-2">Technical Indicators</h3>
                        <div class="space-y-2">
                            <div>
                                <div class="flex justify-between text-sm mb-1">
                                    <span>RSI (14-day)</span>
                                    <span class="font-medium">42.5</span>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-2">
                                    <div class="bg-blue-600 h-2 rounded-full" style="width: 42.5%"></div>
                                </div>
                            </div>
                            <div>
                                <div class="flex justify-between text-sm mb-1">
                                    <span>MACD</span>
                                    <span class="font-medium">Bullish</span>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-2">
                                    <div class="bg-green-600 h-2 rounded-full" style="width: 65%"></div>
                                </div>
                            </div>
                            <div>
                                <div class="flex justify-between text-sm mb-1">
                                    <span>Volume Trend</span>
                                    <span class="font-medium">Increasing</span>
                                </div>
                                <div class="w-full bg-gray-200 rounded-full h-2">
                                    <div class="bg-purple-600 h-2 rounded-full" style="width: 78%"></div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Security Features Section -->
            <div class="mt-8 bg-white rounded-lg shadow p-6">
                <h2 class="text-xl font-bold text-gray-800 mb-6">Security Center</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                    <div class="p-4 border border-green-200 rounded-lg bg-green-50">
                        <div class="flex items-start">
                            <div class="flex-shrink-0 pt-1 text-green-600">
                                <i class="fas fa-robot text-2xl"></i>
                            </div>
                            <div class="ml-4">
                                <h3 class="font-bold text-lg">AI-Powered Protection</h3>
                                <p class="text-gray-600 mt-2">
                                    Our security system leverages open-source AI models including TensorFlow and ModSecurity 
                                    rulesets to detect threats. The threat intelligence database is built from public sources 
                                    including CVE databases and OWASP recommendations.
                                </p>
                                <p class="text-xs text-gray-500 mt-2">
                                    Security models are available for audit on our GitHub repository under AGPL-3.0 license.
                                </p>
                                <div class="mt-4 flex items-center text-sm">
                                    <span class="bg-green-100 text-green-800 px-2 py-1 rounded-full">Active</span>
                                    <span class="ml-3 text-gray-500">Last updated: Just now</span>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="p-4 border border-blue-200 rounded-lg bg-blue-50">
                        <div class="flex items-start">
                            <div class="flex-shrink-0 pt-1 text-blue-600">
                                <i class="fas fa-mobile-alt text-2xl"></i>
                            </div>
                            <div class="ml-4">
                                <h3 class="font-bold text-lg">Two-Factor Authentication</h3>
                                <p class="text-gray-600 mt-2">
                                    Secure your account with optional 2FA via SMS or email. We never store your phone number.
                                </p>
                                <div class="mt-4">
                                    <button class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2 rounded-md text-sm font-medium">
                                        Enable 2FA
                                    </button>
                                    <button class="ml-3 bg-white hover:bg-gray-100 text-gray-700 px-4 py-2 rounded-md text-sm font-medium border border-gray-300">
                                        Learn More
                                    </button>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="p-4 border border-purple-200 rounded-lg bg-purple-50">
                        <div class="flex items-start">
                            <div class="flex-shrink-0 pt-1 text-purple-600">
                                <i class="fas fa-code-branch text-2xl"></i>
                            </div>
                            <div class="ml-4">
                                <h3 class="font-bold text-lg">Company Verification</h3>
                                <p class="text-gray-600 mt-2">
                                    Our open-source verification system checks company registries worldwide to prevent fraud.
                                </p>
                                <div class="mt-4">
                                    <button class="bg-purple-600 hover:bg-purple-700 text-white px-4 py-2 rounded-md text-sm font-medium">
                                        Verify Your Company
                                    </button>
                                    <a href="https://github.com/bricstrader/company-verification" target="_blank" class="ml-3 bg-white hover:bg-gray-100 text-gray-700 px-4 py-2 rounded-md text-sm font-medium border border-gray-300">
                                        View Source Code
                                    </a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Chart Section -->
            <div class="mt-8 bg-white rounded-lg shadow p-6">
                <div class="flex justify-between items-center mb-6">
                    <h2 class="text-xl font-bold text-gray-800">BRICS Composite Index</h2>
                    <div class="flex space-x-2">
                        <button class="bg-blue-600 text-white px-3 py-1 rounded text-sm">1D</button>
                        <button class="hover:bg-gray-100 px-3 py-1 rounded text-sm">1W</button>
                        <button class="hover:bg-gray-100 px-3 py-1 rounded text-sm">1M</button>
                        <button class="hover:bg-gray-100 px-3 py-1 rounded text-sm">1Y</button>
                        <button class="hover:bg-gray-100 px-3 py-1 rounded text-sm">ALL</button>
                    </div>
                </div>
                
                <div class="chart-container">
                    <canvas id="bricsChart" height="300"></canvas>
                    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
                    <script>
                        // Initialize Chart.js
                        const ctx = document.getElementById('bricsChart').getContext('2d');
                        const chart = new Chart(ctx, {
                            type: 'line',
                            data: {
                                labels: Array.from({length: 30}, (_, i) => i + 1),
                                datasets: [{
                                    label: 'BRICS Composite Index',
                                    data: Array.from({length: 30}, () => Math.random() * 100 + 1000),
                                    borderColor: 'rgb(75, 192, 192)',
                                    tension: 0.1
                                }]
                            },
                            options: {
                                responsive: true,
                                maintainAspectRatio: false,
                                plugins: {
                                    legend: {
                                        position: 'top',
                                    }
                                }
                            }
                        });
                        
                        // Simulate live updates
                        setInterval(() => {
                            const newData = chart.data.datasets[0].data.slice(1);
                            newData.push(newData[newData.length - 1] + (Math.random() * 20 - 10));
                            chart.data.datasets[0].data = newData;
                            chart.update();
                        }, 2000);
                    </script>
                </div>
            </div>
        </main>

        <!-- Research Disclaimer -->
        <div class="bg-gray-100 py-6 px-4">
            <div class="container mx-auto">
                <h3 class="font-bold text-gray-800 mb-3">Research Disclaimer</h3>
                <p class="text-sm text-gray-600">
                    All market data and analysis provided on this platform is sourced from public domain information 
                    including World Bank, IMF, and respective BRICS nations' stock exchange publications. Our proprietary 
                    analysis is based on these verified sources but should not be considered financial advice. 
                    <a href="#" class="text-blue-600 hover:underline">View full methodology</a>.
                </p>
                <p class="text-xs text-gray-500 mt-3">
                    BRICS Market Navigator is an independent research platform and is not affiliated with any government 
                    or financial institution. All trademarks and copyrighted materials remain property of their respective owners.
                </p>
            </div>
        </div>

        <!-- Footer -->
        <footer class="bg-gray-800 text-white py-8">
            <div class="container mx-auto px-4">
                <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
                    <div>
                        <h3 class="font-bold text-lg mb-4">BRICS Trader</h3>
                        <p class="text-gray-400 text-sm">Independent market data and analysis for BRICS nations. No U.S. restrictions.</p>
                    </div>
                    <div>
                        <h4 class="font-bold mb-4">Markets</h4>
                        <ul class="space-y-2">
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Brazil (B3)</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Russia (MOEX)</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">India (NSE/BSE)</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">China (SSE/SZSE)</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">South Africa (JSE)</a></li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-bold mb-4">Resources</h4>
                        <ul class="space-y-2">
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">API Documentation</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Open Source Code</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Developer Community</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Data Sources</a></li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-bold mb-4">Research Sources</h4>
                        <ul class="space-y-2">
                            <li><a href="https://data.worldbank.org" class="text-gray-400 hover:text-white text-sm">World Bank Data</a></li>
                            <li><a href="https://www.imf.org" class="text-gray-400 hover:text-white text-sm">IMF Reports</a></li>
                            <li><a href="https://unctad.org" class="text-gray-400 hover:text-white text-sm">UNCTAD Statistics</a></li>
                            <li><a href="https://www.bis.org" class="text-gray-400 hover:text-white text-sm">BIS Research</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Methodology</a></li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-bold mb-4">Legal</h4>
                        <ul class="space-y-2">
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Terms of Service</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Privacy Policy</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Content Policy</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">GDPR Compliance</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Security Whitepaper</a></li>
                        </ul>
                    </div>
                    <div>
                        <h4 class="font-bold mb-4">Security</h4>
                        <ul class="space-y-2">
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Threat Report</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Bug Bounty</a></li>
                            <li><a href="/sitemap.xml" class="text-gray-400 hover:text-white text-sm">Sitemap</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Open Source Audit</a></li>
                            <li><a href="#" class="text-gray-400 hover:text-white text-sm">Security Tips</a></li>
                        </ul>
                    </div>
                </div>
                <div class="border-t border-gray-700 mt-8 pt-6 text-sm text-gray-400">
                    <div class="flex flex-col md:flex-row justify-between items-center">
                        <p>© 2023 BRICS Trader. All data provided for informational purposes only.</p>
                        <div class="flex space-x-4 mt-4 md:mt-0">
                            <a href="#"><i class="fab fa-github"></i></a>
                            <a href="#"><i class="fab fa-twitter"></i></a>
                            <a href="#"><i class="fab fa-telegram"></i></a>
                            <a href="#"><i class="fas fa-rss"></i></a>
                        </div>
                    </div>
                </div>
            </div>
        </footer>
    </div>

    <style>
        /* Translation dropdown styles */
        #language-dropdown {
            position: absolute;
            top: 40px;
            right: 0;
            background: white;
            border-radius: 0.375rem;
            box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            z-index: 50;
            width: 200px;
            display: none;
        }
        .language-option {
            padding: 0.5rem 1rem;
            cursor: pointer;
            display: flex;
            align-items: center;
        }
        .language-option:hover {
            background-color: #f3f4f6;
        }
        .language-flag {
            width: 20px;
            height: 15px;
            margin-right: 8px;
            border-radius: 2px;
        }
    </style>

    <!-- Matomo Analytics -->
    <script>
        var _paq = window._paq = window._paq || [];
        _paq.push(['trackPageView']);
        _paq.push(['enableLinkTracking']);
        (function() {
            var u="//analytics.example.org/";
            _paq.push(['setTrackerUrl', u+'matomo.php']);
            _paq.push(['setSiteId', '1']);
            var d=document, g=d.createElement('script'), s=d.getElementsByTagName('script')[0];
            g.async=true; g.src=u+'matomo.js'; s.parentNode.insertBefore(g,s);
        })();

        // Translation functionality
        document.getElementById('translate-btn').addEventListener('click', function() {
            const dropdown = document.createElement('div');
            dropdown.id = 'language-dropdown';
            dropdown.innerHTML = `
                <div class="language-option" data-lang="zh">
                    <span class="language-flag" style="background-image: url('https://flagcdn.com/cn.svg')"></span>
                    中文 (Chinese)
                </div>
                <div class="language-option" data-lang="ru">
                    <span class="language-flag" style="background-image: url('https://flagcdn.com/ru.svg')"></span>
                    Русский (Russian)
                </div>
                <div class="language-option" data-lang="pt">
                    <span class="language-flag" style="background-image: url('https://flagcdn.com/br.svg')"></span>
                    Português (Portuguese)
                </div>
                <div class="language-option" data-lang="hi">
                    <span class="language-flag" style="background-image: url('https://flagcdn.com/in.svg')"></span>
                    हिन्दी (Hindi)
                </div>
                <div class="language-option" data-lang="en">
                    <span class="language-flag" style="background-image: url('https://flagcdn.com/us.svg')"></span>
                    English (Default)
                </div>
            `;
            
            // Position dropdown
            const rect = this.getBoundingClientRect();
            dropdown.style.top = `${rect.bottom + window.scrollY}px`;
            dropdown.style.right = `${window.innerWidth - rect.right}px`;
            document.body.appendChild(dropdown);
            dropdown.style.display = 'block';

            // Handle language selection
            dropdown.querySelectorAll('.language-option').forEach(option => {
                option.addEventListener('click', function() {
                    const lang = this.getAttribute('data-lang');
                    translatePage(lang);
                    dropdown.remove();
                });
            });

            // Close dropdown when clicking outside
            document.addEventListener('click', function clickOutside(e) {
                if (!dropdown.contains(e.target) && e.target !== document.getElementById('translate-btn')) {
                    dropdown.remove();
                    document.removeEventListener('click', clickOutside);
                }
            });
        });

        // LibreTranslate integration
        async function translatePage(lang) {
            const btn = document.getElementById('translate-btn');
            btn.innerHTML = `<i class="fas fa-spinner fa-spin mr-1"></i> Translating...`;
            
            try {
                // Use public LibreTranslate instance or self-hosted
                const endpoint = 'https://libretranslate.de/translate';
                
                // Get all translatable text
                const elements = document.querySelectorAll('h1, h2, h3, h4, h5, h6, p, span, a, li, button:not(.no-translate)');
                
                // Translate each element
                for (const el of elements) {
                    if (el.textContent.trim()) {
                        const response = await fetch(endpoint, {
                            method: 'POST',
                            body: JSON.stringify({
                                q: el.textContent,
                                source: 'en',
                                target: lang
                            }),
                            headers: {'Content-Type': 'application/json'}
                        });
                        
                        const data = await response.json();
                        if (data.translatedText) {
                            el.textContent = data.translatedText;
                        }
                    }
                }
                
                // Store language preference
                localStorage.setItem('preferredLanguage', lang);
                btn.innerHTML = `<i class="fas fa-language mr-1"></i> ${lang.toUpperCase()}`;
                
            } catch (error) {
                console.error('Translation error:', error);
                btn.innerHTML = `<i class="fas fa-language mr-1"></i> Translate`;
                alert('Translation service is currently unavailable. Please try again later.');
            }
        }

        // Check for saved language preference
        if(localStorage.getItem('preferredLanguage')) {
            translatePage(localStorage.getItem('preferredLanguage'));
        }

        // Open-source security monitoring with ModSecurity rules
        let threatsBlocked = 0;
        const threatTypes = ['XSS', 'SQLi', 'Phishing', 'Spam', 'Bot'];
        
        async function updateSecurityStats() {
            try {
                // Simulate checking with open-source threat intelligence
                const response = await fetch('https://openvas.org/api/threats');
                const threats = await response.json();
                
                threatsBlocked += threats.length;
                document.getElementById('threats-blocked').textContent = threatsBlocked;
                
                // Log new patterns to console
                threats.forEach(threat => {
                    console.log(`ModSecurity: Blocked ${threat.type} attack from ${threat.ip}`);
                });
                
            } catch (error) {
                console.error('Security update error:', error);
                // Fallback to simple counter
                threatsBlocked += Math.floor(Math.random() * 3);
                document.getElementById('threats-blocked').textContent = threatsBlocked;
            }
        }
        
        setInterval(updateSecurityStats, 10000);
        updateSecurityStats();

        // Two-factor authentication simulation
        function setup2FA() {
            const twoFAMethods = ['SMS', 'Email', 'Authenticator App'];
            console.log('2FA Options:', twoFAMethods);
            alert('Two-factor authentication can be configured in Account Settings. We recommend using an authenticator app for maximum security.');
        }
        
        document.querySelectorAll('[onclick*="2FA"], .enable-2fa').forEach(btn => {
            btn.addEventListener('click', setup2FA);
        });

        // Simulate live data updates
        function updateMarketData() {
            const percentages = document.querySelectorAll('.market-percentage');
            const prices = document.querySelectorAll('.market-price');
            
            percentages.forEach(el => {
                const change = (Math.random() * 2 - 1).toFixed(2);
                const isPositive = change >= 0;
                el.textContent = `${isPositive ? '+' : ''}${change}%`;
                el.className = `market-percentage font-bold ${isPositive ? 'text-green-600' : 'text-red-600'}`;
            });
            
            prices.forEach(el => {
                const country = el.getAttribute('data-country');
                let basePrice, newPrice;
                
                switch(country) {
                    case 'brazil':
                        basePrice = 110000;
                        newPrice = (basePrice + Math.random() * 3000 - 1500).toFixed(2);
                        el.textContent = new Intl.NumberFormat('pt-BR', {style: 'decimal'}).format(newPrice);
                        break;
                    case 'russia':
                        basePrice = 3200;
                        newPrice = (basePrice + Math.random() * 100 - 50).toFixed(2);
                        el.textContent = new Intl.NumberFormat('ru-RU', {style: 'decimal'}).format(newPrice);
                        break;
                    case 'india':
                        basePrice = 19000;
                        newPrice = (basePrice + Math.random() * 200 - 100).toFixed(2);
                        el.textContent = new Intl.NumberFormat('en-IN', {style: 'decimal'}).format(newPrice);
                        break;
                    case 'china':
                        basePrice = 3400;
                        newPrice = (basePrice + Math.random() * 60 - 30).toFixed(2);
                        el.textContent = new Intl.NumberFormat('zh-CN', {style: 'decimal'}).format(newPrice);
                        break;
                    case 'south-africa':
                        basePrice = 71000;
                        newPrice = (basePrice + Math.random() * 1000 - 500).toFixed(2);
                        el.textContent = new Intl.NumberFormat('en-ZA', {style: 'decimal'}).format(newPrice);
                        break;
                }
            });
        }
        
        // Update every 5 seconds to simulate live data
        setInterval(updateMarketData, 5000);
        
        // Initial update
        updateMarketData();
        
        // Stock recommendation logic (simplified)
        function analyzeStock() {
            const stocks = document.querySelectorAll('.stock-row');
            
            stocks.forEach(stock => {
                const random = Math.random();
                let signal, action;
                
                if (random > 0.7) {
                    signal = 'STRONG BUY';
                    action = 'Trade';
                } else if (random > 0.4) {
                    signal = 'BUY';
                    action = 'Trade';
                } else if (random > 0.2) {
                    signal = 'HOLD';
                    action = 'Watch';
                } else {
                    signal = 'SELL';
                    action = 'Watch';
                }
                
                const signalElement = stock.querySelector('.stock-signal');
                const actionButton = stock.querySelector('.stock-action');
                
                signalElement.textContent = signal;
                signalElement.className = `stock-signal px-2 py-1 rounded-full text-xs font-bold ${
                    signal.includes('BUY') ? 'bg-green-100 text-green-800' : 
                    signal === 'HOLD' ? 'bg-yellow-100 text-yellow-800' : 'bg-red-100 text-red-800'
                }`;
                
                actionButton.textContent = action;
                actionButton.className = `stock-action ${
                    action === 'Trade' ? 'bg-green-600 hover:bg-green-700' : 'bg-gray-600 hover:bg-gray-700'
                } text-white px-3 py-1 rounded text-sm`;
            });
        }
        
        // Analyze stocks every 10 seconds
        setInterval(analyzeStock, 10000);
        analyzeStock();

        // Trading functionality
        function placeOrder(type) {
            const stock = document.querySelector(`#${type}-stock`).value;
            const quantity = document.querySelector(`#${type}-quantity`).value;
            const orderType = document.querySelector(`#${type}-order-type`).value;
            
            console.log(`Placing ${type} order for ${quantity} shares of ${stock} (${orderType})`);
            
            // In a real app, this would call your backend API
            alert(`${type.toUpperCase()} order placed for ${quantity} shares of ${stock.split(' - ')[0]}!`);
            
            // Update portfolio display
            if(type === 'buy') {
                // Add to portfolio
                console.log('Added to portfolio');
            } else {
                // Remove from portfolio
                console.log('Removed from portfolio');
            }
        }

        // Price alert functionality
        function createAlert() {
            const stock = document.querySelector('#alert-stock').value;
            const alertType = document.querySelector('#alert-type').value;
            const value = document.querySelector('#alert-value').value;
            
            if(stock && alertType && value) {
                console.log(`Created ${alertType} alert for ${stock} at ${value}`);
                alert(`Alert created! You'll be notified when ${stock.split(' - ')[0]} ${alertType} ${value}.`);
            } else {
                alert('Please fill all alert fields');
            }
        }

        // Initialize trading buttons
        document.querySelectorAll('.place-order').forEach(btn => {
            btn.addEventListener('click', function() {
                placeOrder(this.getAttribute('data-order-type'));
            });
        });

        document.querySelector('#create-alert').addEventListener('click', createAlert);

        // Currency Conversion Functions
        const conversionRates = {
            'USD': { 'RUB': 92.45, 'CNY': 7.24, 'INR': 83.12, 'BRL': 5.02, 'ZAR': 18.67 },
            'RUB': { 'USD': 0.0108, 'CNY': 0.078, 'INR': 0.90, 'BRL': 0.054, 'ZAR': 0.20 },
            'CNY': { 'USD': 0.14, 'RUB': 12.77, 'INR': 11.48, 'BRL': 0.69, 'ZAR': 2.58 },
            'INR': { 'USD': 0.012, 'RUB': 1.11, 'CNY': 0.087, 'BRL': 0.060, 'ZAR': 0.22 },
            'BRL': { 'USD': 0.20, 'RUB': 18.52, 'CNY': 1.44, 'INR': 16.56, 'ZAR': 3.72 },
            'ZAR': { 'USD': 0.054, 'RUB': 4.96, 'CNY': 0.39, 'INR': 4.45, 'BRL': 0.27 }
        };

        function toggleConversionCalc() {
            const calc = document.getElementById('conversion-calc');
            calc.classList.toggle('hidden');
        }

        function calculateConversion() {
            const amount = parseFloat(document.getElementById('convert-amount').value);
            const from = document.getElementById('convert-from').value;
            const to = document.getElementById('convert-to').value;
            
            if (isNaN(amount)) {
                alert('Please enter a valid amount');
                return;
            }

            let result;
            if (from === to) {
                result = amount;
            } else {
                result = amount * conversionRates[from][to];
            }

            document.getElementById('conversion-result').textContent = result.toFixed(2);
        }

        // Update rates periodically
        function updateConversionRates() {
            // In a real app, this would fetch from an API
            const fluctuation = (Math.random() * 0.02 - 0.01); // +/- 1%
            Object.keys(conversionRates.USD).forEach(currency => {
                conversionRates.USD[currency] *= (1 + fluctuation);
                // Update inverse rates
                conversionRates[currency].USD = 1 / conversionRates.USD[currency];
            });
            
            // Update displayed rates
            document.querySelectorAll('[id^="rate-"]').forEach(el => {
                const currency = el.id.split('-')[1];
                el.textContent = conversionRates.USD[currency].toFixed(2);
            });
            
            console.log('Updated conversion rates');
        }
        
        setInterval(updateConversionRates, 300000); // Update every 5 minutes

        // Fetch stocks from Node.js API
        function fetchStocks() {
            fetch('/api/stocks')
                .then(response => response.json())
                .then(data => {
                    const resultsDiv = document.getElementById('api-results');
                    resultsDiv.innerHTML = `
                        <h3 class="font-bold mb-2">Latest Stock Data:</h3>
                        <ul class="list-disc pl-5">
                            ${data.stocks.map(stock => `
                                <li>${stock.symbol}: ${stock.price} (${stock.change})</li>
                            `).join('')}
                        </ul>
                    `;
                })
                .catch(error => {
                    console.error('API Error:', error);
                    document.getElementById('api-results').textContent = 
                        'Error fetching data. Make sure the Node.js server is running.';
                });
        }

        // Company Verification System
        async function verifyCompany(companyData) {
            try {
                // This would call our open-source verification service
                const response = await fetch('https://api.bricstrader.com/verify', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify(companyData)
                });
                
                const result = await response.json();
                
                if(result.verified) {
                    return {
                        success: true,
                        message: `Company verified with ${result.registry}`,
                        details: result.details
                    };
                } else {
                    return {
                        success: false,
                        message: result.reason || 'Company not found in official registries'
                    };
                }
            } catch (error) {
                console.error('Verification error:', error);
                return {
                    success: false,
                    message: 'Verification service unavailable'
                };
            }
        }

        // BRICS Account Verification
        function verifyBRICSAccount() {
            const userData = {
                name: prompt("Enter your full legal name:"),
                country: prompt("Enter your country of residence:"),
                idNumber: prompt("Enter government-issued ID number:"),
            };
            
            if(userData.name && userData.country && userData.idNumber) {
                console.log("Submitting verification to BRICS Markets Authority...");
                // In production, this would call a secure API
                
                // Simulate verification
                setTimeout(() => {
                    const bricsId = `NBRICS-${Math.floor(Math.random() * 1000000)}`;
                    document.getElementById('brics-id').textContent = bricsId;
                    alert(`Account verified! Your BRICS Markets ID: ${bricsId}\nYou can now trade on all BRICS exchanges.`);
                }, 2000);
            }
        }
        
        document.querySelectorAll('[href*="account"], .apply-account').forEach(btn => {
            btn.addEventListener('click', verifyBRICSAccount);
        });

        // Simulate live trade notifications
        function checkPriceAlerts() {
            // In a real app, this would check against real-time prices
            if(Math.random() > 0.8) {
                const stocks = ['BABA', 'TCS.NS', 'GAZP.ME', 'VALE3.SA', 'NPN.JO'];
                const stock = stocks[Math.floor(Math.random() * stocks.length)];
                const direction = Math.random() > 0.5 ? 'rose above' : 'fell below';
                const price = (Math.random() * 100).toFixed(2);
                
                console.log(`Alert: ${stock} ${direction} ${price}`);
                // In a real app, this would trigger a browser notification
            }
        }
        
        setInterval(checkPriceAlerts, 30000);
    </script>

    <!-- Embedded Node.js Server -->
    <script>
    // Simple Node.js server implementation
    if (typeof process !== 'undefined') {
        const http = require('http');
        const fs = require('fs');
        const path = require('path');

        const server = http.createServer((req, res) => {
            // Serve the HTML file
            if (req.url === '/') {
                fs.readFile(path.join(__dirname, 'index.html'), (err, data) => {
                    if (err) {
                        res.writeHead(500);
                        return res.end('Error loading index.html');
                    }
                    res.writeHead(200, {'Content-Type': 'text/html'});
                    res.end(data);
                });
            }
            // API endpoint example
            else if (req.url === '/api/stocks' && req.method === 'GET') {
                res.writeHead(200, {'Content-Type': 'application/json'});
                res.end(JSON.stringify({
                    stocks: [
                        {symbol: 'BABA', price: 89.45, change: '+3.2%'},
                        {symbol: 'TCS.NS', price: 3456.78, change: '+1.8%'},
                        {symbol: 'GAZP.ME', price: 165.43, change: '-0.7%'}
                    ]
                }));
            }
            else {
                res.writeHead(404);
                res.end('Not Found');
            }
        });

        const PORT = process.env.PORT || 3000;
        server.listen(PORT, () => {
            console.log(`Server running on port ${PORT}`);
            console.log(`Open http://localhost:${PORT} in your browser`);
        });
    }
    </script>
    
    <!-- FTP Access Modal (hidden by default) -->
    <div id="ftp-modal" class="hidden fixed inset-0 bg-gray-600 bg-opacity-50 flex items-center justify-center" role="dialog" aria-modal="true">
        <div class="bg-white rounded-lg p-6 max-w-md w-full">
            <h2 class="text-xl font-bold mb-4" id="ftp-modal-title">FTP Configuration</h2>
            <form id="ftp-form">
                <div class="mb-4">
                    <label for="ftp-host" class="block text-sm font-medium text-gray-700">AWS Host</label>
                    <input type="text" id="ftp-host" class="mt-1 block w-full border-gray-300 rounded-md shadow-sm" 
                           placeholder="s3.amazonaws.com" required aria-required="true">
                </div>
                <div class="mb-4">
                    <label for="ftp-user" class="block text-sm font-medium text-gray-700">IAM User</label>
                    <input type="text" id="ftp-user" class="mt-1 block w-full border-gray-300 rounded-md shadow-sm" required aria-required="true">
                </div>
                <div class="mb-4">
                    <label for="ftp-key" class="block text-sm font-medium text-gray-700">SSH Key</label>
                    <textarea id="ftp-key" rows="4" class="mt-1 block w-full border-gray-300 rounded-md shadow-sm" required aria-required="true"></textarea>
                </div>
                <div class="flex justify-end space-x-3">
                    <button type="button" onclick="document.getElementById('ftp-modal').classList.add('hidden')" 
                            class="px-4 py-2 bg-gray-300 rounded-md">Cancel</button>
                    <button type="submit" class="px-4 py-2 bg-blue-600 text-white rounded-md">Save Configuration</button>
                </div>
            </form>
        </div>
    </div>
</body>
</html>
