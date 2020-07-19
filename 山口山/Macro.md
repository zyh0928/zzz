## Common

- 随机密语

  ```fundamental
  #showtooltip
  /run D={"str1","str2","str3"};SendChatMessage(D[random(3)],"Whisper",nil,UnitName"Target")
  /use 灵魂石
  ```

- 敌友双技能

  ```fundamental
  #showtooltips 技能名「不监控技能 CD 可不填」
  /cast [@mouseover,help,exists]友方技能;[@mouseover,harm,exists][harm]敌方技能;友方技能
  ```

## State

- `exists`
