# Elementor Page Copy to Another Elementor Site

![Status](https://img.shields.io/badge/status-stable-brightgreen)
![WordPress](https://img.shields.io/badge/WordPress-6.x-blue)
![Elementor](https://img.shields.io/badge/Elementor-Compatible-orange)
![License](https://img.shields.io/badge/license-MIT-green)
![Cross%20Domain](https://img.shields.io/badge/Cross%20Domain-Yes-success)

A clean and simple method to display an Elementor page from **Site A** inside **Site B** — full-screen, responsive, and without headers/footers — using an iframe and a lightweight code snippet.

---

## ✨ Features

- 🔄 Sync Elementor content across multiple sites  
- 🧼 Clean embed (no header, footer, admin bar)  
- 🌍 Works cross-domain  
- 📱 Fully responsive  
- 🧩 Zero plugin required  
- 🧘 Smooth scrolling (no double scrollbars)  

---

## 1️⃣ Sender Site – Code Snippet

Add this to **functions.php** or the **Code Snippets** plugin:

```php
add_action( 'wp_head', function () {

    // Only run when ?sync_embed=1
    if ( isset($_GET['sync_embed']) && $_GET['sync_embed'] === '1' ) {
        ?>
        <style>
            header.elementor-location-header,
            footer.elementor-location-footer {
                display: none !important;
            }

            html.wp-toolbar,
            body {
                padding-top: 0 !important;
                padding-bottom: 0 !important;
                margin-top: 0 !important;
            }

            #wpadminbar,
            section#pulse-chat-button-wrapper {
                display: none !important;
            }

            .site-header,
            .site-footer {
                display: none !important;
            }
        </style>
        <?php
    }

});
```

Embed URL example:

```
https://example.com/page/?sync_embed=1
```

---

## 2️⃣ Receiver Site – Elementor HTML Widget

Paste this in an **HTML widget**:

```html
<iframe 
    id="syncFrame"
    src="https://autoleasingohnebank.ch/fahrzeugliste/?sync_embed=1"
    style="width:100%; height:100vh; border:0; display:block; overflow:hidden;">
</iframe>
```

Replace with your own embedded page URL.

---

## 3️⃣ Receiver Site – Custom CSS (Full Height + No Outer Scroll)

Add this inside:

**Appearance → Customize → Additional CSS**

```css
body.page-id-7 {
    margin: 0 !important;
    overflow: hidden !important;
}

body.page-id-7 #syncFrame {
    position: fixed;
    width: 100vw;
    height: 100vh;
    border: 0;
    display: block;
    left: 0;
}

body.page-id-7.admin-bar #syncFrame {
    top: 32px;
    height: calc(100vh - 32px);
}
```

---

## 📝 Notes

- Scrolling happens **inside the iframe**, not on the receiver page.  
- SEO belongs to the **source site**.  
- Works cross-domain without plugins.  
- Ideal for listings, landing pages, product grids, or dashboard-style pages.

---

## 📜 License

MIT License — free to use, modify, or integrate into a plugin.

---

## ❤️ Credits

Created by **Adnan Habib**  
Top-rated WordPress & Web Developer  
