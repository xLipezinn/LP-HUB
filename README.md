-- Configurações
local fruitName = "Dragon Fruit" -- Nome do fruto que você deseja farmar
local farmLocation = Vector3.new(-1234, 50, 789) -- Localização do farm

-- Variáveis
local player = game.Players.LocalPlayer
local character = player.Character
local humanoid = character.Humanoid

-- Função para farmar frutos
local function farmFruits()
    -- Verificar se o jogador está próximo do local de farm
    if (character.HumanoidRootPart.Position - farmLocation).Magnitude < 10 then
        -- Procurar frutos na área
        for _, fruit in pairs(game.Workspace:GetDescendants()) do
            if fruit.Name == fruitName and fruit:IsA("Model") then
                -- Pegar o fruto
                player.Character.HumanoidRootPart.CFrame = fruit.CFrame
                wait(0.5)
                game.ReplicatedStorage.FruitPick:FireServer(fruit)
            end
        end
    end
end

-- Loop infinito para farmar frutos
while true do
    farmFruits()
    wait(1)
end


-- Configurações
local teleportLocation = Vector3.new(-1234, 50, 789) -- Localização para teleportar

-- Variáveis
local player = game.Players.LocalPlayer
local character = player.Character
local humanoid = character.Humanoid

-- Função para teleportar
local function teleport()
    character.HumanoidRootPart.CFrame = CFrame.new(teleportLocation)
end

-- Loop infinito para teleportar
while true do
    teleport()
    wait(5)
end
