--[[
    🌑 Huy Hợp Hub Pro Max V6
    ✅ Full Chức Năng - Tiếng Việt - No Key
    ✅ Menu Auto Mở 100% + Hotkey Insert
    ✅ Logo TH Gaming
    🔥 Made by Huy Hợp Team
]]

print("🔰 Huy Hợp Hub V6 Đang Tải...")

local Players = game:GetService("Players")
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local Workspace = game:GetService("Workspace")
local TeleportService = game:GetService("TeleportService")
local UserInputService = game:GetService("UserInputService")
local player = Players.LocalPlayer

-- GUI Library
local OrionLib = loadstring(game:HttpGet("https://raw.githubusercontent.com/shlexware/Orion/main/source"))()
local Window = OrionLib:MakeWindow({
    Name = "🌑 Huy Hợp Hub - TH",
    HidePremium = false,
    SaveConfig = false,
    IntroText = "🚀 Đang khởi động Huy Hợp Hub...",
    ConfigFolder = "HuyHopHub"
})

---------------------------------------------------
-- ⚔️ Ví dụ 1 tab Auto Farm (các tab khác giữ nguyên như V5)
---------------------------------------------------
local FarmTab = Window:MakeTab({
    Name = "⚔️ Auto Farm",
    Icon = "rbxassetid://6034287525"
})

FarmTab:AddToggle({
    Name = "Auto Farm Level",
    Default = false,
    Callback = function(Value)
        _G.AutoFarm = Value
        while _G.AutoFarm do task.wait()
            pcall(function()
                local char = player.Character
                if char and char:FindFirstChild("HumanoidRootPart") then
                    for _,v in pairs(Workspace.Enemies:GetChildren()) do
                        if v:FindFirstChild("Humanoid") and v.Humanoid.Health > 0 then
                            char.HumanoidRootPart.CFrame = v.HumanoidRootPart.CFrame * CFrame.new(0,5,0)
                            ReplicatedStorage.Remotes.CommF_:InvokeServer("Attack")
                            break
                        end
                    end
                end
            end)
        end
    end
})

---------------------------------------------------
-- 🖼️ LOGO TH
---------------------------------------------------
local Logo = Instance.new("TextLabel")
Logo.Parent = game:GetService("CoreGui"):FindFirstChild("Orion"):FindFirstChild("OrionLib").MainFrame
Logo.Text = "ＴＨ"
Logo.TextColor3 = Color3.fromRGB(255,0,0)
Logo.Font = Enum.Font.Arcade
Logo.TextScaled = true
Logo.BackgroundTransparency = 1
Logo.Size = UDim2.new(0,100,0,50)
Logo.Position = UDim2.new(0.85,0,0,0)

---------------------------------------------------
-- HOTKEY Insert: Mở / Tắt Menu
---------------------------------------------------
local OrionUI = game:GetService("CoreGui"):FindFirstChild("Orion")
UserInputService.InputBegan:Connect(function(input, gpe)
    if not gpe and input.KeyCode == Enum.KeyCode.Insert then
        if OrionUI.Enabled then
            OrionUI.Enabled = false
        else
            OrionUI.Enabled = true
        end
    end
end)

---------------------------------------------------
-- Khởi động GUI
---------------------------------------------------# Huy-hub-blox-fruit-
