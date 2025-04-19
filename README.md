-- LocalScript em StarterGui

-- Criar GUI principal
local ScreenGui = Instance.new("ScreenGui", game.Players.LocalPlayer:WaitForChild("PlayerGui"))
ScreenGui.Name = "ScriptExecutor"
ScreenGui.ResetOnSpawn = false

-- Frame principal
local MainFrame = Instance.new("Frame", ScreenGui)
MainFrame.Size = UDim2.new(0, 400, 0, 250)
MainFrame.Position = UDim2.new(0.3, 0, 0.3, 0)
MainFrame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
MainFrame.BorderSizePixel = 0
MainFrame.Active = true
MainFrame.Draggable = true -- Permite arrastar com o mouse

-- Título
local Title = Instance.new("TextLabel", MainFrame)
Title.Size = UDim2.new(1, 0, 0, 30)
Title.BackgroundColor3 = Color3.fromRGB(40, 40, 40)
Title.Text = "🧠 Script Executor"
Title.TextColor3 = Color3.new(1, 1, 1)
Title.Font = Enum.Font.SourceSansBold
Title.TextSize = 20
Title.BorderSizePixel = 0

-- Caixa de texto para script
local TextBox = Instance.new("TextBox", MainFrame)
TextBox.Position = UDim2.new(0, 10, 0, 40)
TextBox.Size = UDim2.new(1, -20, 1, -90)
TextBox.MultiLine = true
TextBox.ClearTextOnFocus = false
TextBox.TextWrapped = true
TextBox.Text = "-- Cole seu script aqui"
TextBox.TextXAlignment = Enum.TextXAlignment.Left
TextBox.TextYAlignment = Enum.TextYAlignment.Top
TextBox.Font = Enum.Font.Code
TextBox.TextSize = 16
TextBox.TextColor3 = Color3.new(1, 1, 1)
TextBox.BackgroundColor3 = Color3.fromRGB(45, 45, 45)
TextBox.BorderSizePixel = 0

-- Botão de executar
local ExecuteButton = Instance.new("TextButton", MainFrame)
ExecuteButton.Position = UDim2.new(0.5, -60, 1, -40)
ExecuteButton.Size = UDim2.new(0, 120, 0, 30)
ExecuteButton.Text = "▶️ Executar"
ExecuteButton.Font = Enum.Font.SourceSansBold
ExecuteButton.TextSize = 18
ExecuteButton.TextColor3 = Color3.new(1, 1, 1)
ExecuteButton.BackgroundColor3 = Color3.fromRGB(70, 130, 180)
ExecuteButton.BorderSizePixel = 0

-- Função para executar
ExecuteButton.MouseButton1Click:Connect(function()
	local scriptCode = TextBox.Text
	local success, result = pcall(function()
		loadstring(scriptCode)()
	end)
	
	if not success then
		warn("Erro ao executar:", result)
	end
end)
