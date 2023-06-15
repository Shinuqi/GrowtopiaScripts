FarmWorldID = string.upper(FarmWorldID)
StorageWorld = string.upper(StorageWorld)
StorageWorldSeedID = string.upper(StorageWorldSeedID)
PackDropWorld = string.upper(PackDropWorld)
PackDropWorldID = string.upper(PackDropWorldID)
PickaxeWorld = string.upper(PickaxeWorld)
PickaxeWorldID = string.upper(PickaxeWorldID)
bot.collect_range=4
bot.auto_collect = false
function GonWebhook(Shinuqi)
    local script = [[
    $webHookUrl = "]]..WebhookUrl..[["
    $thumbnailObject = [PSCustomObject]@{
    url = "https://cdn.discordapp.com/emojis/1016295109970645022.gif?size=80&quality=lossless"
    }
    $color = Get-Random -Minimum 0 -Maximum 16777215
    $title = 'Shinuqi#2111 - Rotation'
    $description = "**]]..Shinuqi..[[**"
  
    $footer = [PSCustomObject]@{
        icon_url = "https://cdn.discordapp.com/emojis/978628955907170314.gif?size=96&quality=lossless"
        text = "]].."Shinuqi#2111 | Date : "..(os.date"%d/%m/%y":upper().." Hour : ")..os.date("%I")..":"..os.date("%M").." "..os.date("%p"):upper()..[["
    }
  
    $embedObject = [PSCustomObject]@{
        color = $color
        title = $title
        description = $description
        thumbnail = $thumbnailObject
        footer = $footer
    }
  
    [System.Collections.ArrayList]$embedArray = @()
    $embedArray.Add($embedObject)
  
    $payload = [PSCustomObject]@{
        embeds = $embedArray
    }
    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
    Invoke-RestMethod -Uri $webHookUrl -Body ($payload | ConvertTo-Json -Depth 4) -Method Post -ContentType 'application/json'
    ]]
  
    local pipe = io.popen("powershell -command -", "w")
    pipe:write(script)
    pipe:close()
end

function join(a,b) 
    sleep(3000)
    bot:sendPacket(3,"action|join_request\nname|"..a.."|"..b.."\ninvitedWorld|0")
    sleep(6000)
    Dunyadami = tostring(world.name)
    if Dunyadami == "" or Dunyadami == "EXIT" then
    	join(a,b)
    end
    AnlikYer()
    if Dunyadami ~= "" or Dunyadami ~= "EXIT" then
        if world:getTile(Botx,Boty).fg == 6 then
            join(a,b)
        end
    end
end

function scanTree(id)
    countReady = 0
    countUnready = 0
   	for _, tile in pairs(world:getTiles()) do 
        if tile.fg == id and tile:canHarvest() then
            countReady = countReady + 1
        else
            countUnready = countUnready + 1
		end
    end 
    countUnready = countUnready - 3360
    return { Ready = countReady, Unready = countUnready }
end

function tarama(ids)
  fosel = 0
  for _, tile in pairs(world:getTiles()) do 
      if tile.fg == ids then 
          fosel = fosel + 1
      end
  end
  return {miktr = fosel}
end

function floats(idz)
  float = 0
  for _,obj in pairs(world:getObjects()) do 
      if obj.id == idz then 
          float = float + obj.count
      end
  end
  return {ucanlar = float}
end

function AnlikYer()
    if bot.status ~= 1 then
        GonWebhook("Bot Offline ".."<@" .. YourDiscordid .. ">")
        while bot.status ~= 1 do
            bot:connect()
            sleep(10000)
        end
	sleep(5000)
        GonWebhook("Bot Back To Online ".."<@" .. YourDiscordid .. ">")
    end
    Dunyadami = tostring(world.name)
    if Dunyadami ~= "" and Dunyadami ~= "EXIT" then
        localbot = world:getLocal()
        if localbot then
            Botx = math.floor(localbot.posx / 32) 
            Boty = math.floor(localbot.posy / 32)
        end
    end
end

function Reconnect(list)
    if bot.status ~= 1 then
        GonWebhook("Bot Offline ".."<@" .. YourDiscordid .. ">")
        while bot.status ~= 1 do
            bot:connect()
            sleep(10000)
        end
	sleep(5000)
        GonWebhook("Bot Back To Online ".."<@" .. YourDiscordid .. ">")
        join(list,FarmWorldID)
    end
    if world.name ~= list then
        join(list,FarmWorldID)
    end
    AnlikYer()
    Dunyadami = tostring(world.name)
    if Dunyadami ~= "" and Dunyadami ~= "EXIT" then
        if world:getTile(Botx,Boty).fg == 6 then
            join(list,FarmWorldID)
        end
    end
end

function Reconnectdropseed()
    if bot.status ~= 1 then
        GonWebhook("Bot Offline ".."<@" .. YourDiscordid .. ">")
        while bot.status ~= 1 do
            bot:connect()
            sleep(10000)
        end
	sleep(5000)
        GonWebhook("Bot Back To Online ".."<@" .. YourDiscordid .. ">")
        join(StorageWorld,StorageWorldSeedID)
    end
    if world.name ~= StorageWorld then
        join(StorageWorld,StorageWorldSeedID)
    end
    AnlikYer()
    Dunyadami = tostring(world.name)
    if Dunyadami ~= "" and Dunyadami ~= "EXIT" then
        if world:getTile(Botx,Boty).fg == 6 then
            join(StorageWorld,StorageWorldSeedID)
        end
    end
end

function Reconnectdroppack()
    if bot.status ~= 1 then
        GonWebhook("Bot Offline ".."<@" .. YourDiscordid .. ">")
        while bot.status ~= 1 do
            bot:connect()
            sleep(10000)
        end
	sleep(5000)
        GonWebhook("Bot Back To Online ".."<@" .. YourDiscordid .. ">")
        join(PackDropWorld,PackDropWorldID)
    end
    if world.name ~= PackDropWorld then
        join(PackDropWorld,PackDropWorldID)
    end
    AnlikYer()
    Dunyadami = tostring(world.name)
    if Dunyadami ~= "" and Dunyadami ~= "EXIT" then
        if world:getTile(Botx,Boty).fg == 6 then
            join(PackDropWorld,PackDropWorldID)
        end
    end
end

function harvest(list) 
    Reconnect(list)
    bot.auto_collect = true
    for i, tile in ipairs(world:getTiles()) do
        Reconnect(list)
        if tile.fg == SeedID and tile:canHarvest() then
            Reconnect(list)
            bot:findPath(tile.x,tile.y)
            sleep(delayHarvest)
            if bot.status == 1 then
                if world:getTile(tile.x,tile.y).fg == SeedID or world:getTile(tile.x,tile.y).bg == SeedID then
		    if bot:isInTile(tile.x,tile.y) then
                    	bot:hit(tile.x,tile.y)
		    else
		    	bot:findPath(tile.x,tile.y)
			sleep(delayHarvest)
			bot:hit(tile.x,tile.y)
		    end
                    sleep(delayHarvest) 
                end
            else
                Reconnect(list)
            end
            if bot.status == 1 then
                if world:getTile(tile.x,tile.y).fg == SeedID or world:getTile(tile.x,tile.y).bg == SeedID then
                    if bot:isInTile(tile.x,tile.y) then
                    	bot:hit(tile.x,tile.y)
		    else
		    	bot:findPath(tile.x,tile.y)
			sleep(delayHarvest)
			bot:hit(tile.x,tile.y)
		    end
                    sleep(delayHarvest) 
                end
            else
                Reconnect(list)    
            end
        end
        if inventory:getItemCount(BlockID) >= 150 then
            break
        end
    end
end

AgacHazir = 0
function Hazir(list)
    if world.name ~= list then
        join(list,FarmWorldID)
    end
    AgacHazir = 0
    for i, tile in ipairs(world:getTiles()) do
        if tile:canHarvest() then
            if tile.fg == SeedID or tile.bg == SeedID then
                AgacHazir = 1
            end
        end 
    end
    return AgacHazir
end

function Dropf(list)
    while bot.gem_count > pricepack do
        bot:sendPacket(2, "action|buy\nitem|"..packname)
        sleep(3000) -- you can change delay
    end
    if inventory:getItemCount(BlockID+1) >= 100 then
        bot.auto_collect = false
        Reconnectdropseed()
        join(StorageWorld,StorageWorldSeedID)
        while (inventory:getItemCount(BlockID+1) > 0) do
            Reconnectdropseed()
            sleep(500)
            bot:drop(BlockID+1, inventory:getItemCount(BlockID+1))
            sleep(500)
            bot:moveLeft()
        end
        GonWebhook("<:growbot:992058196439072770> Bot Name : "..bot.name..
        "\n <a:World:997157064008810620> Current World : "..world.name..
        "\n <a:online:1007062631787544666> Status : "..bot.status..
        "\n <:pepper_tree_seed:1012630107715797073> Dropped Seed : "..floats(BlockID+1).ucanlar..
        "\n <:pepper_tree_seed:1012630107715797073> Dropped Block : "..floats(BlockID).ucanlar)
    end 
    if inventory:getItemCount(PackitemID) > PackDropCount then
        bot.auto_collect = false
        Reconnectdroppack()
        join(PackDropWorld,PackDropWorldID)
        while inventory:getItemCount(PackitemID) > PackDropCount do
            Reconnectdroppack()
            sleep(500)
            bot:drop(PackitemID,inventory:getItemCount(PackitemID))
            sleep(500)
            bot:moveLeft()
        end
        GonWebhook("<:growbot:992058196439072770> Bot Name : "..bot.name..
        "\n <a:World:997157064008810620> Current World : "..world.name..
        "\n <a:online:1007062631787544666> Status : "..bot.status..
        "\n <:gems:994218103032520724> Dropped Pack : "..floats(PackitemID).ucanlar)
    end
end

function TrashTheJunks()
    for i, trash in ipairs(trashList) do
        if inventory:getItemCount(trash) > WhenTrashCount then
            bot:trash(trash, inventory:getItemCount(trash))
            sleep(1000)
        end
    end
end

function plant(list)
    Reconnect(list)
    for i, tile in ipairs(world:getTiles()) do
		Reconnect(list)
        if bot.status == 1 then
            if 0 == world:getTile(tile.x, tile.y).fg and 0 ~= world:getTile(tile.x, tile.y + 1).fg and world:getTile(tile.x, tile.y + 1).fg ~= SeedID and inventory:getItemCount(SeedID) > 0 then
                Reconnect(list)
                bot:findPath(tile.x,tile.y)
                sleep(PlantDelay)
		if bot:isInTile(tile.x,tile.y) then
                	bot:place(tile.x,tile.y,SeedID)
			sleep(PlantDelay)
		else
			bot:findPath(tile.x,tile.y)
                	sleep(PlantDelay)
			if bot:isInTile(tile.x,tile.y) then
				bot:place(tile.x,tile.y,SeedID)
				sleep(PlantDelay)
			end
		end
            end
        else
            Reconnect(list)
        end
    end
end

function OnlineControl()
    if bot.status ~= 1 then
        GonWebhook("<@" .. YourDiscordid .. ">".."\n<:growbot:992058196439072770> | Bot Name : "..bot.name.."\n<:mega:984686541383290940> | Information : Bot Is Offline Trying To Reconnect.... \n<:red_circle:987661002868936774> | Status : Offline ")
        while bot.status ~= 1 do
            bot:connect()
            sleep(10000)
        end
        GonWebhook("<@" .. YourDiscordid .. ">".."\n<:growbot:992058196439072770> | Bot Name : "..bot.name.."\n<:mega:984686541383290940> | Information : Bot Is Back Online\n<a:online:1007062631787544666> | Status : Online\n<a:World:997157064008810620>")
    end
end

function tilealfg(x,y)
    OnlineControl()
    AnlikYer()
    Dunyadami = tostring(world.name)
    if Dunyadami ~= "" and Dunyadami ~= "EXIT" then
        tilefgx = world:getTile(x,y).fg
        return {tilefg = tilefgx}
    end
end

function tilealbg(x,y)
    OnlineControl()
    AnlikYer()
    Dunyadami = tostring(world.name)
    if Dunyadami ~= "" and Dunyadami ~= "EXIT" then
        tilebgx = world:getTile(x,y).bg
        return {tilebg = tilebgx}
    end
end


BotPxz = BotPx-1
BotPyz = BotPy-1
function PNB(list)
    PickaxeControl()
    Reconnect(list)
    bot.auto_collect = true
    bot:findPath(BotPxz,BotPyz)
    sleep(2000)
    while inventory:getItemCount(BlockID) > 0 do
        Reconnect(list)
        AnlikYer()

        if BotPxz ~= Botx and BotPyz ~= BotY then
            bot:findPath(BotPxz,BotPyz)
            sleep(2000)
            AnlikYer()
        end
        if tilealfg(Botx-1,Boty).tilefg == 0 then 
	if bot:isInTile(Botx,Boty) then
            bot:place(Botx-1,Boty,BlockID)
            sleep(delayplace)
	end
        end
        if tilealfg(Botx-1,Boty+1).tilefg == 0 then
	if bot:isInTile(Botx,Boty) then
            bot:place(Botx-1,Boty+1,BlockID)
            sleep(delayplace) 
	    end
        end
        if tilealfg(Botx-1,Boty-1).tilefg == 0 then
	if bot:isInTile(Botx,Boty) then
            bot:place(Botx-1,Boty-1,BlockID)
            sleep(delayplace) 
	    end
        end
        while (tilealfg(Botx-1,Boty).tilefg ~= 0 or tilealbg(Botx,Boty).tilebg ~= 0) do
            Reconnect(list)
            if BotPxz ~= Botx and BotPyz ~= BotY then
                bot:findPath(BotPxz,BotPyz)
                sleep(1000)
                AnlikYer()
            end
	    if bot:isInTile(Botx,Boty) then
            bot:hit(Botx-1,Boty) 
            sleep(delaybreak) 
	    end
        end
        while (tilealfg(Botx-1,Boty+1).tilefg ~= 0 or tilealbg(Botx-1,Boty+1).tilebg ~= 0) do
            Reconnect(list)
            if BotPxz ~= Botx and BotPyz ~= BotY then
                bot:findPath(BotPxz,BotPyz)
                sleep(1000)
                AnlikYer()
            end
	    if bot:isInTile(Botx,Boty) then
            bot:hit(Botx-1,Boty+1)
            sleep(delaybreak) 
	    end
        end
        while (tilealfg(Botx-1,Boty-1).tilefg ~= 0 or tilealbg(Botx-1,Boty-1).tilebg ~= 0) do
            Reconnect(list)
            if BotPxz ~= Botx and BotPyz ~= BotY then
                bot:findPath(BotPxz,BotPyz)
                sleep(1000)
                AnlikYer()
            end
	    if bot:isInTile(Botx,Boty) then
            bot:hit(Botx-1,Boty-1) 
            sleep(delaybreak) 
	    end
        end

    end
end

startT = os.time()
function SecondTT(seconds)
  local seconds = tonumber(seconds)
  if seconds <= 0 then
    return "00:00:00";
  else
    hours = string.format("%02.f", math.floor(seconds/3600));
    mins = string.format("%02.f", math.floor(seconds/60 - (hours*60)));
    secs = string.format("%02.f", math.floor(seconds - hours*3600 - mins *60));
    return hours..":"..mins..":"..secs
  end
end

isOwner = true

local message = "Farm Worlds:\n"
for i = 1, #farmWorlds do
    message = message ..i.. ". " .. farmWorlds[i] .. "\n"
end
GonWebhook("<:growbot:992058196439072770> Bot Name : "..bot.name..
"\n <a:online:1007062631787544666> Status : "..bot.status..
"\n <:gems:994218103032520724> "..message)


function takeP()
    for _, obj in pairs(world:getObjects()) do
      if obj.id == 98 then
        xp = math.floor(obj.x / 32)
        yp = math.floor(obj.y / 32)
        bot:findPath(xp,yp)
        sleep(1000)
        bot.auto_collect = true 
        sleep(500)
        bot.auto_collect = false
        if inventory:getItemCount(98) > 0 then
          break
        end
      end
    end
end

function dropPick()
    bot:sendPacket(2, "action|drop\n|itemID|" .. 98)
    bot:sendPacket(2, "action|dialog_return\ndialog_name|drop_item\nitemID|" .. 98 .. "|\ncount|" .. inventory:getItemCount(98) - 1)
    sleep(1000)
end

function PickaxeControl()
    if TakePickaxe == "yes" and inventory:getItemCount(98) == 0 then
        join(PickaxeWorld,PickaxeWorldID)
        sleep(500)
        takeP()
        sleep(3000)
        if inventory:getItemCount(98) > 0 then
            bot:wear(98)
            sleep(2000)
            dropPick()
            sleep(1000)
            if inventory:getItemCount(98) > 1 then
                join(PickaxeWorld,PickaxeWorldID)
                dropPick()
                sleep(1000)
            end
            GonWebhook(bot.name.." took the pickaxe rotation starts"..
            "\n Left Pickaxe : "..floats(98).ucanlar)
        else
            GonWebhook(bot.name.." bot failed to pick up, tries again.")
            while inventory:getItemCount(98) == 0 do
                sleep(5000)
                join(PickaxeWorld,PickaxeWorldID)
                sleep(500)
                takeP()
                sleep(3000)
                if inventory:getItemCount(98) > 0 then
                    bot:wear(98)
                    sleep(2000)
                    dropPick()
                    sleep(1000)
                    if inventory:getItemCount(98) > 1 then
                        join(PickaxeWorld,PickaxeWorldID)
                        dropPick()
                        sleep(1000)
                    end
                end
            end
            GonWebhook(bot.name.." took the pickaxe rotation starts"..
            "\n Left Pickaxe : "..floats(98).ucanlar)
        end
    end
    if inventory:getItemCount(98) > 1 then
        join(PickaxeWorld,PickaxeWorldID)
        dropPick()
        sleep(1000)
    end
end

PickaxeControl()

botcuk = bot.name
dinlenme = 0
while isOwner == true do
    for _, list in pairs(farmWorlds) do
        list = string.upper(list)
        Reconnect(list)
        PickaxeControl()
        if world.name ~= list then
            join(list,FarmWorldID)
        end
        GonWebhook("<:growbot:992058196439072770> Bot Name : "..botcuk..
        "\n <a:World:997157064008810620> Current World : "..world.name..
        "\n <a:online:1007062631787544666> Status : "..bot.status..
        "\n <:peppertree:999318156696887378> Ready Tree : "..scanTree(BlockID+1).Ready..
        "\n <:peppertree:999318156696887378> Unready Tree : "..scanTree(BlockID+1).Unready..
        "\n <:Fossil:997497957848989737> Fossil : "..tarama(3918).miktr..
        "\n <:jam:987145988470898758> UpTime Bot : "..SecondTT(os.difftime(os.time(), startT)))
        Hazir(list)
        while AgacHazir == 1 do
            sleep(3000) 
            Reconnect(list)
            if inventory:getItemCount(BlockID) <= 150 then
                if world.name ~= list then
                    join(list,FarmWorldID)
                end
                TrashTheJunks()
                harvest(list)
                sleep(1000)
            end
            if inventory:getItemCount(BlockID) >= 150 then
                if world.name ~= list then
                    join(list,FarmWorldID)
                end
                TrashTheJunks()
                PNB(list)
                sleep(1000)
            end
            if inventory:getItemCount(BlockID+1) > 0 and PLantSeed == "yes" then
                if world.name ~= list then
                    join(list,FarmWorldID)
                end
                sleep(1000)
                plant(list)
                sleep(500)
            end
            while bot.gem_count > pricepack do
                bot:sendPacket(2, "action|buy\nitem|"..packname)
                sleep(3000) -- you can change delay
            end
            if inventory:getItemCount(PackitemID) > PackDropCount then
                sleep(1000)
                Dropf()
                if world.name ~= list then
                    join(list,FarmWorldID)
                end
            end
            if inventory:getItemCount(BlockID+1) >= 100 then
                sleep(1000)
                Dropf()
                if world.name ~= list then
                    join(list,FarmWorldID)
                end
            end
            Hazir(list)
        end
        dinlenme = dinlenme + 1
        if restBot == "yes" and dinlenme == restWorldComplete then 
            sleep(restMiliSecond)
            dinlenme = 0
        end
    end
end
