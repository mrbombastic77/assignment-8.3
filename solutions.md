HTML
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Magazine Layout — CSS Grid Areas</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <div class="magazine-container">
        <!-- 1. Header Section -->
        <header class="mag-header">
            <h1>The Developer Gazette</h1>
            <p>Insights, Tutorials, and Trends in Modern Software Engineering</p>
        </header>

        <!-- 1. Navigation Section -->
        <nav class="mag-nav">
            <ul>
                <li><a href="#" class="active">Latest</a></li>
                <li><a href="#">Frontend</a></li>
                <li><a href="#">Backend</a></li>
                <li><a href="#">DevOps</a></li>
                <li><a href="#">Opinion</a></li>
            </ul>
        </nav>

        <!-- 1. Main Article Section -->
        <main class="mag-main">
            <article class="featured-article">
                <span class="category-tag">Featured Story</span>
                <h2>Mastering CSS Grid Areas for Complex Magazine Layouts</h2>
                <p class="article-meta">Published on November 7, 2026 by Atim Akhtar</p>
                <p>CSS Grid Template Areas provide a powerful and intuitive way to design magazine and news layouts without relying on complex floating or multi-column hacks. By visually mapping out semantic sections directly in your CSS, developers can build robust, responsive web pages that maintain crystal-clear structure and readability.</p>
                <p>In this article, we explore how named grid areas allow you to rearrange entire page layouts across different viewports simply by redefining the template string in a media query. Whether you're building a multi-author publication or a high-density dashboard, grid areas simplify structural maintenance.</p>
            </article>
        </main>

        <!-- 1. Sidebar Section -->
        <aside class="mag-sidebar">
            <div class="sidebar-widget">
                <h3>Trending Topics</h3>
                <ul>
                    <li><a href="#">Semantic HTML5 & Accessibility</a></li>
                    <li><a href="#">Flexbox vs. CSS Grid: When to Use Which</a></li>
                    <li><a href="#">Modern JavaScript ES6+ Features</a></li>
                    <li><a href="#">Building Accessible Forms</a></li>
                </ul>
            </div>
            <div class="sidebar-widget">
                <h3>Editor's Pick</h3>
                <p>Check out our latest walkthrough on establishing design systems using CSS variables and tokens.</p>
            </div>
        </aside>

        <!-- 1. Footer Section -->
        <footer class="mag-footer">
            <p>&copy; 2026 The Developer Gazette, Invertis University. All rights reserved.</p>
        </footer>
    </div>
</body>
</html>
CSS
/* style.css */
:root {
    --primary-color: #0284c7;
    --secondary-color: #0f172a;
    --accent-color: #b91c1c;
    --bg-color: #f8fafc;
    --surface-color: #ffffff;
    --text-color: #334155;
    --text-muted: #64748b;
    --border-color: #cbd5e1;
    
    --space-sm: 8px;
    --space-md: 16px;
    --space-lg: 24px;
    --space-xl: 32px;
    
    --radius-md: 8px;
    --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.05);
}

* {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
}

body {
    font-family: Georgia, serif; /* Traditional magazine typography style */
    background-color: var(--bg-color);
    color: var(--text-color);
    line-height: 1.7;
}

/* 2 & 3. Magazine Grid Container & Template Areas */
.magazine-container {
    display: grid;
    max-width: 1200px;
    margin: 2rem auto;
    padding: 0 var(--space-md);
    gap: var(--space-lg);
    
    /* 5. Main article gets significantly more horizontal space than sidebar (2fr vs 1fr) */
    grid-template-columns: 2fr 1fr;
    grid-template-rows: auto auto 1fr auto;
    grid-template-areas:
        "header header"
        "nav nav"
        "main sidebar"
        "footer footer";
}

/* 4. Assigning Named Grid Areas */
.mag-header {
    grid-area: header;
    background-color: var(--secondary-color);
    color: var(--surface-color);
    text-align: center;
    padding: 2.5rem var(--space-lg);
    border-radius: var(--radius-md);
}

.mag-header h1 {
    font-family: Arial, sans-serif;
    font-size: 2.5rem;
    letter-spacing: 1px;
    margin-bottom: 0.5rem;
}

.mag-header p {
    font-family: Arial, sans-serif;
    color: #94a3b8;
    font-size: 1.1rem;
}

.mag-nav {
    grid-area: nav;
    background-color: var(--surface-color);
    border-top: 2px solid var(--secondary-color);
    border-bottom: 2px solid var(--border-color);
    padding: var(--space-sm) var(--space-md);
}

.mag-nav ul {
    list-style: none;
    display: flex;
    justify-content: center;
    gap: var(--space-xl);
}

.mag-nav a {
    font-family: Arial, sans-serif;
    text-decoration: none;
    color: var(--text-color);
    font-weight: bold;
    font-size: 0.95rem;
    transition: color 0.2s ease;
}

.mag-nav a:hover,
.mag-nav a.active {
    color: var(--primary-color);
}

.mag-main {
    grid-area: main;
    background-color: var(--surface-color);
    border: 1px solid var(--border-color);
    border-radius: var(--radius-md);
    padding: var(--space-xl);
    box-shadow: var(--shadow-sm);
}

.category-tag {
    font-family: Arial, sans-serif;
    background-color: #fee2e2;
    color: var(--accent-color);
    font-size: 0.75rem;
    font-weight: bold;
    padding: 4px 10px;
    border-radius: 4px;
    text-transform: uppercase;
    display: inline-block;
    margin-bottom: var(--space-md);
}

.featured-article h2 {
    font-family: Arial, sans-serif;
    font-size: 2rem;
    color: var(--secondary-color);
    line-height: 1.3;
    margin-bottom: var(--space-sm);
}

.article-meta {
    font-family: Arial, sans-serif;
    font-size: 0.875rem;
    color: var(--text-muted);
    margin-bottom: var(--space-lg);
    border-bottom: 1px solid var(--border-color);
    padding-bottom: var(--space-sm);
}

.featured-article p {
    margin-bottom: var(--space-md);
    font-size: 1.05rem;
}

.mag-sidebar {
    grid-area: sidebar;
    display: flex;
    flex-direction: column;
    gap: var(--space-lg);
}

.sidebar-widget {
    background-color: var(--surface-color);
    border: 1px solid var(--border-color);
    border-radius: var(--radius-md);
    padding: var(--space-lg);
    box-shadow: var(--shadow-sm);
}

.sidebar-widget h3 {
    font-family: Arial, sans-serif;
    font-size: 1.15rem;
    color: var(--secondary-color);
    margin-bottom: var(--space-md);
    border-bottom: 2px solid var(--primary-color);
    padding-bottom: var(--space-sm);
}

.sidebar-widget ul {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: var(--space-sm);
}

.sidebar-widget a {
    font-family: Arial, sans-serif;
    color: var(--primary-color);
    text-decoration: none;
    font-size: 0.95rem;
}

.sidebar-widget a:hover {
    text-decoration: underline;
}

.sidebar-widget p {
    font-size: 0.95rem;
    color: var(--text-muted);
}

.mag-footer {
    grid-area: footer;
    background-color: var(--secondary-color);
    color: var(--surface-color);
    text-align: center;
    padding: var(--space-lg);
    border-radius: var(--radius-md);
    font-family: Arial, sans-serif;
    font-size: 0.875rem;
}

/* Responsive layout adjustment for smaller viewports */
@media (max-width: 768px) {
    .magazine-container {
        grid-template-columns: 1fr;
        grid-template-areas:
            "header"
            "nav"
            "main"
            "sidebar"
            "footer";
    }
    
    .mag-nav ul {
        flex-direction: column;
        align-items: center;
        gap: var(--space-sm);
    }
}