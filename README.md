local player = game.Players.LocalPlayer
local gui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
gui.Name = "ScriptExecutor"

local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 400, 0, 250)
frame.Position = UDim2.new(0.3, 0, 0.3, 0)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame.Active = true
frame.Draggable = true

local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1, 0, 0, 30)
title.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
title.Text = "🧠 Angel's Executor GUI"
title.TextColor3 = Color3.new(1, 1, 1)
title.Font = Enum.Font.SourceSansBold
title.TextSize = 20

local box = Instance.new("TextBox", frame)
box.Position = UDim2.new(0, 10, 0, 40)
box.Size = UDim2.new(1, -20, 1, -90)
box.MultiLine = true
box.ClearTextOnFocus = false
box.TextWrapped = true
box.Text = "-- Cole seu script aqui"
box.TextXAlignment = Enum.TextXAlignment.Left
box.TextYAlignment = Enum.TextYAlignment.Top
box.Font = Enum.Font.Code
box.TextSize = 16
box.TextColor3 = Color3.new(1, 1, 1)
box.BackgroundColor3 = Color3.fromRGB(45, 45, 45)

local button = Instance.new("TextButton", frame)
button.Position = UDim2.new(0.5, -60, 1, -40)
button.Size = UDim2.new(0, 120, 0, 30)
button.Text = "▶️ Executar Angel"
button.Font = Enum.Font.SourceSansBold
button.TextSize = 18
button.TextColor3 = Color3.new(1, 1, 1)
button.BackgroundColor3 = Color3.fromRGB(70, 130, 180)

button.MouseButton1Click:Connect(function()
    local success, err = pcall(function()
        loadstring(game:HttpGet("https://raw.githubusercontent.com/Shadow6698/angels-executer/main/angels-executer.lua"))()
    end)

    if not success then
        warn("Erro ao executar Angel's Executer:", err)
    end
end)
