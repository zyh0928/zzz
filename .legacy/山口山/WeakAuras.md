## Chonky Character Sheet

### Character Stats Panel

- **comment row** _374_
- **row 390**: `btnfont1:SetText(_G["SPELL_STAT"..primaryStat.."_NAME"])`
- **row 550**: `btnfont1:SetText(ITEM_MOD_VERSATILITY) -- Versatility`

## Efficient Stats

### Action

- **replace row** _74_ - _81_

  ```lua
  primaryToken = _G["SPELL_STAT"..mainStatID.."_NAME"]
  ```

- **replace row** _23_ - _29_

  ```lua
  haste = not aura_env.config.rawvalues["haste"] and _G["STAT_HASTE"] .. ": %.2f%%" or _G["STAT_HASTE"] .. ": %d",
  crit = not aura_env.config.rawvalues["crit"] and _G["STAT_CRITICAL_STRIKE"] .. ": %.2f%%" or _G["STAT_CRITICAL_STRIKE"] .. ": %d",
  vers = not aura_env.config.rawvalues["vers"] and _G["STAT_VERSATILITY"] .. ": %.2f%% / %.2f%%" or _G["STAT_VERSATILITY"] .. ": %d",
  mastery = not aura_env.config.rawvalues["mastery"] and _G["STAT_MASTERY"] .. ": %.2f%%" or _G["STAT_MASTERY"] .. ": %d",
  leech = not aura_env.config.rawvalues["leech"] and _G["STAT_LIFESTEAL"] .. ": %.2f%%" or _G["STAT_LIFESTEAL"] .. ": %d",
  avoidance = not aura_env.config.rawvalues["avoidance"] and _G["STAT_AVOIDANCE"] .. ": %.2f%%" or _G["STAT_AVOIDANCE"] .. ": %d",
  parry = not aura_env.config.rawvalues["parry"] and _G["STAT_PARRY"] .. ": %.2f%%" or _G["STAT_PARRY"] .. ": %d"
  ```

### Custom Function

```lua
function ()
  local s = {}
  s.primary = string.format(aura_env.primaryColor .. "%s: %d", aura_env.primaryToken or "Primary", aura_env.primaryStat or 0)
  s.haste = string.format(aura_env.hasteColor .. aura_env.formatters["haste"], aura_env.haste or 0)
  s.dodge = string.format(aura_env.dodgeColor .._G["STAT_DODGE"] .. ": %.2f%%", aura_env.dodge or 0)

  s.mastery = string.format(aura_env.masteryColor .. aura_env.formatters["mastery"], aura_env.mastery or 0)
  s.crit = string.format(aura_env.critColor .. aura_env.formatters["crit"], aura_env.crit or 0)

  if not aura_env.config.rawvalues["vers"] then
      s.vers = string.format(aura_env.versatilityColor .. aura_env.formatters["vers"], aura_env.versDmgBonus or 0, aura_env.versDR or 0)
  else
      s.vers = string.format(aura_env.versatilityColor .. aura_env.formatters["vers"], aura_env.versDmgBonus or 0)
  end

  s.speed = string.format(aura_env.speedColor .. _G["STAT_MOVEMENT_SPEED"] .. ": %.0f%%", aura_env.speed or 0)
  s.leech = string.format(aura_env.leechColor .. aura_env.formatters["leech"], aura_env.leech or 0)
  s.block = string.format(aura_env.blockColor .. _G["STAT_BLOCK"] .. ": %.2f%%", aura_env.block or 0)
  s.armor = string.format(aura_env.armorColor .. _G["STAT_ARMOR"] .. ": %d", aura_env.armor or 0)
  s.avoidance = string.format(aura_env.avoidanceColor .. aura_env.formatters["avoidance"], aura_env.avoidance or 0)
  s.parry = string.format(aura_env.parryColor .. _G["STAT_PARRY"].. ": %.2f%%", aura_env.parry or 0)

  local r = ""
  for k, v in pairs(aura_env.disp_order) do
      if aura_env.config.toggles[v] then
          if s[v] ~= nil then
              r =  string.format("%s%s\n", r, s[v])
          end
      end
  end

  return r

end
```
