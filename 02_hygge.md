# Message Type 2: Hygge

Probably the simplest of all messages used.

| Name            | Type      | Endianness |
| :-------------- | :-------- | :--------- |
| Temperature (C) | `float32` | Little     |
| Humidity (% rh) | `float32` | Little     |

__Example:__
```
                  /-----------------{ 68.524 } Temperature C
                  v          v------{ 71.081 } % Relative Humidity
            +---------+ +---------+
00000000    4A 0C 89 42 79 29 8E 42
```
