# king of cyripto vip signals
from telethon import TelegramClient, events

# 🔹 API credentials (ersetzen mit echten Werten)
api_id = 20614519  # Dein API ID
api_hash = '409b554b0a8ff1b56afb27be0f973e04'  # Dein API Hash

# 🔹 Kanäle (ersetzen mit echten Namen oder IDs)
source_channel = 'sarafi_dehghan'  # Falls nötig, @ hinzufügen oder ID nutzen
target_channel = 'KingOfCryptoSignals_VIP'  # Falls nötig, @ hinzufügen oder ID nutzen

# 🔹 Telegram-Client initialisieren
client = TelegramClient('session_name', api_id, api_hash)

@client.on(events.NewMessage(chats=source_channel))
async def message_handler(event):
    try:
        # Falls Nachricht Text enthält, senden
        if event.message.text:
            await client.send_message(target_channel, event.message.text)
            print(f"✅ Nachricht weitergeleitet: {event.message.text}")
        else:
            await client.send_message(target_channel, event.message)
            print("✅ Nachricht (ohne Text) weitergeleitet.")
    except Exception as e:
        print(f"❌ Fehler beim Weiterleiten: {e}")

print("✅ Bot aktiviert! Überwache den Kanal...")

client.start()
client.run_until_disconnected()  # Verbindung offen halten
