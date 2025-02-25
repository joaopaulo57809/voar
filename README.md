local player = game.Players.LocalPlayer
local flying = false
local flightSpeed = 50

local button = script.Parent
button.Text = "Ativar Voo"

local function onButtonClicked()
    flying = not flying
    button.Text = flying and "Desativar Voo" or "Ativar Voo"
    
    if flying then
        player.Character.Humanoid.PlatformStand = true
    else
        player.Character.Humanoid.PlatformStand = false
    end
end

button.MouseButton1Click:Connect(onButtonClicked)

game:GetService("RunService").RenderStepped:Connect(function()
    if flying then
        local camera = workspace.CurrentCamera
        local direction = camera.CFrame.LookVector
        player.Character.HumanoidRootPart.Velocity = direction * flightSpeed
    end
end)
