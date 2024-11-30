if game.PlaceId == 83843456738284 then

    -- Load
    local OrionLib = loadstring(game:HttpGet(('https://raw.githubusercontent.com/shlexware/Orion/main/source')))()

    -- Main
    local Window = OrionLib:MakeWindow({Name = "Title of the library", HidePremium = false, SaveConfig = true, ConfigFolder = "OrionTest"})

    -- Create Auto Click Tab
    local AutoClickTab = Window:MakeTab({
        Name = "Auto Click",
        Icon = "rbxassetid://4483345998",
        PremiumOnly = false
    })

    -- Create Section inside Auto Click Tab
    local AutoClickSection = AutoClickTab:AddSection({
        Name = "Auto Click Section"
    })

    -- Function for Auto Click
    local function AutoClick()
        while _G.AutoClickEnabled do
            game:GetService("ReplicatedStorage").TappingRemote.Tap:FireServer()
            wait(0)  -- Set to the fastest possible speed
        end
    end

    -- Function for Auto Super Click
    local function AutoSuperClick()
        while _G.AutoSuperClickEnabled do
            game:GetService("ReplicatedStorage").TappingRemote.SuperTap:FireServer()
            wait(0)  -- Set to the fastest possible speed
        end
    end

    -- Create Checkbox Toggle for Auto Click
    AutoClickSection:AddToggle({
        Name = "Auto Click",
        Default = false,
        Callback = function(Value)
            _G.AutoClickEnabled = Value
            if _G.AutoClickEnabled then
                AutoClick()
            end
        end
    })

    -- Create Checkbox Toggle for Auto Super Click
    AutoClickSection:AddToggle({
        Name = "Auto Super Click",
        Default = false,
        Callback = function(Value)
            _G.AutoSuperClickEnabled = Value
            if _G.AutoSuperClickEnabled then
                AutoSuperClick()
            end
        end
    })

    -- Create Auto Egg Tab
    local AutoEggTab = Window:MakeTab({
        Name = "Auto Egg",
        Icon = "rbxassetid://4483345998",
        PremiumOnly = false
    })

    -- Create Section inside Auto Egg Tab
    local AutoEggSection = AutoEggTab:AddSection({
        Name = "Auto Egg Section"
    })

    -- Function for Auto Egg
    local function AutoEgg()
        while _G.AutoEggEnabled do
            local args = {
                [1] = workspace.Eggs:FindFirstChild("Wild Egg")
            }
            game:GetService("ReplicatedStorage").EggHatchingRemote.HatchServer:InvokeServer(unpack(args))
            wait(0)  -- Set to the fastest possible speed
        end
    end

    -- Create Checkbox Toggle for Auto Egg
    AutoEggSection:AddToggle({
        Name = "Auto Egg",
        Default = false,
        Callback = function(Value)
            _G.AutoEggEnabled = Value
            if _G.AutoEggEnabled then
                AutoEgg()
            end
        end
    })

end
