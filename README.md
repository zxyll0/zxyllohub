-- Football Fusion 2 - ZxylloHub GUI (Scrollable Tabs, Hitbox Visual w/ Occlusion, Magnet Sync, Jump/Angle Boosts)
-- By zxyll0 (2025)

local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer
local PlayerGui = LocalPlayer:WaitForChild("PlayerGui")
local UserInputService = game:GetService("UserInputService")
local TweenService = game:GetService("TweenService")
local RunService = game:GetService("RunService")

-- Clean up any previous GUIs
local guiName = "ZxylloHubGui"
if PlayerGui:FindFirstChild(guiName) then
    PlayerGui[guiName]:Destroy()
end

-- Main GUI
local ScreenGui = Instance.new("ScreenGui")
ScreenGui.Name = guiName
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.Parent = PlayerGui

-- Main Frame
local Frame = Instance.new("Frame")
Frame.Size = UDim2.new(0, 781, 0, 457)
Frame.Position = UDim2.new(0.22, 0, 0.17, 0)
Frame.BorderColor3 = Color3.new(0, 0, 0)
Frame.BorderSizePixel = 0
Frame.BackgroundColor3 = Color3.new(0.05, 0.05, 0.07)
Frame.Parent = ScreenGui

-- TopBar (draggable)
local TopBar = Instance.new("Frame")
TopBar.Name = "TopBar"
TopBar.Size = UDim2.new(1, 0, 0, 45)
TopBar.Position = UDim2.new(0, 0, 0, 0)
TopBar.BorderColor3 = Color3.new(0, 0, 0)
TopBar.BorderSizePixel = 0
TopBar.BackgroundColor3 = Color3.new(0.05, 0.05, 0.07)
TopBar.Parent = Frame

local Title = Instance.new("TextLabel")
Title.Name = "Title"
Title.Size = UDim2.new(0, 200, 0, 37)
Title.Position = UDim2.new(0.01, 0, 0.18, 0)
Title.BorderSizePixel = 0
Title.BackgroundColor3 = Color3.new(0.05, 0.05, 0.07)
Title.FontFace = Font.new("rbxasset://fonts/families/LuckiestGuy.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
Title.TextSize = 34
Title.BorderColor3 = Color3.new(0, 0, 0)
Title.Text = " Zxyllo Hub"
Title.TextColor3 = Color3.new(0, 0.67, 0)
Title.Parent = TopBar

-- Draggable TopBar
local UIS = game:GetService("UserInputService")
local dragging, dragInput, dragStart, startPos
TopBar.InputBegan:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseButton1 then
        dragging = true
        dragStart = input.Position
        startPos = Frame.Position
        input.Changed:Connect(function()
            if input.UserInputState == Enum.UserInputState.End then
                dragging = false
            end
        end)
    end
end)
TopBar.InputChanged:Connect(function(input)
    if input.UserInputType == Enum.UserInputType.MouseMovement then
        dragInput = input
    end
end)
UIS.InputChanged:Connect(function(input)
    if input == dragInput and dragging then
        local delta = input.Position - dragStart
        Frame.Position = UDim2.new(startPos.X.Scale, startPos.X.Offset + delta.X, startPos.Y.Scale, startPos.Y.Offset + delta.Y)
    end
end)

-- Sidebar (TabSection)
local TabSection = Instance.new("Frame")
TabSection.Name = "TabSection"
TabSection.Size = UDim2.new(0, 186, 1, -45)
TabSection.Position = UDim2.new(0, 0, 0, 45)
TabSection.BorderColor3 = Color3.new(0,0,0)
TabSection.BorderSizePixel = 0
TabSection.BackgroundColor3 = Color3.new(0.07, 0.07, 0.11)
TabSection.Parent = Frame

local UICorner1 = Instance.new("UICorner")
UICorner1.Parent = TabSection

-- Main Content Area (switches with tabs)
local ContentHolder = Instance.new("Frame")
ContentHolder.Name = "ContentHolder"
ContentHolder.Size = UDim2.new(1, -186, 1, -45)
ContentHolder.Position = UDim2.new(0, 186, 0, 45)
ContentHolder.BackgroundTransparency = 1
ContentHolder.BorderSizePixel = 0
ContentHolder.Parent = Frame

-- Welcome Section (as before)
local UserWelcome = Instance.new("Frame")
UserWelcome.Name = "UserWelcome"
UserWelcome.Size = UDim2.new(0, 186, 0, 70)
UserWelcome.Position = UDim2.new(0, 0, 0, 0)
UserWelcome.BorderColor3 = Color3.new(0,0,0)
UserWelcome.BorderSizePixel = 0
UserWelcome.BackgroundColor3 = Color3.new(0.07, 0.07, 0.11)
UserWelcome.Parent = TabSection

local UICorner2 = Instance.new("UICorner")
UICorner2.Parent = UserWelcome

local ImageLabel = Instance.new("ImageLabel")
ImageLabel.BorderSizePixel = 0
ImageLabel.BackgroundColor3 = Color3.new(1, 1, 1)
ImageLabel.Size = UDim2.new(0, 52, 0, 51)
ImageLabel.Position = UDim2.new(0, 8, 0, 8)
ImageLabel.BorderColor3 = Color3.new(0, 0, 0)
ImageLabel.Parent = UserWelcome

local thumbType = Enum.ThumbnailType.HeadShot
local thumbSize = Enum.ThumbnailSize.Size420x420
local content, isReady = Players:GetUserThumbnailAsync(LocalPlayer.UserId, thumbType, thumbSize)
ImageLabel.Image = content

local WelcomeLabel = Instance.new("TextLabel")
WelcomeLabel.Name = "WelcomeLabel"
WelcomeLabel.BorderSizePixel = 0
WelcomeLabel.BackgroundColor3 = Color3.new(1, 1, 1)
WelcomeLabel.FontFace = Font.new("rbxasset://fonts/families/FredokaOne.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
WelcomeLabel.TextSize = 12
WelcomeLabel.Size = UDim2.new(0, 110, 0, 18)
WelcomeLabel.BorderColor3 = Color3.new(0, 0, 0)
WelcomeLabel.TextColor3 = Color3.new(0.28, 0.28, 0.28)
WelcomeLabel.BackgroundTransparency = 1
WelcomeLabel.Position = UDim2.new(0, 68, 0, 7)
WelcomeLabel.Text = "Welcome"
WelcomeLabel.Parent = UserWelcome

local DisplayNameLabel = Instance.new("TextLabel")
DisplayNameLabel.Name = "DisplayNameLabel"
DisplayNameLabel.BorderSizePixel = 0
DisplayNameLabel.BackgroundColor3 = Color3.new(1, 1, 1)
DisplayNameLabel.FontFace = Font.new("rbxasset://fonts/families/FredokaOne.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
DisplayNameLabel.TextSize = 14
DisplayNameLabel.Size = UDim2.new(0, 110, 0, 18)
DisplayNameLabel.BorderColor3 = Color3.new(0, 0, 0)
DisplayNameLabel.TextColor3 = Color3.new(0.18, 0.18, 0.18)
DisplayNameLabel.BackgroundTransparency = 1
DisplayNameLabel.Position = UDim2.new(0, 68, 0, 27)
DisplayNameLabel.Text = LocalPlayer.DisplayName
DisplayNameLabel.Parent = UserWelcome

local UsernameLabel = Instance.new("TextLabel")
UsernameLabel.Name = "UsernameLabel"
UsernameLabel.BorderSizePixel = 0
UsernameLabel.BackgroundColor3 = Color3.new(1, 1, 1)
UsernameLabel.FontFace = Font.new("rbxasset://fonts/families/FredokaOne.json", Enum.FontWeight.Regular, Enum.FontStyle.Normal)
UsernameLabel.TextSize = 10
UsernameLabel.Size = UDim2.new(0, 110, 0, 15)
UsernameLabel.BorderColor3 = Color3.new(0, 0, 0)
UsernameLabel.TextColor3 = Color3.new(0.24, 0.24, 0.25)
UsernameLabel.BackgroundTransparency = 1
UsernameLabel.Position = UDim2.new(0, 68, 0, 45)
UsernameLabel.Text = "@" .. LocalPlayer.Name
UsernameLabel.Parent = UserWelcome

-- Tabs (SCROLLABLE PAGES)
local tabNames = {"Catching", "Player", "Automatics", "Throwing", "Settings"}
local tabButtons = {}
local tabPages = {}

local tabListHolder = Instance.new("Frame")
tabListHolder.Name = "TabListHolder"
tabListHolder.Size = UDim2.new(1, 0, 1, -80)
tabListHolder.Position = UDim2.new(0, 0, 0, 80)
tabListHolder.BackgroundTransparency = 1
tabListHolder.Parent = TabSection

local tabListLayout = Instance.new("UIListLayout")
tabListLayout.Parent = tabListHolder
tabListLayout.FillDirection = Enum.FillDirection.Vertical
tabListLayout.SortOrder = Enum.SortOrder.LayoutOrder
tabListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center
tabListLayout.VerticalAlignment = Enum.VerticalAlignment.Center

local EVEN_GAP = 10
tabListLayout.Padding = UDim.new(0, EVEN_GAP)

RunService.RenderStepped:Wait()

local numTabs = #tabNames
local tabListHolderHeight = tabListHolder.AbsoluteSize.Y
local allGaps = EVEN_GAP * (numTabs + 1)
local compactTabHeight = math.floor((tabListHolderHeight - allGaps) / numTabs)

local topPad = Instance.new("Frame")
topPad.Size = UDim2.new(1,0,0,EVEN_GAP)
topPad.BackgroundTransparency = 1
topPad.BorderSizePixel = 0
topPad.LayoutOrder = -1
topPad.Parent = tabListHolder

for i, tabName in ipairs(tabNames) do
    local btn = Instance.new("TextButton")
    btn.Text = tabName
    btn.Name = tabName.."Tab"
    btn.Size = UDim2.new(0.92, 0, 0, compactTabHeight)
    btn.BackgroundColor3 = Color3.fromRGB(36,36,41)
    btn.TextColor3 = Color3.fromRGB(200,200,200)
    btn.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
    btn.TextSize = 18
    btn.AutoButtonColor = true
    btn.Parent = tabListHolder

    btn.TextXAlignment = Enum.TextXAlignment.Center
    btn.TextYAlignment = Enum.TextYAlignment.Center

    local btnCorner = Instance.new("UICorner")
    btnCorner.Parent = btn

    tabButtons[tabName] = btn

    -- SCROLLABLE TAB PAGE:
    local page = Instance.new("ScrollingFrame")
    page.Name = tabName.."Page"
    page.Size = UDim2.new(1, 0, 1, 0)
    page.Position = UDim2.new(0, 0, 0, 0)
    page.Visible = (i == 1)
    page.BackgroundColor3 = Color3.fromRGB(25, 25, 25)
    page.BorderSizePixel = 0
    page.ScrollBarThickness = 6
    page.ScrollBarImageColor3 = Color3.fromRGB(0,170,0)
    page.CanvasSize = UDim2.new(0,0,0,600)
    page.AutomaticCanvasSize = Enum.AutomaticSize.Y
    page.Parent = ContentHolder

    -- Add padding to inside of the scrollable page
    local pagePad = Instance.new("UIPadding")
    pagePad.PaddingTop = UDim.new(0,10)
    pagePad.PaddingLeft = UDim.new(0,12)
    pagePad.PaddingRight = UDim.new(0,12)
    pagePad.PaddingBottom = UDim.new(0,10)
    pagePad.Parent = page

    tabPages[tabName] = page
end

local botPad = Instance.new("Frame")
botPad.Size = UDim2.new(1,0,0,EVEN_GAP)
botPad.BackgroundTransparency = 1
botPad.BorderSizePixel = 0
botPad.LayoutOrder = 1000
botPad.Parent = tabListHolder

for name, btn in pairs(tabButtons) do
    btn.MouseButton1Click:Connect(function()
        for tName, page in pairs(tabPages) do
            page.Visible = (tName == name)
            tabButtons[tName].BackgroundColor3 =
                tName == name and Color3.fromRGB(0,170,0) or Color3.fromRGB(36,36,41)
            tabButtons[tName].TextColor3 =
                tName == name and Color3.fromRGB(255,255,255) or Color3.fromRGB(200,200,200)
        end
    end)
end

TabSection:GetPropertyChangedSignal("AbsoluteSize"):Connect(function()
    local tabListHolderHeight = tabListHolder.AbsoluteSize.Y
    local allGaps = EVEN_GAP * (numTabs + 1)
    local compactTabHeight = math.floor((tabListHolderHeight - allGaps) / numTabs)
    for i, tabName in ipairs(tabNames) do
        tabButtons[tabName].Size = UDim2.new(0.92, 0, 0, compactTabHeight)
    end
    topPad.Size = UDim2.new(1,0,0,EVEN_GAP)
    botPad.Size = UDim2.new(1,0,0,EVEN_GAP)
end)

-- ==== FEATURE CONTROLS (parent into tabPages["Catching"], tabPages["Player"], etc) ====
local catchingPage = tabPages["Catching"]
local playerPage = tabPages["Player"]

-- State variables
local magnetEnabled = false
local magnetDistance = 15
local showHitbox = false
local hitboxTransparency = 0.35

local jumpBoostEnabled = false
local jumpPower = 30

local angleEnhancerEnabled = false
local angleEnhancerPower = 40

-- Clean font for controls
local cleanFont = Font.new("rbxasset://fonts/families/GothamSSm.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
local cleanFontLabel = Font.new("rbxasset://fonts/families/GothamSSm.json", Enum.FontWeight.Medium, Enum.FontStyle.Normal)

-- Helper: modern toggle
local function createToggle(parent, y, text, default, callback)
    local toggle = Instance.new("TextButton")
    toggle.Size = UDim2.new(0, 260, 0, 34)
    toggle.Position = UDim2.new(0, 30, 0, y)
    toggle.BackgroundColor3 = default and Color3.fromRGB(0,170,0) or Color3.fromRGB(60,60,60)
    toggle.TextColor3 = Color3.new(1, 1, 1)
    toggle.Text = (default and "✔ " or "") .. text
    toggle.FontFace = cleanFont
    toggle.TextSize = 18
    toggle.Parent = parent

    local corner = Instance.new("UICorner")
    corner.Parent = toggle

    toggle.MouseButton1Click:Connect(function()
        default = not default
        toggle.Text = (default and "✔ " or "") .. text
        toggle.BackgroundColor3 = default and Color3.fromRGB(0,170,0) or Color3.fromRGB(60,60,60)
        callback(default)
    end)
end

-- Helper: clean slider
local function createSlider(parent, y, text, minVal, maxVal, default, callback)
    local container = Instance.new("Frame")
    container.Size = UDim2.new(0, 260, 0, 60)
    container.Position = UDim2.new(0, 30, 0, y)
    container.BackgroundTransparency = 1
    container.Parent = parent

    local label = Instance.new("TextLabel")
    label.Size = UDim2.new(1, 0, 0, 22)
    label.Position = UDim2.new(0, 0, 0, 0)
    label.BackgroundTransparency = 1
    label.Text = text
    label.TextColor3 = Color3.fromRGB(220, 220, 220)
    label.FontFace = cleanFontLabel
    label.TextSize = 17
    label.TextXAlignment = Enum.TextXAlignment.Left
    label.Parent = container

    local sliderBar = Instance.new("Frame")
    sliderBar.Size = UDim2.new(0.89, 0, 0, 6)
    sliderBar.Position = UDim2.new(0.05, 0, 0, 30)
    sliderBar.BackgroundColor3 = Color3.fromRGB(70, 70, 70)
    sliderBar.BorderSizePixel = 0
    sliderBar.Parent = container

    local barCorner = Instance.new("UICorner")
    barCorner.CornerRadius = UDim.new(1,0)
    barCorner.Parent = sliderBar

    local sliderKnob = Instance.new("Frame")
    sliderKnob.Size = UDim2.new(0, 16, 0, 16)
    sliderKnob.Position = UDim2.new((default-minVal)/(maxVal-minVal), -8, 0.5, -8)
    sliderKnob.BackgroundColor3 = Color3.fromRGB(0,170,0)
    sliderKnob.BorderSizePixel = 0
    sliderKnob.Parent = sliderBar

    local knobCorner = Instance.new("UICorner")
    knobCorner.CornerRadius = UDim.new(1,0)
    knobCorner.Parent = sliderKnob

    -- Value display
    local valueLabel = Instance.new("TextLabel")
    valueLabel.Size = UDim2.new(0, 48, 0, 22)
    valueLabel.Position = UDim2.new(1, -50, 0, 0)
    valueLabel.BackgroundTransparency = 1
    valueLabel.Text = tostring(default)
    valueLabel.TextColor3 = Color3.fromRGB(0,170,0)
    valueLabel.FontFace = cleanFont
    valueLabel.TextSize = 18
    valueLabel.TextXAlignment = Enum.TextXAlignment.Right
    valueLabel.Parent = container

    local value = default

    local draggingSlider = false
    sliderKnob.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            draggingSlider = true
        end
    end)
    sliderKnob.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            draggingSlider = false
        end
    end)
    sliderBar.InputBegan:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            draggingSlider = true
            local rel = (input.Position.X - sliderBar.AbsolutePosition.X) / sliderBar.AbsoluteSize.X
            rel = math.clamp(rel, 0, 1)
            value = math.floor(rel * (maxVal - minVal) + minVal + 0.5)
            sliderKnob.Position = UDim2.new(rel, -8, 0.5, -8)
            valueLabel.Text = tostring(value)
            callback(value)
        end
    end)
    UserInputService.InputChanged:Connect(function(input)
        if draggingSlider and input.UserInputType == Enum.UserInputType.MouseMovement then
            local rel = (input.Position.X - sliderBar.AbsolutePosition.X) / sliderBar.AbsoluteSize.X
            rel = math.clamp(rel, 0, 1)
            value = math.floor(rel * (maxVal - minVal) + minVal + 0.5)
            sliderKnob.Position = UDim2.new(rel, -8, 0.5, -8)
            valueLabel.Text = tostring(value)
            callback(value)
        end
    end)
    UserInputService.InputEnded:Connect(function(input)
        if input.UserInputType == Enum.UserInputType.MouseButton1 then
            draggingSlider = false
        end
    end)
end

-- CATCHING TAB
createToggle(catchingPage, 30, "Magnet", magnetEnabled, function(v) magnetEnabled = v end)
createSlider(catchingPage, 80, "Magnet Power", 0, 30, magnetDistance, function(v) magnetDistance = v end)
createToggle(catchingPage, 150, "Show Hitbox", showHitbox, function(v) showHitbox = v end)
createSlider(catchingPage, 200, "Hitbox Transparency", 0, 100, math.floor(hitboxTransparency * 100), function(val)
    hitboxTransparency = math.clamp(val, 0, 100)/100
end)

-- PLAYER TAB
createToggle(playerPage, 30, "Jump Boost", jumpBoostEnabled, function(v) jumpBoostEnabled = v end)
createSlider(playerPage, 80, "Jump Power", 25, 45, jumpPower, function(v) jumpPower = v end)
createToggle(playerPage, 160, "Angle Enhancer", angleEnhancerEnabled, function(v) angleEnhancerEnabled = v end)
createSlider(playerPage, 210, "Angle Enhancer Power", 25, 70, angleEnhancerPower, function(v) angleEnhancerPower = v end)

-- Magnet Hitbox Visualizer (with occlusion)
local magnetVisuals = {}

local function clearMagnetVisuals()
    for ball, adorn in pairs(magnetVisuals) do
        if adorn then
            adorn:Destroy()
        end
    end
    table.clear(magnetVisuals)
end

local function isBallOccludedForLocalPlayer(ball)
    local char = LocalPlayer.Character
    if not char then return false end
    local camera = workspace.CurrentCamera
    if not camera then return false end

    local origin = camera.CFrame.Position
    local direction = (ball.Position - origin).Unit * (ball.Position - origin).Magnitude
    local params = RaycastParams.new()
    params.FilterDescendantsInstances = {workspace}
    params.IgnoreWater = true

    local result = workspace:Raycast(origin, direction, params)
    if result and result.Instance then
        local inst = result.Instance
        while inst and inst.Parent and inst ~= workspace do
            if inst:IsDescendantOf(char) then
                return true
            end
            inst = inst.Parent
        end
    end
    return false
end

local function updateMagnetVisuals()
    if not showHitbox then
        clearMagnetVisuals()
        return
    end
    for _, obj in pairs(workspace:GetDescendants()) do
        if obj:IsA("BasePart") and obj.Name == "Football" then
            if not magnetVisuals[obj] then
                local adorn = Instance.new("SphereHandleAdornment")
                adorn.Name = "MagnetHitbox"
                adorn.Adornee = obj
                adorn.Color3 = Color3.fromRGB(0, 170, 0)
                adorn.Transparency = hitboxTransparency
                adorn.AlwaysOnTop = true
                adorn.Radius = magnetDistance
                adorn.ZIndex = 5
                adorn.Parent = obj
                magnetVisuals[obj] = adorn
            else
                magnetVisuals[obj].Radius = magnetDistance
                magnetVisuals[obj].Transparency = hitboxTransparency
            end
            if isBallOccludedForLocalPlayer(obj) then
                magnetVisuals[obj].Visible = false
            else
                magnetVisuals[obj].Visible = true
            end
        end
    end
    for obj, adorn in pairs(magnetVisuals) do
        if not obj or not obj.Parent or obj.Name ~= "Football" then
            if adorn then
                adorn:Destroy()
            end
            magnetVisuals[obj] = nil
        end
    end
end

RunService.RenderStepped:Connect(function()
    if showHitbox then
        updateMagnetVisuals()
    else
        clearMagnetVisuals()
    end
end)

-- Magnet Logic
spawn(function()
    while task.wait(0.1) do
        if magnetEnabled then
            local char = LocalPlayer.Character
            if char and char:FindFirstChild("HumanoidRootPart") and char:FindFirstChild("Head") then
                for _, obj in pairs(workspace:GetDescendants()) do
                    if obj:IsA("BasePart") and obj.Name == "Football" then
                        local dist = (obj.Position - char.HumanoidRootPart.Position).Magnitude
                        if dist <= magnetDistance and math.abs(obj.AssemblyLinearVelocity.Y) > 1 then
                            local targetCFrame = char.Head.CFrame * CFrame.new(0, 0, -1)
                            local tweenInfo = TweenInfo.new(0.1, Enum.EasingStyle.Quad, Enum.EasingDirection.Out)
                            local goal = {CFrame = targetCFrame}
                            local tween = TweenService:Create(obj, tweenInfo, goal)
                            tween:Play()
                        end
                    end
                end
            end
        end
    end
end)

-- JUMP BOOST FUNCTIONALITY (One strong boost per ground-jump)
local canJumpBoost = true

local function setupJumpBoost()
    local char = Players.LocalPlayer.Character
    if not char then return end
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    if not humanoid then return end

    humanoid.StateChanged:Connect(function(_, new)
        if new == Enum.HumanoidStateType.Landed or new == Enum.HumanoidStateType.Running or new == Enum.HumanoidStateType.Climbing then
            canJumpBoost = true
        end
    end)

    UserInputService.JumpRequest:Connect(function()
        if jumpBoostEnabled and canJumpBoost then
            canJumpBoost = false
            local hrp = char:FindFirstChild("HumanoidRootPart")
            if hrp then
                hrp.AssemblyLinearVelocity = Vector3.new(hrp.AssemblyLinearVelocity.X, jumpPower, hrp.AssemblyLinearVelocity.Z)
            end
        end
    end)
end

Players.LocalPlayer.CharacterAdded:Connect(function() task.wait(0.2) setupJumpBoost() end)
if Players.LocalPlayer.Character then
    setupJumpBoost()
end

-- ANGLE ENHANCER FUNCTIONALITY (One strong burst after unshiftlock+strafe, per jump)
local wasShiftLocked = false
local lastMoveVec = Vector3.new()
local angleEnhancerReady = false
local lastUnshiftLockTime = 0
local canAngleBoost = true
local angleBoostUsed = false

RunService.RenderStepped:Connect(function()
    if not angleEnhancerEnabled then return end
    local char = Players.LocalPlayer.Character
    if not char then return end
    local hum = char:FindFirstChildOfClass("Humanoid")
    if not hum then return end
    local moveDir = hum.MoveDirection
    lastMoveVec = moveDir

    local currShiftLock = Players.LocalPlayer.DevEnableMouseLock and UserInputService.MouseBehavior == Enum.MouseBehavior.LockCenter
    if wasShiftLocked and not currShiftLock then
        if Vector2.new(moveDir.X, moveDir.Z).Magnitude > 0.3 then
            angleEnhancerReady = true
            lastUnshiftLockTime = tick()
        end
    end
    wasShiftLocked = currShiftLock
end)

local function setupAngleHumanoid()
    local char = Players.LocalPlayer.Character
    if not char then return end
    local humanoid = char:FindFirstChildOfClass("Humanoid")
    if not humanoid then return end

    humanoid.StateChanged:Connect(function(_, new)
        if new == Enum.HumanoidStateType.Landed or new == Enum.HumanoidStateType.Running or new == Enum.HumanoidStateType.Climbing then
            canAngleBoost = true
            angleBoostUsed = false
        end
    end)
end
Players.LocalPlayer.CharacterAdded:Connect(setupAngleHumanoid)
if Players.LocalPlayer.Character then setupAngleHumanoid() end

UserInputService.JumpRequest:Connect(function()
    if angleEnhancerEnabled and angleEnhancerReady and canAngleBoost and not angleBoostUsed then
        angleEnhancerReady = false
        local now = tick()
        if now - lastUnshiftLockTime <= 0.35 then
            local char = Players.LocalPlayer.Character
            if char then
                local hrp = char:FindFirstChild("HumanoidRootPart")
                local hum = char:FindFirstChildOfClass("Humanoid")
                if hrp and hum and (Vector2.new(lastMoveVec.X, lastMoveVec.Z).Magnitude > 0.3) then
                    angleBoostUsed = true
                    canAngleBoost = false
                    hrp.AssemblyLinearVelocity = Vector3.new(hrp.AssemblyLinearVelocity.X, angleEnhancerPower, hrp.AssemblyLinearVelocity.Z)
                end
            end
        end
    end
end)
