import zipfile
import os

# Crear estructura básica de archivos para la página web de PerfumeR
base_path = "/mnt/data/PerfumeR_Web"
os.makedirs(base_path, exist_ok=True)

# Archivo index.html básico con catálogo, imágenes de stock y contacto WhatsApp
html_content = """
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1" />
    <title>Catálogo PerfumeR</title>
    <style>
        body { background-color: #000; color: #d4af37; font-family: Arial, sans-serif; margin: 0; padding: 0; }
        header { padding: 20px; text-align: center; border-bottom: 1px solid #d4af37; }
        header h1 { margin: 0; font-size: 2.5em; }
        .catalog { display: flex; flex-wrap: wrap; justify-content: center; gap: 20px; padding: 20px; }
        .product { background: #111; border: 1px solid #d4af37; border-radius: 10px; width: 250px; padding: 15px; box-sizing: border-box; transition: transform 0.3s; }
        .product:hover { transform: scale(1.05); }
        .product img { width: 100%; border-radius: 10px; }
        .product h2 { font-size: 1.3em; margin: 10px 0 5px 0; }
        .product p { font-size: 1em; margin: 5px 0; }
        footer { text-align: center; padding: 15px; border-top: 1px solid #d4af37; font-size: 1.1em; }
        a.whatsapp { color: #25d366; font-weight: bold; text-decoration: none; }
        a.whatsapp:hover { text-decoration: underline; }
    </style>
</head>
<body>
    <header>
        <h1>PerfumeR</h1>
        <p>Catálogo digital de perfumes - Honduras</p>
    </header>
    <main class="catalog">
        <div class="product">
            <img src="https://images.unsplash.com/photo-1506744038136-46273834b3fb?auto=format&fit=crop&w=400&q=80" alt="Perfume 1" />
            <h2>Perfume Elegance</h2>
            <p>Fragancia fresca y duradera para todo el día.</p>
            <p><strong>L 1,200</strong></p>
        </div>
        <div class="product">
            <img src="https://images.unsplash.com/photo-1504198453319-5ce911bafcde?auto=format&fit=crop&w=400&q=80" alt="Perfume 2" />
            <h2>Perfume Classic</h2>
            <p>Aroma clásico y sofisticado para eventos especiales.</p>
            <p><strong>L 1,500</strong></p>
        </div>
        <div class="product">
            <img src="https://images.unsplash.com/photo-1519710164239-da123dc03ef4?auto=format&fit=crop&w=400&q=80" alt="Perfume 3" />
            <h2>Perfume Night</h2>
            <p>Intenso y seductor para la noche.</p>
            <p><strong>L 1,700</strong></p>
        </div>
    </main>
    <footer>
        Contacto por WhatsApp: <a href="https://wa.me/50431725213" target="_blank" class="whatsapp">+504 3172-5213</a>
    </footer>
</body>
</html>
"""

# Guardar index.html
with open(os.path.join(base_path, "index.html"), "w", encoding="utf-8") as f:
    f.write(html_content)

# Crear archivo zip
zip_filename = "/mnt/data/PerfumeR_Web_Comprimido.zip"
with zipfile.ZipFile(zip_filename, 'w') as zipf:
    for foldername, subfolders, filenames in os.walk(base_path):
        for filename in filenames:
            file_path = os.path.join(foldername, filename)
            arcname = os.path.relpath(file_path, base_path)
            zipf.write(file_path, arcname)

zip_filename
