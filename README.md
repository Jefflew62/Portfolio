<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jeff Liu - ROS Developer</title>
    <link href="https://fonts.googleapis.com/css2?family=DM+Sans:ital,opsz,wght@0,9..40,300;0,9..40,500;0,9..40,700;1,9..40,400&family=Instrument+Serif:ital@0;1&display=swap" rel="stylesheet">
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }

        :root {
            --bg-deep: #0b1120;
            --bg-card: #131b2e;
            --bg-card-hover: #1a2540;
            --accent: #38bdf8;
            --accent-warm: #f59e0b;
            --text-primary: #e2e8f0;
            --text-secondary: #94a3b8;
            --text-muted: #64748b;
            --border: rgba(56, 189, 248, 0.12);
            --glow: rgba(56, 189, 248, 0.15);
        }

        body {
            font-family: 'DM Sans', sans-serif;
            color: var(--text-primary);
            background: var(--bg-deep);
            line-height: 1.6;
            overflow-x: hidden;
        }

        /* ── Header ── */
        header {
            position: fixed; top: 0; left: 0; right: 0; z-index: 1000;
            background: rgba(11, 17, 32, 0.85);
            backdrop-filter: blur(16px);
            border-bottom: 1px solid var(--border);
        }
        nav {
            max-width: 1200px; margin: 0 auto;
            display: flex; justify-content: space-between; align-items: center;
            padding: 1rem 2rem;
        }
        .logo {
            font-family: 'Instrument Serif', serif;
            font-size: 1.6rem; color: var(--accent); letter-spacing: 0.02em;
        }
        .nav-links { display: flex; list-style: none; gap: 2rem; }
        .nav-links a {
            text-decoration: none; color: var(--text-secondary); font-size: 0.9rem;
            font-weight: 500; letter-spacing: 0.04em; text-transform: uppercase;
            transition: color 0.3s;
        }
        .nav-links a:hover { color: var(--accent); }

        /* ── Hero ── */
        .hero {
            min-height: 100vh; display: flex; align-items: center; justify-content: center;
            text-align: center; position: relative;
            background: radial-gradient(ellipse 80% 60% at 50% 40%, rgba(56,189,248,0.08) 0%, transparent 70%);
        }
        .hero-content { max-width: 800px; padding: 2rem; animation: fadeUp 0.8s ease-out; }
        .hero h1 {
            font-family: 'Instrument Serif', serif;
            font-size: clamp(3rem, 7vw, 5rem); font-weight: 400;
            line-height: 1.1; margin-bottom: 1rem;
            background: linear-gradient(135deg, #e2e8f0 30%, var(--accent));
            -webkit-background-clip: text; -webkit-text-fill-color: transparent;
        }
        .hero .subtitle {
            font-size: 1.15rem; color: var(--accent); font-weight: 500;
            letter-spacing: 0.08em; text-transform: uppercase; margin-bottom: 0.75rem;
        }
        .hero .tagline { font-size: 1.05rem; color: var(--text-secondary); margin-bottom: 2.5rem; max-width: 520px; margin-left: auto; margin-right: auto; }
        .cta-button {
            display: inline-block; padding: 14px 36px; border-radius: 6px;
            background: var(--accent); color: var(--bg-deep); font-weight: 700;
            text-decoration: none; font-size: 0.95rem; letter-spacing: 0.03em;
            transition: transform 0.25s, box-shadow 0.25s;
        }
        .cta-button:hover { transform: translateY(-2px); box-shadow: 0 8px 30px var(--glow); }

        /* ── Sections ── */
        .container { max-width: 1200px; margin: 0 auto; padding: 0 2rem; }
        .section { padding: 100px 0; }
        .section-title {
            font-family: 'Instrument Serif', serif;
            font-size: 2.6rem; font-weight: 400; margin-bottom: 1rem; text-align: center;
        }
        .section-subtitle {
            text-align: center; color: var(--text-secondary); margin-bottom: 3.5rem;
            font-size: 1rem;
        }

        /* ── About ── */
        .about-grid {
            display: grid; grid-template-columns: 300px 1fr; gap: 4rem; align-items: start;
        }
        .profile-img-wrap {
            position: relative; border-radius: 16px; overflow: hidden;
            box-shadow: 0 20px 60px rgba(0,0,0,0.4);
        }
        .profile-img-wrap::after {
            content: ''; position: absolute; inset: 0;
            border: 1px solid var(--border); border-radius: 16px; pointer-events: none;
        }
        .profile-img { width: 100%; display: block; border-radius: 16px; }
        .about-text { font-size: 1.05rem; color: var(--text-secondary); line-height: 1.85; }
        .about-text p { margin-bottom: 1.25rem; }

        /* ── Skills ── */
        .skills-section { background: var(--bg-card); border-top: 1px solid var(--border); border-bottom: 1px solid var(--border); }
        .skills-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
            gap: 1.5rem;
        }
        .skill-card {
            background: var(--bg-deep); border: 1px solid var(--border); border-radius: 14px;
            padding: 2rem; transition: border-color 0.3s, box-shadow 0.3s;
        }
        .skill-card:hover { border-color: var(--accent); box-shadow: 0 0 30px var(--glow); }
        .skill-card h3 {
            font-family: 'Instrument Serif', serif;
            font-size: 1.35rem; margin-bottom: 1.25rem; color: var(--accent);
        }
        .skill-list { list-style: none; }
        .skill-list li {
            padding: 0.4rem 0; color: var(--text-secondary); font-size: 0.95rem;
            border-bottom: 1px solid rgba(255,255,255,0.04);
        }
        .skill-list li:last-child { border-bottom: none; }

        /* ── Projects ── */
        .projects-grid {
            display: grid; grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
            gap: 1.5rem;
        }
        .project-card {
            background: var(--bg-card); border: 1px solid var(--border); border-radius: 14px;
            overflow: hidden; cursor: pointer;
            transition: transform 0.3s, border-color 0.3s, box-shadow 0.3s;
        }
        .project-card:hover {
            transform: translateY(-4px); border-color: var(--accent);
            box-shadow: 0 12px 40px rgba(0,0,0,0.3);
        }
        .project-icon {
            height: 160px; display: flex; align-items: center; justify-content: center;
            font-size: 3.5rem;
            background: linear-gradient(135deg, rgba(56,189,248,0.08), rgba(245,158,11,0.06));
        }
        .project-content { padding: 1.5rem; }
        .project-title { font-size: 1.15rem; font-weight: 700; margin-bottom: 0.5rem; }
        .project-description { color: var(--text-secondary); font-size: 0.95rem; margin-bottom: 1rem; }
        .tech-stack { display: flex; flex-wrap: wrap; gap: 0.4rem; margin-bottom: 1rem; }
        .tech-tag {
            background: rgba(56,189,248,0.1); color: var(--accent); border: 1px solid rgba(56,189,248,0.2);
            padding: 0.2rem 0.65rem; border-radius: 4px; font-size: 0.8rem; font-weight: 500;
        }
        .view-details {
            display: inline-flex; align-items: center; gap: 0.4rem;
            color: var(--accent); font-size: 0.9rem; font-weight: 500;
        }
        .view-details svg { transition: transform 0.3s; }
        .project-card:hover .view-details svg { transform: translateX(4px); }

        /* ── Modal ── */
        .modal-overlay {
            position: fixed; inset: 0; z-index: 2000;
            background: rgba(0,0,0,0.75); backdrop-filter: blur(8px);
            display: none; align-items: center; justify-content: center;
            padding: 2rem; opacity: 0; transition: opacity 0.3s;
        }
        .modal-overlay.active { display: flex; opacity: 1; }
        .modal {
            background: var(--bg-card); border: 1px solid var(--border); border-radius: 16px;
            max-width: 720px; width: 100%; max-height: 85vh; overflow-y: auto;
            transform: translateY(20px); transition: transform 0.3s;
            box-shadow: 0 30px 80px rgba(0,0,0,0.5);
        }
        .modal-overlay.active .modal { transform: translateY(0); }
        .modal-header {
            display: flex; align-items: flex-start; justify-content: space-between;
            padding: 2rem 2rem 1rem;
        }
        .modal-header h2 { font-family: 'Instrument Serif', serif; font-size: 1.8rem; }
        .modal-close {
            background: none; border: none; color: var(--text-muted); font-size: 1.5rem;
            cursor: pointer; padding: 0.25rem 0.5rem; border-radius: 6px;
            transition: color 0.2s, background 0.2s;
        }
        .modal-close:hover { color: var(--text-primary); background: rgba(255,255,255,0.05); }
        .modal-body { padding: 0 2rem 2rem; }
        .modal-body p { color: var(--text-secondary); line-height: 1.8; margin-bottom: 1rem; font-size: 0.98rem; }
        .modal-body h3 { color: var(--accent); font-size: 1rem; text-transform: uppercase; letter-spacing: 0.06em; margin: 1.5rem 0 0.75rem; }
        .modal-body ul { list-style: none; padding: 0; }
        .modal-body ul li { padding: 0.4rem 0; color: var(--text-secondary); font-size: 0.95rem; padding-left: 1.2rem; position: relative; }
        .modal-body ul li::before { content: '→'; position: absolute; left: 0; color: var(--accent); }
        .modal-icon { font-size: 3rem; margin-bottom: 0.5rem; display: block; }

        /* ── Contact ── */
        .contact-section {
            background: var(--bg-card); border-top: 1px solid var(--border);
        }
        .contact-form { max-width: 560px; margin: 0 auto; }
        .form-group { margin-bottom: 1.25rem; }
        .form-group label { display: block; margin-bottom: 0.4rem; font-size: 0.9rem; color: var(--text-secondary); font-weight: 500; }
        .form-group input, .form-group textarea {
            width: 100%; padding: 12px 14px; border-radius: 8px; font-size: 1rem;
            background: var(--bg-deep); border: 1px solid var(--border); color: var(--text-primary);
            font-family: inherit; transition: border-color 0.3s;
        }
        .form-group input:focus, .form-group textarea:focus { outline: none; border-color: var(--accent); }
        .form-group textarea { height: 120px; resize: vertical; }
        .submit-btn {
            background: var(--accent); color: var(--bg-deep); padding: 13px 32px;
            border: none; border-radius: 6px; font-size: 1rem; font-weight: 700;
            cursor: pointer; transition: transform 0.25s, box-shadow 0.25s;
        }
        .submit-btn:hover { transform: translateY(-2px); box-shadow: 0 8px 30px var(--glow); }

        /* ── Footer ── */
        footer { text-align: center; padding: 2.5rem; color: var(--text-muted); font-size: 0.9rem; border-top: 1px solid var(--border); }

        /* ── Animations ── */
        @keyframes fadeUp { from { opacity: 0; transform: translateY(24px); } to { opacity: 1; transform: translateY(0); } }

        /* ── Responsive ── */
        @media (max-width: 768px) {
            .nav-links { display: none; }
            .about-grid { grid-template-columns: 1fr; text-align: center; }
            .profile-img-wrap { max-width: 260px; margin: 0 auto; }
            .projects-grid { grid-template-columns: 1fr; }
            .modal { margin: 1rem; }
        }
    </style>
</head>
<body>
    <header>
        <nav>
            <div class="logo">Jeff Liu</div>
            <ul class="nav-links">
                <li><a href="#home">Home</a></li>
                <li><a href="#about">About</a></li>
                <li><a href="#skills">Skills</a></li>
                <li><a href="#projects">Projects</a></li>
                <li><a href="#contact">Contact</a></li>
            </ul>
        </nav>
    </header>

    <section id="home" class="hero">
        <div class="hero-content">
            <p class="subtitle">ROS Developer &amp; Robotics Systems Engineer</p>
            <h1>Jeff Liu</h1>
            <p class="tagline">Bringing autonomous systems to life with cutting-edge robotics solutions</p>
            <a href="#contact" class="cta-button">Let's Build Something Amazing</a>
        </div>
    </section>

    <section id="about" class="section">
        <div class="container">
            <h2 class="section-title">About Me</h2>
            <div class="section-subtitle">Robotics student, engineer, and WorldSkills medalist</div>
            <div class="about-grid">
                <div class="profile-img-wrap">
                    <img src="data:image/jpeg;base64,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" alt="Jeff Liu" class="profile-img">
                </div>
                <div class="about-text">
                    <p>I'm a passionate robotics systems engineering student at Singapore Institute of Technology with hands-on experience in ROS development and factory automation. Currently pursuing my degree in Robotics Systems while building expertise in C++, Python, and ROS1.</p>
                    <p>My background spans from electrical engineering and mechatronics to industrial automation, with valuable experience at Mitsubishi Electronics working on factory automation products and IIoT solutions. I've also served as an Assistant Master Technician Trainer in the Singapore Army Forces, where I honed my leadership and technical maintenance skills.</p>
                    <p>As a WorldSkills medalist in Information Network Cabling, I bring precision and excellence to every project. I'm passionate about bridging the gap between traditional engineering and cutting-edge robotics technology.</p>
                </div>
            </div>
        </div>
    </section>

    <section id="skills" class="section skills-section">
        <div class="container">
            <h2 class="section-title">Technical Skills</h2>
            <div class="section-subtitle">A blend of software, hardware, and systems engineering</div>
            <div class="skills-grid">
                <div class="skill-card">
                    <h3>ROS &amp; Robotics</h3>
                    <ul class="skill-list">
                        <li>ROS 1 Development</li>
                        <li>Robot Automation Systems</li>
                        <li>Robotics Systems Engineering</li>
                        <li>Industrial Automation</li>
                        <li>IIoT Solutions</li>
                    </ul>
                </div>
                <div class="skill-card">
                    <h3>Programming</h3>
                    <ul class="skill-list">
                        <li>Python (Experienced)</li>
                        <li>C++ (Skilled)</li>
                        <li>C Language (Skilled)</li>
                        <li>Computer Programming</li>
                        <li>Electronic Prototyping</li>
                    </ul>
                </div>
                <div class="skill-card">
                    <h3>Design &amp; Manufacturing</h3>
                    <ul class="skill-list">
                        <li>CAD Modeling (Skilled)</li>
                        <li>Electrical CAD (Skilled)</li>
                        <li>3D Printing (Experienced)</li>
                        <li>Electronic Soldering (Skilled)</li>
                        <li>Mechanical Design</li>
                    </ul>
                </div>
                <div class="skill-card">
                    <h3>Technical Skills</h3>
                    <ul class="skill-list">
                        <li>Microsoft Office (Skilled)</li>
                        <li>Information Network Cabling</li>
                        <li>Electrical Installation</li>
                        <li>Power Distribution Systems</li>
                        <li>Lab Equipment Maintenance</li>
                    </ul>
                </div>
            </div>
        </div>
    </section>

    <section id="projects" class="section">
        <div class="container">
            <h2 class="section-title">Featured Projects</h2>
            <div class="section-subtitle">Click on a project to explore the details</div>
            <div class="projects-grid">

                <div class="project-card" onclick="openModal('factory')">
                    <div class="project-icon">🏭</div>
                    <div class="project-content">
                        <h3 class="project-title">Factory Automation Solutions</h3>
                        <p class="project-description">IIoT integration and IT interfacing at Mitsubishi Electronics.</p>
                        <div class="tech-stack">
                            <span class="tech-tag">IIoT</span>
                            <span class="tech-tag">Factory Automation</span>
                            <span class="tech-tag">IT Integration</span>
                        </div>
                        <span class="view-details">View details <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg></span>
                    </div>
                </div>

                <div class="project-card" onclick="openModal('ros')">
                    <div class="project-icon">🤖</div>
                    <div class="project-content">
                        <h3 class="project-title">ROS-Based Robot Automation</h3>
                        <p class="project-description">Autonomous robot control and navigation using ROS1, C++, and Python.</p>
                        <div class="tech-stack">
                            <span class="tech-tag">ROS 1</span>
                            <span class="tech-tag">Python</span>
                            <span class="tech-tag">C++</span>
                            <span class="tech-tag">Automation</span>
                        </div>
                        <span class="view-details">View details <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg></span>
                    </div>
                </div>

                <div class="project-card" onclick="openModal('worldskills')">
                    <div class="project-icon">🔌</div>
                    <div class="project-content">
                        <h3 class="project-title">WorldSkills Network Cabling</h3>
                        <p class="project-description">Award-winning precision network cabling at international competitions.</p>
                        <div class="tech-stack">
                            <span class="tech-tag">Network Cabling</span>
                            <span class="tech-tag">Electrical Systems</span>
                            <span class="tech-tag">Competition</span>
                        </div>
                        <span class="view-details">View details <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg></span>
                    </div>
                </div>

                <div class="project-card" onclick="openModal('prototyping')">
                    <div class="project-icon">⚙️</div>
                    <div class="project-content">
                        <h3 class="project-title">Electronic Prototyping Systems</h3>
                        <p class="project-description">Advanced prototyping with CAD, 3D printing, and electronic design.</p>
                        <div class="tech-stack">
                            <span class="tech-tag">CAD</span>
                            <span class="tech-tag">3D Printing</span>
                            <span class="tech-tag">Soldering</span>
                        </div>
                        <span class="view-details">View details <svg width="16" height="16" viewBox="0 0 16 16" fill="none"><path d="M3 8h10M9 4l4 4-4 4" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg></span>
                    </div>
                </div>

            </div>
        </div>
    </section>

    <!-- Project Modals -->
    <div class="modal-overlay" id="modal-factory">
        <div class="modal">
            <div class="modal-header">
                <h2>🏭 Factory Automation Solutions</h2>
                <button class="modal-close" onclick="closeModal('factory')">&times;</button>
            </div>
            <div class="modal-body">
                <p>Developed expertise in factory automation products and engineering software during internship at Mitsubishi Electronics, focusing on Industrial Internet of Things (IIoT) integration and IT interfacing.</p>
                <h3>Key Contributions</h3>
                <ul>
                    <li>Gained hands-on experience with Mitsubishi's factory automation product line, including PLCs, HMIs, and servo systems</li>
                    <li>Worked on IIoT integration projects connecting shop-floor equipment to enterprise IT systems</li>
                    <li>Supported engineering software deployment and configuration for automation solutions</li>
                    <li>Collaborated with cross-functional teams on IT interfacing and data acquisition projects</li>
                </ul>
                <h3>Technologies Used</h3>
                <div class="tech-stack" style="margin-top:0.5rem;">
                    <span class="tech-tag">IIoT</span>
                    <span class="tech-tag">Factory Automation</span>
                    <span class="tech-tag">Engineering Software</span>
                    <span class="tech-tag">IT Integration</span>
                    <span class="tech-tag">PLCs</span>
                    <span class="tech-tag">HMIs</span>
                </div>
                <h3>Outcome</h3>
                <p>Built a strong foundation in industrial automation that bridges the gap between traditional manufacturing and smart factory concepts, directly informing current robotics studies.</p>
            </div>
        </div>
    </div>

    <div class="modal-overlay" id="modal-ros">
        <div class="modal">
            <div class="modal-header">
                <h2>🤖 ROS-Based Robot Automation</h2>
                <button class="modal-close" onclick="closeModal('ros')">&times;</button>
            </div>
            <div class="modal-body">
                <p>Currently developing ROS1-based robot automation systems as part of the Robotics Systems degree program at SIT, integrating C++ and Python programming for autonomous robot control and navigation.</p>
                <h3>Key Contributions</h3>
                <ul>
                    <li>Developing ROS1 nodes for sensor data processing and robot actuation</li>
                    <li>Implementing autonomous navigation algorithms using Python and C++</li>
                    <li>Integrating hardware sensors (LiDAR, IMU, cameras) with ROS middleware</li>
                    <li>Building custom robot control pipelines for task automation</li>
                </ul>
                <h3>Technologies Used</h3>
                <div class="tech-stack" style="margin-top:0.5rem;">
                    <span class="tech-tag">ROS 1</span>
                    <span class="tech-tag">Python</span>
                    <span class="tech-tag">C++</span>
                    <span class="tech-tag">Robot Control</span>
                    <span class="tech-tag">Automation</span>
                    <span class="tech-tag">Linux</span>
                </div>
                <h3>Outcome</h3>
                <p>Ongoing academic project building real-world competency in autonomous systems development and robotic software architecture.</p>
            </div>
        </div>
    </div>

    <div class="modal-overlay" id="modal-worldskills">
        <div class="modal">
            <div class="modal-header">
                <h2>🔌 WorldSkills Network Cabling</h2>
                <button class="modal-close" onclick="closeModal('worldskills')">&times;</button>
            </div>
            <div class="modal-body">
                <p>Designed and implemented precision information network cabling systems that earned Silver Medal at WorldSkills Singapore and Medal of Excellence at WorldSkills ASEAN competitions.</p>
                <h3>Key Achievements</h3>
                <ul>
                    <li>Silver Medal — WorldSkills Singapore, Information Network Cabling</li>
                    <li>Medal of Excellence — WorldSkills ASEAN</li>
                    <li>Demonstrated competition-level precision in copper and fibre optic cabling</li>
                    <li>Completed complex cabling installations under strict time constraints and quality standards</li>
                </ul>
                <h3>Technologies Used</h3>
                <div class="tech-stack" style="margin-top:0.5rem;">
                    <span class="tech-tag">Network Cabling</span>
                    <span class="tech-tag">Fibre Optics</span>
                    <span class="tech-tag">Electrical Systems</span>
                    <span class="tech-tag">Precision Work</span>
                    <span class="tech-tag">Competition Level</span>
                </div>
                <h3>Outcome</h3>
                <p>Internationally recognised skill set in network infrastructure, reflecting the same attention to detail and systematic approach now applied to robotics engineering.</p>
            </div>
        </div>
    </div>

    <div class="modal-overlay" id="modal-prototyping">
        <div class="modal">
            <div class="modal-header">
                <h2>⚙️ Electronic Prototyping Systems</h2>
                <button class="modal-close" onclick="closeModal('prototyping')">&times;</button>
            </div>
            <div class="modal-body">
                <p>Created advanced electronic prototyping solutions using CAD modeling, 3D printing, and electronic soldering techniques, achieving distinction-level performance in academic projects.</p>
                <h3>Key Contributions</h3>
                <ul>
                    <li>Designed custom PCB layouts and enclosures using CAD software</li>
                    <li>Rapid-prototyped mechanical components with FDM and resin 3D printing</li>
                    <li>Assembled and soldered SMD and through-hole electronic circuits</li>
                    <li>Iterated designs through multiple prototype cycles based on testing feedback</li>
                </ul>
                <h3>Technologies Used</h3>
                <div class="tech-stack" style="margin-top:0.5rem;">
                    <span class="tech-tag">CAD Modeling</span>
                    <span class="tech-tag">3D Printing</span>
                    <span class="tech-tag">Electronic Design</span>
                    <span class="tech-tag">Prototyping</span>
                    <span class="tech-tag">Soldering</span>
                    <span class="tech-tag">PCB Layout</span>
                </div>
                <h3>Outcome</h3>
                <p>Distinction-level academic results and a robust prototyping workflow that accelerates idea-to-hardware timelines for robotics projects.</p>
            </div>
        </div>
    </div>

    <section id="contact" class="section contact-section">
        <div class="container">
            <h2 class="section-title">Let's Connect</h2>
            <div class="section-subtitle">Ready to bring your robotics vision to life? Let's discuss your project.</div>
            <div class="contact-form">
                <form id="contactForm">
                    <div class="form-group">
                        <label for="name">Name</label>
                        <input type="text" id="name" name="name" required>
                    </div>
                    <div class="form-group">
                        <label for="email">Email</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                    <div class="form-group">
                        <label for="project">Project Type</label>
                        <input type="text" id="project" name="project" placeholder="e.g., Autonomous Navigation, Robotic Arm">
                    </div>
                    <div class="form-group">
                        <label for="message">Message</label>
                        <textarea id="message" name="message" placeholder="Tell me about your robotics project..." required></textarea>
                    </div>
                    <button type="submit" class="submit-btn">Send Message</button>
                </form>
            </div>
        </div>
    </section>

    <footer>
        <p>&copy; 2025 Jeff Liu — ROS Developer. Building the future, one robot at a time.</p>
    </footer>

    <script>
        // Smooth scrolling
        document.querySelectorAll('a[href^="#"]').forEach(a => {
            a.addEventListener('click', e => {
                e.preventDefault();
                document.querySelector(a.getAttribute('href'))?.scrollIntoView({ behavior: 'smooth' });
            });
        });

        // Form
        document.getElementById('contactForm').addEventListener('submit', e => {
            e.preventDefault();
            alert("Thank you for your message! I'll get back to you soon.");
            e.target.reset();
        });

        // Modal
        function openModal(id) {
            const overlay = document.getElementById('modal-' + id);
            overlay.style.display = 'flex';
            requestAnimationFrame(() => overlay.classList.add('active'));
            document.body.style.overflow = 'hidden';
        }
        function closeModal(id) {
            const overlay = document.getElementById('modal-' + id);
            overlay.classList.remove('active');
            setTimeout(() => { overlay.style.display = 'none'; }, 300);
            document.body.style.overflow = '';
        }
        // Close on overlay click
        document.querySelectorAll('.modal-overlay').forEach(overlay => {
            overlay.addEventListener('click', e => {
                if (e.target === overlay) {
                    const id = overlay.id.replace('modal-', '');
                    closeModal(id);
                }
            });
        });
        // Close on Escape
        document.addEventListener('keydown', e => {
            if (e.key === 'Escape') {
                document.querySelectorAll('.modal-overlay.active').forEach(overlay => {
                    const id = overlay.id.replace('modal-', '');
                    closeModal(id);
                });
            }
        });

        // Scroll animations
        const observer = new IntersectionObserver(entries => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.style.opacity = '1';
                    entry.target.style.transform = 'translateY(0)';
                }
            });
        }, { threshold: 0.1 });
        document.querySelectorAll('.skill-card, .project-card').forEach(el => {
            el.style.opacity = '0';
            el.style.transform = 'translateY(20px)';
            el.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
            observer.observe(el);
        });
    </script>
</body>
</html>
