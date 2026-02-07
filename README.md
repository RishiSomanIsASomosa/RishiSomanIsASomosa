<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Rishi Rahul - GitHub Profile Card</title>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Outfit:wght@400;600;700&family=Caveat:wght@700&display=swap');

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: 'Outfit', sans-serif;
            background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #0f172a 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
            overflow: hidden;
            position: relative;
        }

        /* Animated background elements */
        body::before {
            content: '';
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: 
                radial-gradient(circle at 20% 50%, rgba(34, 197, 94, 0.05) 0%, transparent 50%),
                radial-gradient(circle at 80% 80%, rgba(59, 130, 246, 0.05) 0%, transparent 50%);
            pointer-events: none;
            z-index: 0;
        }

        .container {
            position: relative;
            z-index: 1;
        }

        .card {
            background: linear-gradient(135deg, #1e293b 0%, #334155 100%);
            border: 1px solid rgba(148, 163, 184, 0.2);
            border-radius: 20px;
            padding: 40px;
            max-width: 500px;
            width: 100%;
            backdrop-filter: blur(10px);
            box-shadow: 
                0 20px 60px rgba(0, 0, 0, 0.3),
                inset 0 1px 0 rgba(255, 255, 255, 0.1);
            animation: slideUp 0.8s cubic-bezier(0.34, 1.56, 0.64, 1);
            position: relative;
            overflow: hidden;
        }

        .card::before {
            content: '';
            position: absolute;
            top: -50%;
            right: -50%;
            width: 200%;
            height: 200%;
            background: radial-gradient(circle, rgba(34, 197, 94, 0.1) 0%, transparent 70%);
            animation: float 8s ease-in-out infinite;
            pointer-events: none;
        }

        .card-content {
            position: relative;
            z-index: 2;
        }

        .avatar-wrapper {
            position: relative;
            width: 120px;
            height: 120px;
            margin: 0 auto 25px;
            animation: bounceIn 0.8s cubic-bezier(0.34, 1.56, 0.64, 1) 0.2s both;
        }

        .avatar {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            background: linear-gradient(135deg, #22c55e, #3b82f6);
            padding: 3px;
            box-shadow: 0 0 30px rgba(34, 197, 94, 0.4);
            animation: glow 3s ease-in-out infinite;
        }

        .avatar img {
            width: 100%;
            height: 100%;
            border-radius: 50%;
            border: 3px solid #1e293b;
            object-fit: cover;
            display: block;
        }

        @keyframes glow {
            0%, 100% {
                box-shadow: 0 0 30px rgba(34, 197, 94, 0.4), 0 0 60px rgba(34, 197, 94, 0.2);
            }
            50% {
                box-shadow: 0 0 40px rgba(34, 197, 94, 0.6), 0 0 80px rgba(34, 197, 94, 0.3);
            }
        }

        @keyframes float {
            0%, 100% { transform: translate(0, 0); }
            50% { transform: translate(30px, -30px); }
        }

        .name {
            text-align: center;
            margin-bottom: 8px;
            animation: fadeInUp 0.8s ease 0.3s both;
        }

        .name h1 {
            font-size: 28px;
            font-weight: 700;
            color: #f1f5f9;
            letter-spacing: -0.5px;
            font-family: 'Space Mono', monospace;
        }

        .handle {
            text-align: center;
            font-size: 14px;
            color: #94a3b8;
            font-family: 'Space Mono', monospace;
            letter-spacing: 1px;
            margin-bottom: 20px;
            animation: fadeInUp 0.8s ease 0.4s both;
        }

        .bio {
            text-align: center;
            font-size: 14px;
            color: #cbd5e1;
            line-height: 1.6;
            margin-bottom: 25px;
            animation: fadeInUp 0.8s ease 0.5s both;
        }

        .stats {
            display: flex;
            justify-content: space-around;
            margin-bottom: 30px;
            padding-bottom: 25px;
            border-bottom: 1px solid rgba(148, 163, 184, 0.2);
            animation: fadeInUp 0.8s ease 0.6s both;
        }

        .stat {
            text-align: center;
        }

        .stat-value {
            font-size: 24px;
            font-weight: 700;
            color: #22c55e;
            font-family: 'Space Mono', monospace;
            display: block;
            margin-bottom: 4px;
        }

        .stat-label {
            font-size: 12px;
            color: #94a3b8;
            text-transform: uppercase;
            letter-spacing: 1px;
        }

        .focus {
            background: rgba(34, 197, 94, 0.1);
            border: 1px solid rgba(34, 197, 94, 0.3);
            border-radius: 12px;
            padding: 16px;
            margin-bottom: 20px;
            animation: fadeInUp 0.8s ease 0.7s both;
        }

        .focus-title {
            font-size: 12px;
            color: #22c55e;
            font-weight: 700;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 8px;
        }

        .focus-text {
            font-size: 13px;
            color: #cbd5e1;
            line-height: 1.5;
        }

        .tech-stack {
            margin-bottom: 20px;
            animation: fadeInUp 0.8s ease 0.8s both;
        }

        .tech-title {
            font-size: 12px;
            color: #94a3b8;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-bottom: 12px;
            font-weight: 700;
        }

        .tech-items {
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }

        .tech-item {
            background: rgba(59, 130, 246, 0.15);
            border: 1px solid rgba(59, 130, 246, 0.3);
            color: #93c5fd;
            padding: 6px 14px;
            border-radius: 20px;
            font-size: 12px;
            font-weight: 600;
            font-family: 'Space Mono', monospace;
            transition: all 0.3s ease;
        }

        .tech-item:hover {
            background: rgba(59, 130, 246, 0.25);
            border-color: rgba(59, 130, 246, 0.6);
            transform: translateY(-2px);
            box-shadow: 0 8px 16px rgba(59, 130, 246, 0.2);
        }

        .buttons {
            display: flex;
            gap: 12px;
            animation: fadeInUp 0.8s ease 0.9s both;
        }

        .btn {
            flex: 1;
            padding: 12px 20px;
            border: none;
            border-radius: 10px;
            font-family: 'Outfit', sans-serif;
            font-weight: 700;
            font-size: 13px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 0.5px;
            position: relative;
            overflow: hidden;
        }

        .btn-primary {
            background: linear-gradient(135deg, #22c55e, #16a34a);
            color: #0f172a;
            box-shadow: 0 10px 25px rgba(34, 197, 94, 0.3);
        }

        .btn-primary:hover {
            transform: translateY(-3px);
            box-shadow: 0 15px 35px rgba(34, 197, 94, 0.4);
        }

        .btn-secondary {
            background: rgba(59, 130, 246, 0.15);
            color: #93c5fd;
            border: 1.5px solid rgba(59, 130, 246, 0.4);
        }

        .btn-secondary:hover {
            background: rgba(59, 130, 246, 0.25);
            border-color: rgba(59, 130, 246, 0.7);
            transform: translateY(-3px);
            box-shadow: 0 10px 25px rgba(59, 130, 246, 0.2);
        }

        .btn:active {
            transform: translateY(-1px);
        }

        @keyframes slideUp {
            from {
                opacity: 0;
                transform: translateY(40px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        @keyframes bounceIn {
            from {
                opacity: 0;
                transform: scale(0.6);
            }
            to {
                opacity: 1;
                transform: scale(1);
            }
        }

        @keyframes fadeInUp {
            from {
                opacity: 0;
                transform: translateY(15px);
            }
            to {
                opacity: 1;
                transform: translateY(0);
            }
        }

        .emoji {
            display: inline-block;
            margin: 0 4px;
        }

        @media (max-width: 600px) {
            .card {
                padding: 30px 20px;
            }

            .name h1 {
                font-size: 24px;
            }

            .buttons {
                flex-direction: column;
            }

            .stats {
                gap: 15px;
            }
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="card">
            <div class="card-content">
                <div class="avatar-wrapper">
                    <div class="avatar">
                        <img src="https://avatars.githubusercontent.com/u/235717695?v=4" alt="Rishi Rahul">
                    </div>
                </div>

                <div class="name">
                    <h1>Rishi Rahul</h1>
                </div>

                <div class="handle">
                    @RishiSomanIsASomosa
                </div>

                <div class="bio">
                    <span class="emoji">👨‍💻</span> Developer | Open Source Enthusiast
                    <br>
                    <span class="emoji">🧠</span> Focused on Computer Vision & Deep Learning
                </div>

                <div class="stats">
                    <div class="stat">
                        <span class="stat-value">37</span>
                        <div class="stat-label">Repos</div>
                    </div>
                    <div class="stat">
                        <span class="stat-value">4</span>
                        <div class="stat-label">Followers</div>
                    </div>
                    <div class="stat">
                        <span class="stat-value">3</span>
                        <div class="stat-label">Following</div>
                    </div>
                </div>

                <div class="focus">
                    <div class="focus-title"><span class="emoji">🔭</span> Currently Working On</div>
                    <div class="focus-text"><strong>LoadCheck</strong> & Computer Vision projects for solar energy optimization</div>
                </div>

                <div class="tech-stack">
                    <div class="tech-title">Tech Stack</div>
                    <div class="tech-items">
                        <div class="tech-item">Python</div>
                        <div class="tech-item">OpenCV</div>
                        <div class="tech-item">JavaScript</div>
                        <div class="tech-item">ML</div>
                        <div class="tech-item">Git</div>
                    </div>
                </div>

                <div class="buttons">
                    <a href="https://github.com/RishiSomanIsASomosa" class="btn btn-primary">GitHub</a>
                    <a href="/cdn-cgi/l/email-protection#17657e647f7e65767f627b64787a767957707a767e7b3974787a" class="btn btn-secondary">Email</a>
                </div>
            <
