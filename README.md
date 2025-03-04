local Script = Instance.new("Frame")
local TextButton = Instance.new("TextButton")

--Properties:

Script.Name = "Script"
Script.Parent = game.StarterGui.ScreenGui
Script.BackgroundColor3 = Color3.fromRGB(168, 45, 45)
Script.BorderColor3 = Color3.fromRGB(0, 0, 0)
Script.BorderSizePixel = 0
Script.Position = UDim2.new(0.652985096, 0, 0.758130074, 0)
Script.Size = UDim2.new(0, 188, 0, 62)

TextButton.Parent = Script
TextButton.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
TextButton.BorderColor3 = Color3.fromRGB(0, 0, 0)
TextButton.BorderSizePixel = 0
TextButton.Position = UDim2.new(0.0719539598, 0, 0.289462805, 0)
TextButton.Size = UDim2.new(0, 159, 0, 31)
TextButton.Font = Enum.Font.SourceSans
TextButton.Text = "Spam test"
TextButton.TextColor3 = Color3.fromRGB(0, 0, 0)
TextButton.TextSize = 14.000

-- Scripts:

local function BMEJD_fake_script() -- TextButton.LocalScript 
	local script = Instance.new('LocalScript', TextButton)

	local Players = game:GetService("Players")
	local player = Players.LocalPlayer
	local button = script.Parent  -- Assume que o botão já existe
	local isSpamming = false
	
	-- Mensagens para o spamming
	local messages = {"Teste1", "Teste2", "Teste3"}
	
	-- Função para começar o spamming
	local function startSpamming()
		while isSpamming do
			local randomMessage = messages[math.random(1, #messages)]
			game:GetService("ReplicatedStorage").DefaultChatSystemChatEvents.SayMessageRequest:FireServer(randomMessage, "All")
			wait(0.05)  -- Intervalo aleatório de 1 a 3 segundos
		end
	end
	
	-- Função para parar o spamming
	local function stopSpamming()
		isSpamming = false
	end
	
	-- Conectar o evento de clique do botão
	button.MouseButton1Click:Connect(function()
		if not isSpamming then
			isSpamming = true
			startSpamming()
			button.Text = "Parar Spamming"
			button.TextColor3 = Color3.fromRGB(0, 255, 0)
		else
			stopSpamming()
			button.Text = "Iniciar Spamming"
			button.TextColor3 = Color3.fromRGB(255, 0, 0)
		end
	end)
	
end
coroutine.wrap(BMEJD_fake_script)()
