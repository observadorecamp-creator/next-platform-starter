// ========================================
// OFERTAS ML HUB - Sistema Completo
// ========================================

// Estado global de la aplicación
let appData = {
    products: [],
    settings: {
        instagram: '',
        facebook: '',
        whatsapp: '',
        telegram: '',
        website: ''
    },
    stats: {
        totalClicks: 0,
        totalViews: 0
    }
};

// ========================================
// INICIALIZACIÓN
// ========================================

document.addEventListener('DOMContentLoaded', function() {
    loadData();
    renderProducts();
    setupEventListeners();
    loadExampleProducts();
});

// ========================================
// CARGA Y GUARDADO DE DATOS
// ========================================

function loadData() {
    const saved = localStorage.getItem('ofertasMLData');
    if (saved) {
        appData = JSON.parse(saved);
    }
}

function saveData() {
    localStorage.setItem('ofertasMLData', JSON.stringify(appData));
}

// ========================================
// PRODUCTOS DE EJEMPLO
// ========================================

function loadExampleProducts() {
    if (appData.products.length === 0) {
        appData.products = [
            {
                id: 1,
                emoji: '📱',
                name: 'iPhone 15 Pro Max 256GB',
                category: 'tecnologia',
                price: 18999,
                oldPrice: 25999,
                url: 'https://mercadolibre.com.mx'
            },
            {
                id: 2,
                emoji: '💻',
                name: 'Laptop Lenovo IdeaPad 3 16GB RAM',
                category: 'tecnologia',
                price: 8499,
                oldPrice: 12999,
                url: 'https://mercadolibre.com.mx'
            },
            {
                id: 3,
                emoji: '🎧',
                name: 'AirPods Pro 2da Generación',
                category: 'tecnologia',
                price: 4299,
                oldPrice: 6999,
                url: 'https://mercadolibre.com.mx'
            },
            {
                id: 4,
                emoji: '🏠',
                name: 'Aspiradora Robot Xiaomi',
                category: 'hogar',
                price: 3999,
                oldPrice: 7999,
                url: 'https://mercadolibre.com.mx'
            },
            {
                id: 5,
                emoji: '☕',
                name: 'Cafetera Nespresso Essenza Mini',
                category: 'hogar',
                price: 2499,
                oldPrice: 4999,
                url: 'https://mercadolibre.com.mx'
            },
            {
                id: 6,
                emoji: '👟',
                name: 'Tenis Nike Air Max 270',
                category: 'moda',
                price: 1899,
                oldPrice: 2999,
                url: 'https://mercadolibre.com.mx'
            }
        ];
        saveData();
    }
}

// ========================================
// RENDERIZADO DE PRODUCTOS
// ========================================

function renderProducts(filter = 'all') {
    const grid = document.getElementById('products');
    if (!grid) return;

    grid.innerHTML = '';

    const filtered = filter === 'all' 
        ? appData.products 
        : appData.products.filter(p => p.category === filter);

    if (filtered.length === 0) {
        grid.innerHTML = '<p style="text-align: center; grid-column: 1/-1; padding: 50px; color: white;">No hay productos en esta categoría</p>';
        return;
    }

    filtered.forEach(product => {
        const discount = Math.round(((product.oldPrice - product.price) / product.oldPrice) * 100);
        
        const card = document.createElement('div');
        card.className = 'product-card';
        card.innerHTML = `
            <div class="product-image">
                <span style="font-size: 5rem;">${product.emoji}</span>
                <div class="discount-badge">-${discount}%</div>
            </div>
            <div class="product-info">
                <div class="product-title">${product.name}</div>
                <div style="background: #E8F5E9; padding: 0.5rem; border-radius: 5px; text-align: center; color: #00A650; font-weight: bold; margin: 1rem 0;">
                    ✅ Envío GRATIS
                </div>
                <div class="product-price">
                    <span class="current-price">$${product.price.toLocaleString()}</span>
                    <span class="old-price">$${product.oldPrice.toLocaleString()}</span>
                </div>
                <button class="buy-btn" onclick="trackClick(${product.id})">
                    VER OFERTA 🔥
                </button>
            </div>
        `;
        grid.appendChild(card);
    });
}

// ========================================
// FILTRADO DE PRODUCTOS
// ========================================

function filterProducts(category) {
    // Actualizar botones activos
    document.querySelectorAll('.filter-btn').forEach(btn => {
        btn.classList.remove('active');
    });
    event.target.classList.add('active');

    // Renderizar productos filtrados
    renderProducts(category);
}

// ========================================
// TRACKING DE CLICKS
// ========================================

function trackClick(productId) {
    const product = appData.products.find(p => p.id === productId);
    if (!product) return;

    // Incrementar contador
    appData.stats.totalClicks++;
    saveData();

    // Abrir enlace
    window.open(product.url, '_blank');

    // Mostrar notificación
    alert(`Redirigiendo a: ${product.name}\n\nClicks totales: ${appData.stats.totalClicks}`);
}

// ========================================
// FORMULARIO DE PRODUCTOS
// ========================================

function setupEventListeners() {
    const form = document.getElementById('productForm');
    if (form) {
        form.addEventListener('submit', function(e) {
            e.preventDefault();
            addProduct();
        });
    }
}

function addProduct() {
    const product = {
        id: Date.now(),
        emoji: document.getElementById('emoji').value,
        name: document.getElementById('name').value,
        category: document.getElementById('category').value,
        price: parseFloat(document.getElementById('price').value),
        oldPrice: parseFloat(document.getElementById('oldPrice').value),
        url: document.getElementById('url').value
    };

    appData.products.push(product);
    saveData();
    renderProducts();

    // Limpiar formulario
    document.getElementById('productForm').reset();

    alert('✅ Producto agregado correctamente!');
}

// ========================================
// PANEL DE ADMINISTRACIÓN
// ========================================

function toggleAdmin() {
    const panel = document.getElementById('admin-panel');
    if (panel) {
        panel.style.display = panel.style.display === 'none' ? 'block' : 'none';
    }
}

// ========================================
// UTILIDADES
// ========================================

function scrollTo(id) {
    const element = document.getElementById(id);
    if (element) {
        element.scrollIntoView({ behavior: 'smooth' });
    }
}

// ========================================
// EXPORTAR/IMPORTAR DATOS
// ========================================

function exportData() {
    const dataStr = JSON.stringify(appData, null, 2);
    const dataBlob = new Blob([dataStr], { type: 'application/json' });
    const url = URL.createObjectURL(dataBlob);
    
    const a = document.createElement('a');
    a.href = url;
    a.download = `ofertas-ml-backup-${new Date().toISOString().split('T')[0]}.json`;
    a.click();
    
    URL.revokeObjectURL(url);
}

function importData(file) {
    const reader = new FileReader();
    reader.onload = function(e) {
        try {
            appData = JSON.parse(e.target.result);
            saveData();
            renderProducts();
            alert('✅ Datos importados correctamente!');
        } catch (error) {
            alert('❌ Error al importar datos');
        }
    };
    reader.readAsText(file);
}

// ========================================
// COMPARTIR EN REDES SOCIALES
// ========================================

function shareToWhatsApp(productId) {
    const product = appData.products.find(p => p.id === productId);
    if (!product) return;

    const discount = Math.round(((product.oldPrice - product.price) / product.oldPrice) * 100);
    const message = `🔥 OFERTA IMPERDIBLE 🔥\n\n${product.emoji} ${product.name}\n\n💰 Precio: $${product.price.toLocaleString()}\n❌ Antes: $${product.oldPrice.toLocaleString()}\n✅ Descuento: ${discount}%\n\n📦 Envío GRATIS\n\n👉 ${product.url}`;

    const whatsappUrl = `https://wa.me/?text=${encodeURIComponent(message)}`;
    window.open(whatsappUrl, '_blank');
}

function shareToFacebook() {
    const url = window.location.href;
    const fbUrl = `https://www.facebook.com/sharer/sharer.php?u=${encodeURIComponent(url)}`;
    window.open(fbUrl, '_blank', 'width=600,height=400');
}

function shareToTwitter() {
    const text = '🔥 Las mejores ofertas de Mercado Libre';
    const url = window.location.href;
    const twitterUrl = `https://twitter.com/intent/tweet?text=${encodeURIComponent(text)}&url=${encodeURIComponent(url)}`;
    window.open(twitterUrl, '_blank', 'width=600,height=400');
}

// ========================================
// BÚSQUEDA DE PRODUCTOS
// ========================================

function searchProducts(query) {
    const results = appData.products.filter(p => 
        p.name.toLowerCase().includes(query.toLowerCase()) ||
        p.category.toLowerCase().includes(query.toLowerCase())
    );
    
    renderSearchResults(results);
}

function renderSearchResults(results) {
    const grid = document.getElementById('products');
    if (!grid) return;

    grid.innerHTML = '';

    if (results.length === 0) {
        grid.innerHTML = '<p style="text-align: center; grid-column: 1/-1; padding: 50px; color: white;">No se encontraron productos</p>';
        return;
    }

    results.forEach(product => {
        const discount = Math.round(((product.oldPrice - product.price) / product.oldPrice) * 100);
        
        const card = document.createElement('div');
        card.className = 'product-card';
        card.innerHTML = `
            <div class="product-image">
                <span style="font-size: 5rem;">${product.emoji}</span>
                <div class="discount-badge">-${discount}%</div>
            </div>
            <div class="product-info">
                <div class="product-title">${product.name}</div>
                <div style="background: #E8F5E9; padding: 0.5rem; border-radius: 5px; text-align: center; color: #00A650; font-weight: bold; margin: 1rem 0;">
                    ✅ Envío GRATIS
                </div>
                <div class="product-price">
                    <span class="current-price">$${product.price.toLocaleString()}</span>
                    <span class="old-price">$${product.oldPrice.toLocaleString()}</span>
                </div>
                <button class="buy-btn" onclick="trackClick(${product.id})">
                    VER OFERTA 🔥
                </button>
            </div>
        `;
        grid.appendChild(card);
    });
}

// ========================================
// NOTIFICACIONES
// ========================================

function showNotification(message, type = 'success') {
    const notification = document.createElement('div');
    notification.style.cssText = `
        position: fixed;
        bottom: 20px;
        right: 20px;
        background: ${type === 'success' ? '#00A650' : '#FF0000'};
        color: white;
        padding: 1rem 2rem;
        border-radius: 10px;
        box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        z-index: 9999;
        animation: slideIn 0.3s ease;
    `;
    notification.textContent = message;
    
    document.body.appendChild(notification);
    
    setTimeout(() => {
        notification.remove();
    }, 3000);
}

// ========================================
// ESTADÍSTICAS
// ========================================

function getStats() {
    return {
        totalProducts: appData.products.length,
        totalClicks: appData.stats.totalClicks,
        totalViews: appData.stats.totalViews,
        avgDiscount: calculateAvgDiscount(),
        topCategory: getTopCategory()
    };
}

function calculateAvgDiscount() {
    if (appData.products.length === 0) return 0;
    
    const total = appData.products.reduce((sum, p) => {
        const discount = ((p.oldPrice - p.price) / p.oldPrice) * 100;
        return sum + discount;
    }, 0);
    
    return Math.round(total / appData.products.length);
}

function getTopCategory() {
    const categories = {};
    appData.products.forEach(p => {
        categories[p.category] = (categories[p.category] || 0) + 1;
    });
    
    return Object.keys(categories).reduce((a, b) => 
        categories[a] > categories[b] ? a : b, 'ninguna'
    );
}

// ========================================
// PWA - SERVICE WORKER
// ========================================

if ('serviceWorker' in navigator) {
    navigator.serviceWorker.register('/service-worker.js')
        .then(reg => console.log('Service Worker registrado'))
        .catch(err => console.log('Error al registrar SW:', err));
}

// ========================================
// CONSOLA DE ADMINISTRACIÓN
// ========================================

// Funciones disponibles en consola del navegador:
window.ofertasML = {
    exportar: exportData,
    stats: getStats,
    productos: () => appData.products,
    limpiar: () => {
        if (confirm('¿Eliminar todos los datos?')) {
            localStorage.removeItem('ofertasMLData');
            location.reload();
        }
    }
};

console.log('🔥 Ofertas ML Hub cargado');
console.log('📊 Usa window.ofertasML para ver comandos disponibles');