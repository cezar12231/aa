# -- Criando a GUI
local gui = Instance.new("ScreenGui")
local button = Instance.new("TextButton")

-- Configurações do GUI
gui.Parent = game.Players.LocalPlayer:WaitForChild("PlayerGui")
button.Parent = gui
button.Text = "Ativar"
button.Size = UDim2.new(0, 200, 0, 50)
button.Position = UDim2.new(0.5, -100, 0.5, -25)

-- Variável para rastrear o estado
local ativo = false
local autoToque

-- Função para simular toque automático
local function tocarNaTela()
    while ativo do
        wait(0.5) -- Intervalo entre toques (0.5 segundos)
        -- Substitua por sua lógica de clique
        print("Toque automático!")
    end
end

-- Evento de clique no botão
button.MouseButton1Click:Connect(function()
    ativo = not ativo
    if ativo then
        button.Text = "Desativar"
        autoToque = coroutine.create(tocarNaTela)
        coroutine.resume(autoToque)
    else
        button.Text = "Ativar"
    end
end)
