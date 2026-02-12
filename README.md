
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Torn Trading Pro - Fixed & Working</title>
    <style>
        :root {
            --primary: #6366f1;
            --success: #10b981;
            --danger: #ef4444;
            --dark: #1e293b;
            --light: #f8fafc;
        }
        
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            background: linear-gradient(135deg, #1e293b 0%, #0f172a 100%);
            color: #e2e8f0;
            line-height: 1.6;
            padding: 20px;
        }
        
        .container {
            max-width: 1100px;
            margin: 0 auto;
        }
        
        header {
            text-align: center;
            padding: 25px;
            background: rgba(30, 41, 59, 0.9);
            border-radius: 15px;
            margin-bottom: 25px;
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.5);
        }
        
        h1 {
            font-size: 2.3rem;
            margin-bottom: 10px;
            background: linear-gradient(90deg, var(--primary), #8b5cf6);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
        
        .subtitle {
            color: #94a3b8;
            font-size: 1.05rem;
            margin-top: 8px;
        }
        
        .card {
            background: rgba(30, 41, 59, 0.9);
            border-radius: 15px;
            padding: 25px;
            margin-bottom: 25px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.4);
            border: 1px solid rgba(99, 102, 241, 0.3);
        }
        
        .card-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid rgba(99, 102, 241, 0.3);
        }
        
        .card-title {
            font-size: 1.3rem;
            color: var(--primary);
            font-weight: 600;
        }
        
        .form-group {
            margin-bottom: 20px;
        }
        
        label {
            display: block;
            margin-bottom: 8px;
            color: #cbd5e1;
            font-weight: 500;
        }
        
        input, button {
            padding: 12px 15px;
            background: rgba(15, 23, 42, 0.85);
            border: 2px solid rgba(99, 102, 241, 0.4);
            border-radius: 8px;
            color: white;
            font-size: 1rem;
            width: 100%;
        }
        
        input:focus {
            outline: none;
            border-color: var(--primary);
            box-shadow: 0 0 0 3px rgba(99, 102, 241, 0.25);
        }
        
        button {
            cursor: pointer;
            border: none;
            font-weight: 600;
            transition: all 0.25s;
        }
        
        .btn-primary {
            background: linear-gradient(90deg, var(--primary), #8b5cf6);
            color: white;
        }
        
        .btn-primary:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 18px rgba(99, 102, 241, 0.45);
        }
        
        .btn-success {
            background: linear-gradient(90deg, var(--success), #059669);
            color: white;
        }
        
        .btn-group {
            display: flex;
            gap: 12px;
            margin-top: 18px;
            flex-wrap: wrap;
        }
        
        .stats-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(140px, 1fr));
            gap: 15px;
            margin-top: 15px;
        }
        
        .stat-card {
            background: rgba(15, 23, 42, 0.75);
            padding: 15px;
            border-radius: 10px;
            text-align: center;
            border-left: 4px solid var(--primary);
        }
        
        .stat-value {
            font-size: 1.45rem;
            font-weight: 700;
            color: white;
            margin-bottom: 5px;
        }
        
        .stat-label {
            font-size: 0.9rem;
            color: #94a3b8;
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 20px;
            background: rgba(15, 23, 42, 0.75);
            border-radius: 10px;
            overflow: hidden;
        }
        
        th, td {
            padding: 12px 15px;
            text-align: left;
            border-bottom: 1px solid rgba(99, 102, 241, 0.25);
        }
        
        th {
            background: rgba(30, 41, 59, 0.92);
            color: var(--primary);
            font-weight: 600;
        }
        
        tr:hover {
            background: rgba(99, 102, 241, 0.12);
        }
        
        .profit-positive {
            color: var(--success);
            font-weight: 600;
        }
        
        .profit-negative {
            color: var(--danger);
            font-weight: 600;
        }
        
        .batch-container {
            background: rgba(15, 23, 42, 0.6);
            padding: 16px;
            border-radius: 10px;
            margin-bottom: 16px;
            border-left: 4px solid var(--primary);
        }
        
        .batch-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }
        
        .batch-id {
            background: rgba(99, 102, 241, 0.25);
            padding: 4px 10px;
            border-radius: 6px;
            font-size: 0.92rem;
            font-weight: 600;
        }
        
        .progress-bar {
            width: 100%;
            height: 8px;
            background: rgba(15, 23, 42, 0.6);
            border-radius: 4px;
            overflow: hidden;
            margin-top: 12px;
            display: none;
        }
        
        .progress {
            height: 100%;
            background: linear-gradient(90deg, var(--primary), #8b5cf6);
            width: 0%;
            transition: width 0.3s;
        }
        
        .notification {
            position: fixed;
            top: 20px;
            right: 20px;
            padding: 14px 24px;
            background: rgba(30, 41, 59, 0.96);
            border-radius: 10px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.5);
            z-index: 9999;
            transform: translateX(400px);
            transition: transform 0.3s;
            border-left: 4px solid var(--primary);
            max-width: 380px;
            font-size: 0.95rem;
        }
        
        .notification.show {
            transform: translateX(0);
        }
        
        .notification.success {
            border-left-color: var(--success);
        }
        
        .notification.error {
            border-left-color: var(--danger);
        }
        
        .player-info {
            display: none;
            margin-top: 18px;
            padding: 16px;
            background: rgba(15, 23, 42, 0.6);
            border-radius: 10px;
            text-align: center;
            font-size: 1.1rem;
            font-weight: 500;
        }
        
        .tabs {
            display: flex;
            gap: 10px;
            margin-bottom: 22px;
            border-bottom: 2px solid rgba(99, 102, 241, 0.35);
            padding-bottom: 15px;
        }
        
        .tab {
            padding: 10px 20px;
            background: rgba(15, 23, 42, 0.55);
            border: none;
            border-radius: 8px 8px 0 0;
            color: #a0aec0;
            cursor: pointer;
            transition: all 0.25s;
            font-weight: 500;
        }
        
        .tab.active {
            background: rgba(99, 102, 241, 0.22);
            color: var(--primary);
        }
        
        .tab-content {
            display: none;
        }
        
        .tab-content.active {
            display: block;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>🎮 Torn Trading Pro</h1>
            <p class="subtitle">Batch Tracking • Real API Integration • Exportable History</p>
            
            <div style="margin-top: 22px; background: rgba(15, 23, 42, 0.6); padding: 22px; border-radius: 12px; max-width: 650px; margin-left: auto; margin-right: auto;">
                <label style="color: white; font-weight: 600; display: block; margin-bottom: 12px; font-size: 1.05rem;">
                    🔑 Enter Your Torn API Key (16 characters):
                </label>
                <div style="display: flex; gap: 12px;">
                    <input type="text" id="apiKey" placeholder="e.g., abcdef1234567890" maxlength="16" style="flex: 1; font-size: 1.05rem;">
                    <button class="btn-primary" onclick="connectAPI()" style="width: auto; padding: 12px 18px; font-size: 1.05rem;">🔌 Connect</button>
                </div>
                <p style="margin-top: 14px; font-size: 0.93rem; color: #a0aec0; line-height: 1.5;">
                    Get key from: Torn.com → Settings → API Access → Create Key<br>
                    Required permissions: <strong>Basic</strong> + <strong>Inventory</strong> (Money permission NOT required)
                </p>
            </div>
            
            <div class="player-info" id="playerInfo">
                <span id="playerName">-</span> | Level: <span id="playerLevel">-</span> | ✅ Connected to Torn API
            </div>
        </header>

        <div class="tabs">
            <button class="tab active" onclick="switchTab('trading')">📈 Trading</button>
            <button class="tab" onclick="switchTab('inventory')">📦 Inventory</button>
            <button class="tab" onclick="switchTab('history')">📊 History</button>
            <button class="tab" onclick="switchTab('batches')">🔖 Batches</button>
        </div>

        <!-- TRADING TAB -->
        <div class="tab-content active" id="tradingTab">
            <div class="card">
                <div class="card-header">
                    <h3 class="card-title">➕ Add Trade (Batch Tracking)</h3>
                </div>
                <div class="form-group">
                    <label for="itemInput">📦 Item Name</label>
                    <input type="text" id="itemInput" placeholder="e.g., Smartphone, Laptop">
                </div>
                <div class="form-group">
                    <label for="quantity">🔢 Quantity</label>
                    <input type="number" id="quantity" placeholder="Enter quantity" min="1" value="1">
                </div>
                <div class="form-group">
                    <label for="purchasePrice">💰 Purchase Price per Unit</label>
                    <input type="number" id="purchasePrice" placeholder="Enter purchase price" step="0.01">
                </div>
                <div class="form-group">
                    <label for="sellPrice">💵 Sell Price per Unit</label>
                    <input type="number" id="sellPrice" placeholder="Enter sell price" step="0.01">
                </div>
                <div class="btn-group">
                    <button class="btn-primary" onclick="addTrade()">✅ Add Trade</button>
                    <button class="btn-success" onclick="calculateProfit()">🧮 Calculate Profit</button>
                </div>
            </div>

            <div class="card">
                <div class="card-header">
                    <h3 class="card-title">📊 Profit Analysis (15% Total Fees)</h3>
                </div>
                <div class="stats-grid">
                    <div class="stat-card">
                        <div class="stat-value" id="purchaseCost">0.00</div>
                        <div class="stat-label">Purchase Cost</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value" id="revenueAfterFees">0.00</div>
                        <div class="stat-label">Revenue (After Fees)</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value" id="profitPerUnit">0.00</div>
                        <div class="stat-label">Profit per Unit</div>
                    </div>
                    <div class="stat-card">
                        <div class="stat-value" id="totalProfit">0.00</div>
                        <div class="stat-label">Total Profit</div>
                    </div>
                </div>
                <div style="margin-top: 20px; padding: 14px; background: rgba(15, 23, 42, 0.6); border-radius: 10px; text-align: center; font-size: 0.95rem;">
                    Fee Structure: 10% Anonymous Fee + 5% Market Fee = 15% Total Fees
                </div>
            </div>
        </div>

        <!-- INVENTORY TAB -->
        <div class="tab-content" id="inventoryTab">
            <div class="card">
                <div class="card-header">
                    <h3 class="card-title">🎮 Your Torn Inventory</h3>
                    <button class="btn-primary" onclick="loadInventory()" style="width: auto; padding: 10px 16px;">🔄 Load Inventory</button>
                </div>
                <div class="progress-bar" id="syncProgressContainer">
                    <div class="progress" id="syncProgress"></div>
                </div>
                <div style="margin-top: 18px; overflow-x: auto;">
                    <table>
                        <thead>
                            <tr>
                                <th>Item Name</th>
                                <th>Quantity</th>
                                <th>Actions</th>
                            </tr>
                        </thead>
                        <tbody id="inventoryBody">
                            <tr>
                                <td colspan="3" style="text-align: center; padding: 40px; color: #a0aec0;">
                                    🔌 Connect your API key first, then click "Load Inventory"
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- HISTORY TAB -->
        <div class="tab-content" id="historyTab">
            <div class="card">
                <div class="card-header">
                    <h3 class="card-title">📜 Transaction History</h3>
                    <div style="display: flex; gap: 12px; flex-wrap: wrap;">
                        <button class="btn-success" onclick="exportHistory('csv')" style="width: auto; padding: 10px 16px;">📥 Export CSV</button>
                        <button class="btn-success" onclick="exportHistory('json')" style="width: auto; padding: 10px 16px;">📥 Export JSON</button>
                    </div>
                </div>
                <div style="overflow-x: auto;">
                    <table>
                        <thead>
                            <tr>
                                <th>Date</th>
                                <th>Item</th>
                                <th>Batch</th>
                                <th>Qty</th>
                                <th>Buy Price</th>
                                <th>Sell Price</th>
                                <th>Profit</th>
                            </tr>
                        </thead>
                        <tbody id="historyBody">
                            <tr>
                                <td colspan="7" style="text-align: center; padding: 40px; color: #a0aec0;">
                                    No transactions yet. Add your first trade!
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>

        <!-- BATCHES TAB -->
        <div class="tab-content" id="batchesTab">
            <div class="card">
                <div class="card-header">
                    <h3 class="card-title">🔖 Batch Tracking System</h3>
                    <button class="btn-success" onclick="exportBatches()" style="width: auto; padding: 10px 16px;">📥 Export Batches</button>
                </div>
                <div style="margin-bottom: 20px; padding: 16px; background: rgba(15, 23, 42, 0.6); border-radius: 10px;">
                    <strong>💡 How Batches Work:</strong><br>
                    • Buy "Laptop" at $500 × 10 → Creates <strong>Batch #1</strong><br>
                    • Buy "Laptop" at $450 × 5 → Creates <strong>Batch #2</strong> (separate tracking!)<br>
                    • Each batch tracks its own profit independently
                </div>
                <div id="batchesContainer">
                    <p style="text-align: center; color: #a0aec0; padding: 25px; font-size: 1.05rem;">
                        Add trades to see batches appear here
                    </p>
                </div>
            </div>
        </div>
    </div>

    <!-- Notification System -->
    <div class="notification" id="notification"></div>

    <script>
        // ===== GLOBAL VARIABLES =====
        let trades = JSON.parse(localStorage.getItem('tornTrades') || '[]');
        let batches = JSON.parse(localStorage.getItem('tornBatches') || '[]');
        let inventory = [];
        let apiKey = localStorage.getItem('tornApiKey') || '';
        let apiConnected = false;
        let batchCounter = 1;

        // Load saved data on startup
        document.addEventListener('DOMContentLoaded', () => {
            if (apiKey) {
                document.getElementById('apiKey').value = apiKey;
            }
            updateHistoryTable();
            updateBatchesDisplay();
        });

        // ===== SAFE API CONNECTION (No Money Permission Required) =====
        async function connectAPI() {
            apiKey = document.getElementById('apiKey').value.trim();
            
            if (!apiKey || apiKey.length !== 16) {
                showNotification('❌ Invalid API key! Must be exactly 16 characters.', 'error');
                return;
            }

            showNotification('🔌 Connecting to Torn API...');
            
            try {
                // Only request basic info (no money - avoids permission errors)
                const response = await fetch(`https://api.torn.com/user/?selections=basic&key=${apiKey}`);
                const data = await response.json();
                
                if (data.error) {
                    throw new Error(data.error.error || 'API Error');
                }
                
                // Save API key
                localStorage.setItem('tornApiKey', apiKey);
                apiConnected = true;
                
                // Display player info (SAFE ACCESS - no .money.cash)
                document.getElementById('playerName').textContent = data.name || 'Player';
                document.getElementById('playerLevel').textContent = data.level || '?';
                document.getElementById('playerInfo').style.display = 'block';
                
                showNotification(`✅ Connected! Welcome, ${data.name || 'Player'}!`, 'success');
                
            } catch (error) {
                showNotification(`❌ Connection failed: ${error.message}`, 'error');
                console.error('API Error:', error);
            }
        }

        // ===== LOAD INVENTORY (Works with Basic + Inventory permissions) =====
        async function loadInventory() {
            if (!apiConnected) {
                showNotification('❌ Please connect API first!', 'error');
                return;
            }

            showNotification('🔄 Loading your inventory...');
            
            // Show progress bar
            const progressContainer = document.getElementById('syncProgressContainer');
            const progressBar = document.getElementById('syncProgress');
            progressContainer.style.display = 'block';
            
            let progress = 0;
            const interval = setInterval(() => {
                progress += 15;
                progressBar.style.width = `${progress}%`;
                if (progress >= 100) clearInterval(interval);
            }, 80);

            try {
                // Fetch inventory (only requires Inventory permission)
                const response = await fetch(`https://api.torn.com/user/?selections=inventory&key=${apiKey}`);
                const data = await response.json();
                
                if (data.error) {
                    throw new Error(data.error.error || 'Failed to load inventory');
                }
                
                // SAFE INVENTORY ACCESS - handle missing/empty inventory
                const invData = data.inventory || {};
                const itemIds = Object.keys(invData);
                
                if (itemIds.length === 0) {
                    throw new Error('Your inventory is empty!');
                }
                
                // Process inventory items
                inventory = itemIds.map(itemId => {
                    const item = invData[itemId];
                    return {
                        id: itemId,
                        name: item.name || 'Unknown Item',
                        quantity: item.quantity || 1,
                        type: item.type || 'other'
                    };
                });
                
                // Update UI after delay for smooth UX
                setTimeout(() => {
                    progressContainer.style.display = 'none';
                    updateInventoryTable();
                    showNotification(`✅ Loaded ${inventory.length} items from your inventory!`, 'success');
                }, 350);
                
            } catch (error) {
                progressContainer.style.display = 'none';
                showNotification(`❌ ${error.message}`, 'error');
                console.error('Inventory Error:', error);
            }
        }

        // ===== UPDATE INVENTORY TABLE =====
        function updateInventoryTable() {
            const tbody = document.getElementById('inventoryBody');
            
            if (inventory.length === 0) {
                tbody.innerHTML = `
                    <tr>
                        <td colspan="3" style="text-align: center; padding: 40px; color: #a0aec0;">
                            Your inventory is empty
                        </td>
                    </tr>
                `;
                return;
            }

            tbody.innerHTML = inventory.map(item => `
                <tr>
                    <td>${item.name}</td>
                    <td>${item.quantity.toLocaleString()}</td>
                    <td>
                        <button class="btn-primary" style="padding: 6px 12px; font-size: 0.88rem;" 
                                onclick="quickAdd('${item.name.replace(/'/g, "\\'")}', ${item.quantity})">
                            Add Batch
                        </button>
                    </td>
                </tr>
            `).join('');
        }

        // ===== QUICK ADD FROM INVENTORY =====
        function quickAdd(itemName, quantity) {
            document.getElementById('itemInput').value = itemName;
            document.getElementById('quantity').value = quantity;
            switchTab('trading');
            showNotification(`Pre-filled: ${itemName} × ${quantity}. Set prices and click "Add Trade".`, 'success');
        }

        // ===== ADD TRADE WITH BATCH TRACKING =====
        function addTrade() {
            const item = document.getElementById('itemInput').value.trim();
            const quantity = parseFloat(document.getElementById('quantity').value) || 0;
            const purchasePrice = parseFloat(document.getElementById('purchasePrice').value) || 0;
            const sellPrice = parseFloat(document.getElementById('sellPrice').value) || 0;

            if (!item) {
                showNotification('❌ Please enter item name!', 'error');
                return;
            }
            if (quantity <= 0) {
                showNotification('❌ Quantity must be greater than 0!', 'error');
                return;
            }
            if (purchasePrice <= 0) {
                showNotification('❌ Purchase price must be greater than 0!', 'error');
                return;
            }
            if (sellPrice <= 0) {
                showNotification('❌ Sell price must be greater than 0!', 'error');
                return;
            }

            // Calculate profit (15% fees)
            const totalCost = quantity * purchasePrice;
            const revenueAfterFees = quantity * sellPrice * 0.85;
            const totalProfit = revenueAfterFees - totalCost;
            const profitPerUnit = totalProfit / quantity;

            // Create UNIQUE batch for this purchase
            const batchName = `Batch #${batchCounter++}`;

            // Create trade
            const trade = {
                id: Date.now(),
                timestamp: new Date().toISOString(),
                item: item,
                quantity: quantity,
                purchasePrice: purchasePrice,
                sellPrice: sellPrice,
                totalCost: totalCost,
                revenueAfterFees: revenueAfterFees,
                totalProfit: totalProfit,
                profitPerUnit: profitPerUnit,
                batchName: batchName
            };

            trades.push(trade);

            // Create separate batch (even for same item bought at different price)
            batches.push({
                name: batchName,
                item: item,
                quantity: quantity,
                purchasePrice: purchasePrice,
                sellPrice: sellPrice,
                totalProfit: totalProfit,
                createdAt: new Date().toISOString()
            });

            // Save
            localStorage.setItem('tornTrades', JSON.stringify(trades));
            localStorage.setItem('tornBatches', JSON.stringify(batches));

            // Update UI
            updateHistoryTable();
            updateBatchesDisplay();
            resetForm();

            showNotification(`✅ Added to ${batchName}! Profit: ${formatMoney(totalProfit)}`, 'success');
        }

        // ===== CALCULATE PROFIT =====
        function calculateProfit() {
            const quantity = parseFloat(document.getElementById('quantity').value) || 0;
            const purchasePrice = parseFloat(document.getElementById('purchasePrice').value) || 0;
            const sellPrice = parseFloat(document.getElementById('sellPrice').value) || 0;

            if (quantity <= 0 || purchasePrice <= 0 || sellPrice <= 0) {
                showNotification('⚠️ Enter valid prices & quantity', 'warning');
                return;
            }

            const totalCost = quantity * purchasePrice;
            const revenueAfterFees = quantity * sellPrice * 0.85;
            const totalProfit = revenueAfterFees - totalCost;
            const profitPerUnit = totalProfit / quantity;

            document.getElementById('purchaseCost').textContent = formatMoney(totalCost);
            document.getElementById('revenueAfterFees').textContent = formatMoney(revenueAfterFees);
            document.getElementById('profitPerUnit').textContent = formatMoney(profitPerUnit);
            document.getElementById('totalProfit').textContent = formatMoney(totalProfit);
            document.getElementById('totalProfit').className = totalProfit >= 0 ? 'stat-value profit-positive' : 'stat-value profit-negative';
        }

        // ===== UPDATE HISTORY TABLE =====
        function updateHistoryTable() {
            const tbody = document.getElementById('historyBody');
            
            if (trades.length === 0) {
                tbody.innerHTML = `
                    <tr>
                        <td colspan="7" style="text-align: center; padding: 40px; color: #a0aec0;">
                            No transactions yet. Add your first trade!
                        </td>
                    </tr>
                `;
                return;
            }

            // Sort newest first
            const sorted = [...trades].sort((a, b) => new Date(b.timestamp) - new Date(a.timestamp));
            
            tbody.innerHTML = sorted.map(trade => `
                <tr>
                    <td>${new Date(trade.timestamp).toLocaleDateString()}<br><small>${new Date(trade.timestamp).toLocaleTimeString([], {hour: '2-digit', minute:'2-digit'})}</small></td>
                    <td>${trade.item}</td>
                    <td>${trade.batchName}</td>
                    <td>${trade.quantity.toLocaleString()}</td>
                    <td>${formatMoney(trade.purchasePrice)}</td>
                    <td>${formatMoney(trade.sellPrice)}</td>
                    <td class="${trade.totalProfit >= 0 ? 'profit-positive' : 'profit-negative'}">
                        ${formatMoney(trade.totalProfit)}
                    </td>
                </tr>
            `).join('');
        }

        // ===== UPDATE BATCHES DISPLAY =====
        function updateBatchesDisplay() {
            if (batches.length === 0) {
                document.getElementById('batchesContainer').innerHTML = `
                    <p style="text-align: center; color: #a0aec0; padding: 25px; font-size: 1.05rem;">
                        Add trades to see batches appear here<br>
                        <small style="display: block; margin-top: 10px; color: #64748b;">
                            Each purchase creates a new batch for separate profit tracking
                        </small>
                    </p>
                `;
                return;
            }

            let html = '';
            batches.slice().reverse().forEach((batch, index) => {
                const profitPerUnit = batch.totalProfit / batch.quantity;
                html += `
                    <div class="batch-container">
                        <div class="batch-header">
                            <span class="batch-id">${batch.name}</span>
                            <span style="color: #94a3b8; font-size: 0.9rem;">${batch.item}</span>
                        </div>
                        <div style="display: grid; grid-template-columns: repeat(2, 1fr); gap: 12px; font-size: 0.98rem;">
                            <div><span style="color: #94a3b8;">Quantity:</span> <strong>${batch.quantity.toLocaleString()}</strong></div>
                            <div><span style="color: #94a3b8;">Buy Price:</span> <strong>${formatMoney(batch.purchasePrice)}</strong></div>
                            <div><span style="color: #94a3b8;">Sell Price:</span> <strong>${formatMoney(batch.sellPrice)}</strong></div>
                            <div><span style="color: #94a3b8;">Total Profit:</span> <strong class="${batch.totalProfit >= 0 ? 'profit-positive' : 'profit-negative'}">${formatMoney(batch.totalProfit)}</strong></div>
                        </div>
                    </div>
                `;
            });

            document.getElementById('batchesContainer').innerHTML = html;
        }

        // ===== EXPORT FUNCTIONS =====
        function exportHistory(format) {
            if (trades.length === 0) {
                showNotification('❌ No history to export!', 'error');
                return;
            }

            let data = '';
            if (format === 'csv') {
                const headers = ['Date', 'Item', 'Batch', 'Quantity', 'Buy_Price', 'Sell_Price', 'Profit'];
                const rows = trades.map(t => [
                    new Date(t.timestamp).toISOString(),
                    `"${t.item}"`,
                    t.batchName,
                    t.quantity,
                    t.purchasePrice.toFixed(2),
                    t.sellPrice.toFixed(2),
                    t.totalProfit.toFixed(2)
                ]);
                data = headers.join(',') + '\n' + rows.map(r => r.join(',')).join('\n');
            } else {
                data = JSON.stringify(trades, null, 2);
            }

            downloadFile(`torn_trades_${Date.now()}.${format}`, data, format === 'csv' ? 'text/csv' : 'application/json');
            showNotification(`✅ Exported ${trades.length} trades`, 'success');
        }

        function exportBatches() {
            if (batches.length === 0) {
                showNotification('❌ No batches to export!', 'error');
                return;
            }

            const data = JSON.stringify(batches, null, 2);
            downloadFile(`torn_batches_${Date.now()}.json`, data, 'application/json');
            showNotification(`✅ Exported ${batches.length} batches`, 'success');
        }

        // ===== UTILITY FUNCTIONS =====
        function formatMoney(amount) {
            return '$' + Math.abs(amount).toFixed(2).replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        }

        function downloadFile(filename, data, mimeType) {
            const blob = new Blob([data], { type: mimeType });
            const url = URL.createObjectURL(blob);
            const a = document.createElement('a');
            a.href = url;
            a.download = filename;
            document.body.appendChild(a);
            a.click();
            document.body.removeChild(a);
            URL.revokeObjectURL(url);
        }

        function showNotification(message, type = 'info') {
            const notif = document.getElementById('notification');
            notif.textContent = message;
            notif.className = `notification ${type === 'success' ? 'success' : type === 'error' ? 'error' : 'warning'}`;
            notif.classList.add('show');
            setTimeout(() => notif.classList.remove('show'), 3500);
        }

        function resetForm() {
            document.getElementById('itemInput').value = '';
            document.getElementById('quantity').value = '1';
            document.getElementById('purchasePrice').value = '';
            document.getElementById('sellPrice').value = '';
            document.getElementById('purchaseCost').textContent = '0.00';
            document.getElementById('revenueAfterFees').textContent = '0.00';
            document.getElementById('profitPerUnit').textContent = '0.00';
            document.getElementById('totalProfit').textContent = '0.00';
            document.getElementById('totalProfit').className = 'stat-value';
        }

        function switchTab(tabName) {
            document.querySelectorAll('.tab-content').forEach(t => t.classList.remove('active'));
            document.querySelectorAll('.tab').forEach(t => t.classList.remove('active'));
            document.getElementById(tabName + 'Tab').classList.add('active');
            event.target.classList.add('active');
        }
    </script>
</body>
</html>
