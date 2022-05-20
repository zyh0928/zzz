## Chonky Character Sheet

- **comment row** _367_
- **row 383**: `btnfont1:SetText(_G["SPELL_STAT"..primaryStat.."_NAME"]) -- Primary Stat`
- **row 542**: `btnfont1:SetText(ITEM_MOD_VERSATILITY) -- Versatility`

## Default Soulbind Pack

- **row 66**: `if frame and frame:IsShown() and frame.text:GetText():find("盟约") then`
- **row 73**: `if(msg:find("深厚联结")) then`

## Efficient Stats - Shadowlands

- **delete row** _64_ - _70_
- **add**: `primaryToken = _G["SPELL_STAT"..mainStatID.."_NAME"]`

- Text

  ```fundamental
  function ()
    local s = {}
    s.primary = string.format(aura_env.primaryColor .. "%s: %d", aura_env.primaryToken or "Primary", aura_env.primaryStat or 0)
    s.haste = string.format(aura_env.hasteColor .. _G["STAT_HASTE"] .. ": %.2f%%", aura_env.haste or 0)
    s.crit = string.format(aura_env.critColor .. _G["STAT_CRITICAL_STRIKE"] .. ": %.2f%%", aura_env.crit or 0)
    s.mastery = string.format(aura_env.masteryColor .. _G["STAT_MASTERY"] .. ": %.2f%%", aura_env.mastery or 0)
    s.vers = string.format(aura_env.versatilityColor .. _G["STAT_VERSATILITY"] .. ": %.2f%% / %.2f%%", aura_env.versDmgBonus or 0, aura_env.versDR or 0)
    s.dodge = string.format(aura_env.dodgeColor .._G["STAT_DODGE"] .. ": %.2f%%", aura_env.dodge or 0)
    s.block = string.format(aura_env.blockColor .. _G["STAT_BLOCK"] .. ": %.2f%%", aura_env.block or 0)
    s.leech = string.format(aura_env.leechColor .. _G["STAT_LIFESTEAL"] .. ": %.2f%%", aura_env.leech or 0)
    s.speed = string.format(aura_env.speedColor .. _G["STAT_MOVEMENT_SPEED"] .. ": %.0f%%", aura_env.speed or 0)
    s.armor = string.format(aura_env.armorColor .. _G["STAT_ARMOR"] .. ": %d", aura_env.armor or 0)
    s.avoidance = string.format(aura_env.avoidanceColor .. _G["STAT_AVOIDANCE"] .. ": %.2f%%", aura_env.avoidance or 0)
    s.parry = string.format(aura_env.parryColor .. _G["STAT_PARRY"] .. ": %.2f%%", aura_env.parry or 0)


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
