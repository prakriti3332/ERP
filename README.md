<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student ERP System</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
        }
        
        .container {
            display: flex;
            min-height: 100vh;
        }
        
        /* Sidebar Styles */
        .sidebar {
            width: 250px;
            background: linear-gradient(135deg, #1e3c72, #2a5298);
            color: white;
            padding: 20px 0;
            box-shadow: 2px 0 5px rgba(0,0,0,0.1);
        }
        
        .logo {
            text-align: center;
            padding: 20px 0;
            border-bottom: 1px solid rgba(255,255,255,0.2);
            margin-bottom: 20px;
        }
        
        .logo h1 {
            font-size: 24px;
            font-weight: 600;
        }
        
        .menu-item {
            padding: 15px 25px;
            display: flex;
            align-items: center;
            cursor: pointer;
            transition: all 0.3s;
        }
        
        .menu-item:hover, .menu-item.active {
            background-color: rgba(255,255,255,0.1);
            border-left: 4px solid #4CAF50;
        }
        
        .menu-item i {
            margin-right: 10px;
            font-size: 18px;
        }
        
        /* Main Content Styles */
        .main-content {
            flex: 1;
            padding: 20px;
            overflow-y: auto;
        }
        
        .header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 1px solid #e0e0e0;
        }
        
        .header h2 {
            font-weight: 600;
            color: #2c3e50;
        }
        
        .user-info {
            display: flex;
            align-items: center;
        }
        
        .user-info img {
            width: 40px;
            height: 40px;
            border-radius: 50%;
            margin-right: 10px;
        }
        
        /* Dashboard Cards */
        .dashboard-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }
        
        .card {
            background: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
        }
        
        .stat-card {
            text-align: center;
        }
        
        .stat-card .number {
            font-size: 32px;
            font-weight: 700;
            color: #2c3e50;
            margin: 10px 0;
        }
        
        .stat-card .label {
            color: #7f8c8d;
            font-size: 14px;
        }
        
        .stat-card i {
            font-size: 24px;
            padding: 15px;
            border-radius: 50%;
            margin-bottom: 10px;
        }
        
        .card-1 i { background: #e3f2fd; color: #1565C0; }
        .card-2 i { background: #e8f5e9; color: #2E7D32; }
        .card-3 i { background: #fff3e0; color: #EF6C00; }
        .card-4 i { background: #fbe9e7; color: #D84315; }
        
        /* Table Styles */
        .table-container {
            background: white;
            border-radius: 10px;
            padding: 20px;
            box-shadow: 0 4px 8px rgba(0,0,0,0.1);
            margin-bottom: 30px;
            overflow-x: auto;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th, td {
            padding: 15px;
            text-align: left;
            border-bottom: 1px solid #e0e0e0;
        }
        
        th {
            background-color: #f5f7fa;
            font-weight: 600;
            color: #2c3e50;
        }
        
        tr:hover {
            background-color: #f9f9f9;
        }
        
        .status {
            padding: 5px 10px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 500;
        }
        
        .present {
            background: #e8f5e9;
            color: #2E7D32;
        }
        
        .warning {
            background: #fff3e0;
            color: #EF6C00;
        }
        
        .danger {
            background: #ffebee;
            color: #D32F2F;
        }
        
        /* Alert Styles */
        .alert {
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
        }
        
        .alert-warning {
            background: #fff3e0;
            color: #EF6C00;
            border-left: 4px solid #EF6C00;
        }
        
        .alert-danger {
            background: #ffebee;
            color: #D32F2F;
            border-left: 4px solid #D32F2F;
        }
        
        .alert i {
            margin-right: 10px;
            font-size: 20px;
        }
        
        /* Form Styles */
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: #2c3e50;
        }
        
        input, select {
            width: 100%;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 6px;
            font-size: 16px;
        }
        
        button {
            background: #2a5298;
            color: white;
            border: none;
            padding: 12px 20px;
            border-radius: 6px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 500;
            transition: background 0.3s;
        }
        
        button:hover {
            background: #1e3c72;
        }
        
        .btn-secondary {
            background: #7f8c8d;
        }
        
        .btn-secondary:hover {
            background: #636e70;
        }
        
        .btn-danger {
            background: #D32F2F;
        }
        
        .btn-danger:hover {
            background: #b71c1c;
        }
        
        /* Modal Styles */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            z-index: 1000;
            justify-content: center;
            align-items: center;
        }
        
        .modal-content {
            background: white;
            padding: 30px;
            border-radius: 10px;
            width: 400px;
            max-width: 90%;
            box-shadow: 0 5px 15px rgba(0,0,0,0.3);
        }
        
        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 1px solid #e0e0e0;
        }
        
        .modal-header h3 {
            color: #2c3e50;
        }
        
        .close {
            font-size: 24px;
            cursor: pointer;
            color: #7f8c8d;
        }
        
        /* Responsive Design */
        @media (max-width: 768px) {
            .container {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
                padding: 10px 0;
            }
            
            .dashboard-cards {
                grid-template-columns: 1fr;
            }
        }
        
        /* Action buttons */
        .action-buttons {
            display: flex;
            gap: 10px;
        }
        
        .action-btn {
            padding: 8px 12px;
            font-size: 14px;
        }
        
        /* Certificate preview */
        .certificate-preview {
            border: 2px dashed #ccc;
            padding: 20px;
            margin-top: 20px;
            text-align: center;
            background: #f9f9f9;
            border-radius: 8px;
        }
        
        .certificate-content {
            padding: 30px;
            background: white;
            border: 1px solid #ddd;
            margin-top: 20px;
        }
    </style>
</head>
<body>
    <div class="container">
        <!-- Sidebar -->
        <div class="sidebar">
            <div class="logo">
                <h1><i class="fas fa-graduation-cap"></i> Student ERP</h1>
            </div>
            <div class="menu-item active">
                <i class="fas fa-home"></i>
                <span>Dashboard</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-user-graduate"></i>
                <span>Students</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-chalkboard-teacher"></i>
                <span>Attendance</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-money-bill-wave"></i>
                <span>Fee Management</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-book"></i>
                <span>Subjects</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-bell"></i>
                <span>Notifications</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-exclamation-triangle"></i>
                <span>Detention List</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-certificate"></i>
                <span>Certificates</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-id-card"></i>
                <span>Admit Cards</span>
            </div>
            <div class="menu-item">
                <i class="fas fa-cog"></i>
                <span>Settings</span>
            </div>
        </div>
        
        <!-- Main Content -->
        <div class="main-content">
            <div class="header">
                <h2>Student Dashboard</h2>
                <div class="user-info">
                    <img src="https://ui-avatars.com/api/?name=Admin+User&background=0D8ABC&color=fff" alt="Admin">
                    <span>Admin User</span>
                </div>
            </div>
            
            <!-- Alert Section -->
            <div class="alert alert-warning">
                <i class="fas fa-exclamation-circle"></i>
                <span>3 students have attendance below 75%. Notifications have been sent.</span>
            </div>
            
            <!-- Dashboard Cards -->
            <div class="dashboard-cards">
                <div class="card stat-card card-1">
                    <i class="fas fa-users"></i>
                    <div class="number">125</div>
                    <div class="label">Total Students</div>
                </div>
                <div class="card stat-card card-2">
                    <i class="fas fa-check-circle"></i>
                    <div class="number">87%</div>
                    <div class="label">Average Attendance</div>
                </div>
                <div class="card stat-card card-3">
                    <i class="fas fa-money-bill"></i>
                    <div class="number">₹82,500</div>
                    <div class="label">Total Fees Collected</div>
                </div>
                <div class="card stat-card card-4">
                    <i class="fas fa-exclamation-triangle"></i>
                    <div class="number">5</div>
                    <div class="label">Pending Detentions</div>
                </div>
            </div>
            
            <!-- Student List -->
            <div class="table-container">
                <h3>Student Attendance Summary</h3>
                <table>
                    <thead>
                        <tr>
                            <th>Student ID</th>
                            <th>Name</th>
                            <th>Class</th>
                            <th>Attendance %</th>
                            <th>Fees Due</th>
                            <th>Status</th>
                            <th>Actions</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>S001</td>
                            <td>Rahul Sharma</td>
                            <td>10-A</td>
                            <td>82%</td>
                            <td>₹0</td>
                            <td><span class="status present">Good</span></td>
                            <td class="action-buttons">
                                <button class="action-btn btn-secondary" onclick="generateCertificate('S001')">
                                    <i class="fas fa-certificate"></i>
                                </button>
                                <button class="action-btn" onclick="generateAdmitCard('S001')">
                                    <i class="fas fa-id-card"></i>
                                </button>
                            </td>
                        </tr>
                        <tr>
                            <td>S002</td>
                            <td>Priya Patel</td>
                            <td>10-A</td>
                            <td>91%</td>
                            <td>₹2,500</td>
                            <td><span class="status present">Good</span></td>
                            <td class="action-buttons">
                                <button class="action-btn btn-secondary" onclick="generateCertificate('S002')">
                                    <i class="fas fa-certificate"></i>
                                </button>
                                <button class="action-btn" onclick="generateAdmitCard('S002')">
                                    <i class="fas fa-id-card"></i>
                                </button>
                            </td>
                        </tr>
                        <tr>
                            <td>S003</td>
                            <td>Amit Kumar</td>
                            <td>10-B</td>
                            <td>74%</td>
                            <td>₹0</td>
                            <td><span class="status warning">Warning</span></td>
                            <td class="action-buttons">
                                <button class="action-btn btn-secondary" onclick="generateCertificate('S003')">
                                    <i class="fas fa-certificate"></i>
                                </button>
                                <button class="action-btn" onclick="generateAdmitCard('S003')">
                                    <i class="fas fa-id-card"></i>
                                </button>
                            </td>
                        </tr>
                        <tr>
                            <td>S004</td>
                            <td>Neha Singh</td>
                            <td>10-B</td>
                            <td>68%</td>
                            <td>₹5,000</td>
                            <td><span class="status danger">Critical</span></td>
                            <td class="action-buttons">
                                <button class="action-btn btn-secondary" onclick="generateCertificate('S004')">
                                    <i class="fas fa-certificate"></i>
                                </button>
                                <button class="action-btn" onclick="generateAdmitCard('S004')">
                                    <i class="fas fa-id-card"></i>
                                </button>
                            </td>
                        </tr>
                        <tr>
                            <td>S005</td>
                            <td>Karan Malhotra</td>
                            <td>10-C</td>
                            <td>79%</td>
                            <td>₹1,500</td>
                            <td><span class="status present">Good</span></td>
                            <td class="action-buttons">
                                <button class="action-btn btn-secondary" onclick="generateCertificate('S005')">
                                    <i class="fas fa-certificate"></i>
                                </button>
                                <button class="action-btn" onclick="generateAdmitCard('S005')">
                                    <i class="fas fa-id-card"></i>
                                </button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
            
            <!-- Low Attendance Alerts -->
            <div class="table-container">
                <h3>Low Attendance Alerts</h3>
                <table>
                    <thead>
                        <tr>
                            <th>Student ID</th>
                            <th>Name</th>
                            <th>Class</th>
                            <th>Attendance %</th>
                            <th>Days Notified</th>
                            <th>Action</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>S003</td>
                            <td>Amit Kumar</td>
                            <td>10-B</td>
                            <td>74%</td>
                            <td>2 days</td>
                            <td><button>Send Reminder</button></td>
                        </tr>
                        <tr>
                            <td>S004</td>
                            <td>Neha Singh</td>
                            <td>10-B</td>
                            <td>68%</td>
                            <td>3 days</td>
                            <td><button class="btn-danger" onclick="moveToDetention('S004')">Move to Detention</button></td>
                        </tr>
                        <tr>
                            <td>S012</td>
                            <td>Sanjay Mehta</td>
                            <td>10-C</td>
                            <td>71%</td>
                            <td>1 day</td>
                            <td><button>Send Reminder</button></td>
                        </tr>
                    </tbody>
                </table>
            </div>
            
            <!-- Fee Details -->
            <div class="table-container">
                <h3>Fee Management</h3>
                <table>
                    <thead>
                        <tr>
                            <th>Student ID</th>
                            <th>Name</th>
                            <th>Total Fees</th>
                            <th>Fees Paid</th>
                            <th>Due Fees</th>
                            <th>Due Date</th>
                            <th>Status</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>S001</td>
                            <td>Rahul Sharma</td>
                            <td>₹15,000</td>
                            <td>₹15,000</td>
                            <td>₹0</td>
                            <td>15/08/2023</td>
                            <td><span class="status present">Paid</span></td>
                        </tr>
                        <tr>
                            <td>S002</td>
                            <td>Priya Patel</td>
                            <td>₹15,000</td>
                            <td>₹12,500</td>
                            <td>₹2,500</td>
                            <td>15/08/2023</td>
                            <td><span class="status warning">Partial</span></td>
                        </tr>
                        <tr>
                            <td>S004</td>
                            <td>Neha Singh</td>
                            <td>₹15,000</td>
                            <td>₹10,000</td>
                            <td>₹5,000</td>
                            <td>15/08/2023</td>
                            <td><span class="status danger">Pending</span></td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
    </div>

    <!-- Certificate Modal -->
    <div id="certificateModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Generate Certificate</h3>
                <span class="close" onclick="closeModal('certificateModal')">&times;</span>
            </div>
            <div class="form-group">
                <label for="rollNumber">Roll Number</label>
                <input type="text" id="rollNumber" placeholder="Enter roll number">
            </div>
            <div class="form-group">
                <label for="certificateType">Certificate Type</label>
                <select id="certificateType">
                    <option value="course">Course Completion</option>
                    <option value="participation">Participation</option>
                    <option value="merit">Merit</option>
                    <option value="character">Character</option>
                </select>
            </div>
            <button onclick="generateCertificatePreview()">Generate Certificate</button>
            
            <div class="certificate-preview" id="certificatePreview" style="display: none;">
                <h4>Certificate Preview</h4>
                <div class="certificate-content">
                    <h2>CERTIFICATE OF COMPLETION</h2>
                    <p>This is to certify that</p>
                    <h3 id="studentName">[Student Name]</h3>
                    <p>with Roll Number: <span id="certRollNo">[Roll Number]</span></p>
                    <p>has successfully completed the course</p>
                    <p>on <span id="completionDate">[Date]</span></p>
                </div>
                <button onclick="downloadCertificate()" style="margin-top: 15px;">
                    <i class="fas fa-download"></i> Download Certificate
                </button>
            </div>
        </div>
    </div>

    <!-- Admit Card Modal -->
    <div id="admitCardModal" class="modal">
        <div class="modal-content">
            <div class="modal-header">
                <h3>Generate Admit Card</h3>
                <span class="close" onclick="closeModal('admitCardModal')">&times;</span>
            </div>
            <div class="form-group">
                <label for="admitRollNumber">Roll Number</label>
                <input type="text" id="admitRollNumber" placeholder="Enter roll number">
            </div>
            <div class="form-group">
                <label for="examType">Exam Type</label>
                <select id="examType">
                    <option value="midterm">Mid-Term Examination</option>
                    <option value="final">Final Examination</option>
                    <option value="semester">Semester Examination</option>
                </select>
            </div>
            <button onclick="generateAdmitCardPreview()">Generate Admit Card</button>
            
            <div class="certificate-preview" id="admitCardPreview" style="display: none;">
                <h4>Admit Card Preview</h4>
                <div class="certificate-content">
                    <h2>EXAMINATION ADMIT CARD</h2>
                    <p>This is to certify that</p>
                    <h3 id="admitStudentName">[Student Name]</h3>
                    <p>with Roll Number: <span id="admitRollNo">[Roll Number]</span></p>
                    <p>is permitted to appear for the <span id="examName">[Exam Name]</span></p>
                    <p>scheduled on <span id="examDate">[Date]</span></p>
                </div>
                <button onclick="downloadAdmitCard()" style="margin-top: 15px;">
                    <i class="fas fa-download"></i> Download Admit Card
                </button>
            </div>
        </div>
    </div>

    <script>
        // Sample student data
        const students = {
            'S001': { name: 'Rahul Sharma', class: '10-A' },
            'S002': { name: 'Priya Patel', class: '10-A' },
            'S003': { name: 'Amit Kumar', class: '10-B' },
            'S004': { name: 'Neha Singh', class: '10-B' },
            'S005': { name: 'Karan Malhotra', class: '10-C' }
        };

        // JavaScript for functionality
        document.addEventListener('DOMContentLoaded', function() {
            // Highlight menu items on click
            const menuItems = document.querySelectorAll('.menu-item');
            menuItems.forEach(item => {
                item.addEventListener('click', function() {
                    menuItems.forEach(i => i.classList.remove('active'));
                    this.classList.add('active');
                });
            });
        });

        // Modal functions
        function generateCertificate(rollNo) {
            document.getElementById('rollNumber').value = rollNo;
            document.getElementById('certificatePreview').style.display = 'none';
            document.getElementById('certificateModal').style.display = 'flex';
        }

        function generateAdmitCard(rollNo) {
            document.getElementById('admitRollNumber').value = rollNo;
            document.getElementById('admitCardPreview').style.display = 'none';
            document.getElementById('admitCardModal').style.display = 'flex';
        }

        function closeModal(modalId) {
            document.getElementById(modalId).style.display = 'none';
        }

        function generateCertificatePreview() {
            const rollNo = document.getElementById('rollNumber').value;
            const certType = document.getElementById('certificateType').value;
            
            if (students[rollNo]) {
                document.getElementById('studentName').textContent = students[rollNo].name;
                document.getElementById('certRollNo').textContent = rollNo;
                document.getElementById('completionDate').textContent = new Date().toLocaleDateString();
                document.getElementById('certificatePreview').style.display = 'block';
            } else {
                alert('Student not found with this roll number!');
            }
        }

        function generateAdmitCardPreview() {
            const rollNo = document.getElementById('admitRollNumber').value;
            const examType = document.getElementById('examType').value;
            
            if (students[rollNo]) {
                document.getElementById('admitStudentName').textContent = students[rollNo].name;
                document.getElementById('admitRollNo').textContent = rollNo;
                
                // Set exam name based on type
                let examName = '';
                if (examType === 'midterm') examName = 'Mid-Term Examination';
                else if (examType === 'final') examName = 'Final Examination';
                else examName = 'Semester Examination';
                
                document.getElementById('examName').textContent = examName;
                
                // Set exam date (2 weeks from now)
                const examDate = new Date();
                examDate.setDate(examDate.getDate() + 14);
                document.getElementById('examDate').textContent = examDate.toLocaleDateString();
                
                document.getElementById('admitCardPreview').style.display = 'block';
            } else {
                alert('Student not found with this roll number!');
            }
        }

        function downloadCertificate() {
            alert('Certificate downloaded successfully!');
            closeModal('certificateModal');
        }

        function downloadAdmitCard() {
            alert('Admit card downloaded successfully!');
            closeModal('admitCardModal');
        }

        function moveToDetention(rollNo) {
            if (confirm('Are you sure you want to move this student to the detention list?')) {
                alert('Student ' + rollNo + ' has been moved to the detention list.');
                // In a real application, you would update the database here
            }
        }

        // Close modals if clicked outside
        window.onclick = function(event) {
            if (event.target.classList.contains('modal')) {
                event.target.style.display = 'none';
            }
        }
    </script>
</body>
</html>
