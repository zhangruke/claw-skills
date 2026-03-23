---
name: weather
description: Query weather for a city. Usage /weather Beijing or /weather 上海
user-invocable: true
allowed-tools:
  - Bash(curl *)
---

# /weather — Weather Query

Query real-time weather for any city using wttr.in API.

Arguments passed: `$ARGUMENTS`

---

## Dispatch on Arguments

### With city name

The user provides a city name (Chinese or English), e.g. `/weather Beijing`, `/weather 上海`.

Steps:

1. Extract the city name from `$ARGUMENTS`. If Chinese, use it directly — wttr.in supports Chinese city names.

2. Run the following curl command to get JSON weather data:
   ```
   curl -s "wttr.in/{city}?format=j1&lang=zh"
   ```

3. Also fetch a compact text summary for display:
   ```
   curl -s "wttr.in/{city}?format=%l:+%C+%t+%h+%w+%P&lang=zh"
   ```

4. Parse the JSON response and present a clean weather report in this format:

   **{city} 天气报告**

   | 指标 | 当前 |
   |---|---|
   | 天气 | {description} |
   | 温度 | {temp_C}°C (体感 {FeelsLikeC}°C) |
   | 湿度 | {humidity}% |
   | 风速 | {windspeedKmph} km/h {winddir16Point} |
   | 气压 | {pressure} hPa |
   | 能见度 | {visibility} km |
   | 紫外线指数 | {uvIndex} |

   **未来 3 天预报：**

   | 日期 | 天气 | 最高温 | 最低温 |
   |---|---|---|---|
   | ... | ... | ...°C | ...°C |

5. If the curl command fails or returns an error, tell the user the city name may be incorrect and suggest retrying.

### No args

If `$ARGUMENTS` is empty, ask the user to provide a city name. Example: "请提供城市名，例如 `/weather 北京`"

---

## Implementation Notes

- wttr.in supports Chinese city names directly (e.g. `wttr.in/北京`)
- URL-encode the city name if it contains spaces
- Use `lang=zh` parameter for Chinese output
- If the response contains "Unknown location", inform the user
- Keep the output concise and readable
