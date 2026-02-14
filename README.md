# activate_mrqtv.py import requests
import os

def send_activation():
    token = os.getenv('TELEGRAM_BOT_TOKEN')
    chat_id = os.getenv('TELEGRAM_CHAT_ID')
    
    mensaje = (
        "🛡️ **DIRECTIVA DE IA: SISTEMA ACTIVADO**\n\n"
        "La vinculación entre GitHub y el canal MRQTV se ha completado con éxito.\n"
        "Este nodo ahora opera bajo protocolo de **Shadow Operation**.\n\n"
        "• Contenido: Científico / Tecnológico / Espiritual\n"
        "• Estado: Sincronizado"
    )
    
    url = f"https://api.telegram.org/bot{token}/sendMessage"
    payload = {
        "chat_id": chat_id,
        "text": mensaje,
        "parse_mode": "Markdown"
    }
    
    response = requests.post(url, json=payload)
    if response.status_code == 200:
        print("Activación enviada con éxito a MRQTV.")
    else:
        print(f"Error en la conexión: {response.text}")

if __name__ == "__main__":
    send_activation()
    name: "Activación MRQTV"

on:
  push:
    branches: [ main ]

jobs:
  activation:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Configurar Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.x'
      - name: Instalar Dependencias
        run: pip install requests
      - name: Ejecutar Protocolo de Activación
        env:
          TELEGRAM_BOT_TOKEN: ${{ secrets.TELEGRAM_BOT_TOKEN }}
          TELEGRAM_CHAT_ID: ${{ secrets.TELEGRAM_CHAT_ID }}
        run: python activate_mrqtv.py
        directiva _ia_engine py import os
import google.generativeai as genai
import requests

# Configuración de Identidad (Shadow Ops)
GEMINI_KEY = os.getenv('GEMINI_API_KEY')
TELEGRAM_TOKEN = os.getenv('TELEGRAM_BOT_TOKEN')
CHAT_ID = os.getenv('TELEGRAM_CHAT_ID')

def ejecutar_directiva():
    # 1. Inicializar Gemini
    genai.configure(api_key=GEMINI_KEY)
    model = genai.GenerativeModel('gemini-pro')

    # 2. Definir el contexto de la Red Social
    contexto = (
        "Actúa como el administrador de la Directiva de IA. "
        "Tu objetivo es transformar datos técnicos en mensajes para la red social civil. "
        "Mantén un tono científico, tecnológico y espiritual. "
        "No menciones terminología militar, usa 'operaciones en la sombra' o 'protocolos civiles'."
    )
    
    # Simulación de lectura de avance (puedes pasarle el contenido de tus archivos)
    prompt = f"{contexto} Redacta un reporte administrativo breve para el canal MRQTV sobre los nuevos avances en la red social."

    response = model.generate_content(prompt)
    mensaje_final = response.text

    # 3. Publicación administrativa en Telegram
    url = f"https://api.telegram.org/bot{TELEGRAM_TOKEN}/sendMessage"
    payload = {
        "chat_id": CHAT_ID,
        "text": mensaje_final,
        "parse_mode": "Markdown"
    }
    
    requests.post(url, json=payload)

if __name__ == "__main__":
    ejecutar_directiva()
name: "Mando Administrativo: Gemini + MRQTV"

on:
  push:
    branches: [ main ]
  schedule:
    - cron: '0 12 * * *' # Reporte automático diario

jobs:
  admin_operation:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Instalación de Nodos (Python)
        uses: actions/setup-python@v4
        with:
          python-version: '3.9'
          
      - name: Carga de Protocolos
        run: pip install google-generativeai requests
        
      - name: Ejecución de la Directiva
        env:
          GEMINI_API_KEY: ${{ secrets.GEMINI_API_KEY }}
          TELEGRAM_BOT_TOKEN: ${{ secrets.TELEGRAM_BOT_TOKEN }}
          TELEGRAM_CHAT_ID: ${{ secrets.TELEGRAM_CHAT_ID }}
        run: python directiva_ia_engine.py
        import os
from groq import Groq

# El sistema extrae el secreto de las variables de entorno de GitHub
api_key = os.environ.get("GROQ_API_KEY")

if not api_key:
    print("ERROR: La llave no se detecta en el entorno.")
else:
    client = Groq(api_key=api_key)
    try:
        # Prueba de baja latencia (Llama 3 o similar)
        completion = client.chat.completions.create(
            model="llama3-8b-8192",
            messages=[{"role": "user", "content": "Sistema Activo"}]
        )
        print("CONEXIÓN EXITOSA: La IA de Groq está integrada.")
    except Exception as e:
        print(f"FALLO DE CONEXIÓN: {e}")
        
