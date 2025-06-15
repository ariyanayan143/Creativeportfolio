<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Creative Portfolio | Professional Services</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }
        
        :root {
            --primary: #4361ee;
            --secondary: #3f37c9;
            --accent: #4895ef;
            --dark: #2b2d42;
            --light: #f8f9fa;
            --success: #4cc9f0;
            --warning: #f72585;
        }
        
        body {
            background: linear-gradient(135deg, #0f2027, #203a43, #2c5364);
            color: var(--light);
            line-height: 1.6;
            overflow-x: hidden;
        }
        
        .container {
            width: 100%;
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* Header Styles */
        header {
            background: rgba(10, 25, 47, 0.85);
            backdrop-filter: blur(10px);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
        }
        
        nav {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 20px 0;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: 700;
            color: var(--accent);
            display: flex;
            align-items: center;
        }
        
        .logo i {
            margin-right: 10px;
            color: var(--success);
        }
        
        .nav-links {
            display: flex;
            list-style: none;
        }
        
        .nav-links li {
            margin-left: 30px;
        }
        
        .nav-links a {
            text-decoration: none;
            color: var(--light);
            font-weight: 500;
            font-size: 1.1rem;
            transition: all 0.3s ease;
            position: relative;
            padding: 5px 0;
        }
        
        .nav-links a:after {
            content: '';
            position: absolute;
            width: 0;
            height: 2px;
            bottom: 0;
            left: 0;
            background: var(--accent);
            transition: width 0.3s ease;
        }
        
        .nav-links a:hover:after {
            width: 100%;
        }
        
        .nav-links a.active {
            color: var(--accent);
        }
        
        .nav-links a.active:after {
            width: 100%;
        }
        
        .page {
            display: none;
            padding: 100px 0 50px;
            min-height: 100vh;
        }
        
        .page.active {
            display: block;
            animation: fadeIn 0.5s ease;
        }
        
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }
        
        /* Home Page Styles */
        .hero {
            text-align: center;
            padding: 60px 0;
            margin-bottom: 50px;
        }
        
        .hero h1 {
            font-size: 3.5rem;
            margin-bottom: 20px;
            background: linear-gradient(90deg, var(--accent), var(--success));
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
        }
        
        .hero p {
            font-size: 1.3rem;
            max-width: 800px;
            margin: 0 auto 30px;
            color: #c0c0c0;
        }
        
        .btn {
            display: inline-block;
            background: var(--primary);
            color: white;
            padding: 12px 30px;
            border-radius: 30px;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
            border: 2px solid var(--primary);
            cursor: pointer;
            margin: 10px 5px;
        }
        
        .btn:hover {
            background: transparent;
            color: var(--primary);
            transform: translateY(-3px);
            box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
        }
        
        .btn-outline {
            background: transparent;
            color: var(--primary);
        }
        
        .btn-outline:hover {
            background: var(--primary);
            color: white;
        }
        
        .section-title {
            text-align: center;
            margin-bottom: 50px;
            font-size: 2.5rem;
            position: relative;
        }
        
        .section-title:after {
            content: '';
            position: absolute;
            width: 100px;
            height: 4px;
            background: var(--accent);
            bottom: -15px;
            left: 50%;
            transform: translateX(-50%);
            border-radius: 2px;
        }
        
        .work-description {
            background: rgba(255, 255, 255, 0.05);
            padding: 40px;
            border-radius: 15px;
            margin-bottom: 60px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .work-description p {
            font-size: 1.1rem;
            margin-bottom: 20px;
            line-height: 1.8;
        }
        
        .team-section {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 30px;
            margin-top: 50px;
        }
        
        .team-member {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            overflow: hidden;
            text-align: center;
            transition: transform 0.3s ease;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .team-member:hover {
            transform: translateY(-10px);
        }
        
        .member-img {
            height: 200px;
            overflow: hidden;
        }
        
        .member-img img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: transform 0.5s ease;
        }
        
        .team-member:hover .member-img img {
            transform: scale(1.1);
        }
        
        .member-info {
            padding: 20px;
        }
        
        .member-info h3 {
            font-size: 1.4rem;
            margin-bottom: 5px;
        }
        
        .member-info p {
            color: var(--accent);
            margin-bottom: 15px;
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 15px;
        }
        
        .social-links a {
            color: var(--light);
            font-size: 1.2rem;
            transition: color 0.3s ease;
        }
        
        .social-links a:hover {
            color: var(--accent);
        }
        
        /* Services Page Styles */
        .services-container {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }
        
        .service-card {
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 30px;
            text-align: center;
            transition: all 0.3s ease;
            border: 1px solid rgba(255, 255, 255, 0.1);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
        }
        
        .service-card:hover {
            transform: translateY(-10px);
            background: rgba(67, 97, 238, 0.1);
            border-color: var(--accent);
        }
        
        .service-icon {
            font-size: 3rem;
            color: var(--accent);
            margin-bottom: 20px;
        }
        
        .service-card h3 {
            font-size: 1.5rem;
            margin-bottom: 15px;
        }
        
        .service-card p {
            margin-bottom: 20px;
            color: #c0c0c0;
        }
        
        .price {
            font-size: 2rem;
            font-weight: 700;
            color: var(--success);
            margin: 20px 0;
        }
        
        .features {
            list-style: none;
            margin-bottom: 20px;
            text-align: left;
        }
        
        .features li {
            padding: 8px 0;
            border-bottom: 1px dashed rgba(255, 255, 255, 0.1);
        }
        
        .features li:last-child {
            border-bottom: none;
        }
        
        .features li:before {
            content: "✓";
            color: var(--success);
            margin-right: 10px;
        }
        
        /* Contact Page Styles */
        .contact-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 40px;
            margin-top: 30px;
        }
        
        .contact-info {
            background: rgba(255, 255, 255, 0.05);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .contact-info h3 {
            font-size: 1.8rem;
            margin-bottom: 20px;
            color: var(--accent);
        }
        
        .contact-details {
            margin-top: 30px;
        }
        
        .contact-item {
            display: flex;
            margin-bottom: 20px;
        }
        
        .contact-icon {
            font-size: 1.5rem;
            color: var(--accent);
            margin-right: 15px;
            min-width: 30px;
        }
        
        .contact-form {
            background: rgba(255, 255, 255, 0.05);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
        }
        
        .form-group input,
        .form-group textarea {
            width: 100%;
            padding: 12px 15px;
            background: rgba(255, 255, 255, 0.07);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 8px;
            color: white;
            font-size: 1rem;
        }
        
        .form-group textarea {
            min-height: 150px;
            resize: vertical;
        }
        
        .chat-container {
            margin-top: 50px;
            background: rgba(255, 255, 255, 0.05);
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            border: 1px solid rgba(255, 255, 255, 0.1);
        }
        
        .chat-header {
            display: flex;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .chat-icon {
            font-size: 2rem;
            color: var(--success);
            margin-right: 15px;
        }
        
        .chat-box {
            height: 300px;
            background: rgba(0, 0, 0, 0.2);
            border-radius: 10px;
            padding: 20px;
            overflow-y: auto;
            margin-bottom: 20px;
            display: flex;
            flex-direction: column;
        }
        
        .message {
            max-width: 80%;
            padding: 12px 15px;
            margin-bottom: 15px;
            border-radius: 10px;
            position: relative;
        }
        
        .received {
            align-self: flex-start;
            background: rgba(67, 97, 238, 0.3);
            border-bottom-left-radius: 0;
        }
        
        .sent {
            align-self: flex-end;
            background: rgba(76, 201, 240, 0.3);
            border-bottom-right-radius: 0;
        }
        
        .chat-input {
            display: flex;
            gap: 10px;
        }
        
        .chat-input input {
            flex: 1;
            padding: 12px 15px;
            background: rgba(255, 255, 255, 0.07);
            border: 1px solid rgba(255, 255, 255, 0.1);
            border-radius: 30px;
            color: white;
            font-size: 1rem;
        }
        
        .chat-input button {
            width: 50px;
            height: 50px;
            border-radius: 50%;
            background: var(--primary);
            color: white;
            border: none;
            cursor: pointer;
            transition: all 0.3s ease;
        }
        
        .chat-input button:hover {
            background: var(--secondary);
            transform: scale(1.05);
        }
        
        /* Footer Styles */
        footer {
            background: rgba(10, 25, 47, 0.9);
            padding: 30px 0;
            text-align: center;
            margin-top: 50px;
        }
        
        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .copyright {
            margin-top: 20px;
            font-size: 0.9rem;
            color: #aaa;
        }
        
        /* Responsive Styles */
        @media (max-width: 768px) {
            .nav-links {
                display: none;
            }
            
            .hero h1 {
                font-size: 2.5rem;
            }
            
            .contact-container {
                grid-template-columns: 1fr;
            }
            
            .team-section, .services-container {
                grid-template-columns: 1fr;
            }
        }
    </style>
</head>
<body>
    <!-- Header/Navigation -->
    <header>
        <div class="container">
            <nav>
                <div class="logo">
                    <i class="fas fa-code"></i>
                    <span>CreativePortfolio</span>
                </div>
                <ul class="nav-links">
                    <li><a href="#" class="nav-link active" data-page="home">Home</a></li>
                    <li><a href="#" class="nav-link" data-page="services">Services</a></li>
                    <li><a href="#" class="nav-link" data-page="contact">Contact</a></li>
                </ul>
            </nav>
        </div>
    </header>

    <!-- Home Page -->
    <section id="home" class="page active">
        <div class="container">
            <div class="hero">
                <h1>Creative Digital Solutions</h1>
                <p>We create stunning digital experiences that help your business grow and stand out in the competitive online world.</p>
                <a href="#" class="btn" data-page="services">Our Services</a>
                <a href="#" class="btn btn-outline" data-page="contact">Contact Us</a>
            </div>

            <h2 class="section-title">About Our Work</h2>
            <div class="work-description">
                <p>Welcome to our creative portfolio! We are a team of passionate designers and developers dedicated to creating exceptional digital experiences. With years of industry experience, we've helped businesses of all sizes achieve their online goals.</p>
                <p>Our approach combines cutting-edge technology with creative design thinking. We focus on creating user-centered solutions that not only look beautiful but also deliver measurable results. From responsive websites to complex web applications, we handle every project with the utmost attention to detail.</p>
                <p>We believe in collaboration and transparency throughout our process. By working closely with our clients, we ensure that the final product exceeds expectations and aligns perfectly with their vision and objectives.</p>
            </div>

            <h2 class="section-title">Our Team</h2>
            <div class="team-section">
                <!-- সদস্য ১ -->
                <div class="team-member">
                    <div class="member-img">
                        <!-- আপনার ইমেজ লিঙ্ক দিন -->
                        <img src="https://i.postimg.cc/1zSwf27X/1749818416002.jpg" alt="Team Member 1">
                    </div>
                    <div class="member-info">
                        <!-- আপনার তথ্য দিন -->
                        <h3>Eaminul Islam</h3>
                        <p>Team Leader</p>
                        <p>Ethical Hacking Expert Coding Master Intelligent and Technically Knowledgeable</p>
                        <div class="social-links">
                            <a href="#"><i class="fab fa-linkedin"></i></a>
                            <a href="#"><i class="fab fa-facebook"></i></a>
                            <a href="#"><i class="fab fa-twitter"></i></a>
                        </div>
                    </div>
                </div>

                <!-- সদস্য ২ -->
                <div class="team-member">
                    <div class="member-img">
                        <!-- আপনার ইমেজ লিঙ্ক দিন -->
                        <img src="https://i.postimg.cc/R0fmbbv7/1749818358917.jpg" alt="Team Member 2">
                    </div>
                    <div class="member-info">
                        <!-- আপনার তথ্য দিন -->
                        <h3>Rafsan</h3>
                        <p>Team Manager</p>
                        <p> Iconic theoretical and coding Super skills that researchers and various content holders</p>
                        <div class="social-links">
                            <a href="#"><i class="fab fa-linkedin"></i></a>
                            <a href="#"><i class="fab fa-instagram"></i></a>
                            <a href="#"><i class="fab fa-github"></i></a>
                        </div>
                    </div>
                </div>

                <!-- সদস্য ৩ -->
                <div class="team-member">
                    <div class="member-img">
                        <!-- আপনার ইমেজ লিঙ্ক দিন -->
                        <img src="https://i.postimg.cc/yx6zx1cj/1749818480521.jpg" alt="Team Member 3">
                    </div>
                    <div class="member-info">
                        <!-- আপনার তথ্য দিন -->
                        <h3>Sumon RD</h3>
                        <p>class live operator</p>
                        <p>HTML Researcher Basic Coding Generate and High Technology Develop Super Skill and Attack Knowledge High level</p>
                        <div class="social-links">
                            <a href="#"><i class="fab fa-linkedin"></i></a>
                            <a href="#"><i class="fab fa-twitter"></i></a>
                            <a href="#"><i class="fab fa-dribbble"></i></a>
                        </div>
                    </div>
                </div>

                <!-- সদস্য ৪ -->
                <div class="team-member">
                    <div class="member-img">
                        <!-- আপনার ইমেজ লিঙ্ক দিন -->
                        <img src="https://i.postimg.cc/J7KLgXC2/Photoroom-20240503-071440.png" alt="Team Member 4">
                    </div>
                    <div class="member-info">
                        <!-- আপনার তথ্য দিন -->
                        <h3>ARIYAN Khan Ayan</h3>
                        <p>Junior icon</p>
                        <p>Basic Idea End General Information provider</p>
                        <div class="social-links">
                            <a href="#"><i class="fab fa-linkedin"></i></a>
                       
