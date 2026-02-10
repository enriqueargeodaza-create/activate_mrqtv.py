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
        
