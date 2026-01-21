-- ⚠️ ALERTA: Este script pode travar seu computador/jogo
-- Use com EXTREMO cuidado e por sua conta e risco

local Players = game:GetService("Players")
local RunService = game:GetService("RunService")
local Workspace = game:GetService("Workspace")
local Lighting = game:GetService("Lighting")
local Terrain = Workspace:FindFirstChildOfClass("Terrain")
local HttpService = game:GetService("HttpService")
local CoreGui = game:GetService("CoreGui")
local UserInputService = game:GetService("UserInputService")

print("⚡ HYPERLAG GENERATOR INICIANDO...")
print("⚠️ AVISO: Isso pode causar travamentos!")

local Player = Players.LocalPlayer
local LagLevel = 10 -- 1-10 (10 = máximo)

-- Função para criar objetos massivos
local function createMassiveObjects()
    print("📦 Criando objetos massivos...")
    
    for i = 1, LagLevel * 50 do
        task.spawn(function()
            local part = Instance.new("Part")
            part.Size = Vector3.new(100, 100, 100)
            part.Position = Vector3.new(
                math.random(-500, 500),
                math.random(50, 200),
                math.random(-500, 500)
            )
            part.Anchored = true
            part.CanCollide = true
            part.Material = Enum.Material.Neon
            part.Color = Color3.fromHSV(i/100, 1, 1)
            part.Parent = Workspace
            
            -- Adiciona scripts pesados
            local script = Instance.new("Script")
            script.Source = [[
                while true do
                    for i = 1, 1000 do
                        local a = math.sin(tick())
                        local b = math.cos(tick())
                        local c = a * b * i
                    end
                    wait()
                end
            ]]
            script.Parent = part
        end)
    end
end

-- Função para criar partículas extremas
local function createExtremeParticles()
    print("✨ Criando partículas extremas...")
    
    local emitter = Instance.new("ParticleEmitter")
    emitter.Rate = 1000 * LagLevel
    emitter.Lifetime = NumberRange.new(5, 10)
    emitter.Size = NumberSequence.new({
        NumberSequenceKeypoint.new(0, 5),
        NumberSequenceKeypoint.new(1, 20)
    })
    emitter.Transparency = NumberSequence.new({
        NumberSequenceKeypoint.new(0, 0),
        NumberSequenceKeypoint.new(1, 1)
    })
    emitter.Speed = NumberRange.new(50, 100)
    emitter.SpreadAngle = Vector2.new(180, 180)
    emitter.Parent = Workspace
    
    -- Cria múltiplos emitters
    for i = 1, LagLevel * 5 do
        task.spawn(function()
            local newEmitter = emitter:Clone()
            newEmitter.Parent = Workspace
        end)
    end
end

-- Função para criar loops infinitos pesados
local function createHeavyLoops()
    print("🔄 Criando loops pesados...")
    
    for i = 1, LagLevel * 20 do
        task.spawn(function()
            while true do
                -- Loop matemático pesado
                for x = 1, 10000 do
                    local value = math.sin(x) * math.cos(x) * math.tan(x)
                    local array = {}
                    for y = 1, 100 do
                        table.insert(array, {x = x, y = y, value = value})
                    end
                end
                
                -- Cria tabelas gigantes
                local hugeTable = {}
                for j = 1, 5000 do
                    hugeTable[j] = {
                        data = string.rep("LAG", 100),
                        number = math.random(1, 1000000),
                        nested = {
                            a = {b = {c = {d = {e = "DEEP"}}}},
                            array = {}
                        }
                    }
                    for k = 1, 100 do
                        table.insert(hugeTable[j].nested.array, k)
                    end
                end
                
                task.wait(0.01)
            end
        end)
    end
end

-- Função para sobrecarregar a memória
local function overloadMemory()
    print("💾 Sobrecarregando memória...")
    
    local memoryHog = {}
    
    for i = 1, LagLevel * 10000 do
        task.spawn(function()
            memoryHog[i] = {
                string = string.rep("MEMORY_HOG", 100),
                number = i,
                table = {},
                nested = {
                    level1 = {level2 = {level3 = {level4 = {level5 = "DEEP"}}}}
                }
            }
            
            -- Adiciona mais dados
            for j = 1, 100 do
                memoryHog[i].table[j] = {
                    data = HttpService:GenerateGUID(false),
                    timestamp = tick()
                }
            end
        end)
    end
end

-- Função para criar múltiplas conexões
local function createMultipleConnections()
    print("🔗 Criando múltiplas conexões...")
    
    for i = 1, LagLevel * 100 do
        RunService.RenderStepped:Connect(function()
            -- Cálculos pesados a cada frame
            local startTime = tick()
            while tick() - startTime < 0.001 do
                local complex = math.sin(tick()) * math.cos(tick())
                local matrix = {}
                for x = 1, 10 do
                    matrix[x] = {}
                    for y = 1, 10 do
                        matrix[x][y] = complex * x * y
                    end
                end
            end
        end)
    end
    
    -- Conexões de heartbeat
    for i = 1, LagLevel * 50 do
        RunService.Heartbeat:Connect(function(delta)
            -- Mais cálculos
            local total = 0
            for j = 1, 1000 do
                total = total + math.sqrt(j) * math.log(j + 1)
            end
        end)
    end
end

-- Função para criar efeitos visuais extremos
local function createExtremeVisuals()
    print("🎨 Criando efeitos visuais extremos...")
    
    -- Modifica a iluminação constantemente
    task.spawn(function()
        while true do
            Lighting.Brightness = math.sin(tick()) * 5 + 5
            Lighting.OutdoorAmbient = Color3.fromHSV(math.sin(tick()), 1, 1)
            Lighting.ColorShift_Bottom = Color3.fromHSV(math.cos(tick()), 1, 1)
            Lighting.ColorShift_Top = Color3.fromHSV(math.sin(tick() * 2), 1, 1)
            task.wait()
        end
    end)
    
    -- Cria múltiplas telas de GUI
    for i = 1, LagLevel * 10 do
        task.spawn(function()
            local screenGui = Instance.new("ScreenGui")
            screenGui.Parent = CoreGui
            
            for j = 1, 100 do
                local frame = Instance.new("Frame")
                frame.Size = UDim2.new(0, 50, 0, 50)
                frame.Position = UDim2.new(
                    math.random(), 0,
                    math.random(), 0
                )
                frame.BackgroundColor3 = Color3.fromHSV((i+j)/100, 1, 1)
                frame.BorderSizePixel = 0
                frame.Parent = screenGui
                
                -- Anima a frame
                task.spawn(function()
                    while true do
                        frame.Rotation = tick() * 100
                        frame.BackgroundTransparency = math.sin(tick() + j) * 0.5 + 0.5
                        task.wait()
                    end
                end)
            end
        end)
    end
end

-- Função para criar scripts recursivos
local function createRecursiveScripts()
    print("📝 Criando scripts recursivos...")
    
    local function createScript(parent, depth)
        if depth > 5 then return end
        
        local script = Instance.new("Script")
        script.Source = [[
            local data = {}
            for i = 1, 1000 do
                data[i] = {
                    value = math.sin(tick() + i),
                    array = {}
                }
                for j = 1, 100 do
                    table.insert(data[i].array, j * math.cos(tick()))
                end
            end
        ]]
        
        script.Parent = parent
        
        -- Cria scripts filhos
        for i = 1, 3 do
            createScript(script, depth + 1)
        end
    end
    
    for i = 1, LagLevel do
        createScript(Workspace, 1)
    end
end

-- Função para criar rede massiva
local function createMassiveNetwork()
    print("🌐 Criando rede massiva...")
    
    for i = 1, LagLevel * 5 do
        task.spawn(function()
            while true do
                -- Simula requisições de rede
                local success, result = pcall(function()
                    return HttpService:GetAsync("http://httpbin.org/delay/1", true)
                end)
                
                -- Processa dados "recebidos"
                if success then
                    local fakeData = string.rep("NETWORK_DATA", 1000)
                    for j = 1, 100 do
                        local processed = string.gsub(fakeData, "DATA", tostring(j))
                    end
                end
                
                task.wait(0.1)
            end
        end)
    end
end

-- Função para sobrecarregar a física
local function overloadPhysics()
    print("⚙️ Sobrecarregando física...")
    
    if Terrain then
        for i = 1, LagLevel * 100 do
            task.spawn(function()
                Terrain:FillBlock(
                    Region3.new(
                        Vector3.new(math.random(-500, 500), 0, math.random(-500, 500)),
                        Vector3.new(math.random(10, 50), 50, math.random(10, 50))
                    ),
                    4, -- Material
                    10 -- Collision group
                )
            end)
        end
    end
    
    -- Cria muitas partes físicas
    for i = 1, LagLevel * 200 do
        task.spawn(function()
            local part = Instance.new("Part")
            part.Size = Vector3.new(math.random(5, 20), math.random(5, 20), math.random(5, 20))
            part.Position = Vector3.new(
                math.random(-200, 200),
                math.random(100, 300),
                math.random(-200, 200)
            )
            part.Anchored = false
            part.CanCollide = true
            part.Massless = false
            part.Parent = Workspace
            
            -- Adiciona força
            local bodyForce = Instance.new("BodyForce")
            bodyForce.Force = Vector3.new(
                math.random(-10000, 10000),
                math.random(0, 20000),
                math.random(-10000, 10000)
            )
            bodyForce.Parent = part
        end)
    end
end

-- Função para criar loops de renderização
local function createRenderLoops()
    print("🎥 Criando loops de renderização...")
    
    for i = 1, LagLevel * 20 do
        RunService.RenderStepped:Connect(function()
            -- Manipula muitos objetos
            for _, obj in pairs(Workspace:GetChildren()) do
                if obj:IsA("BasePart") then
                    obj.Color = Color3.fromHSV((tick() + i) % 1, 1, 1)
                    obj.Transparency = math.sin(tick() + i) * 0.5 + 0.5
                end
            end
        end)
    end
end

-- Sistema de controle de lag
local LagController = {
    active = true,
    
    increaseLag = function()
        if LagLevel < 10 then
            LagLevel = LagLevel + 1
            print("📈 Nível de lag aumentado para: " .. LagLevel)
        end
    end,
    
    decreaseLag = function()
        if LagLevel > 1 then
            LagLevel = LagLevel - 1
            print("📉 Nível de lag diminuído para: " .. LagLevel)
        end
    end,
    
    stopLag = function()
        LagController.active = false
        print("🛑 Lag parado!")
        
        -- Limpa algumas coisas (nem tudo será limpo)
        for _, obj in pairs(Workspace:GetChildren()) do
            if obj.Name == "Part" then
                obj:Destroy()
            end
        end
    end
}

-- Controles por teclado
UserInputService.InputBegan:Connect(function(input)
    if input.KeyCode == Enum.KeyCode.F8 then
        LagController.increaseLag()
    elseif input.KeyCode == Enum.KeyCode.F9 then
        LagController.decreaseLag()
    elseif input.KeyCode == Enum.KeyCode.F10 then
        LagController.stopLag()
    end
end)

-- Interface de controle
local function createLagUI()
    local screenGui = Instance.new("ScreenGui")
    screenGui.Name = "LagControllerUI"
    screenGui.Parent = CoreGui
    
    local frame = Instance.new("Frame")
    frame.Size = UDim2.new(0, 250, 0, 150)
    frame.Position = UDim2.new(0.5, -125, 0, 10)
    frame.BackgroundColor3 = Color3.fromRGB(30, 10, 10)
    frame.BackgroundTransparency = 0.2
    frame.BorderSizePixel = 0
    frame.Parent = screenGui
    
    local title = Instance.new("TextLabel")
    title.Size = UDim2.new(1, 0, 0, 30)
    title.BackgroundTransparency = 1
    title.Text = "⚡ HYPERLAG CONTROLLER ⚡"
    title.TextColor3 = Color3.fromRGB(255, 50, 50)
    title.Font = Enum.Font.GothamBold
    title.TextSize = 16
    title.Parent = frame
    
    local levelText = Instance.new("TextLabel")
    levelText.Size = UDim2.new(1, 0, 0, 25)
    levelText.Position = UDim2.new(0, 0, 0.2, 0)
    levelText.BackgroundTransparency = 1
    levelText.Text = "Nível: " .. LagLevel .. "/10"
    levelText.TextColor3 = Color3.fromRGB(255, 100, 100)
    levelText.Font = Enum.Font.Gotham
    levelText.TextSize = 14
    levelText.Name = "LevelText"
    levelText.Parent = frame
    
    local controls = Instance.new("TextLabel")
    controls.Size = UDim2.new(1, 0, 0, 60)
    controls.Position = UDim2.new(0, 0, 0.4, 0)
    controls.BackgroundTransparency = 1
    controls.Text = "CONTROLES:\nF8 - Aumentar Lag\nF9 - Diminuir Lag\nF10 - Parar Lag"
    controls.TextColor3 = Color3.fromRGB(200, 150, 150)
    controls.Font = Enum.Font.Gotham
    controls.TextSize = 12
    controls.Parent = frame
    
    -- Atualiza o nível
    RunService.Heartbeat:Connect(function()
        levelText.Text = "Nível: " .. LagLevel .. "/10"
        levelText.TextColor3 = Color3.fromRGB(
            255,
            math.clamp(255 - LagLevel * 25, 50, 255),
            math.clamp(255 - LagLevel * 25, 50, 255)
        )
    end)
    
    return screenGui
end

-- Inicia tudo
print("🚀 INICIANDO TODOS OS SISTEMAS DE LAG...")

-- Cria UI
createLagUI()

-- Executa todas as funções de lag
task.spawn(createMassiveObjects)
task.wait(0.5)
task.spawn(createExtremeParticles)
task.wait(0.5)
task.spawn(createHeavyLoops)
task.wait(0.5)
task.spawn(overloadMemory)
task.wait(0.5)
task.spawn(createMultipleConnections)
task.wait(0.5)
task.spawn(createExtremeVisuals)
task.wait(0.5)
task.spawn(createRecursiveScripts)
task.wait(0.5)
task.spawn(createMassiveNetwork)
task.wait(0.5)
task.spawn(overloadPhysics)
task.wait(0.5)
task.spawn(createRenderLoops)

print("✅ TODOS OS SISTEMAS DE LAG INICIADOS!")
print("⚠️ O LAG COMEÇARÁ EM 3 SEGUNDOS...")
task.wait(3)

print("💥 LAG ATIVADO! O jogo pode travar a qualquer momento!")
print("🎮 Use F8/F9/F10 para controlar o nível de lag")

-- Sistema de monitoramento
task.spawn(function()
    while LagController.active do
        local memory = collectgarbage("count")
        print(string.format("📊 Status: Lag Nível %d | Memória: %.2f MB", LagLevel, memory/1000))
        task.wait(5)
    end
end)

-- Aviso final
warn("==================================================================")
warn("⚠️  EXTREME WARNING: This script may crash your game/computer!")
warn("⚠️  Use at your own risk!")
warn("⚠️  Press F10 to stop the lag if it gets too intense!")
warn("==================================================================")
