# TKHUPfor i,v in pairs(game:GetService("CoreGui"):GetChildren()) do
    if v.Name == "FluxLib" then
        v:Destroy()
    end
end
--loading ui ddos hub
local ddoshub = loadstring(game:HttpGet("https://raw.githubusercontent.com/MeONaJa1/All-Game/main/Ul%20Lib.lua"))()
--local
local player = game.Players.LocalPlayer
local killauraRange = 60
local distUnderNPC = 0
local waitTimeKillaura = 3
local runSpeeds = 30
local shouldNoClip = false
local mainPageIds = {}
local pages = game:GetService("AssetService"):GetGamePlacesAsync()
local places = {}
local TeleportService = game:GetService("TeleportService")
local gameNAME = ""
--game local
local Shindolife = false
--all fuc need
--noclip
game:getService("RunService"):UnbindFromRenderStep("noclOppl")
	game:getService("RunService"):BindToRenderStep("noclOppl",0,function()
		pcall(function()
			local char = game.Players.LocalPlayer.Character or game.Players.LocalPlayer.CharacterAdded:Wait()
			if shouldNoClip then
				pcall(function()
					local char = game.Players.LocalPlayer.Character or game.Players.LocalPlayer.CharacterAdded:Wait()
					char.Humanoid:ChangeState(11)
				end)
			elseif char.Humanoid:GetState() == 11 then
				pcall(function()
					local char = game.Players.LocalPlayer.Character or game.Players.LocalPlayer.CharacterAdded:Wait()
					char.Humanoid:ChangeState(1)
				end)
			end
		end)
	end)
--find game PlaceId
while true do
	for _,place in pairs(pages:GetCurrentPage()) do
		places[place.Name] = place.PlaceId
	end
	if pages.IsFinished then
		break
	end
	pages:AdvanceToNextPageAsync()
end
--find game
for i,v in pairs(places) do
	if i:lower():find("shindo") then
		Shindolife = true
		gameNAME = "Shindo Life"
	end
end
--------------------------------------------------------------------------------------------------------------------------------------
--check shindolife game

if Shindolife then
--come to sl2 script
--old-antitp bypass
local old
	setreadonly(getrenv().table, false)
	old = hookfunction(getrenv().table.insert, function(tab, ...)
		if #tab == 1 and not checkcaller() then
			for i,v in pairs(tab) do
				if typeof(v) == 'Vector3' or typeof(v) == 'CFrame' then
					return
				end
			end
		end
		return old(tab, ...)
	end)
setreadonly(getrenv().table, true)
--Destroy CCoff
if workspace:FindFirstChild("CCoff") then
		workspace:FindFirstChild("CCoff"):Destroy()
	end
	workspace.ChildAdded:Connect(function(p)
		if p.Name == "CCoff" then
			p:Destroy()
		end
	end)
--variables
local spins = game.Players.LocalPlayer.statz.spins.Value
local lvl = player.statz.lvl.lvl.Value
local mission = player.PlayerGui:WaitForChild("Main"):WaitForChild("ingame"):WaitForChild("Missionstory")
local menuplace = 4616652839
local forestplace = 5447073001
local rainplace = 5084678830
local trainingplace = 5431071837
local akatsukiplace = 5431069982
local worldxplace = 5943874201
local villageplace = game:GetService("Workspace"):FindFirstChild("rank")
local warplace = game:GetService("Workspace"):FindFirstChild("warmode")

-- load ui
local green = "http://www.roblox.com/asset/?id=5459241648"
local red = "http://www.roblox.com/asset/?id=5459241799"

game:GetService("UserInputService").MouseIconEnabled = true --ใช้เม้าส์
-- title doshub
local windon = ddoshub:Window("TK HUB", "shindo Life", Color3.fromRGB(255, 110, 48), Enum.KeyCode.RightShift)
--make 1 tab
local tab = windon:Tab("Quests", "http://www.roblox.com/asset/?id=6023426915")
_G.AutoFarmG = false
tab:Toggle("Auto-Farm", "Auto farm mob", default, function(Value)
	if Value == true then _G.AutoFarmG = true shouldNoClip = true end
		while _G.AutoFarmG do wait(0.1)
			--loop auto Farm
			if Value == false then _G.AutoFarmG = false shouldNoClip = false end --ถ้า value = false auto farm ก็จะ false
			if  player.currentmission.Value == nil then --ถ้าไม่มีเควช
					for i,v in pairs(workspace.missiongivers:GetChildren()) do -- ถึงบรรทักที่ 51 เช็ค npc เควช เขียว
						pcall(function()
							if player.currentmission.Value == nil and v.Name == "" and v:FindFirstChild("Head") and v.Head:FindFirstChild("givemission").Enabled and v.Head.givemission:FindFirstChild("color").Visible  then
								local TALK = v:FindFirstChild("Talk")
								if lvl >= 1 and lvl < 700 then -- เช็ค level มากกว่า 1 และ ร้อยกว่า 700
									if player.currentmission.Value == nil  and v.Talk:FindFirstChild("typ").Value == "defeat" and v.Head.givemission.Enabled and v.Head.givemission.color.Visible and v.Head.givemission.color.Image == green then
										local getmission = v:FindFirstChild("HumanoidRootPart")
										local clienttalk = v:FindFirstChild("CLIENTTALK")
										repeat wait(.1)
											game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,distUnderNPC,0)
											if (player.Character.HumanoidRootPart.Position-v.HumanoidRootPart.Position).Magnitude < 10 then
												clienttalk:FireServer()
												wait(.1)
												clienttalk:FireServer("accept")
											end
										until mission.Visible or v:FindFirstChild("Head").givemission.Enabled == false or player.currentmission.Value == "mission" or not _G.AutoFarmG
									end
								elseif lvl >= 700 then -- มากกว่าหรือเท่ากับ 700
									if player.currentmission.Value == nil and TALK.typ.Value == "defeat" and v.Head.givemission.Enabled and v.Head.givemission.color.Visible and v.Head.givemission.color.Image == green or v.Head.givemission.color.Image == red then
										local getmission = v:FindFirstChild("HumanoidRootPart")
										local clienttalk = v:FindFirstChild("CLIENTTALK")
										repeat wait(.1)
											game.Players.LocalPlayer.Character.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,distUnderNPC,0)
											if (player.Character.HumanoidRootPart.Position-v.HumanoidRootPart.Position).Magnitude < 10 then
												clienttalk:FireServer()
												wait(.1)
												clienttalk:FireServer("accept")
											end
										until mission.Visible or v:FindFirstChild("Head").givemission.Enabled == false or player.currentmission.Value == "mission" or not _G.AutoFarmG
									end
								end
							end
						end)
					end
				else
					for i,v in pairs(workspace.npc:GetChildren()) do --ให้เชคว่ามี npc หรือป่าวถ้ามีก็ปรับเลือดเป็น 0
						pcall(function()
						    if v.ClassName == "Model" and v:FindFirstChild("npctype") and string.find(v.Name, "npc") and v:FindFirstChild("HumanoidRootPart") and v:FindFirstChild("Humanoid") and v.Head.CFrame.Y > -1000 then
								repeat wait(.1)
									local char = game.Players.LocalPlayer.Character
									char.combat.update:FireServer("mouse1", true)
									char.combat.update:FireServer("mouse1", false)
									char.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,distUnderNPC,2)
									wait()
									v.Humanoid.Health = 0
								until v.Humanoid.Health == 0 or not _G.AutoFarmG or player.currentmission.Value == nil
							end
						end)
					end
				end
		end
end)

--สร้าง tab แรกเพื่อให้ user เลือก speed เสร็จแล้วเอาใส่ลงในตัวแปร speed
tab:Slider("Distance", "", 0, -15,0,function(speed)
	distUnderNPC = speed
end)
--สร้าง autoPrestige 
_G.Autorelvl = false
tab:Toggle("Auto Prestige", "rankup", default, function(Value)
	if Value == true then Autorelvl = true end
	while _G.Autorelvl do wait(.1)
		if Value == false then _G.Autorelvl = false end
		if lvl == 1000 then
			game:GetService("Players").LocalPlayer.startevent:FireServer("rankup")
		end
	end
end)
--สร้าง tab 2 เริ่มใหม่
local tab2 = windon:Tab("Auto Spin KG", "http://www.roblox.com/asset/?id=6022668888")
_G.AutoSpin = false
local bs --ตัวแปรไว้เก็บ kg slot ที่ user เลือก
local kgslot --ตัวแปรไว้หา kg slot
local kgvalue --ตัวแปรเก็บ value
local forkg --ตัวแปรไว้เก็บ spin ที่ต้องการ
--สร้าง drop down เลือก kg slot
tab2:Dropdown("Choose an KG Slot:", {"kg1", "kg2", "kg3", "kg4"}, function(kgS)
	bs = kgS
	kgslot = game.Players.LocalPlayer.statz.main:FindFirstChild(bs)
	kgvalue = kgslot.Value
	print(kgslot)
	print(kgvalue)
end)
--ฟังชั่นจัดเรียง table
function metago(a,b)
	return a < b
	end
--สร้างไว้เพื่อหาขีดจำกัดสายเลือกทุกอัน (ชื่อเก่า)
local kgs = {} --เอาไว้เป็นเก็บตัวขีดจำกัดสายเลือดทั้งหมด
	for i,v in pairs(game:GetService("ReplicatedStorage").alljutsu:GetChildren()) do
		if v:FindFirstChild("KG") then
			table.insert(kgs, v.Name)
			table.sort(kgs, metago)
		end
	end
--สร้าง dropdown เพื่อให้ user เลือก kg 
tab2:Dropdown("Spin For:", kgs, function(whokg)
	forkg = whokg
	print(forkg)
end)
--สร้าง Button ไว้ reset log
tab2:Button("RESET DATA (Change logs)", "Reset data", function()
	player.statz.spins:Destroy()
	game:GetService('TeleportService'):Teleport(game.PlaceId, player)
	end)
	--สร้าง Toogle เพื่อเริ่มสุ่ม
tab2:Toggle("Start Spin KG", "ก่อนที่จะใช้ให้เลือก kg slot และ ขีดจำกัดสายเลือดที่ต้องการซะก่อน", default, function(Value)
	if Value == true then _G.AutoSpin = true end
        while _G.AutoSpin do
        kgslot.ChildAdded:Connect(function(yes)
            if yes.Name == "dontspin" then -- จำเป็นต้อง bypass ตัว delay ของ spin kg ก่อน
                wait(.1)
                yes:Destroy() --ทำลายที่ชื่อ dontspinแล้วถึงจะเริ่มสุ่ม
            end
        end)
		local des = game.Players.LocalPlayer.statz.spins
        spawn(function()
            for i,v in pairs(game:GetService("ReplicatedStorage").alljutsu:GetChildren()) do
            	if v:FindFirstChild("KG") then
                    local a = Instance.new("StringValue")
                    a.Name = v.Name
                    a.Parent = game.Players.LocalPlayer.statz.genkailevel
            	end
            end
        end)
        	wait(0.1)
        	if Value == false then _G.AutoSpin = false end
		        if spins > 0 then
            		spins = game.Players.LocalPlayer.statz.spins.Value
            		kgvalue = kgslot.Value
            		print("Rolled: " .. kgvalue)
            		if kgvalue ~= kg1 and kgvalue ~= kg2 and kgvalue ~= kg3 and kgvalue ~= kg4 then
            		    kgvalue = kgslot.Value
            			game.Players.LocalPlayer.startevent:FireServer("spin", bs)
            			wait(.2)
            			kgvalue = kgslot.Value
            		if kgslot.Value == forkg then
            		    print("You have got: " .. kgvalue)
            		    ddoshub:Notification("YOU HAVE GOT: " .. kgvalue, "OMG MOM!!!")
            		    Value = false
            		    _G.AutoSpin = false
            		    break
            		end
            	end
                else
                    player.statz.spins:Destroy()
                    game:GetService('TeleportService'):Teleport(game.PlaceId, player)
		    end
		    end
	end)
--tab33333333333333333333333333
local tab3 = windon:Tab("Game", "http://www.roblox.com/asset/?id=6023426915")
--Kill aura 2
local function killNPC2(npc, iskillaura)
		wait(waitTimeKillaura)
		pcall(function()
			repeat wait()
				npc.Humanoid.Health = npc.Humanoid.MaxHealth
				wait()
				npc.Humanoid.Health = 0
			until
				npc == nil or npc.Parent == nil or npc.fakehealth.Value == 0
		end)
	end
--สร้าง Toggle ไว้เพื่อเรียกใช้งานฟังชั่น killNPC2
_G.Ekill_aura2 = false
tab3:Toggle("KILL Aura (NPC)", "Kill aura mob", default, function(Value)
	if Value == true then _G.Ekill_aura2 = true end
	while _G.Ekill_aura2 do wait(.1)
		if Value == false then _G.Ekill_aura2 = false end
		pcall(function()
			for i,v in pairs(workspace.npc:children'') do
				if (v.HumanoidRootPart.Position - game.Players.LocalPlayer.Character.HumanoidRootPart.Position).magnitude < killauraRange then
					spawn(function()
						killNPC2(v, true)
						end)
				end
			end
			end)
	end
	end)
--Slider กำหนด killauraRange
tab3:Slider("Kill Aura Range", "", 31, 60000,30,function(Value)
	killauraRange = Value
	print(killauraRange)
end)
--runSpeeds
_G.RunSpeed = false
game:GetService('RunService').RenderStepped:Connect(function()
		if _G.RunSpeed then
			local UserInputService = game:GetService("UserInputService")
			local shift = UserInputService:IsKeyDown(Enum.KeyCode.LeftShift)
			if shift then
				pcall(function()
					game.Players.LocalPlayer.Character.Humanoid.WalkSpeed = runSpeeds
				end)
			end
		end
	end)
--สร้าง Toogle โปริ่งเร็ว
tab3:Toggle("Run Speed Modifier", "", default, function(Value)
	_G.RunSpeed = Value
	while _G.RunSpeed do wait(.1)
		if Value == false then _G.RunSpeed = false end
	end
end)
--สร้าง Slider ไว้ให้ set ค่าวิ่งเร็ว
tab3:Slider("+ Run Speed", "", 16, 1000,15,function(speed)
	runSpeeds = speed
end)
--tab4
local tab4 = windon:Tab("Settings", "http://www.roblox.com/asset/?id=6022668888")
--antiafk
_G.AntiAfk = false
local VirtualUser = game:service'VirtualUser'
	game:service'Players'.LocalPlayer.Idled:connect(function()
		if _G.AntiAfk then
			VirtualUser:CaptureController()
			VirtualUser:ClickButton2(Vector2.new())
			warn("AntiAfk")
		end
	end)
--สร้าง Toggle เรียกใช้งาน antiafk
tab4:Toggle("AntiAfk", "", default, function(state)
	_G.AntiAfk = state
	while _G.AntiAfk do wait(.1)
		if state == false then _G.AntiAfk = false end
	end
	end)
--ปุ่มไว้ copy inv discord
tab4:Button("Copy Discord Invite", "", function()
	ddoshub:Notification("Done!", "Alright")
end)
end
