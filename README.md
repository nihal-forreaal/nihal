<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nihal's Enhanced Portfolio</title>
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        /* General Styles */
        body {
            font-family: 'Poppins', sans-serif;
            margin: 0;
            padding: 0;
            background-color: black;
            overflow-x: hidden;
            color: #f5f5f5;
        }

        header {
            background-color: rgba(0, 0, 0, 0.8);
            color: #ffd700;
            text-align: center;
            padding: 20px 0;
            position: sticky;
            top: 0;
            z-index: 100;
            transition: background-color 0.3s ease, padding 0.3s ease;
        }

        header.shrink {
            background-color: rgba(0, 0, 0, 0.9);
            padding: 10px 0;
        }

        nav {
            text-align: center;
            margin-top: 20px;
        }

        nav a {
            color: #ff5733;
            text-decoration: none;
            margin: 0 15px;
            font-size: 18px;
            font-weight: 600;
            position: relative;
            transition: all 0.3s;
        }

        nav a:hover {
            color: #ffd700;
        }

        nav a::after {
            content: '';
            position: absolute;
            bottom: -5px;
            left: 0;
            width: 0;
            height: 2px;
            background-color: #ff5733;
            transition: width 0.3s ease;
        }

        nav a:hover::after {
            width: 100%;
        }

        section {
            padding: 60px 20px;
            text-align: center;
            opacity: 0;
            transform: translateY(50px);
            transition: opacity 0.6s ease-out, transform 0.6s ease-out;
        }

        section.visible {
            opacity: 1;
            transform: translateY(0);
        }

        section h2 {
            color: #ffd700;
            font-size: 2rem;
            margin-bottom: 20px;
        }

        section p {
            color: #e0e0e0;
            font-size: 1.1rem;
            line-height: 1.6;
        }

        .btn {
            background-color: #ff5733;
            color: white;
            padding: 10px 20px;
            font-size: 1.2rem;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            position: relative;
            overflow: hidden;
        }

        .btn::after {
            content: '';
            position: absolute;
            top: 50%;
            left: 50%;
            width: 0;
            height: 0;
            background: rgba(255, 255, 255, 0.5);
            border-radius: 50%;
            transform: translate(-50%, -50%);
            transition: width 0.5s ease, height 0.5s ease;
        }

        .btn:hover::after {
            width: 200%;
            height: 200%;
        }

        .services {
            display: flex;
            justify-content: center;
            gap: 20px;
            flex-wrap: wrap;
        }

        .service-item {
            background-color: white;
            padding: 20px;
            width: 300px;
            border-radius: 10px;
            text-align: center;
            box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
            transform: translateY(50px);
            opacity: 0;
            transition: transform 0.5s ease-out, opacity 0.5s ease-out;
        }

        .service-item.visible {
            transform: translateY(0);
            opacity: 1;
        }

        .service-item:hover {
            transform: translateY(-10px) scale(1.05);
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.2);
        }

        .service-item h3 {
            color: #333;
        }

        .service-item p {
            color: #666;
        }

        footer {
            text-align: center;
            padding: 20px;
            background: #333;
            color: #fff;
        }

        footer a {
            color: #ffd700;
            text-decoration: none;
        }

        .contact-form {
            max-width: 400px;
            margin: 0 auto;
        }

        .contact-form input,
        .contact-form textarea {
            width: 100%;
            padding: 8px;
            margin-bottom: 10px;
            border: 1px solid #ccc;
            border-radius: 4px;
            font-size: 14px;
        }

        .contact-form button {
            font-size: 14px;
            padding: 8px 16px;
        }
    </style>
</head>
<body>
    <header>
        <h1>Nihal Bio</h1>
    </header>

    <nav>
        <a href="#about">About Me</a>
        <a href="#services">Services</a>
        <a href="#contact">Contact</a>
    </nav>

    <section id="about">
        <h2>About Me</h2>
        <p>I’m a passionate After Effects editor specializing in dynamic and creative video editing!</p>
    </section>

    <section id="services">
        <h2>My Services</h2>
        <div class="services">
            <div class="service-item">
                <h3>Video Editing</h3>
                <p>High-quality editing for social media, YouTube, and more.</p>
            </div>
            <div class="service-item">
                <h3>Motion Graphics</h3>
                <p>Create dynamic animations and visuals.</p>
            </div>
            <div class="service-item">
                <h3>After Effects</h3>
                <p>Advanced compositing and animation services.</p>
            </div>
        </div>
    </section>

    <section id="contact">
        <h2>Contact Me</h2>
        <p>Please feel free to reach out with any inquiries. I’d love to hear about your project and discuss how I can help!</p>
        <form class="contact-form" action="https://formspree.io/f/movvoqvl" method="POST">
            <input type="text" name="name" placeholder="Your Name">
            <input type="email" name="email" placeholder="Your Email">
            <textarea name="message" placeholder="Your Message" rows="4"></textarea>
            <input type="text" name="budget" placeholder="Your Budget">
            <button class="btn" type="submit">Send Message</button>
        </form>
    </section>

    <footer>
        <p>© 2025 Nihal's Portfolio | <a href="#">LinkedIn</a> | <a href="#">GitHub</a></p>
    </footer>

    <script>
        // Scroll-based animations
        const sections = document.querySelectorAll('section');
        const serviceItems = document.querySelectorAll('.service-item');
        const header = document.querySelector('header');

        window.addEventListener('scroll', () => {
            const scrollPos = window.scrollY;

            // Shrink header on scroll
            if (scrollPos > 50) {
                header.classList.add('shrink');
            } else {
                header.classList.remove('shrink');
            }

            // Reveal sections and service items on scroll
            sections.forEach(section => {
                const rect = section.getBoundingClientRect();
                if (rect.top < window.innerHeight - 100) {
                    section.classList.add('visible');
                }
            });

            serviceItems.forEach(item => {
                const rect = item.getBoundingClientRect();
                if (rect.top < window.innerHeight - 100) {
                    item.classList.add('visible');
                }
            });
        });
    </script>
</body>
</html>
