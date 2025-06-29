# Projeto-de-Credenciamento
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sistema Integrado de Gestão de Credenciamentos Municipais - Prefeitura de Colíder/MT</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        :root {
            --primary: #1e40af;
            --primary-dark: #1e3a8a;
            --secondary: #059669;
            --accent: #dc2626;
            --warning: #d97706;
            --success: #16a34a;
            --info: #0284c7;
            --light: #f8fafc;
            --dark: #1e293b;
            --gray-100: #f1f5f9;
            --gray-200: #e2e8f0;
            --gray-300: #cbd5e1;
            --gray-400: #94a3b8;
            --gray-500: #64748b;
            --gray-600: #475569;
            --gray-700: #334155;
            --gray-800: #1e293b;
            --gray-900: #0f172a;
            --border-radius: 8px;
            --shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1);
            --shadow-lg: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
        }

        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, var(--light) 0%, var(--gray-100) 100%);
            color: var(--gray-800);
            line-height: 1.6;
            min-height: 100vh;
        }

        .container {
            max-width: 100%;
            margin: 0 auto;
            padding: 0 15px;
        }

        /* Header */
        .header {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            padding: 15px 0;
            box-shadow: var(--shadow-lg);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 15px;
        }

        .logo {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .logo-icon {
            width: 40px;
            height: 40px;
            background: rgba(255, 255, 255, 0.2);
            border-radius: 8px;
            display: flex;
            align-items: center;
            justify-content: center;
            font-weight: bold;
            font-size: 18px;
        }

        .logo-text h1 {
            font-size: 1.25rem;
            font-weight: 700;
        }

        .logo-text p {
            font-size: 0.875rem;
            opacity: 0.9;
        }

        .user-info {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .user-badge {
            background: rgba(255, 255, 255, 0.15);
            padding: 8px 15px;
            border-radius: var(--border-radius);
            backdrop-filter: blur(10px);
        }

        /* Navigation */
        .nav-tabs {
            background: white;
            border-bottom: 2px solid var(--gray-200);
            padding: 0;
            margin: 0;
            display: flex;
            overflow-x: auto;
            scrollbar-width: none;
            -ms-overflow-style: none;
        }

        .nav-tabs::-webkit-scrollbar {
            display: none;
        }

        .nav-tab {
            background: none;
            border: none;
            padding: 15px 25px;
            cursor: pointer;
            font-weight: 500;
            color: var(--gray-600);
            border-bottom: 3px solid transparent;
            transition: all 0.3s ease;
            white-space: nowrap;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .nav-tab:hover {
            background: var(--gray-100);
            color: var(--primary);
        }

        .nav-tab.active {
            color: var(--primary);
            border-bottom-color: var(--primary);
            background: var(--gray-50);
        }

        /* Content Area */
        .content {
            padding: 25px 15px;
        }

        .tab-content {
            display: none;
            animation: fadeIn 0.3s ease-in-out;
        }

        .tab-content.active {
            display: block;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Cards */
        .card {
            background: white;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            margin-bottom: 25px;
            overflow: hidden;
            transition: all 0.3s ease;
        }

        .card:hover {
            box-shadow: var(--shadow-lg);
            transform: translateY(-2px);
        }

        .card-header {
            background: linear-gradient(135deg, var(--gray-50) 0%, var(--gray-100) 100%);
            padding: 20px 25px;
            border-bottom: 1px solid var(--gray-200);
            display: flex;
            justify-content: space-between;
            align-items: center;
            flex-wrap: wrap;
            gap: 15px;
        }

        .card-title {
            font-size: 1.125rem;
            font-weight: 600;
            color: var(--gray-800);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .card-body {
            padding: 25px;
        }

        /* Stats Cards */
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 20px;
            margin-bottom: 30px;
        }

        .stat-card {
            background: linear-gradient(135deg, var(--primary) 0%, var(--primary-dark) 100%);
            color: white;
            padding: 25px;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            position: relative;
            overflow: hidden;
        }

        .stat-card::before {
            content: '';
            position: absolute;
            top: 0;
            right: 0;
            width: 100px;
            height: 100px;
            background: rgba(255, 255, 255, 0.1);
            border-radius: 50%;
            transform: translate(30px, -30px);
        }

        .stat-card.secondary {
            background: linear-gradient(135deg, var(--secondary) 0%, #047857 100%);
        }

        .stat-card.warning {
            background: linear-gradient(135deg, var(--warning) 0%, #c2410c 100%);
        }

        .stat-card.accent {
            background: linear-gradient(135deg, var(--accent) 0%, #b91c1c 100%);
        }

        .stat-value {
            font-size: 2.5rem;
            font-weight: 700;
            margin-bottom: 5px;
        }

        .stat-label {
            opacity: 0.9;
            font-size: 0.875rem;
        }

        /* Forms */
        .form-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
        }

        .form-group {
            margin-bottom: 20px;
        }

        .form-label {
            display: block;
            margin-bottom: 8px;
            font-weight: 500;
            color: var(--gray-700);
        }

        .form-control {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid var(--gray-300);
            border-radius: var(--border-radius);
            font-size: 0.875rem;
            transition: all 0.3s ease;
            background: white;
        }

        .form-control:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(30, 64, 175, 0.1);
        }

        .form-control.is-invalid {
            border-color: var(--accent);
        }

        .form-control.is-valid {
            border-color: var(--success);
        }

        select.form-control {
            cursor: pointer;
        }

        /* Buttons */
        .btn {
            display: inline-flex;
            align-items: center;
            gap: 8px;
            padding: 10px 20px;
            border: none;
            border-radius: var(--border-radius);
            font-size: 0.875rem;
            font-weight: 500;
            cursor: pointer;
            transition: all 0.3s ease;
            text-decoration: none;
            justify-content: center;
        }

        .btn:hover {
            transform: translateY(-1px);
            box-shadow: var(--shadow);
        }

        .btn-primary {
            background: var(--primary);
            color: white;
        }

        .btn-primary:hover {
            background: var(--primary-dark);
        }

        .btn-secondary {
            background: var(--secondary);
            color: white;
        }

        .btn-secondary:hover {
            background: #047857;
        }

        .btn-outline {
            background: transparent;
            color: var(--primary);
            border: 2px solid var(--primary);
        }

        .btn-outline:hover {
            background: var(--primary);
            color: white;
        }

        .btn-sm {
            padding: 6px 12px;
            font-size: 0.75rem;
        }

        .btn-lg {
            padding: 15px 30px;
            font-size: 1rem;
        }

        /* Tables */
        .table-container {
            overflow-x: auto;
            margin-top: 20px;
        }

        .table {
            width: 100%;
            border-collapse: collapse;
            background: white;
            border-radius: var(--border-radius);
            overflow: hidden;
            box-shadow: var(--shadow);
        }

        .table th,
        .table td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid var(--gray-200);
        }

        .table th {
            background: var(--gray-100);
            font-weight: 600;
            color: var(--gray-700);
        }

        .table tbody tr:hover {
            background: var(--gray-50);
        }

        /* Status Badges */
        .badge {
            display: inline-flex;
            align-items: center;
            gap: 5px;
            padding: 4px 10px;
            border-radius: 20px;
            font-size: 0.75rem;
            font-weight: 500;
        }

        .badge-success {
            background: rgba(22, 163, 74, 0.1);
            color: var(--success);
        }

        .badge-warning {
            background: rgba(217, 119, 6, 0.1);
            color: var(--warning);
        }

        .badge-danger {
            background: rgba(220, 38, 38, 0.1);
            color: var(--accent);
        }

        .badge-info {
            background: rgba(2, 132, 199, 0.1);
            color: var(--info);
        }

        /* Progress Bars */
        .progress {
            width: 100%;
            height: 8px;
            background: var(--gray-200);
            border-radius: 4px;
            overflow: hidden;
        }

        .progress-bar {
            height: 100%;
            background: var(--primary);
            transition: width 0.3s ease;
        }

        .progress-bar.success {
            background: var(--success);
        }

        .progress-bar.warning {
            background: var(--warning);
        }

        .progress-bar.danger {
            background: var(--accent);
        }

        /* Charts Container */
        .chart-container {
            position: relative;
            height: 300px;
            margin: 20px 0;
        }

        /* Filters */
        .filters {
            background: white;
            padding: 20px;
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            margin-bottom: 25px;
        }

        .filters-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 15px;
            align-items: end;
        }

        /* Modals */
        .modal {
            display: none;
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0, 0, 0, 0.5);
            z-index: 10000;
            animation: fadeIn 0.3s ease;
        }

        .modal.active {
            display: flex;
            align-items: center;
            justify-content: center;
        }

        .modal-content {
            background: white;
            padding: 30px;
            border-radius: var(--border-radius);
            max-width: 90%;
            max-height: 90%;
            overflow-y: auto;
            box-shadow: var(--shadow-lg);
            animation: slideIn 0.3s ease;
        }

        @keyframes slideIn {
            from { transform: translateY(-50px); opacity: 0; }
            to { transform: translateY(0); opacity: 1; }
        }

        /* Alerts */
        .alert {
            padding: 15px 20px;
            border-radius: var(--border-radius);
            margin-bottom: 20px;
            border-left: 4px solid;
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .alert-success {
            background: rgba(22, 163, 74, 0.1);
            color: var(--success);
            border-color: var(--success);
        }

        .alert-warning {
            background: rgba(217, 119, 6, 0.1);
            color: var(--warning);
            border-color: var(--warning);
        }

        .alert-danger {
            background: rgba(220, 38, 38, 0.1);
            color: var(--accent);
            border-color: var(--accent);
        }

        .alert-info {
            background: rgba(2, 132, 199, 0.1);
            color: var(--info);
            border-color: var(--info);
        }

        /* Timeline */
        .timeline {
            position: relative;
            padding-left: 30px;
        }

        .timeline::before {
            content: '';
            position: absolute;
            left: 10px;
            top: 0;
            bottom: 0;
            width: 2px;
            background: var(--gray-300);
        }

        .timeline-item {
            position: relative;
            margin-bottom: 25px;
        }

        .timeline-item::before {
            content: '';
            position: absolute;
            left: -35px;
            top: 5px;
            width: 12px;
            height: 12px;
            border-radius: 50%;
            background: var(--primary);
        }

        /* Responsive Design */
        @media (max-width: 768px) {
            .header-content {
                text-align: center;
            }

            .logo-text h1 {
                font-size: 1rem;
            }

            .nav-tab {
                padding: 12px 15px;
            }

            .content {
                padding: 15px 10px;
            }

            .card-header {
                padding: 15px 20px;
            }

            .card-body {
                padding: 20px;
            }

            .stats-grid {
                grid-template-columns: 1fr;
            }

            .form-grid {
                grid-template-columns: 1fr;
            }

            .filters-grid {
                grid-template-columns: 1fr;
            }

            .stat-value {
                font-size: 2rem;
            }

            .modal-content {
                margin: 20px;
                max-width: calc(100% - 40px);
            }
        }

        @media (max-width: 480px) {
            .container {
                padding: 0 10px;
            }

            .header {
                padding: 10px 0;
            }

            .logo-text h1 {
                font-size: 0.875rem;
            }

            .logo-text p {
                font-size: 0.75rem;
            }

            .nav-tab {
                padding: 10px 12px;
                font-size: 0.875rem;
            }

            .stat-value {
                font-size: 1.75rem;
            }

            .btn {
                padding: 8px 15px;
                font-size: 0.8rem;
            }
        }

        /* Additional Utility Classes */
        .text-center { text-align: center; }
        .text-right { text-align: right; }
        .text-muted { color: var(--gray-500); }
        .text-primary { color: var(--primary); }
        .text-success { color: var(--success); }
        .text-warning { color: var(--warning); }
        .text-danger { color: var(--accent); }

        .mb-0 { margin-bottom: 0; }
        .mb-1 { margin-bottom: 0.5rem; }
        .mb-2 { margin-bottom: 1rem; }
        .mb-3 { margin-bottom: 1.5rem; }
        .mb-4 { margin-bottom: 2rem; }

        .mt-0 { margin-top: 0; }
        .mt-1 { margin-top: 0.5rem; }
        .mt-2 { margin-top: 1rem; }
        .mt-3 { margin-top: 1.5rem; }
        .mt-4 { margin-top: 2rem; }

        .d-flex { display: flex; }
        .d-block { display: block; }
        .d-none { display: none; }

        .justify-between { justify-content: space-between; }
        .justify-center { justify-content: center; }
        .align-center { align-items: center; }

        .w-100 { width: 100%; }
        .h-100 { height: 100%; }

        .rounded { border-radius: var(--border-radius); }
        .shadow { box-shadow: var(--shadow); }
        .shadow-lg { box-shadow: var(--shadow-lg); }
    </style>
</head>
<body>
    <!-- Header -->
    <header class="header">
        <div class="container">
            <div class="header-content">
                <div class="logo">
                    <div class="logo-icon">PMC</div>
                    <div class="logo-text">
                        <h1>Sistema de Gestão de Credenciamentos</h1>
                        <p>Prefeitura Municipal de Colíder - MT | Lei 14.133/2021</p>
                    </div>
                </div>
                <div class="user-info">
                    <div class="user-badge">
                        <strong>Miquéias Felipe B. Carvalho</strong><br>
                        <small>Coordenador de Credenciamento</small>
                    </div>
                </div>
            </div>
        </div>
    </header>

    <!-- Navigation -->
    <nav class="nav-tabs">
        <button class="nav-tab active" data-tab="dashboard">
            📊 Dashboard
        </button>
        <button class="nav-tab" data-tab="processos">
            📋 Pipeline de Processos
        </button>
        <button class="nav-tab" data-tab="credenciados">
            🏢 Base de Credenciados
        </button>
        <button class="nav-tab" data-tab="financeiro">
            💰 Gestão Financeira
        </button>
        <button class="nav-tab" data-tab="controle">
            🛡️ Controle e Compliance
        </button>
        <button class="nav-tab" data-tab="documentos">
            📄 Gestão Documental
        </button>
        <button class="nav-tab" data-tab="relatorios">
            📈 Business Intelligence
        </button>
        <button class="nav-tab" data-tab="configuracoes">
            ⚙️ Configurações
        </button>
    </nav>

    <!-- Content -->
    <div class="container content">
        <!-- Dashboard Tab -->
        <div id="dashboard" class="tab-content active">
            <!-- Stats Cards -->
            <div class="stats-grid">
                <div class="stat-card">
                    <div class="stat-value" id="stat-processos">24</div>
                    <div class="stat-label">Processos em Andamento</div>
                </div>
                <div class="stat-card secondary">
                    <div class="stat-value" id="stat-credenciados">187</div>
                    <div class="stat-label">Credenciados Ativos</div>
                </div>
                <div class="stat-card warning">
                    <div class="stat-value" id="stat-pendencias">8</div>
                    <div class="stat-label">Pendências Críticas</div>
                </div>
                <div class="stat-card accent">
                    <div class="stat-value">R$ 2.4M</div>
                    <div class="stat-label">Valor Total Credenciado</div>
                </div>
            </div>

            <!-- Quick Actions -->
            <div class="card">
                <div class="card-header">
                    <h3 class="card-title">🚀 Ações Rápidas</h3>
                </div>
                <div class="card-body">
                    <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px;">
                        <button class="btn btn-primary" onclick="novoProcesso()">
                            ➕ Novo Processo de Credenciamento
                        </button>
                        <button class="btn btn-secondary" onclick="novoCredenciado()">
                            🏢 Cadastrar Credenciado
                        </button>
                        <button class="btn btn-outline" onclick="gerarRelatorio()">
                            📊 Gerar Relatório
                        </button>
                        <button class="btn btn-outline" onclick="exportarDados()">
                            📤 Exportar Dados
                        </button>
                    </div>
                </div>
            </div>

            <!-- Processos Críticos -->
            <div class="card">
                <div class="card-header">
                    <h3 class="card-title">⚠️ Processos com Prazos Críticos</h3>
                    <button class="btn btn-sm btn-outline">Ver Todos</button>
                </div>
                <div class="card-body">
                    <div class="table-container">
                        <table class="table">
                            <thead>
                                <tr>
                                    <th>Objeto</th>
                                    <th>Status</th>
                                    <th>Prazo</th>
                                    <th>Responsável</th>
                                    <th>Ações</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>Serviços de Manutenção Predial</td>
                                    <td><span class="badge badge-warning">Análise Jurídica</span></td>
                                    <td class="text-danger">2 dias restantes</td>
                                    <td>João Silva</td>
                                    <td>
                                        <button class="btn btn-sm btn-primary">Acompanhar</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>Fornecimento de Material de Limpeza</td>
                                    <td><span class="badge badge-danger">Atrasado</span></td>
                                    <td class="text-danger">3 dias de atraso</td>
                                    <td>Maria Santos</td>
                                    <td>
                                        <button class="btn btn-sm btn-primary">Acompanhar</button>
                                    </td>
                                </tr>
                                <tr>
                                    <td>Serviços de Transporte Escolar</td>
                                    <td><span class="badge badge-info">ETP em Elaboração</span></td>
                                    <td class="text-warning">5 dias restantes</td>
                                    <td>Carlos Oliveira</td>
                                    <td>
                                        <button class="btn btn-sm btn-primary">Acompanhar</button>
                                    </td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>
            </div>

            <!-- Indicadores de Performance -->
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 25px;">
                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">📈 Processos por Status</h3>
                    </div>
                    <div class="card-body">
                        <div style="margin-bottom: 15px;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>ETP em Elaboração</span>
                                <span>35%</span>
                            </div>
                            <div class="progress">
                                <div class="progress-bar" style="width: 35%"></div>
                            </div>
                        </div>
                        <div style="margin-bottom: 15px;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Análise Jurídica</span>
                                <span>25%</span>
                            </div>
                            <div class="progress">
                                <div class="progress-bar warning" style="width: 25%"></div>
                            </div>
                        </div>
                        <div style="margin-bottom: 15px;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Publicação</span>
                                <span>20%</span>
                            </div>
                            <div class="progress">
                                <div class="progress-bar success" style="width: 20%"></div>
                            </div>
                        </div>
                        <div>
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Homologação</span>
                                <span>20%</span>
                            </div>
                            <div class="progress">
                                <div class="progress-bar danger" style="width: 20%"></div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="card">
                    <div class="card-header">
                        <h3 class="card-title">💰 Impacto Orçamentário</h3>
                    </div>
                    <div class="card-body">
                        <div style="margin-bottom: 20px;">
                            <div class="stat-value" style="font-size: 1.5rem; color: var(--primary);">R$ 2.432.150,00</div>
                            <div class="stat-label">Valor Total dos Credenciamentos</div>
                        </div>
                        <div style="margin-bottom: 15px;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Orçamento Utilizado</span>
                                <span>68%</span>
                            </div>
                            <div class="progress">
                                <div class="progress-bar" style="width: 68%"></div>
                            </div>
                        </div>
                        <div style="margin-bottom: 15px;">
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Reserva de Contingência</span>
                                <span>15%</span>
                            </div>
                            <div class="progress">
                                <div class="progress-bar warning" style="width: 15%"></div>
                            </div>
                        </div>
                        <div>
                            <div style="display: flex; justify-content: space-between; margin-bottom: 5px;">
                                <span>Disponível</span>
                                <span>17%</span>
                            </div>
                            <div class="progress">
                                <div class="progress-bar success" style="width: 17%"></div>
                            </div>
                        </div>
