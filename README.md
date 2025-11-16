<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lagan Bus Booking</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">
    <script src="https://cdn.jsdelivr.net/npm/sweetalert2@11"></script>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            padding: 20px;
            color: #333;
        }

        .header {
            text-align: center;
            color: white;
            margin-bottom: 30px;
            padding: 20px;
        }

        .header h1 {
            font-size: 2.5em;
            margin-bottom: 10px;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.2);
        }

        .header h1 i {
            margin-right: 10px;
        }

        .subtitle {
            font-size: 1.2em;
            margin-bottom: 15px;
            opacity: 0.9;
        }

        .contact-info {
            font-size: 1.1em;
            background: rgba(255,255,255,0.2);
            padding: 10px 20px;
            border-radius: 25px;
            display: inline-block;
            backdrop-filter: blur(10px);
        }

        .contact-info i {
            margin-right: 8px;
        }

        .container {
            max-width: 500px;
            margin: 0 auto;
        }

        .form-container {
            background: white;
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
            text-align: center;
        }

        .icon {
            font-size: 60px;
            color: #667eea;
            margin-bottom: 20px;
        }

        .form h2 {
            color: #333;
            margin-bottom: 10px;
            font-size: 1.8em;
        }

        .form p {
            color: #666;
            margin-bottom: 25px;
            font-size: 0.95em;
        }

        .form input {
            width: 100%;
            padding: 15px;
            margin-bottom: 20px;
            border: 2px solid #e0e0e0;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s;
        }

        .form input:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .form button {
            width: 100%;
            padding: 15px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            border: none;
            border-radius: 10px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            transition: transform 0.2s, box-shadow 0.2s;
        }

        .form button:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(102, 126, 234, 0.4);
        }

        .form button:active {
            transform: translateY(0);
        }

        .form button i {
            margin-right: 8px;
        }

        .ghost {
            background: transparent !important;
            border: 2px solid #667eea !important;
            color: #667eea !important;
        }

        .ghost:hover {
            background: #667eea !important;
            color: white !important;
        }

        .notification {
            padding: 12px;
            border-radius: 8px;
            margin-top: 15px;
            display: none;
            font-size: 14px;
        }

        .notification.error {
            background: #ffebee;
            color: #c62828;
            border-left: 4px solid #c62828;
        }

        .notification.success {
            background: #e8f5e9;
            color: #2e7d32;
            border-left: 4px solid #2e7d32;
        }

        /* Admin Panel Styles */
        .admin-panel {
            display: none;
            max-width: 1200px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
        }

        .admin-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 2px solid #e0e0e0;
        }

        .admin-title {
            color: #333;
            font-size: 1.8em;
        }

        .admin-title i {
            margin-right: 10px;
            color: #667eea;
        }

        .logout-btn {
            padding: 10px 20px;
            background: #dc3545;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 14px;
            transition: background 0.3s;
        }

        .logout-btn:hover {
            background: #c82333;
        }

        .logout-btn i {
            margin-right: 5px;
        }

        .passenger-form {
            background: #f8f9fa;
            padding: 25px;
            border-radius: 15px;
            margin-bottom: 30px;
        }

        .form-title {
            color: #333;
            margin-bottom: 20px;
            font-size: 1.5em;
        }

        .form-title i {
            margin-right: 10px;
            color: #667eea;
        }

        .form-row {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 20px;
            margin-bottom: 20px;
        }

        .form-group {
            display: flex;
            flex-direction: column;
        }

        .form-group label {
            margin-bottom: 8px;
            color: #555;
            font-weight: 500;
            font-size: 14px;
        }

        .form-control {
            padding: 12px;
            border: 2px solid #e0e0e0;
            border-radius: 8px;
            font-size: 15px;
            transition: all 0.3s;
        }

        .form-control:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .bus-image-preview {
            margin: 20px 0;
            text-align: center;
            display: none;
        }

        .bus-image-preview img {
            max-width: 100%;
            border-radius: 10px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
        }

        .action-buttons {
            display: flex;
            gap: 15px;
            margin-top: 20px;
        }

        .save-btn {
            flex: 1;
            padding: 12px;
            background: #28a745;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 15px;
            font-weight: 600;
            transition: background 0.3s;
        }

        .save-btn:hover {
            background: #218838;
        }

        .cancel-btn {
            flex: 1;
            padding: 12px;
            background: #6c757d;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 15px;
            font-weight: 600;
            transition: background 0.3s;
        }

        .cancel-btn:hover {
            background: #5a6268;
        }

        /* Table Styles */
        .passengers-table-container {
            margin-top: 30px;
        }

        .table-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }

        .table-title {
            color: #333;
            font-size: 1.5em;
        }

        .table-title i {
            margin-right: 10px;
            color: #667eea;
        }

        .search-box {
            position: relative;
            display: flex;
            align-items: center;
        }

        .search-box i {
            position: absolute;
            left: 15px;
            color: #999;
        }

        .search-box input {
            padding: 10px 15px 10px 40px;
            border: 2px solid #e0e0e0;
            border-radius: 25px;
            font-size: 14px;
            width: 300px;
            transition: all 0.3s;
        }

        .search-box input:focus {
            outline: none;
            border-color: #667eea;
            box-shadow: 0 0 0 3px rgba(102, 126, 234, 0.1);
        }

        .passengers-table {
            width: 100%;
            border-collapse: collapse;
            background: white;
            border-radius: 10px;
            overflow: hidden;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }

        .passengers-table thead {
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
        }

        .passengers-table th {
            padding: 15px;
            text-align: left;
            font-weight: 600;
            font-size: 14px;
        }

        .passengers-table td {
            padding: 15px;
            border-bottom: 1px solid #e0e0e0;
            font-size: 14px;
        }

        .passengers-table tbody tr:hover {
            background: #f8f9fa;
        }

        .passengers-table tbody tr:last-child td {
            border-bottom: none;
        }

        .action-btn {
            padding: 6px 12px;
            margin-right: 8px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 12px;
            transition: all 0.2s;
        }

        .edit-btn {
            background: #ffc107;
            color: #333;
        }

        .edit-btn:hover {
            background: #e0a800;
        }

        .delete-btn {
            background: #dc3545;
            color: white;
        }

        .delete-btn:hover {
            background: #c82333;
        }

        .action-btn i {
            margin-right: 5px;
        }

        .paid-status {
            color: #28a745;
            font-weight: 600;
        }

        .pending-status {
            color: #ffc107;
            font-weight: 600;
        }

        .cancelled-status {
            color: #dc3545;
            font-weight: 600;
        }

        .spinner {
            display: none;
            text-align: center;
            padding: 20px;
        }

        .spinner::after {
            content: '';
            display: inline-block;
            width: 40px;
            height: 40px;
            border: 4px solid #f3f3f3;
            border-top: 4px solid #667eea;
            border-radius: 50%;
            animation: spin 1s linear infinite;
        }

        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }

        /* Passenger Details View */
        .passenger-details {
            display: none;
            max-width: 800px;
            margin: 0 auto;
            background: white;
            border-radius: 20px;
            padding: 30px;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
        }

        .details-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 20px;
            border-bottom: 2px solid #e0e0e0;
        }

        .details-header h2 {
            color: #333;
            font-size: 1.8em;
        }

        .details-header h2 i {
            margin-right: 10px;
            color: #667eea;
        }

        .back-btn {
            padding: 10px 20px;
            background: #6c757d;
            color: white;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 14px;
            transition: background 0.3s;
        }

        .back-btn:hover {
            background: #5a6268;
        }

        .back-btn i {
            margin-right: 5px;
        }

        .bookings-container {
            display: grid;
            gap: 20px;
        }

        .bus-card {
            background: #f8f9fa;
            border-radius: 15px;
            padding: 25px;
            box-shadow: 0 4px 10px rgba(0,0,0,0.1);
            position: relative;
            transition: transform 0.2s, box-shadow 0.2s;
        }

        .bus-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 6px 20px rgba(0,0,0,0.15);
        }

        .bus-image-container {
            text-align: center;
            margin-bottom: 15px;
        }

        .bus-image-container img {
            max-width: 100%;
            border-radius: 10px;
            max-height: 200px;
            object-fit: cover;
        }

        .bus-name {
            font-size: 1.5em;
            font-weight: 700;
            color: #333;
            margin-bottom: 10px;
            text-align: center;
        }

        .bus-time {
            text-align: center;
            color: #666;
            margin-bottom: 15px;
            font-size: 1.1em;
        }

        .seat-badge {
            position: absolute;
            top: 20px;
            right: 20px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            padding: 8px 15px;
            border-radius: 20px;
            font-weight: 600;
            font-size: 14px;
        }

        .info-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 15px;
            margin-top: 20px;
        }

        .info-item {
            background: white;
            padding: 15px;
            border-radius: 8px;
        }

        .info-label {
            font-size: 12px;
            color: #999;
            margin-bottom: 5px;
            text-transform: uppercase;
            letter-spacing: 0.5px;
        }

        .info-value {
            font-size: 16px;
            color: #333;
            font-weight: 600;
        }

        /* Improved loading states */
        .loading {
            opacity: 0.7;
            pointer-events: none;
        }

        /* Better form validation */
        .form input:invalid, .form select:invalid {
            border-color: #ff6b6b;
        }

        .form input:valid, .form select:valid {
            border-color: #51cf66;
        }

        /* Enhanced responsive design */
        @media (max-width: 768px) {
            .header h1 {
                font-size: 2em;
            }

            .form-container {
                padding: 30px 20px;
            }

            .form-row {
                grid-template-columns: 1fr;
            }

            .admin-panel {
                padding: 20px;
            }

            .admin-header {
                flex-direction: column;
                gap: 15px;
                align-items: flex-start;
            }

            .table-header {
                flex-direction: column;
                gap: 15px;
                align-items: flex-start;
            }

            .search-box input {
                width: 100%;
            }

            .passengers-table {
                font-size: 12px;
            }

            .passengers-table th,
            .passengers-table td {
                padding: 10px 8px;
            }

            .info-grid {
                grid-template-columns: 1fr;
            }

            .action-buttons {
                flex-direction: column;
            }

            .action-buttons button {
                width: 100%;
            }

            .details-header {
                flex-direction: column;
                gap: 15px;
                align-items: flex-start;
            }
        }

        @media (max-width: 480px) {
            body {
                padding: 10px;
            }

            .header h1 {
                font-size: 1.5em;
            }

            .subtitle {
                font-size: 1em;
            }

            .contact-info {
                font-size: 0.9em;
                padding: 8px 15px;
            }
        }

        /* Better empty state */
        .empty-state {
            text-align: center;
            padding: 40px 20px;
            color: #546e7a;
        }

        .empty-state i {
            font-size: 48px;
            margin-bottom: 15px;
            color: #bbdefb;
        }

        .empty-state h3 {
            margin-bottom: 10px;
            color: #333;
        }

        /* Improved search results */
        .search-results-count {
            padding: 10px 15px;
            background: #e3f2fd;
            border-radius: 10px;
            margin-bottom: 15px;
            font-size: 14px;
            color: #0d47a1;
        }

        /* Debug Panel */
        .debug-panel {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #1e1e1e;
            color: #00ff00;
            padding: 15px;
            border-radius: 8px;
            font-family: 'Courier New', monospace;
            font-size: 12px;
            max-width: 400px;
            max-height: 300px;
            overflow-y: auto;
            z-index: 10000;
            box-shadow: 0 4px 20px rgba(0,0,0,0.3);
            display: none;
        }

        .debug-panel.active {
            display: block;
        }

        .debug-panel h4 {
            color: #00ff00;
            margin: 0 0 10px 0;
            font-size: 14px;
        }

        .debug-panel .debug-log {
            margin: 5px 0;
            padding: 5px;
            background: rgba(0,255,0,0.1);
            border-left: 2px solid #00ff00;
            word-break: break-all;
        }

        .debug-panel .debug-error {
            color: #ff6b6b;
            border-left-color: #ff6b6b;
            background: rgba(255,107,107,0.1);
        }

        .debug-toggle {
            position: fixed;
            bottom: 20px;
            right: 20px;
            background: #667eea;
            color: white;
            border: none;
            padding: 10px 15px;
            border-radius: 25px;
            cursor: pointer;
            z-index: 10001;
            font-size: 12px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.2);
        }

        .debug-toggle:hover {
            background: #764ba2;
        }

        .test-connection-btn {
            background: #28a745;
            color: white;
            border: none;
            padding: 8px 15px;
            border-radius: 5px;
            cursor: pointer;
            font-size: 12px;
            margin-left: 10px;
        }

        .test-connection-btn:hover {
            background: #218838;
        }
    </style>
</head>
<body>
<div class="header">
    <h1><i class="fas fa-bus"></i> Lagan Bus Booking</h1>
    <p class="subtitle">Your journey, our priority</p>
    <div class="contact-info">
        <i class="fas fa-phone"></i> For Reservations: <strong>0777 402 886</strong>
    </div>
</div>

<div class="container" id="container">
    <div class="form-container passenger-container">
        <div class="icon">
            <i class="fas fa-users"></i>
        </div>
        <form class="form" id="passenger-form">
            <h2>Passenger Access</h2>
            <p>Enter your contact number to view all your bookings</p>
            <input type="tel" placeholder="Your Phone Number" id="passenger-contact"
                   pattern="[0-9]{10}" title="Please enter a valid 10-digit phone number" required />
            <button type="submit" id="passenger-login"><i class="fas fa-search"></i> Find My Bookings</button>
            <div class="notification error" id="passenger-error">
                Please enter a valid contact number
            </div>
        </form>

        <!-- Admin Login Button -->
        <button type="button" id="admin-login-btn" class="ghost" style="margin-top: 10px;">
            <i class="fas fa-lock"></i> Admin Login
        </button>
    </div>
</div>

<!-- Admin Panel -->
<div class="admin-panel" id="admin-panel">
    <div class="admin-header">
        <h2 class="admin-title"><i class="fas fa-tachometer-alt"></i> Admin Dashboard</h2>
        <button class="logout-btn" id="admin-logout"><i class="fas fa-sign-out-alt"></i> Logout</button>
    </div>

    <div class="passenger-form">
        <h3 class="form-title"><i class="fas fa-user-plus"></i>Add/Edit Passenger</h3>
        <div class="form-row">
            <div class="form-group">
                <label for="p-name">Passenger Name *</label>
                <input type="text" id="p-name" class="form-control" placeholder="Full Name" required>
            </div>
            <div class="form-group">
                <label for="p-contact">Contact Number *</label>
                <input type="tel" id="p-contact" class="form-control" placeholder="Phone Number"
                       pattern="[0-9]{10}" title="Please enter a valid 10-digit phone number" required>
            </div>
        </div>
        <div class="form-row">
            <div class="form-group">
                <label for="p-bus">Bus Name *</label>
                <select id="p-bus" class="form-control" required onchange="showBusImage()">
                    <option value="">Select Bus</option>
                    <option value="Super Line">Super Line</option>
                    <option value="Loyds">Loyds</option>
                    <option value="Sakeer Express">Sakeer Express</option>
                    <option value="RS Express">RS Express</option>
                    <option value="My Own Express">My Own Express</option>
                    <option value="Al Ahla">Al Ahla</option>
                    <option value="Star Travels">Star Travels</option>
                    <option value="AL Rashith">AL Rashith</option>
                </select>
            </div>
            <div class="form-group">
                <label for="p-time">Bus Time *</label>
                <input type="time" id="p-time" class="form-control" value="20:30" required>
            </div>
        </div>
        <div class="bus-image-preview" id="bus-image-preview">
            <!-- Bus image will be shown here -->
        </div>
        <div class="form-row">
            <div class="form-group">
                <label for="p-date">Date *</label>
                <input type="date" id="p-date" class="form-control" required>
            </div>
            <div class="form-group">
                <label for="p-seat">Seat Number *</label>
                <input type="text" id="p-seat" class="form-control" placeholder="Seat Number" required>
            </div>
        </div>
        <div class="form-row">
            <div class="form-group">
                <label for="p-pickup">Pickup Location</label>
                <select id="p-pickup" class="form-control">
                    <option value="">Select Location</option>
                    <option value="Lagan Bus Center">Lagan Bus Center</option>
                    <option value="Rajagiriya">Rajagiriya</option>
                    <option value="Technigal Junction">Technigal Junction</option>
                    <option value="Colombo Airport">Colombo Airport</option>
                    <option value="Wellawatta">Wellawatta</option>
                </select>
            </div>
            <div class="form-group">
                <label for="p-payment">Payment Status</label>
                <select id="p-payment" class="form-control">
                    <option value="Paid">Paid</option>
                    <option value="Pending">Pending</option>
                    <option value="Cancelled">Cancelled</option>
                </select>
            </div>
        </div>
        <div class="action-buttons">
            <button type="button" id="save-passenger" class="save-btn"><i class="fas fa-save"></i> Save Passenger</button>
            <button type="button" id="cancel-edit" class="cancel-btn" style="display:none;"><i class="fas fa-times"></i> Cancel</button>
        </div>
        <div class="notification success" id="save-success">
            Passenger details saved successfully!
        </div>
        <div class="notification error" id="save-error">
            Please fill all required fields
        </div>
    </div>

    <div class="passengers-table-container">
        <div class="table-header">
            <h3 class="table-title"><i class="fas fa-list"></i> All Passengers</h3>
            <div class="search-box">
                <i class="fas fa-search"></i>
                <input type="text" id="search-passenger" placeholder="Search...">
            </div>
        </div>
        <div class="search-results-count" id="search-results-count" style="display: none;"></div>
        <table class="passengers-table">
            <thead>
            <tr>
                <th>Name</th>
                <th>Contact</th>
                <th>Bus</th>
                <th>Time</th>
                <th>Date</th>
                <th>Seat</th>
                <th>Pickup</th>
                <th>Payment</th>
                <th>Actions</th>
            </tr>
            </thead>
            <tbody id="passengers-list">
            <!-- Passenger data will be loaded here -->
            </tbody>
        </table>
        <div class="spinner" id="table-spinner"></div>
    </div>
</div>

<!-- Passenger Details View -->
<div class="passenger-details" id="passenger-details">
    <div class="details-header">
        <h2><i class="fas fa-ticket-alt"></i> My Bookings</h2>
        <button class="back-btn" id="back-to-search"><i class="fas fa-arrow-left"></i> Back</button>
    </div>
    <!-- Dynamic content for each booking will be inserted here -->
</div>

<!-- Debug Panel -->
<button class="debug-toggle" id="debug-toggle" onclick="toggleDebug()">🔍 Debug</button>
<div class="debug-panel" id="debug-panel">
    <h4>Debug Log</h4>
    <button class="test-connection-btn" onclick="testConnection()">Test Connection</button>
    <button style="background: #dc3545; color: white; border: none; padding: 8px 15px; border-radius: 5px; cursor: pointer; font-size: 12px; margin-left: 10px;" onclick="clearDebug()">Clear</button>
    <div id="debug-content"></div>
</div>

<script>
    // Google Sheets API configuration - Replace with your deployed script URL
    // IMPORTANT: For POST requests to work, your Google Apps Script must be deployed as a Web App with:
    // - Execute as: Me (your account)
    // - Who has access: Anyone (or Anyone with Google account)
    // - The script should return JSON responses for best compatibility
    // 
    // TO SET UP: Follow the instructions in SETUP INSTRUCTIONS.md
    // Replace the URL below with your Web App URL from Google Apps Script deployment
    const scriptURL = 'https://script.google.com/macros/s/AKfycbyoK2-5STzhOmL2DnIy0A522benVq0f_YLxKfWSxXGN6hskd20u-TJbCRWWtxgYx5uj/exec';
    
    // Log script URL for debugging (check browser console)
    console.log('Script URL:', scriptURL);
    console.log('To test the connection, open this URL in your browser:', scriptURL);

    // Debug Panel Functions
    function debugLog(message, isError = false) {
        const debugContent = document.getElementById('debug-content');
        const logDiv = document.createElement('div');
        logDiv.className = 'debug-log' + (isError ? ' debug-error' : '');
        const timestamp = new Date().toLocaleTimeString();
        logDiv.textContent = `[${timestamp}] ${message}`;
        debugContent.appendChild(logDiv);
        debugContent.scrollTop = debugContent.scrollHeight;
        
        // Also log to console if available
        if (isError) {
            console.error(message);
        } else {
            console.log(message);
        }
    }

    function toggleDebug() {
        const panel = document.getElementById('debug-panel');
        panel.classList.toggle('active');
    }

    function clearDebug() {
        document.getElementById('debug-content').innerHTML = '';
    }

    function testConnection() {
        debugLog('Testing connection to: ' + scriptURL);
        debugLog('Making request...');
        
        fetch(scriptURL)
            .then(response => {
                debugLog('Response status: ' + response.status);
                return response.text();
            })
            .then(text => {
                debugLog('Response received: ' + text.substring(0, 100));
                try {
                    const data = JSON.parse(text);
                    debugLog('Parsed JSON successfully!');
                    debugLog('Data type: ' + (Array.isArray(data) ? 'Array' : 'Object'));
                    debugLog('Data length: ' + (Array.isArray(data) ? data.length : 'N/A'));
                    Swal.fire({
                        icon: 'success',
                        title: 'Connection Successful!',
                        html: `
                            <p>Script URL is working correctly!</p>
                            <p>Response: <code>${text.substring(0, 200)}</code></p>
                            <p>This means your Google Apps Script is deployed correctly.</p>
                        `
                    });
                } catch (e) {
                    debugLog('Failed to parse JSON: ' + e.message, true);
                    Swal.fire({
                        icon: 'warning',
                        title: 'Connection Test',
                        html: `
                            <p>Got response but couldn't parse as JSON.</p>
                            <p>Response: <code>${text.substring(0, 200)}</code></p>
                        `
                    });
                }
            })
            .catch(error => {
                debugLog('Connection failed: ' + error.message, true);
                Swal.fire({
                    icon: 'error',
                    title: 'Connection Failed',
                    html: `
                        <p>Failed to connect to script URL.</p>
                        <p>Error: ${error.message}</p>
                        <p>Check that the script is deployed as a Web App.</p>
                    `
                });
            });
    }

    // DOM Elements
    const container = document.getElementById('container');
    const passengerForm = document.getElementById('passenger-form');
    const adminPanel = document.getElementById('admin-panel');
    const passengerDetails = document.getElementById('passenger-details');
    const adminLoginBtn = document.getElementById('admin-login-btn');
    const adminLogoutBtn = document.getElementById('admin-logout');
    const backToSearchBtn = document.getElementById('back-to-search');
    const searchPassenger = document.getElementById('search-passenger');
    const tableSpinner = document.getElementById('table-spinner');
    const busImagePreview = document.getElementById('bus-image-preview');
    const searchResultsCount = document.getElementById('search-results-count');

    // Form Fields
    const passengerContact = document.getElementById('passenger-contact');

    // Admin Form Fields
    const pName = document.getElementById('p-name');
    const pContact = document.getElementById('p-contact');
    const pBus = document.getElementById('p-bus');
    const pTime = document.getElementById('p-time');
    const pDate = document.getElementById('p-date');
    const pSeat = document.getElementById('p-seat');
    const pPickup = document.getElementById('p-pickup');
    const pPayment = document.getElementById('p-payment');
    const savePassengerBtn = document.getElementById('save-passenger');
    const cancelEditBtn = document.getElementById('cancel-edit');

    // Notification Elements
    const passengerError = document.getElementById('passenger-error');
    const saveSuccess = document.getElementById('save-success');
    const saveError = document.getElementById('save-error');

    // Passenger List
    const passengersList = document.getElementById('passengers-list');

    // Improved bus images mapping with fallback
    const busImages = {
        "Super Line": "https://via.placeholder.com/300x150/0d47a1/ffffff?text=Super+Line",
        "Loyds": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSH5TDKneY-w7z9_Hq8fbiVvSGbZv4yoZHrmg&s",
        "Sakeer Express": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTDmxDNDXSrkmXau-UMt8dsW73sQV3DtQ8vYw&s",
        "RS Express": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRZK2o5jTogVMMOeoXlDSlflRiFSpauF02Dhjrc2CtPifgmUZFLRmS6TWFe0tK6SAr_oDE&usqp=CAU",
        "My Own Express": "https://via.placeholder.com/300x150/2196f3/ffffff?text=My+Own+Express",
        "Al Ahla": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ7AN4cyIEzxKqPkLBErL68G68p--M6tKAgyA&s",
        "Star Travels": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQse3K0_owtq6OqU5mVzmantIce_b0FVn7B3w&s",
        "AL Rashith": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcStxaqtD3_cI4VW8VMCAY639gcnozolEwrJyg&s"
    };

    // Set default date to today
    pDate.valueAsDate = new Date();

    // Track current editing passenger
    let editingPassengerIndex = null;
    let allPassengers = [];

    // Event Listeners
    passengerForm.addEventListener('submit', (e) => {
        e.preventDefault();
        checkPassengerBooking();
    });

    adminLoginBtn.addEventListener('click', adminLogin);
    adminLogoutBtn.addEventListener('click', adminLogout);
    backToSearchBtn.addEventListener('click', backToSearch);
    savePassengerBtn.addEventListener('click', savePassengerToSheet);
    cancelEditBtn.addEventListener('click', cancelEdit);
    searchPassenger.addEventListener('input', filterPassengers);

    // Functions
    function adminLogin() {
        const password = prompt('Enter admin password:');
        if (password === 'admin123') { // Change this to your preferred password
            container.style.display = 'none';
            adminPanel.style.display = 'block';
            loadPassengers();
        } else {
            alert('Invalid password');
        }
    }

    function adminLogout() {
        adminPanel.style.display = 'none';
        container.style.display = 'block';
        resetForm();
    }

    function backToSearch() {
        passengerDetails.style.display = 'none';
        container.style.display = 'block';
        passengerContact.value = '';

        // Clear passenger details content
        const bookingsContainer = passengerDetails.querySelector('.bookings-container');
        if (bookingsContainer) {
            bookingsContainer.remove();
        }
    }

    function showBusImage() {
        const busName = pBus.value;
        const imagePath = busImages[busName] || "";
        const previewDiv = document.getElementById("bus-image-preview");
        if (imagePath) {
            previewDiv.innerHTML = `<img src="${imagePath}" alt="${busName}" onerror="this.style.display='none'">`;
            previewDiv.style.display = "block";
        } else {
            previewDiv.innerHTML = "";
            previewDiv.style.display = "none";
        }
    }

    function checkPassengerBooking() {
        const contact = passengerContact.value.trim();
        if (!contact) {
            showNotification(passengerError, 'Please enter your contact number');
            return;
        }

        // Validate phone number format
        const phoneRegex = /^[0-9]{10}$/;
        if (!phoneRegex.test(contact)) {
            showNotification(passengerError, 'Please enter a valid 10-digit phone number');
            return;
        }

        // Show loading state
        container.classList.add('loading');

        Swal.fire({
            title: 'Searching...',
            text: 'Finding your bookings',
            allowOutsideClick: false,
            didOpen: () => {
                Swal.showLoading();
            }
        });

        // Use XMLHttpRequest for better compatibility
        const xhr = new XMLHttpRequest();
        xhr.open('GET', scriptURL, true);
        xhr.timeout = 30000;

        xhr.onload = function() {
                Swal.close();
                container.classList.remove('loading');
            
            if (xhr.status === 200 || xhr.status === 0) {
                try {
                    const passengers = JSON.parse(xhr.responseText);
                    
                    if (!Array.isArray(passengers)) {
                        throw new Error('Invalid response format');
                    }

                const matchingBookings = passengers.filter(passenger =>
                    passenger.contact && passenger.contact.toString().includes(contact)
                );

                if (matchingBookings.length === 0) {
                    Swal.fire({
                        icon: 'info',
                        title: 'No Bookings Found',
                        text: 'We couldn\'t find any bookings for this number.'
                    });
                    return;
                }

                container.style.display = 'none';
                passengerDetails.style.display = 'block';
                showPassengerBookings(matchingBookings);
                } catch (e) {
                    console.error('Error parsing response:', e);
                    Swal.fire({
                        icon: 'error',
                        title: 'Error',
                        text: 'Failed to fetch booking data. Please check your Google Apps Script setup.'
                    });
                }
            } else {
                Swal.fire({
                    icon: 'error',
                    title: 'Error',
                    text: `Failed to load data (Status: ${xhr.status}). Please check your Google Apps Script deployment.`
                });
            }
        };

        xhr.onerror = function() {
                Swal.close();
                container.classList.remove('loading');
            // Try fetch as fallback
            fetch(scriptURL)
                .then(res => res.json())
                .then(passengers => {
                    const matchingBookings = passengers.filter(passenger =>
                        passenger.contact && passenger.contact.toString().includes(contact)
                    );

                    if (matchingBookings.length === 0) {
                        Swal.fire({
                            icon: 'info',
                            title: 'No Bookings Found',
                            text: 'We couldn\'t find any bookings for this number.'
                        });
                        return;
                    }

                    container.style.display = 'none';
                    passengerDetails.style.display = 'block';
                    showPassengerBookings(matchingBookings);
                })
                .catch(err => {
                console.error('Error fetching data:', err);
                Swal.fire({
                    icon: 'error',
                    title: 'Error',
                        html: 'Failed to fetch booking data. Please check:<br>1) Your internet connection<br>2) Google Apps Script is deployed correctly<br>3) The script URL is correct'
                });
            });
        };

        xhr.ontimeout = function() {
            Swal.close();
            container.classList.remove('loading');
            Swal.fire({
                icon: 'error',
                title: 'Timeout',
                text: 'Request timed out. Please check your connection and try again.'
            });
        };

        xhr.send();
    }

    function showPassengerBookings(bookings) {
        // Clear previous content
        const existingContainer = passengerDetails.querySelector('.bookings-container');
        if (existingContainer) {
            existingContainer.remove();
        }

        // Create bookings container
        const bookingsContainer = document.createElement('div');
        bookingsContainer.className = 'bookings-container';
        bookingsContainer.style.padding = '20px 0';

        // Sort by date
        bookings.sort((a, b) => new Date(a.date) - new Date(b.date));

        // Create a card for each booking
        bookings.forEach((booking, index) => {
            const busCard = document.createElement('div');
            busCard.className = 'bus-card';

            // Format date
            const bookingDate = new Date(booking.date);
            const formattedDate = bookingDate.toLocaleDateString('en-US', {
                weekday: 'short',
                year: 'numeric',
                month: 'short',
                day: 'numeric'
            });

            // Format time
            const formattedTime = formatTime(booking.time);

            // Get bus image path
            const busImagePath = busImages[booking.bus] || "";

            // Determine payment status class
            const paymentClass = booking.payment === 'Paid' ? 'paid-status' :
                booking.payment === 'Pending' ? 'pending-status' : 'cancelled-status';

            busCard.innerHTML = `
                    <div class="bus-image-container">
                        ${busImagePath ? `<img src="${busImagePath}" alt="${booking.bus}" onerror="this.style.display='none'">` :
                `<div style="color: #0d47a1; font-size: 40px;"><i class="fas fa-bus"></i></div>`}
                    </div>
                    <div class="bus-name">${booking.bus}</div>
                    <div class="bus-time">${formattedTime} • ${formattedDate}</div>
                    <div class="seat-badge">${booking.seat}</div>
                    <div class="info-grid">
                        <div class="info-item">
                            <div class="info-label">Passenger</div>
                            <div class="info-value">${booking.name}</div>
                        </div>
                        <div class="info-item">
                            <div class="info-label">Contact</div>
                            <div class="info-value">${booking.contact}</div>
                        </div>
                        <div class="info-item">
                            <div class="info-label">Pickup</div>
                            <div class="info-value">${booking.pickup || 'Not specified'}</div>
                        </div>
                        <div class="info-item">
                            <div class="info-label">Payment</div>
                            <div class="info-value ${paymentClass}">${booking.payment}</div>
                        </div>
                    </div>
                `;

            bookingsContainer.appendChild(busCard);
        });

        passengerDetails.appendChild(bookingsContainer);
    }

    function formatTime(timeString) {
        if (!timeString) return '';

        // Handle both "HH:MM" and "HH:MM:SS" formats
        const timeParts = timeString.split(':');
        const hours = parseInt(timeParts[0]);
        const minutes = timeParts[1];

        const period = hours >= 12 ? 'PM' : 'AM';
        const formattedHours = hours % 12 || 12;

        return `${formattedHours}:${minutes} ${period}`;
    }

    function loadPassengers() {
        tableSpinner.style.display = 'block';
        debugLog('Loading passengers from: ' + scriptURL);

        // Try fetch first (works better with CORS)
        fetch(scriptURL)
            .then(response => {
                debugLog('Response status: ' + response.status);
                debugLog('Response ok: ' + response.ok);
                
                // Google Apps Script may return status 0 or 200
                if (response.ok || response.status === 0 || response.status === 200) {
                    return response.text().then(text => {
                        debugLog('Response text: ' + text.substring(0, 200));
                        return text;
                    });
                } else {
                    throw new Error(`HTTP ${response.status}`);
                }
            })
            .then(text => {
                try {
                    // Try to parse as JSON
                    let passengers;
                    try {
                        passengers = JSON.parse(text);
                        debugLog('Successfully parsed JSON');
                    } catch (parseError) {
                        // If parsing fails, check if it's wrapped in HTML
                        debugLog('Direct JSON parse failed, trying to extract from text', true);
                        // Try to find JSON in the text
                        const jsonMatch = text.match(/\[.*\]/s) || text.match(/\{.*\}/s);
                        if (jsonMatch) {
                            passengers = JSON.parse(jsonMatch[0]);
                            debugLog('Extracted JSON from text');
                        } else {
                            throw new Error('No valid JSON found in response');
                        }
                    }
                    
                    // Handle the response
                    if (Array.isArray(passengers)) {
                        debugLog('Loaded passengers: ' + passengers.length);
                allPassengers = passengers;
                displayPassengers(passengers);
                tableSpinner.style.display = 'none';
                    } else if (passengers && passengers.error) {
                        throw new Error(passengers.error);
                    } else if (passengers && passengers.success === false) {
                        throw new Error(passengers.message || 'Failed to load data');
                    } else {
                        // Empty or unexpected format - treat as empty array
                        debugLog('Empty or unexpected response, treating as empty');
                        allPassengers = [];
                        displayPassengers([]);
                        tableSpinner.style.display = 'none';
                    }
                } catch (e) {
                    debugLog('Error parsing response: ' + e.message, true);
                    debugLog('Response text: ' + text.substring(0, 200), true);
                    tableSpinner.style.display = 'none';
                    // Try XMLHttpRequest as fallback
                    tryXHRLoad();
                }
            })
            .catch(error => {
                debugLog('Fetch error: ' + error.message, true);
                tableSpinner.style.display = 'none';
                // Try XMLHttpRequest as fallback
                tryXHRLoad();
            });

        // Fallback function using XMLHttpRequest
        function tryXHRLoad() {
            debugLog('Trying XMLHttpRequest as fallback...');
            const xhr = new XMLHttpRequest();
            xhr.open('GET', scriptURL, true);
            xhr.timeout = 30000;

            xhr.onload = function() {
                tableSpinner.style.display = 'none';
                debugLog('XHR Status: ' + xhr.status);
                debugLog('XHR Response: ' + xhr.responseText.substring(0, 200));
                
                if (xhr.status === 200 || xhr.status === 0) {
                    try {
                        const passengers = JSON.parse(xhr.responseText);
                        if (Array.isArray(passengers)) {
                            debugLog('XHR: Loaded ' + passengers.length + ' passengers');
                            allPassengers = passengers;
                            displayPassengers(passengers);
                        } else {
                            debugLog('XHR: Empty response');
                            allPassengers = [];
                            displayPassengers([]);
                        }
                    } catch (e) {
                        debugLog('XHR Parse error: ' + e.message, true);
                        showLoadError('Failed to parse response. Check debug panel for details.');
                    }
                } else {
                    debugLog('XHR: Server returned status ' + xhr.status, true);
                    showLoadError(`Server returned status ${xhr.status}`);
                }
            };

            xhr.onerror = function() {
                tableSpinner.style.display = 'none';
                debugLog('XHR Network error', true);
                showLoadError('Network error. Please check your internet connection.');
            };

            xhr.ontimeout = function() {
                tableSpinner.style.display = 'none';
                debugLog('XHR Timeout', true);
                showLoadError('Request timed out. Please try again.');
            };

            xhr.send();
        }

        function showLoadError(customMessage) {
                Swal.fire({
                    icon: 'error',
                title: 'Failed to Load Data',
                html: `
                    <p>${customMessage || 'Unable to load passenger data. Please check:'}</p>
                    <ol style="text-align: left; margin: 15px 0;">
                        <li>Your internet connection is working</li>
                        <li>Google Apps Script is deployed as a <strong>Web App</strong></li>
                        <li>Deployment settings: <strong>"Execute as: Me"</strong> and <strong>"Who has access: Anyone"</strong></li>
                        <li>The script URL is correct: <br><small style="word-break: break-all;">${scriptURL}</small></li>
                        <li>Open browser console (F12) to see detailed error messages</li>
                    </ol>
                    <p><strong>Debug:</strong> Open the script URL directly: <a href="${scriptURL}" target="_blank">${scriptURL}</a></p>
                `,
                width: 600,
                confirmButtonText: 'Open Script URL',
                showCancelButton: true,
                cancelButtonText: 'Close'
            }).then((result) => {
                if (result.isConfirmed) {
                    window.open(scriptURL, '_blank');
                }
            });
        }
    }

    function displayPassengers(passengers) {
        passengersList.innerHTML = '';

        if (passengers.length === 0) {
            passengersList.innerHTML = `
                    <tr>
                        <td colspan="9" style="text-align: center; padding: 30px; color: #546e7a;">
                            <div class="empty-state">
                                <i class="fas fa-users"></i>
                                <h3>No passengers found</h3>
                                <p>Add your first passenger using the form above</p>
                            </div>
                        </td>
                    </tr>
                `;
            return;
        }

        passengers.forEach((passenger, index) => {
            const row = document.createElement('tr');

            // Format date
            const bookingDate = new Date(passenger.date);
            const formattedDate = bookingDate.toLocaleDateString('en-US', {
                month: 'short',
                day: 'numeric',
                year: 'numeric'
            });

            // Format time
            const formattedTime = formatTime(passenger.time);

            // Determine payment status class
            const paymentClass = passenger.payment === 'Paid' ? 'paid-status' :
                passenger.payment === 'Pending' ? 'pending-status' : 'cancelled-status';

            row.innerHTML = `
                    <td>${passenger.name}</td>
                    <td>${passenger.contact}</td>
                    <td>${passenger.bus}</td>
                    <td>${formattedTime}</td>
                    <td>${formattedDate}</td>
                    <td>${passenger.seat}</td>
                    <td>${passenger.pickup || 'Not specified'}</td>
                    <td class="${paymentClass}">${passenger.payment}</td>
                    <td>
                        <button class="action-btn edit-btn" onclick="editPassenger(${index})">
                            <i class="fas fa-edit"></i> Edit
                        </button>
                        <button class="action-btn delete-btn" onclick="deletePassenger(${index})">
                            <i class="fas fa-trash"></i> Delete
                        </button>
                    </td>
                `;

            passengersList.appendChild(row);
        });
    }

    function filterPassengers() {
        const searchTerm = searchPassenger.value.toLowerCase();
        const filteredPassengers = allPassengers.filter(passenger =>
            passenger.name.toLowerCase().includes(searchTerm) ||
            passenger.contact.includes(searchTerm) ||
            passenger.bus.toLowerCase().includes(searchTerm) ||
            passenger.seat.toLowerCase().includes(searchTerm) ||
            (passenger.pickup && passenger.pickup.toLowerCase().includes(searchTerm))
        );

        displayPassengers(filteredPassengers);

        // Show search results count
        if (searchTerm) {
            searchResultsCount.textContent = `Found ${filteredPassengers.length} passenger(s) matching "${searchTerm}"`;
            searchResultsCount.style.display = 'block';
        } else {
            searchResultsCount.style.display = 'none';
        }
    }

    function savePassengerToSheet() {
        // Validate required fields
        if (!pName.value.trim() || !pContact.value.trim() || !pBus.value || !pTime.value || !pDate.value || !pSeat.value.trim()) {
            showNotification(saveError, 'Please fill all required fields');
            return;
        }

        // Validate phone number
        const phoneRegex = /^[0-9]{10}$/;
        if (!phoneRegex.test(pContact.value.trim())) {
            showNotification(saveError, 'Please enter a valid 10-digit phone number');
            return;
        }

        const passengerData = {
            name: pName.value.trim(),
            contact: pContact.value.trim(),
            bus: pBus.value,
            time: pTime.value,
            date: pDate.value,
            seat: pSeat.value.trim(),
            pickup: pPickup.value,
            payment: pPayment.value
        };

        // Show loading
        savePassengerBtn.disabled = true;
        savePassengerBtn.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Saving...';

        // Send data to Google Sheets using XMLHttpRequest (more reliable with Google Apps Script)
        const xhr = new XMLHttpRequest();
        const params = new URLSearchParams();
        params.append('name', passengerData.name);
        params.append('contact', passengerData.contact);
        params.append('bus', passengerData.bus);
        params.append('time', passengerData.time);
        params.append('date', passengerData.date);
        params.append('seat', passengerData.seat);
        params.append('pickup', passengerData.pickup);
        params.append('payment', passengerData.payment);
        
        if (editingPassengerIndex !== null) {
            params.append('action', 'edit');
            params.append('index', allPassengers[editingPassengerIndex].index);
        }

        xhr.open('POST', scriptURL, true);
        xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');

        xhr.onload = function() {
            if (xhr.status === 200 || xhr.status === 0) {
                try {
                    const result = JSON.parse(xhr.responseText);
                    if (result && result.success !== false) {
                        showNotification(saveSuccess, result.message || 'Passenger saved successfully!');
                        resetForm();
                        setTimeout(() => loadPassengers(), 500);
                    } else {
                        throw new Error(result.message || 'Server returned error');
                    }
                } catch (e) {
                    // If response is not JSON (might be HTML redirect page), assume success
                    // Google Apps Script sometimes returns HTML redirect pages
                    showNotification(saveSuccess, 'Passenger saved successfully!');
                    resetForm();
                    setTimeout(() => loadPassengers(), 1000);
                }
            } else {
                // Try fetch as fallback
                tryFetchMethod();
            }
            savePassengerBtn.disabled = false;
            savePassengerBtn.innerHTML = '<i class="fas fa-save"></i> Save Passenger';
        };

        xhr.onerror = function() {
            console.error('XMLHttpRequest error, trying fetch method...');
            tryFetchMethod();
        };

        xhr.ontimeout = function() {
            console.error('XMLHttpRequest timeout, trying fetch method...');
            tryFetchMethod();
        };

        xhr.timeout = 30000; // 30 second timeout
        xhr.send(params.toString());

        // Fallback function using fetch
        function tryFetchMethod() {
        fetch(scriptURL, {
            method: 'POST',
                mode: 'no-cors',
                headers: {
                    'Content-Type': 'application/x-www-form-urlencoded',
                },
                body: params.toString()
            })
            .then(() => {
                // With no-cors, we can't read response, but assume success
                showNotification(saveSuccess, 'Passenger saved successfully!');
                    resetForm();
                setTimeout(() => loadPassengers(), 1000);
            })
            .catch(error => {
                console.error('All methods failed:', error);
                Swal.fire({
                    icon: 'error',
                    title: 'Save Failed',
                    html: `
                        <p>Unable to save passenger. Please verify:</p>
                        <ol style="text-align: left; margin: 15px 0;">
                            <li>Your internet connection is working</li>
                            <li>Google Apps Script is deployed as a <strong>Web App</strong></li>
                            <li>Deployment settings: <strong>"Execute as: Me"</strong> and <strong>"Who has access: Anyone"</strong></li>
                            <li>The script URL is correct: <br><small>${scriptURL}</small></li>
                        </ol>
                        <p><strong>Tip:</strong> Try redeploying your Google Apps Script and updating the URL.</p>
                    `,
                    width: 600
                });
            })
            .finally(() => {
                savePassengerBtn.disabled = false;
                savePassengerBtn.innerHTML = '<i class="fas fa-save"></i> Save Passenger';
            });
        }
    }

    function editPassenger(index) {
        const passenger = allPassengers[index];

        // Fill form with passenger data
        pName.value = passenger.name;
        pContact.value = passenger.contact;
        pBus.value = passenger.bus;
        pTime.value = passenger.time;
        pDate.value = passenger.date;
        pSeat.value = passenger.seat;
        pPickup.value = passenger.pickup || '';
        pPayment.value = passenger.payment || 'Paid';

        // Show bus image
        showBusImage();

        // Update UI for editing mode
        editingPassengerIndex = index;
        savePassengerBtn.innerHTML = '<i class="fas fa-save"></i> Update Passenger';
        cancelEditBtn.style.display = 'inline-block';

        // Scroll to form
        document.querySelector('.passenger-form').scrollIntoView({ behavior: 'smooth' });
    }

    function deletePassenger(index) {
        const passenger = allPassengers[index];

        Swal.fire({
            title: 'Are you sure?',
            text: `Delete ${passenger.name}'s booking?`,
            icon: 'warning',
            showCancelButton: true,
            confirmButtonColor: '#d33',
            cancelButtonColor: '#3085d6',
            confirmButtonText: 'Yes, delete it!'
        }).then((result) => {
            if (result.isConfirmed) {
                // Send delete request using XMLHttpRequest (more reliable with Google Apps Script)
                const xhr = new XMLHttpRequest();
                const params = new URLSearchParams();
                params.append('action', 'delete');
                params.append('index', passenger.index);

                xhr.open('POST', scriptURL, true);
                xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');

                xhr.onload = function() {
                    if (xhr.status === 200 || xhr.status === 0) {
                        try {
                            const result = JSON.parse(xhr.responseText);
                            if (result && result.success !== false) {
                                Swal.fire('Deleted!', 'Booking has been deleted.', 'success');
                                setTimeout(() => loadPassengers(), 500);
                            } else {
                                throw new Error(result.message || 'Server returned error');
                            }
                        } catch (e) {
                            // If response is not JSON, assume success
                            Swal.fire('Deleted!', 'Booking has been deleted.', 'success');
                            setTimeout(() => loadPassengers(), 1000);
                        }
                    } else {
                        tryDeleteFetch();
                    }
                };

                xhr.onerror = function() {
                    console.error('XMLHttpRequest error, trying fetch method...');
                    tryDeleteFetch();
                };

                xhr.ontimeout = function() {
                    console.error('XMLHttpRequest timeout, trying fetch method...');
                    tryDeleteFetch();
                };

                xhr.timeout = 30000;
                xhr.send(params.toString());

                function tryDeleteFetch() {
                fetch(scriptURL, {
                    method: 'POST',
                        mode: 'no-cors',
                        headers: {
                            'Content-Type': 'application/x-www-form-urlencoded',
                        },
                        body: params.toString()
                    })
                    .then(() => {
                            Swal.fire('Deleted!', 'Booking has been deleted.', 'success');
                        setTimeout(() => loadPassengers(), 1000);
                    })
                    .catch(error => {
                        console.error('Delete failed:', error);
                        Swal.fire({
                            icon: 'error',
                            title: 'Delete Failed',
                            text: 'Failed to delete booking. Please check your internet connection and Google Apps Script deployment.'
                        });
                    });
                }
            }
        });
    }

    function cancelEdit() {
        resetForm();
    }

    function resetForm() {
        pName.value = '';
        pContact.value = '';
        pBus.value = '';
        pTime.value = '20:30';
        pDate.valueAsDate = new Date();
        pSeat.value = '';
        pPickup.value = '';
        pPayment.value = 'Paid';

        editingPassengerIndex = null;
        savePassengerBtn.innerHTML = '<i class="fas fa-save"></i> Save Passenger';
        cancelEditBtn.style.display = 'none';
        busImagePreview.style.display = 'none';

        // Hide notifications
        saveSuccess.style.display = 'none';
        saveError.style.display = 'none';
    }

    function showNotification(element, message) {
        element.textContent = message;
        element.style.display = 'block';

        setTimeout(() => {
            element.style.display = 'none';
        }, 5000);
    }

    // Initialize the page
    document.addEventListener('DOMContentLoaded', function() {
        // Set minimum date to today
        const today = new Date().toISOString().split('T')[0];
        pDate.min = today;

        // Hide notifications initially
        passengerError.style.display = 'none';
        saveSuccess.style.display = 'none';
        saveError.style.display = 'none';
    });
</script>
</body>
</html>
