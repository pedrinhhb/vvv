local player = game.Players.LocalPlayer

-- Função para criar semente realista
local function criarSemente(nome)
	local semente = Instance.new("Part")
	semente.Name = nome
	semente.Size = Vector3.new(1, 1, 1)
	semente.Position = player.Character.HumanoidRootPart.Position + Vector3.new(0, 3, -4)
	semente.Anchored = false
	semente.CanCollide = true
	semente.Shape = Enum.PartType.Ball
	semente.Material = Enum.Material.SmoothPlastic
	semente.BrickColor = BrickColor.new(nome == "CandyBlossomSeed" and "Pink" or "Really blue")
	semente.TopSurface = Enum.SurfaceType.Smooth
	semente.BottomSurface = Enum.SurfaceType.Smooth
	semente.Parent = workspace

	-- Billboard com nome
	local tag = Instance.new("BillboardGui", semente)
	tag.Size = UDim2.new(0, 100, 0, 40)
	tag.AlwaysOnTop = true
	tag.StudsOffset = Vector3.new(0, 2, 0)

	local label = Instance.new("TextLabel", tag)
	label.Size = UDim2.new(1, 0, 1, 0)
	label.Text = "🌸 " .. (nome == "CandyBlossomSeed" and "Candy Blossom" or "Moon Blossom")
	label.TextScaled = true
	label.BackgroundTransparency = 1
	label.TextColor3 = Color3.fromRGB(255, 200, 255)

	return semente
end

-- Interface simples com botões
local gui = Instance.new("ScreenGui", player:WaitForChild("PlayerGui"))
gui.Name = "SpecialSeedSpawner"

local frame = Instance.new("Frame", gui)
frame.Size = UDim2.new(0, 200, 0, 140)
frame.Position = UDim2.new(0.5, -100, 0.3, -70)
frame.BackgroundColor3 = Color3.fromRGB(30, 30, 30)
frame.BorderSizePixel = 0
frame.Active = true
frame.Draggable = true

local title = Instance.new("TextLabel", frame)
title.Size = UDim2.new(1, 0, 0, 40)
title.Text = "🌙 Spawn Especial"
title.Font = Enum.Font.GothamBold
title.TextSize = 20
title.TextColor3 = Color3.new(1, 1, 1)
title.BackgroundColor3 = Color3.fromRGB(153, 50, 204)

local btn1 = Instance.new("TextButton", frame)
btn1.Size = UDim2.new(1, -20, 0, 40)
btn1.Position = UDim2.new(0, 10, 0, 50)
btn1.Text = "🍬 Candy Blossom"
btn1.Font = Enum.Font.Gotham
btn1.TextSize = 18
btn1.BackgroundColor3 = Color3.fromRGB(255, 105, 180)
btn1.TextColor3 = Color3.new(1, 1, 1)

btn1.MouseButton1Click:Connect(function()
	criarSemente("CandyBlossomSeed")
end)

local btn2 = Instance.new("TextButton", frame)
btn2.Size = UDim2.new(1, -20, 0, 40)
btn2.Position = UDim2.new(0, 10, 0, 100)
btn2.Text = "🌕 Moon Blossom"
btn2.Font = Enum.Font.Gotham
btn2.TextSize = 18
btn2.BackgroundColor3 = Color3.fromRGB(100, 149, 237)
btn2.TextColor3 = Color3.new(1, 1, 1)

btn2.MouseButton1Click:Connect(function()
	criarSemente("MoonBlossomSeed")
end)
