// Global variables
let colorStops = [
    { color: '#667eea', position: 0, opacity: 1, id: 1 },
    { color: '#764ba2', position: 100, opacity: 1, id: 2 }
];

let nextId = 3;
let gradientHistory = JSON.parse(localStorage.getItem('gradientHistory') || '[]');
let currentGradientType = 'linear';
let currentDirection = '135deg';
let globalOpacity = 100;
let radialCenterX = 50;
let radialCenterY = 50;
let radialShape = 'circle';

const presetGradients = [
    { name: 'Ocean Breeze', type: 'linear', stops: [{color:'#667eea',position:0},{color:'#764ba2',position:100}], direction: '135deg' },
    { name: 'Sunset Glow', type: 'linear', stops: [{color:'#fa709a',position:0},{color:'#fee140',position:100}], direction: '135deg' },
    { name: 'Forest Mist', type: 'linear', stops: [{color:'#134e5e',position:0},{color:'#71b280',position:100}], direction: '180deg' },
    { name: 'Purple Dream', type: 'linear', stops: [{color:'#667eea',position:0},{color:'#f093fb',position:50},{color:'#764ba2',position:100}], direction: '45deg' },
    { name: 'Mint Fresh', type: 'linear', stops: [{color:'#00b09b',position:0},{color:'#96c93d',position:100}], direction: '90deg' },
    { name: 'Cherry Blossom', type: 'linear', stops: [{color:'#ff9a9e',position:0},{color:'#fecfef',position:50},{color:'#fad0c4',position:100}], direction: '135deg' }
];

// DOM elements
let gradientPreview, cssOutput, toast, colorStopsContainer, historyGrid, presetsGrid;
let linearControls, radialControls, sidebar, sidebarOverlay, mobileMenuToggle;

// Initialize
function init() {
    gradientPreview = document.getElementById('gradientPreview');
    cssOutput = document.getElementById('cssOutput');
    toast = document.getElementById('toast');
    colorStopsContainer = document.getElementById('colorStopsContainer');
    historyGrid = document.getElementById('historyGrid');
    presetsGrid = document.getElementById('presetsGrid');
    linearControls = document.getElementById('linearControls');
    radialControls = document.getElementById('radialControls');
    sidebar = document.getElementById('sidebar');
    sidebarOverlay = document.getElementById('sidebarOverlay');
    mobileMenuToggle = document.getElementById('mobileMenuToggle');

    setupEventListeners();
    setupMobileMenu();
    renderColorStops();
    updateGradient();
    renderPresets();
    renderHistory();
    setupPanelNavigation();
    showToast('Grafla へようこそ！グラデーションを作成しましょう');
}

// Mobile menu functionality
function setupMobileMenu() {
    mobileMenuToggle.addEventListener('click', () => {
        sidebar.classList.toggle('active');
        sidebarOverlay.classList.toggle('active');
        
        // Toggle icon
        const icon = mobileMenuToggle.querySelector('i');
        if (sidebar.classList.contains('active')) {
            icon.className = 'fas fa-times';
        } else {
            icon.className = 'fas fa-bars';
        }
    });

    sidebarOverlay.addEventListener('click', () => {
        sidebar.classList.remove('active');
        sidebarOverlay.classList.remove('active');
        mobileMenuToggle.querySelector('i').className = 'fas fa-bars';
    });

    // Close sidebar when nav button is clicked on mobile
    document.querySelectorAll('.nav-btn').forEach(btn => {
        btn.addEventListener('click', () => {
            if (window.innerWidth <= 1200) {
                sidebar.classList.remove('active');
                sidebarOverlay.classList.remove('active');
                mobileMenuToggle.querySelector('i').className = 'fas fa-bars';
            }
        });
    });
}

// Panel navigation
function setupPanelNavigation() {
    const navButtons = document.querySelectorAll('.nav-btn');
    const panels = document.querySelectorAll('.control-panel');

    navButtons.forEach(btn => {
        btn.addEventListener('click', () => {
            const targetPanelId = btn.dataset.target;

            navButtons.forEach(b => b.classList.remove('active'));
            btn.classList.add('active');

            panels.forEach(p => p.classList.remove('active'));
            document.getElementById(targetPanelId).classList.add('active');
        });
    });
}

// Event listeners
function setupEventListeners() {
    // Gradient type selection
    document.querySelectorAll('.gradient-type').forEach(btn => {
        btn.addEventListener('click', (e) => {
            document.querySelectorAll('.gradient-type').forEach(b => b.classList.remove('active'));
            e.target.classList.add('active');
            currentGradientType = e.target.dataset.type;
            updateUIForGradientType();
            updateGradient();
        });
    });

    // Circular direction control
    setupDirectionControl();

    // Angle slider
    const angleSlider = document.getElementById('angleSlider');
    angleSlider.addEventListener('input', (e) => {
        currentDirection = e.target.value + 'deg';
        document.getElementById('angleValue').textContent = currentDirection;
        updateDirectionHandle();
        updateGradient();
    });

    // Radial controls
    document.getElementById('radialCenterX').addEventListener('input', (e) => {
        radialCenterX = e.target.value;
        document.getElementById('radialCenterXValue').textContent = radialCenterX + '%';
        updateGradient();
    });

    document.getElementById('radialCenterY').addEventListener('input', (e) => {
        radialCenterY = e.target.value;
        document.getElementById('radialCenterYValue').textContent = radialCenterY + '%';
        updateGradient();
    });

    document.getElementById('radialShapeSelect').addEventListener('change', (e) => {
        radialShape = e.target.value;
        updateGradient();
    });

    // Effects
    document.getElementById('animateGradient').addEventListener('change', (e) => {
        if (e.target.checked) {
            gradientPreview.classList.add('gradient-animation');
        } else {
            gradientPreview.classList.remove('gradient-animation');
        }
    });

    document.getElementById('noiseOverlay').addEventListener('change', (e) => {
        if (e.target.checked) {
            gradientPreview.classList.add('noise');
        } else {
            gradientPreview.classList.remove('noise');
        }
    });

    document.getElementById('globalOpacity').addEventListener('input', (e) => {
        globalOpacity = e.target.value;
        document.getElementById('opacityValue').textContent = e.target.value + '%';
        updateGradient();
    });
}

// Circular direction control
function setupDirectionControl() {
    const control = document.getElementById('directionControl');
    const handle = document.getElementById('directionHandle');
    let isDragging = false;

    function getAngleFromPoint(x, y) {
        const rect = control.getBoundingClientRect();
        const centerX = rect.left + rect.width / 2;
        const centerY = rect.top + rect.height / 2;
        const deltaX = x - centerX;
        const deltaY = y - centerY;
        let angle = Math.atan2(deltaY, deltaX) * 180 / Math.PI;
        angle = (angle + 90) % 360;
        if (angle < 0) angle += 360;
        return Math.round(angle);
    }

    function updateHandlePosition(angle) {
        const radians = (angle - 90) * Math.PI / 180;
        const radius = 50;
        const x = Math.cos(radians) * radius;
        const y = Math.sin(radians) * radius;
        handle.style.transform = `translate(calc(-50% + ${x}px), ${y}px)`;
    }

    function updateDirectionHandle() {
        const angle = parseInt(currentDirection);
        updateHandlePosition(angle);
    }

    function handleInteraction(e) {
        if (!isDragging && e.type !== 'click') return;

        const clientX = e.clientX || (e.touches && e.touches[0].clientX);
        const clientY = e.clientY || (e.touches && e.touches[0].clientY);

        if (clientX !== undefined && clientY !== undefined) {
            const angle = getAngleFromPoint(clientX, clientY);
            currentDirection = angle + 'deg';

            document.getElementById('angleSlider').value = angle;
            document.getElementById('angleValue').textContent = currentDirection;
            updateHandlePosition(angle);
            updateGradient();
        }
    }

    // Mouse events
    control.addEventListener('mousedown', (e) => {
        isDragging = true;
        handleInteraction(e);
        e.preventDefault();
    });

    document.addEventListener('mousemove', (e) => {
        if (isDragging) {
            handleInteraction(e);
        }
    });

    document.addEventListener('mouseup', () => {
        isDragging = false;
    });

    // Touch events for mobile
    control.addEventListener('touchstart', (e) => {
        isDragging = true;
        handleInteraction(e);
        e.preventDefault();
    });

    document.addEventListener('touchmove', (e) => {
        if (isDragging) {
            handleInteraction(e);
            e.preventDefault();
        }
    });

    document.addEventListener('touchend', () => {
        isDragging = false;
    });

    // Click event for direct positioning
    control.addEventListener('click', handleInteraction);

    // Initialize handle position
    updateDirectionHandle();

    // Make updateDirectionHandle globally accessible
    window.updateDirectionHandle = updateDirectionHandle;
}

// Color stop management
function addColorStop() {
    const newPosition = Math.random() * 100;
    const colors = ['#ff6b6b', '#4ecdc4', '#45b7d1', '#f9ca24', '#f0932b', '#eb4d4b', '#6c5ce7', '#a29bfe'];
    const randomColor = colors[Math.floor(Math.random() * colors.length)];

    colorStops.push({
        color: randomColor,
        position: newPosition,
        opacity: 1,
        id: nextId++
    });

    colorStops.sort((a, b) => a.position - b.position);
    renderColorStops();
    updateGradient();
}

function removeColorStop(id) {
    if (colorStops.length > 2) {
        colorStops = colorStops.filter(stop => stop.id !== id);
        renderColorStops();
        updateGradient();
    }
}

function renderColorStops() {
    colorStopsContainer.innerHTML = '';
    colorStops.forEach(stop => {
        const stopEl = document.createElement('div');
        stopEl.classList.add('color-stop');
        stopEl.innerHTML = `
            <div class="color-stop-header">
                <span class="color-stop-title">色 #${stop.id}</span>
                <button class="mini-btn danger" onclick="removeColorStop(${stop.id})">
                    <i class="fas fa-trash"></i>
                    削除
                </button>
            </div>
            <div class="color-input-row">
                <input type="color" class="color-picker" value="${stop.color}" data-id="${stop.id}">
                <input type="text" class="hex-input" value="${stop.color}" data-id="${stop.id}">
            </div>
            <div class="position-opacity-grid">
                <div class="control-group">
                    <label class="control-label">位置</label>
                    <div class="slider-group">
                        <input type="range" class="slider stop-position-slider" min="0" max="100" value="${stop.position}" data-id="${stop.id}">
                        <span class="slider-value stop-position-value">${Math.round(stop.position)}%</span>
                    </div>
                </div>
                <div class="control-group">
                    <label class="control-label">透明度</label>
                    <div class="slider-group">
                        <input type="range" class="slider stop-opacity-slider" min="0" max="100" value="${stop.opacity * 100}" data-id="${stop.id}">
                        <span class="slider-value stop-opacity-value">${Math.round(stop.opacity * 100)}%</span>
                    </div>
                </div>
            </div>
        `;
        colorStopsContainer.appendChild(stopEl);
    });

    // Add event listeners for new elements
    document.querySelectorAll('.color-picker').forEach(el => {
        el.addEventListener('input', (e) => {
            const id = parseInt(e.target.dataset.id);
            const stop = colorStops.find(s => s.id === id);
            stop.color = e.target.value;
            e.target.nextElementSibling.value = e.target.value;
            updateGradient();
        });
    });

    document.querySelectorAll('.hex-input').forEach(el => {
        el.addEventListener('input', (e) => {
            const id = parseInt(e.target.dataset.id);
            const stop = colorStops.find(s => s.id === id);
            const hex = e.target.value;
            if (/^#[0-9A-Fa-f]{6}$/.test(hex)) {
                stop.color = hex;
                e.target.previousElementSibling.value = hex;
                updateGradient();
            }
        });
    });

    document.querySelectorAll('.stop-position-slider').forEach(el => {
        el.addEventListener('input', (e) => {
            const id = parseInt(e.target.dataset.id);
            const stop = colorStops.find(s => s.id === id);
            stop.position = parseFloat(e.target.value);
            e.target.nextElementSibling.textContent = Math.round(stop.position) + '%';
            updateGradient();
        });
    });

    document.querySelectorAll('.stop-opacity-slider').forEach(el => {
        el.addEventListener('input', (e) => {
            const id = parseInt(e.target.dataset.id);
            const stop = colorStops.find(s => s.id === id);
            stop.opacity = parseFloat(e.target.value) / 100;
            e.target.nextElementSibling.textContent = Math.round(stop.opacity * 100) + '%';
            updateGradient();
        });
    });
}

function updateGradient() {
    colorStops.sort((a, b) => a.position - b.position);
    const stopString = colorStops.map(stop => {
        const color = hexToRgba(stop.color, stop.opacity);
        const position = Math.round(stop.position) + '%';
        return `${color} ${position}`;
    }).join(', ');

    let gradientCss = '';
    const opacityCss = `opacity: ${globalOpacity / 100};`;

    if (currentGradientType === 'linear') {
        gradientCss = `linear-gradient(${currentDirection}, ${stopString})`;
    } else if (currentGradientType === 'radial') {
        const position = `${radialCenterX}% ${radialCenterY}%`;
        const shape = radialShape;
        gradientCss = `radial-gradient(${shape} at ${position}, ${stopString})`;
    } else if (currentGradientType === 'conic') {
        gradientCss = `conic-gradient(from ${currentDirection}, ${stopString})`;
    }

    gradientPreview.style.background = gradientCss;
    gradientPreview.style.opacity = globalOpacity / 100;

    cssOutput.textContent = `background: ${gradientCss};\n${opacityCss}`;
}

function hexToRgba(hex, alpha) {
    const r = parseInt(hex.slice(1, 3), 16);
    const g = parseInt(hex.slice(3, 5), 16);
    const b = parseInt(hex.slice(5, 7), 16);
    return `rgba(${r}, ${g}, ${b}, ${alpha})`;
}

// Function to update UI for gradient type
function updateUIForGradientType() {
    const isLinearOrConic = currentGradientType === 'linear' || currentGradientType === 'conic';
    linearControls.classList.toggle('hidden', !isLinearOrConic);
    radialControls.classList.toggle('hidden', isLinearOrConic);
}

// Manual save functionality
function manualSaveGradient() {
    const nameInput = document.getElementById('saveNameInput');
    const customName = nameInput.value.trim();
    
    const currentState = {
        type: currentGradientType,
        direction: currentDirection,
        stops: JSON.parse(JSON.stringify(colorStops)), // Deep copy
        opacity: globalOpacity,
        radialCenter: { x: radialCenterX, y: radialCenterY },
        radialShape: radialShape,
        name: customName || `グラデーション ${new Date().toLocaleString('ja-JP')}`,
        timestamp: Date.now(),
        favorite: false,
        manual: true
    };

    gradientHistory.unshift(currentState);
    if (gradientHistory.length > 50) { // 履歴の上限を50に設定
        gradientHistory = gradientHistory.slice(0, 50);
    }
    
    localStorage.setItem('gradientHistory', JSON.stringify(gradientHistory));
    renderHistory();
    nameInput.value = '';
    showToast(`"${currentState.name}" を保存しました！`);
}

// History item controls
function toggleFavorite(index) {
    gradientHistory[index].favorite = !gradientHistory[index].favorite;
    localStorage.setItem('gradientHistory', JSON.stringify(gradientHistory));
    renderHistory();
    const status = gradientHistory[index].favorite ? 'お気に入りに追加' : 'お気に入りから削除';
    showToast(`${status}しました`);
}

function deleteHistoryItem(index) {
    const item = gradientHistory[index];
    if (confirm(`"${item.name}" を削除しますか？`)) {
        gradientHistory.splice(index, 1);
        localStorage.setItem('gradientHistory', JSON.stringify(gradientHistory));
        renderHistory();
        showToast(`"${item.name}" を削除しました`);
    }
}

function sortHistoryByFavorites() {
    gradientHistory.sort((a, b) => {
        if (a.favorite && !b.favorite) return -1;
        if (!a.favorite && b.favorite) return 1;
        return b.timestamp - a.timestamp;
    });
    localStorage.setItem('gradientHistory', JSON.stringify(gradientHistory));
    renderHistory();
    showToast('お気に入り順で並び替えました');
}

// Presets
function renderPresets() {
    presetsGrid.innerHTML = '';
    presetGradients.forEach(preset => {
        const presetEl = document.createElement('div');
        presetEl.classList.add('preset-item');
        
        let cssString = '';
        if (preset.type === 'linear') {
            const stops = preset.stops.map(stop => `${stop.color} ${stop.position}%`).join(', ');
            cssString = `linear-gradient(${preset.direction}, ${stops})`;
        } else if (preset.type === 'radial') {
            const stops = preset.stops.map(stop => `${stop.color} ${stop.position}%`).join(', ');
            cssString = `radial-gradient(${stops})`;
        }

        presetEl.style.background = cssString;
        presetEl.title = preset.name;
        
        presetEl.addEventListener('click', () => {
            applyPreset(preset);
        });
        presetsGrid.appendChild(presetEl);
    });
}

function applyPreset(preset) {
    currentGradientType = preset.type;
    currentDirection = preset.direction || '135deg';
    colorStops = preset.stops.map((stop, index) => ({
        color: stop.color,
        position: stop.position,
        opacity: stop.opacity || 1,
        id: nextId++
    }));
    document.getElementById('angleSlider').value = parseInt(currentDirection);
    document.getElementById('angleValue').textContent = currentDirection;
    document.querySelectorAll('.gradient-type').forEach(btn => {
        btn.classList.remove('active');
        if (btn.dataset.type === currentGradientType) {
            btn.classList.add('active');
        }
    });
    if (window.updateDirectionHandle) {
        window.updateDirectionHandle();
    }
    renderColorStops();
    updateUIForGradientType();
    updateGradient();
    showToast(`プリセット "${preset.name}" を適用しました！`);
}

// History
function renderHistory() {
    historyGrid.innerHTML = '';
    if (gradientHistory.length === 0) {
        historyGrid.innerHTML = '<p style="color: var(--muted-text-color); font-size: 0.9rem; grid-column: 1 / -1; text-align: center; padding: 20px;">履歴はありません。手動保存またはプリセットを使用してください。</p>';
        return;
    }
    
    gradientHistory.forEach((item, index) => {
        const historyEl = document.createElement('div');
        historyEl.classList.add('history-item');
        historyEl.style.opacity = item.opacity / 100;

        let cssString = '';
        const stopString = item.stops.map(stop => `${stop.color} ${stop.position}%`).join(', ');
        if (item.type === 'linear') {
            cssString = `linear-gradient(${item.direction}, ${stopString})`;
        } else if (item.type === 'radial') {
            const position = `${item.radialCenter.x}% ${item.radialCenter.y}%`;
            cssString = `radial-gradient(${item.radialShape} at ${position}, ${stopString})`;
        } else if (item.type === 'conic') {
            cssString = `conic-gradient(from ${item.direction}, ${stopString})`;
        }
        historyEl.style.background = cssString;
        historyEl.title = item.name || 'グラデーション';

        // Controls
        historyEl.innerHTML = `
            <div class="history-item-controls">
                <button class="history-control-btn favorite ${item.favorite ? 'active' : ''}" onclick="event.stopPropagation(); toggleFavorite(${index})" title="${item.favorite ? 'お気に入りから削除' : 'お気に入りに追加'}">
                    <i class="fas fa-star"></i>
                </button>
                <button class="history-control-btn delete" onclick="event.stopPropagation(); deleteHistoryItem(${index})" title="削除">
                    <i class="fas fa-trash"></i>
                </button>
            </div>
            <div class="history-timestamp">${new Date(item.timestamp).toLocaleDateString('ja-JP', {month: 'short', day: 'numeric'})}</div>
        `;

        historyEl.addEventListener('click', () => {
            applyHistoryItem(item);
        });
        historyGrid.appendChild(historyEl);
    });
}

function applyHistoryItem(item) {
    currentGradientType = item.type;
    currentDirection = item.direction;
    colorStops = JSON.parse(JSON.stringify(item.stops)); // Deep copy
    globalOpacity = item.opacity;
    radialCenterX = item.radialCenter.x;
    radialCenterY = item.radialCenter.y;
    radialShape = item.radialShape;

    // Update UI controls
    document.querySelectorAll('.gradient-type').forEach(btn => {
        btn.classList.remove('active');
        if (btn.dataset.type === currentGradientType) {
            btn.classList.add('active');
        }
    });
    document.getElementById('angleSlider').value = parseInt(currentDirection);
    document.getElementById('angleValue').textContent = currentDirection;
    document.getElementById('globalOpacity').value = globalOpacity;
    document.getElementById('opacityValue').textContent = globalOpacity + '%';
    document.getElementById('radialCenterX').value = radialCenterX;
    document.getElementById('radialCenterXValue').textContent = radialCenterX + '%';
    document.getElementById('radialCenterY').value = radialCenterY;
    document.getElementById('radialCenterYValue').textContent = radialCenterY + '%';
    document.getElementById('radialShapeSelect').value = radialShape;

    if (window.updateDirectionHandle) {
        window.updateDirectionHandle();
    }
    renderColorStops();
    updateUIForGradientType();
    updateGradient();
    showToast(`"${item.name}" を復元しました！`);
}

function clearHistory() {
    if (confirm('すべての履歴を削除しますか？この操作は取り消せません。')) {
        gradientHistory = [];
        localStorage.removeItem('gradientHistory');
        renderHistory();
        showToast('履歴をすべて削除しました');
    }
}

// Toast notification
function showToast(message) {
    toast.textContent = message;
    toast.classList.add('show');
    setTimeout(() => {
        toast.classList.remove('show');
    }, 4000);
}

// Export functions
function copyCSSCode() {
    const css = cssOutput.textContent;
    navigator.clipboard.writeText(css).then(() => {
        showToast('CSSコードをクリップボードにコピーしました！');
    }).catch(err => {
        console.error('Failed to copy CSS: ', err);
        showToast('CSSのコピーに失敗しました');
        
        // Fallback for older browsers
        const textArea = document.createElement('textarea');
        textArea.value = css;
        document.body.appendChild(textArea);
        textArea.select();
        try {
            document.execCommand('copy');
            showToast('CSSコードをコピーしました！');
        } catch (err) {
            showToast('コピーに失敗しました。手動でコピーしてください。');
        }
        document.body.removeChild(textArea);
    });
}

function exportAsImage(format) {
    if (typeof domtoimage === 'undefined') {
        showToast('画像エクスポート機能が利用できません');
        return;
    }

    const node = document.getElementById('gradientPreview');

    // Make the preview background fully opaque temporarily for correct image export
    const originalOpacity = node.style.opacity;
    node.style.opacity = 1;

    let options = {
        quality: 1,
        style: {
            opacity: 1
        },
        width: node.offsetWidth * 2,
        height: node.offsetHeight * 2
    };

    if (format === 'jpeg') {
        options.quality = 0.95;
    }

    domtoimage.toBlob(node, options)
        .then(function (blob) {
            const url = window.URL.createObjectURL(blob);
            const link = document.createElement('a');
            link.href = url;
            link.download = `grafla-gradient-${Date.now()}.${format}`;
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            window.URL.revokeObjectURL(url);
            showToast(`${format.toUpperCase()}ファイルとして保存しました！`);
        })
        .catch(function (error) {
            console.error('Export failed:', error);
            showToast('画像の書き出しに失敗しました');
        })
        .finally(() => {
            // Restore original opacity
            node.style.opacity = originalOpacity;
        });
}

// Initialize the app
document.addEventListener('DOMContentLoaded', init);
