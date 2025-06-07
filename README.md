# 🌤️ Basic_Weather Report Automation – n8n Workflow

This is a small automation project created in n8n, designed to send you a personalized daily weather report directly to your email inbox — every morning at **6 AM**.

---

## 🛠️ What It Does

- ⏰ **Scheduled Trigger** at 6 AM daily
- 🌐 **Fetches Weather Data** using the Open-Meteo API
- 🧠 **Processes the Forecast** with a Python code node
- 📧 **Sends a Personalized Email** with high/low temperature report for the day

---

## 📬 Email Example

> **Subject**: Today's Weather Report  
> **Message**: In Mirpurkhas, the high temperature is 38°C and low temperature is 26°C.

---

## 💡 Workflow Overview

| Step | Node Name         | Description                                  |
|------|-------------------|----------------------------------------------|
| 1    | Manual / Schedule | Triggers the workflow manually or at 6 AM   |
| 2    | get wheather      | Makes API call to Open-Meteo for forecast   |
| 3    | create message     | Python code to generate temperature summary |
| 4    | Gmail             | Sends the email to your inbox               |

---

## 🌐 API Used

- **Open-Meteo API**  
  Endpoint: `https://api.open-meteo.com/v1/forecast?...`

---

## 🐍 Python Logic (in n8n)

```python
# Extract high and low temperature from hourly forecast
hourly_temperatures = weather_data["hourly"]["temperature_2m"]
high_temperature = max(hourly_temperatures[:24])
low_temperature = min(hourly_temperatures[:24])

message = f"In Mirpurkhas, the high temperature is {high_temperature}°C and low temperature is {low_temperature}°C."
