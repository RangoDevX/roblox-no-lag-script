# roblox-no-lag-script
for _, part in pairs(game.Workspace:GetDescendants()) do
    if part:IsA("BasePart") then
        part.Material = Enum.Material.SmoothPlastic
        part.Reflectance = 0
        part.CastShadow = false
    end
end

for _, obj in pairs(game.Workspace:GetDescendants()) do
    if obj:IsA("ParticleEmitter") or obj:IsA("Trail") or obj:IsA("Smoke") or obj:IsA("Fire") then
        obj.Enabled = false
    end
end

game.Players.PlayerAdded:Connect(function(player)
    player.CharacterAdded:Connect(function(character)
        local head = character:WaitForChild("Head", 5)
        if head then
            for _, decal in pairs(head:GetChildren()) do
                if decal:IsA("Decal") and decal.Name == "face" then
                    decal:Destroy()
                end
            end
        end
    end)
end)

if game.Lighting:FindFirstChildOfClass("Sky") then
    game.Lighting:FindFirstChildOfClass("Sky"):Destroy()
end

for _, obj in pairs(game.Workspace:GetDescendants()) do
    if obj:IsA("Model") and obj.Name:lower():find("tree") then
        obj:Destroy()
    end
end
