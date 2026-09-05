# aerputih.github.io
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portofolio Profesional | TEFA PPLG 5</title>
    <!-- Google Fonts -->
    <link href="https://googleapis.com" rel="stylesheet">
    <style>
        /* Pengaturan Dasar & Tema Terang Biru Profesional */
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Plus Jakarta Sans', sans-serif;
            transition: all 0.2s ease;
        }

        body {
            background-color: #f0f4f8; /* Abu-abu kebiruan terang */
            color: #1e293b; /* Teks gelap kontras */
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        /* Container Utama Gaya Dashboard */
        .dashboard-container {
            display: grid;
            grid-template-columns: 320px 1fr; /* Kolom kiri (Navigasi/Profil) & Kanan (Teks Penjelasan) */
            width: 100%;
            max-width: 1100px;
            background: #ffffff;
            border-radius: 24px;
            box-shadow: 0 15px 35px rgba(15, 23, 42, 0.08);
            border: 1px solid #e2e8f0;
            overflow: hidden;
            min-height: 680px;
        }

        /* ================= KIRI: PANEL NAVIGASI & PROFIL ================= */
        .left-panel {
            background: #f8fafc;
            border-right: 1px solid #e2e8f0;
            padding: 40px 24px;
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        /* Komponen Unggah Logo Utama */
        .logo-container {
            position: relative;
            width: 120px;
            height: 120px;
            margin-bottom: 20px;
        }

        .logo-preview {
            width: 120px;
            height: 120px;
            border-radius: 20px;
            object-fit: cover;
            border: 3px solid #2563eb; /* Biru Profesional */
            background: #e2e8f0;
        }

        .upload-label {
            position: absolute;
            bottom: -5px;
            right: -5px;
            background: #2563eb;
            color: white;
            width: 34px;
            height: 34px;
            border-radius: 50%;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 0.95rem;
            cursor: pointer;
            border: 2px solid #ffffff;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        .upload-label:hover { background: #1d4ed8; transform: scale(1.05); }
        #logo-input { display: none; }

        h1 {
            font-size: 1.8rem; /* Font agak besar untuk nama perusahaan */
            color: #0f172a;
            font-weight: 800;
            margin-bottom: 30px;
            text-align: center;
        }

        /* Menu Navigasi Sisi Kiri */
        .nav-menu {
            width: 100%;
            display: flex;
            flex-direction: column;
            gap: 10px;
        }

        .nav-item {
            width: 100%;
            padding: 14px 20px;
            background: #ffffff;
            border: 1px solid #e2e8f0;
            border-radius: 12px;
            font-size: 1rem;
            font-weight: 700;
            color: #475569;
            cursor: pointer;
            text-align: left;
            display: flex;
            align-items: center;
            gap: 12px;
            box-shadow: 0 2px 4px rgba(0,0,0,0.02);
        }

        .nav-item:hover, .nav-item.active {
            background: #2563eb;
            color: #ffffff;
            border-color: #2563eb;
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(37, 99, 235, 0.2);
        }

        /* ================= KANAN: PANEL PENJELASAN ================= */
        .right-panel {
            padding: 45px;
            background: #ffffff;
            overflow-y: auto;
            max-height: 750px;
        }

        /* Struktur Konten Teks */
        .content-section {
            display: none; /* Disembunyikan secara default, muncul lewat JS */
        }

        .content-section.active {
            display: block;
            animation: fadeIn 0.4s ease forwards;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .section-title {
            font-size: 1.6rem;
            font-weight: 800;
            color: #0f172a;
            margin-bottom: 20px;
            border-bottom: 3px solid #2563eb;
            padding-bottom: 8px;
            display: inline-block;
        }

        /* Font deskripsi perusahaan lebih kecil sesuai instruksi */
        .company-desc {
            font-size: 0.95rem; 
            line-height: 1.7;
            color: #475569;
            text-align: justify;
        }

        .text-box {
            font-size: 1.1rem;
            line-height: 1.7;
            color: #334155;
            background: #f8fafc;
            border: 1px solid #e2e8f0;
            padding: 24px;
            border-radius: 16px;
        }

        .list-style {
            list-style: none;
        }

        .list-style li {
            margin-bottom: 14px;
            padding-left: 10px;
            border-left: 4px solid #2563eb;
        }

        /* SUSUNAN GRID 15 ANGGOTA */
        .member-grid {
            display: grid;
            grid-template-columns: 1fr 1fr; /* Membagi grid kanan menjadi 2 kolom */
            gap: 14px;
            margin-top: 15px;
        }

        .member-card {
            display: flex;
            align-items: center;
            background: #ffffff;
            border: 1px solid #e2e8f0;
            border-radius: 14px;
            padding: 12px 18px;
            cursor: pointer;
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.02);
        }

        .member-card:hover {
            border-color: #2563eb;
            background: #f1f5f9;
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(37, 99, 235, 0.1);
        }

        .avatar-box {
            width: 48px;
            height: 48px;
            border-radius: 10px;
            background: linear-gradient(135deg, #3b82f6, #1d4ed8);
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 1.1rem;
            color: white;
            font-weight: 700;
            margin-right: 14px;
            flex-shrink: 0;
        }

        .m-name { font-size: 1rem; font-weight: 700; color: #0f172a; margin-bottom: 2px; }
        .m-role { font-size: 0.85rem; color: #64748b; font-weight: 600; }

        /* ================= MODAL POP-UP BIODATA ANGGOTA ================= */
        .modal {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(15, 23, 42, 0.6);
            backdrop-filter: blur(6px);
            display: flex;
            justify-content: center;
            align-items: center;
            z-index: 9999;
            opacity: 0;
            pointer-events: none;
        }

        .modal.active { opacity: 1; pointer-events: auto; }

        .modal-content {
            background: #ffffff;
            border: 1px solid #e2e8f0;
            padding: 30px;
            border-radius: 20px;
            width: 90%;
            max-width: 420px;
            text-align: center;
            box-shadow: 0 25px 50px rgba(0,0,0,0.15);
            transform: scale(0.9);
        }

        .modal.active .modal-content { transform: scale(1); }

        .modal-avatar {
            width: 80px; height: 80px;
            border-radius: 50%;
            background: #2563eb;
            margin: 0 auto 15px;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 1.8rem;
            color: white;
            font-weight: 700;
            border: 3px solid #d9e6ff;
        }

        .modal-title-name { font-size: 1.35rem; font-weight: 800; color: #0f172a; margin-bottom: 4px; }
        .modal-title-role { font-size: 0.95rem; color: #2563eb; font-weight: 600; margin-bottom: 20px; }

        .bio-info-grid {
            text-align: left;
            display: grid;
            grid-template-columns: 80px 12px 1fr;
            row-gap: 10px;
            font-size: 0.95rem;
            border-top: 1px solid #f1f5f9;
            padding-top: 15px;
        }

        .b-lbl { color: #64748b; font-weight: 600; }
        .b-cln { color: #cbd5e1; font-weight: 700; }
        .b-val { color: #334155; font-weight: 600; }
        .b-link { color: #2563eb; text-decoration: none; font-weight: 700; }
        .b-link:hover { text-decoration: underline; }

        .close-btn {
            margin-top: 25px;
            background: #2563eb;
            border: none; color: white;
            padding: 12px;
            border-radius: 10px;
            font-weight: 700;
            cursor: pointer;
            width: 100%;
        }
        .close-btn:hover { background: #1d4ed8; }
    </style>
</head>
<body>

    <div class="dashboard-container">
        <!-- ================= SEBELAH KIRI (PROFIL & MENU NAVIGASI) ================= -->
        <div class="left-panel">
            <!-- Komponen Unggah Foto Logo Utama -->
            <div class="logo-container">
