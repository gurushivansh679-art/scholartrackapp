<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>ScholarTrack - Coaching Management System</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet">
    <style>
        .active-tab {
            background-color: #3b82f6 !important;
            color: white !important;
        }
    </style>
</head>
<body class="bg-slate-50 font-sans text-slate-800 antialiased min-h-screen flex flex-col md:flex-row">

    <!-- Sidebar Navigation -->
    <aside class="w-full md:w-64 bg-slate-900 text-slate-300 flex-shrink-0 flex flex-col justify-between min-h-screen">
        <div>
            <!-- Logo / Header -->
            <div class="p-5 border-b border-slate-800 flex items-center space-x-3">
                <div class="bg-blue-600 text-white p-2.5 rounded-xl shadow-lg">
                    <i class="fa-solid fa-graduation-cap text-xl"></i>
                </div>
                <div>
                    <h1 class="font-bold text-lg text-white tracking-wide">ScholarTrack</h1>
                    <p class="text-xs text-slate-400">Coaching Center Portal</p>
                </div>
            </div>

            <!-- Navigation Links -->
            <nav class="p-4 space-y-1">
                <button onclick="switchTab('dashboard')" id="nav-dashboard" class="nav-btn active-tab w-full flex items-center space-x-3 px-4 py-3 rounded-lg text-sm font-medium transition hover:bg-slate-800 text-slate-300">
                    <i class="fa-solid fa-chart-pie w-5"></i>
                    <span>Dashboard</span>
                </button>
                <button onclick="switchTab('students')" id="nav-students" class="nav-btn w-full flex items-center space-x-3 px-4 py-3 rounded-lg text-sm font-medium transition hover:bg-slate-800 text-slate-300">
                    <i class="fa-solid fa-users w-5"></i>
                    <span>Students</span>
                </button>
                <button onclick="switchTab('attendance')" id="nav-attendance" class="nav-btn w-full flex items-center space-x-3 px-4 py-3 rounded-lg text-sm font-medium transition hover:bg-slate-800 text-slate-300">
                    <i class="fa-solid fa-calendar-check w-5"></i>
                    <span>Attendance</span>
                </button>
                <button onclick="switchTab('tests')" id="nav-tests" class="nav-btn w-full flex items-center space-x-3 px-4 py-3 rounded-lg text-sm font-medium transition hover:bg-slate-800 text-slate-300">
                    <i class="fa-solid fa-file-pen w-5"></i>
                    <span>Tests</span>
                </button>
                <button onclick="switchTab('scores')" id="nav-scores" class="nav-btn w-full flex items-center space-x-3 px-4 py-3 rounded-lg text-sm font-medium transition hover:bg-slate-800 text-slate-300">
                    <i class="fa-solid fa-trophy w-5"></i>
                    <span>Test Scores & Analysis</span>
                </button>
            </nav>
        </div>

        <!-- Footer Info -->
        <div class="p-4 border-t border-slate-800 text-xs text-slate-500 text-center">
            ScholarTrack System v2.0
        </div>
    </aside>

    <!-- Main Content Area -->
    <main class="flex-1 p-6 lg:p-8 overflow-y-auto">

        <!-- DASHBOARD TAB -->
        <section id="tab-dashboard" class="tab-content space-y-6">
            <div>
                <h2 class="text-2xl font-bold text-slate-900">Dashboard</h2>
                <p class="text-sm text-slate-500">Class-level performance overview at a glance</p>
            </div>

            <!-- Metric Cards -->
            <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-5">
                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200 flex items-center justify-between">
                    <div>
                        <p class="text-xs font-semibold uppercase text-slate-400">Total Students</p>
                        <h3 id="dash-total-students" class="text-2xl font-bold text-slate-800 mt-1">0</h3>
                    </div>
                    <div class="bg-blue-50 text-blue-600 p-3.5 rounded-xl">
                        <i class="fa-solid fa-users text-xl"></i>
                    </div>
                </div>

                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200 flex items-center justify-between">
                    <div>
                        <p class="text-xs font-semibold uppercase text-slate-400">Active Classes</p>
                        <h3 id="dash-total-classes" class="text-2xl font-bold text-slate-800 mt-1">4</h3>
                    </div>
                    <div class="bg-emerald-50 text-emerald-600 p-3.5 rounded-xl">
                        <i class="fa-solid fa-chalkboard text-xl"></i>
                    </div>
                </div>

                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200 flex items-center justify-between">
                    <div>
                        <p class="text-xs font-semibold uppercase text-slate-400">Tests Scheduled</p>
                        <h3 id="dash-total-tests" class="text-2xl font-bold text-slate-800 mt-1">0</h3>
                    </div>
                    <div class="bg-purple-50 text-purple-600 p-3.5 rounded-xl">
                        <i class="fa-solid fa-book-open text-xl"></i>
                    </div>
                </div>

                <div class="bg-white p-5 rounded-2xl shadow-sm border border-slate-200 flex items-center justify-between">
                    <div>
                        <p class="text-xs font-semibold uppercase text-slate-400">Avg Attendance</p>
                        <h3 id="dash-avg-attendance" class="text-2xl font-bold text-slate-800 mt-1">0%</h3>
                    </div>
                    <div class="bg-amber-50 text-amber-600 p-3.5 rounded-xl">
                        <i class="fa-solid fa-chart-line text-xl"></i>
                    </div>
                </div>
            </div>

            <!-- Recent Summary / Quick Actions -->
            <div class="grid grid-cols-1 lg:grid-cols-2 gap-6">
                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                    <h3 class="font-bold text-slate-800 mb-4 flex items-center space-x-2">
                        <i class="fa-solid fa-rocket text-blue-600"></i>
                        <span>Quick Actions</span>
                    </h3>
                    <div class="grid grid-cols-2 gap-3">
                        <button onclick="switchTab('students')" class="p-4 bg-slate-50 hover:bg-blue-50 border border-slate-200 rounded-xl text-left transition group">
                            <i class="fa-solid fa-user-plus text-blue-600 mb-2 text-lg"></i>
                            <p class="font-semibold text-slate-700 text-sm group-hover:text-blue-600">Add Student</p>
                            <p class="text-xs text-slate-400">Register new batch entry</p>
                        </button>
                        <button onclick="switchTab('attendance')" class="p-4 bg-slate-50 hover:bg-emerald-50 border border-slate-200 rounded-xl text-left transition group">
                            <i class="fa-solid fa-clipboard-user text-emerald-600 mb-2 text-lg"></i>
                            <p class="font-semibold text-slate-700 text-sm group-hover:text-emerald-600">Mark Attendance</p>
                            <p class="text-xs text-slate-400">Daily attendance log</p>
                        </button>
                        <button onclick="switchTab('tests')" class="p-4 bg-slate-50 hover:bg-purple-50 border border-slate-200 rounded-xl text-left transition group">
                            <i class="fa-solid fa-calendar-plus text-purple-600 mb-2 text-lg"></i>
                            <p class="font-semibold text-slate-700 text-sm group-hover:text-purple-600">Schedule Test</p>
                            <p class="text-xs text-slate-400">Create new assessment</p>
                        </button>
                        <button onclick="switchTab('scores')" class="p-4 bg-slate-50 hover:bg-amber-50 border border-slate-200 rounded-xl text-left transition group">
                            <i class="fa-solid fa-pen-to-square text-amber-600 mb-2 text-lg"></i>
                            <p class="font-semibold text-slate-700 text-sm group-hover:text-amber-600">Enter Scores</p>
                            <p class="text-xs text-slate-400">Record marks & grades</p>
                        </button>
                    </div>
                </div>

                <div class="bg-white p-6 rounded-2xl shadow-sm border border-slate-200">
                    <h3 class="font-bold text-slate-800 mb-4 flex items-center space-x-2">
                        <i class="fa-solid fa-clock-rotate-left text-blue-600"></i>
                        <span>Recent Students Overview</span>
                    </h3>
                    <div id="dash-recent-list" class="space-y-3">
                        <p class="text-slate-400 text-sm text-center py-8">No students added yet. Start by adding students!</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- STUDENTS TAB -->
        <section id="tab-students" class="tab-content hidden space-y-6">
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4">
                <div>
                    <h2 class="text-2xl font-bold text-slate-900">Students</h2>
                    <p class="text-sm text-slate-500">Manage enrolled students across classes</p>
                </div>
                <button onclick="toggleModal('student-modal')" class="bg-blue-600 hover:bg-blue-700 text-white px-4 py-2.5 rounded-xl font-medium text-sm flex items-center space-x-2 shadow-sm transition">
                    <i class="fa-solid fa-plus"></i>
                    <span>Add New Student</span>
                </button>
            </div>

            <!-- Search & Filter Bar -->
            <div class="bg-white p-4 rounded-2xl shadow-sm border border-slate-200 flex flex-col sm:flex-row gap-3">
                <div class="relative flex-1">
                    <i class="fa-solid fa-magnifying-glass absolute left-3.5 top-3 text-slate-400 text-sm"></i>
                    <input type="text" id="student-search" oninput="renderStudents()" placeholder="Search by name, roll number..." class="w-full pl-10 pr-4 py-2 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-blue-500">
                </div>
                <select id="student-filter-class" onchange="renderStudents()" class="px-4 py-2 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-blue-500">
                    <option value="">All Classes</option>
                    <option value="Class 9">Class 9</option>
                    <option value="Class 10">Class 10</option>
                    <option value="Class 11">Class 11</option>
                    <option value="Class 12">Class 12</option>
                </select>
            </div>

            <!-- Student Table -->
            <div class="bg-white rounded-2xl shadow-sm border border-slate-200 overflow-hidden">
                <div class="overflow-x-auto">
                    <table class="w-full text-left border-collapse">
                        <thead>
                            <tr class="bg-slate-50 border-b border-slate-200 text-slate-500 text-xs font-semibold uppercase tracking-wider">
                                <th class="p-4">Roll No</th>
                                <th class="p-4">Student Name</th>
                                <th class="p-4">Class</th>
                                <th class="p-4">Phone Number</th>
                                <th class="p-4 text-right">Actions</th>
                            </tr>
                        </thead>
                        <tbody id="student-table-body" class="divide-y divide-slate-100 text-sm">
                            <!-- Injected by JS -->
                        </tbody>
                    </table>
                </div>
            </div>
        </section>

        <!-- ATTENDANCE TAB -->
        <section id="tab-attendance" class="tab-content hidden space-y-6">
            <div>
                <h2 class="text-2xl font-bold text-slate-900">Attendance</h2>
                <p class="text-sm text-slate-500">Mark daily attendance for each class</p>
            </div>

            <!-- Attendance Control Bar -->
            <div class="bg-white p-4 rounded-2xl shadow-sm border border-slate-200 grid grid-cols-1 md:grid-cols-3 gap-4 items-center">
                <div>
                    <label class="block text-xs font-semibold text-slate-500 mb-1">Select Date</label>
                    <input type="date" id="att-date" onchange="renderAttendance()" class="w-full px-3 py-2 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-blue-500">
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-500 mb-1">Select Class</label>
                    <select id="att-class" onchange="renderAttendance()" class="w-full px-3 py-2 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-blue-500">
                        <option value="Class 9">Class 9</option>
                        <option value="Class 10">Class 10</option>
                        <option value="Class 11" selected>Class 11</option>
                        <option value="Class 12">Class 12</option>
                    </select>
                </div>
                <div class="flex items-end space-x-2 pt-1 md:pt-0">
                    <button onclick="markAllAttendance('Present')" class="flex-1 bg-emerald-50 hover:bg-emerald-100 text-emerald-700 border border-emerald-200 py-2 rounded-xl font-medium text-xs transition">
                        Mark All Present
                    </button>
                    <button onclick="saveAttendance()" class="flex-1 bg-blue-600 hover:bg-blue-700 text-white py-2 rounded-xl font-medium text-xs shadow-sm transition">
                        Save Attendance
                    </button>
                </div>
            </div>

            <!-- Attendance List -->
            <div class="bg-white rounded-2xl shadow-sm border border-slate-200 p-6">
                <div id="attendance-list" class="space-y-3">
                    <!-- Injected by JS -->
                </div>
            </div>
        </section>

        <!-- TESTS TAB -->
        <section id="tab-tests" class="tab-content hidden space-y-6">
            <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-4">
                <div>
                    <h2 class="text-2xl font-bold text-slate-900">Tests Management</h2>
                    <p class="text-sm text-slate-500">Schedule and manage test assessments</p>
                </div>
                <button onclick="toggleModal('test-modal')" class="bg-purple-600 hover:bg-purple-700 text-white px-4 py-2.5 rounded-xl font-medium text-sm flex items-center space-x-2 shadow-sm transition">
                    <i class="fa-solid fa-plus"></i>
                    <span>Schedule New Test</span>
                </button>
            </div>

            <!-- Tests Grid -->
            <div id="tests-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">
                <!-- Injected by JS -->
            </div>
        </section>

        <!-- TEST SCORES TAB -->
        <section id="tab-scores" class="tab-content hidden space-y-6">
            <div>
                <h2 class="text-2xl font-bold text-slate-900">Test Scores & Performance</h2>
                <p class="text-sm text-slate-500">Enter scores, view performance analysis, and identify weak areas</p>
            </div>

            <!-- Select Test Bar -->
            <div class="bg-white p-4 rounded-2xl shadow-sm border border-slate-200 flex flex-col sm:flex-row items-center gap-4">
                <label class="font-semibold text-sm text-slate-700 whitespace-nowrap">Select Test:</label>
                <select id="score-test-select" onchange="renderScoresTable()" class="w-full sm:w-auto flex-1 px-4 py-2 bg-slate-50 border border-slate-200 rounded-xl text-sm focus:outline-none focus:ring-2 focus:ring-blue-500">
                    <option value="">-- Choose a test --</option>
                </select>
                <button onclick="saveScores()" class="w-full sm:w-auto bg-emerald-600 hover:bg-emerald-700 text-white px-5 py-2 rounded-xl text-sm font-medium shadow-sm transition">
                    Save Scores
                </button>
            </div>

            <!-- Scores Entry Table -->
            <div class="bg-white rounded-2xl shadow-sm border border-slate-200 overflow-hidden">
                <div id="scores-table-container" class="p-6 text-center text-slate-400">
                    <i class="fa-solid fa-clipboard-list text-3xl mb-2 text-slate-300"></i>
                    <p>Select a test from the dropdown above to enter scores or view performance.</p>
                </div>
            </div>
        </section>

    </main>

    <!-- MODAL: ADD STUDENT -->
    <div id="student-modal" class="fixed inset-0 bg-slate-900/50 backdrop-blur-sm hidden flex items-center justify-center p-4 z-50">
        <div class="bg-white rounded-2xl shadow-xl max-w-md w-full p-6 space-y-4">
            <div class="flex items-center justify-between border-b pb-3">
                <h3 class="font-bold text-lg text-slate-800">Add New Student</h3>
                <button onclick="toggleModal('student-modal')" class="text-slate-400 hover:text-slate-600"><i class="fa-solid fa-xmark text-lg"></i></button>
            </div>
            <form id="add-student-form" onsubmit="handleAddStudent(event)" class="space-y-4">
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">Full Name</label>
                    <input type="text" id="m-student-name" required placeholder="e.g. Rahul Sharma" class="w-full p-2.5 border rounded-xl text-sm outline-none focus:border-blue-500">
                </div>
                <div class="grid grid-cols-2 gap-3">
                    <div>
                        <label class="block text-xs font-semibold text-slate-600 mb-1">Roll Number</label>
                        <input type="text" id="m-student-roll" required placeholder="e.g. 101" class="w-full p-2.5 border rounded-xl text-sm outline-none focus:border-blue-500">
                    </div>
                    <div>
                        <label class="block text-xs font-semibold text-slate-600 mb-1">Class</label>
                        <select id="m-student-class" class="w-full p-2.5 border rounded-xl text-sm outline-none focus:border-blue-500">
                            <option value="Class 9">Class 9</option>
                            <option value="Class 10">Class 10</option>
                            <option value="Class 11" selected>Class 11</option>
                            <option value="Class 12">Class 12</option>
                        </select>
                    </div>
                </div>
                <div>
                    <label class="block text-xs font-semibold text-slate-600 mb-1">Parent Contact Number</label>
                    <input type="tel" id="m-student-phone" placeholder="e.g. 9876543210" class="w-full p-2.5 border rounded-xl text-sm outline-none focus:border-blue-500">
                </div>
                <div class="flex justify-end space-x-2 pt-2">
