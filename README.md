local ScreenGui = Instance.new("ScreenGui")
ScreenGui.ZIndexBehavior = Enum.ZIndexBehavior.Sibling
ScreenGui.Parent = game:GetService("StarterGui")

local Frame = Instance.new("Frame")
Frame.Size = UDim2.new(0.00, 781.00, 0.00, 457.00)
Frame.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
Frame.Position = UDim2.new(0.22, 0.00, 0.17, 0.00)
Frame.BorderSizePixel = 0
Frame.BackgroundColor3 = Color3.new(0.05, 0.05, 0.07)
Frame.Parent = ScreenGui

local UserWelcome = Instance.new("Frame")
UserWelcome.Name = "UserWelcome"
UserWelcome.Size = UDim2.new(0.00, 207.00, 0.00, 51.00)
UserWelcome.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
UserWelcome.Position = UDim2.new(0.01, 0.00, 0.11, 0.00)
UserWelcome.BorderSizePixel = 0
UserWelcome.BackgroundColor3 = Color3.new(0.07, 0.07, 0.11)
UserWelcome.Parent = Frame

local TextLabel = Instance.new("TextLabel")
TextLabel.BorderSizePixel = 0
TextLabel.BackgroundColor3 = Color3.new(1.00, 1.00, 1.00)
TextLabel.FontFace = Font.new("rbxasset://fonts/families/FredokaOne.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
TextLabel.TextSize = 12
TextLabel.Size = UDim2.new(0.00, 154.00, 0.00, 25.00)
TextLabel.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
TextLabel.TextColor3 = Color3.new(0.28, 0.28, 0.28)
TextLabel.BackgroundTransparency = 1
TextLabel.Position = UDim2.new(0.25, 0.00, -0.01, 0.00)
TextLabel.Parent = UserWelcome

local ImageLabel = Instance.new("ImageLabel")
ImageLabel.BorderSizePixel = 0
ImageLabel.BackgroundColor3 = Color3.new(1.00, 1.00, 1.00)
ImageLabel.Image = "rbxasset://textures/ui/GuiImagePlaceholder.png"
ImageLabel.Size = UDim2.new(0.00, 52.00, 0.00, 51.00)
ImageLabel.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
ImageLabel.Position = UDim2.new(-0.00, 0.00, -0.00, 0.00)
ImageLabel.Parent = UserWelcome

local UpdatePlayerInfo = Instance.new("LocalScript")
UpdatePlayerInfo.Name = "UpdatePlayerInfo"
UpdatePlayerInfo.Parent = UserWelcome

local TextLabel_1 = Instance.new("TextLabel")
TextLabel_1.Name = "TextLabel 1"
TextLabel_1.BorderSizePixel = 0
TextLabel_1.BackgroundColor3 = Color3.new(1.00, 1.00, 1.00)
TextLabel_1.FontFace = Font.new("rbxasset://fonts/families/FredokaOne.json", Enum.FontWeight.Regular, Enum.FontStyle.Normal)
TextLabel_1.TextSize = 10
TextLabel_1.Size = UDim2.new(0.00, 154.00, 0.00, 23.00)
TextLabel_1.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
TextLabel_1.TextColor3 = Color3.new(0.24, 0.24, 0.25)
TextLabel_1.BackgroundTransparency = 1
TextLabel_1.Position = UDim2.new(0.25, 0.00, 0.48, 0.00)
TextLabel_1.Parent = UserWelcome

local UICorner = Instance.new("UICorner")
UICorner.Parent = UserWelcome

local TabSection = Instance.new("Frame")
TabSection.Name = "TabSection"
TabSection.Size = UDim2.new(0.00, 186.00, 0.00, 342.00)
TabSection.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
TabSection.Position = UDim2.new(0.01, 0.00, 0.23, 0.00)
TabSection.BorderSizePixel = 0
TabSection.BackgroundColor3 = Color3.new(0.07, 0.07, 0.11)
TabSection.Parent = Frame

local UICorner_1 = Instance.new("UICorner")
UICorner_1.Parent = TabSection

local SettingsTab = Instance.new("TextButton")
SettingsTab.Name = "SettingsTab"
SettingsTab.BorderSizePixel = 0
SettingsTab.BackgroundColor3 = Color3.new(0.10, 0.10, 0.15)
SettingsTab.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
SettingsTab.TextSize = 20
SettingsTab.Size = UDim2.new(0.00, 174.00, 0.00, 54.00)
SettingsTab.TextColor3 = Color3.new(0.00, 0.00, 0.00)
SettingsTab.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
SettingsTab.Text = "Settings"
SettingsTab.Position = UDim2.new(0.03, 0.00, 0.80, 0.00)
SettingsTab.Parent = TabSection

local UICorner_1 = Instance.new("UICorner")
UICorner_1.Parent = SettingsTab

local SettingsPage = Instance.new("Frame")
SettingsPage.Name = "SettingsPage"
SettingsPage.Size = UDim2.new(0.00, 536.00, 0.00, 386.00)
SettingsPage.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
SettingsPage.Position = UDim2.new(1.26, 0.00, -6.13, 0.00)
SettingsPage.BorderSizePixel = 0
SettingsPage.BackgroundColor3 = Color3.new(0.07, 0.07, 0.11)
SettingsPage.Parent = SettingsTab

local AutomaticsTab = Instance.new("TextButton")
AutomaticsTab.Name = "AutomaticsTab"
AutomaticsTab.BorderSizePixel = 0
AutomaticsTab.BackgroundColor3 = Color3.new(0.10, 0.10, 0.15)
AutomaticsTab.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
AutomaticsTab.TextSize = 20
AutomaticsTab.Size = UDim2.new(0.00, 174.00, 0.00, 54.00)
AutomaticsTab.TextColor3 = Color3.new(0.00, 0.00, 0.00)
AutomaticsTab.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
AutomaticsTab.Text = "Automatics"
AutomaticsTab.Position = UDim2.new(0.03, 0.00, 0.41, 0.00)
AutomaticsTab.Parent = TabSection

local UICorner_1 = Instance.new("UICorner")
UICorner_1.Parent = AutomaticsTab

local AutomaticsPage = Instance.new("Frame")
AutomaticsPage.Name = "AutomaticsPage"
AutomaticsPage.Size = UDim2.new(0.00, 536.00, 0.00, 386.00)
AutomaticsPage.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
AutomaticsPage.Position = UDim2.new(1.25, 0.00, -3.69, 0.00)
AutomaticsPage.BorderSizePixel = 0
AutomaticsPage.BackgroundColor3 = Color3.new(0.07, 0.07, 0.11)
AutomaticsPage.Parent = AutomaticsTab

local PlayerTab = Instance.new("TextButton")
PlayerTab.Name = "PlayerTab"
PlayerTab.BorderSizePixel = 0
PlayerTab.BackgroundColor3 = Color3.new(0.10, 0.10, 0.15)
PlayerTab.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
PlayerTab.TextSize = 20
PlayerTab.Size = UDim2.new(0.00, 174.00, 0.00, 54.00)
PlayerTab.TextColor3 = Color3.new(0.00, 0.00, 0.00)
PlayerTab.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
PlayerTab.Text = "Player"
PlayerTab.Position = UDim2.new(0.03, 0.00, 0.23, 0.00)
PlayerTab.Parent = TabSection

local UICorner_1 = Instance.new("UICorner")
UICorner_1.Parent = PlayerTab

local PlayerPage = Instance.new("Frame")
PlayerPage.Name = "PlayerPage"
PlayerPage.Size = UDim2.new(0.00, 536.00, 0.00, 386.00)
PlayerPage.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
PlayerPage.Position = UDim2.new(1.25, 0.00, -2.50, 0.00)
PlayerPage.BorderSizePixel = 0
PlayerPage.BackgroundColor3 = Color3.new(0.07, 0.07, 0.11)
PlayerPage.Parent = PlayerTab

local CatchingTab = Instance.new("TextButton")
CatchingTab.Name = "CatchingTab"
CatchingTab.BorderSizePixel = 0
CatchingTab.BackgroundColor3 = Color3.new(0.10, 0.10, 0.15)
CatchingTab.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
CatchingTab.TextSize = 20
CatchingTab.Size = UDim2.new(0.00, 174.00, 0.00, 54.00)
CatchingTab.TextColor3 = Color3.new(0.00, 0.00, 0.00)
CatchingTab.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
CatchingTab.Text = "Catching"
CatchingTab.Position = UDim2.new(0.03, 0.00, 0.03, 0.00)
CatchingTab.Parent = TabSection

local UICorner_1 = Instance.new("UICorner")
UICorner_1.Parent = CatchingTab

local CatchingPage = Instance.new("Frame")
CatchingPage.Name = "CatchingPage"
CatchingPage.Size = UDim2.new(0.00, 536.00, 0.00, 386.00)
CatchingPage.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
CatchingPage.Position = UDim2.new(1.25, 0.00, -1.30, 0.00)
CatchingPage.BorderSizePixel = 0
CatchingPage.BackgroundColor3 = Color3.new(0.07, 0.07, 0.11)
CatchingPage.Parent = CatchingTab

local ThrowingTab = Instance.new("TextButton")
ThrowingTab.Name = "ThrowingTab"
ThrowingTab.BorderSizePixel = 0
ThrowingTab.BackgroundColor3 = Color3.new(0.10, 0.10, 0.15)
ThrowingTab.FontFace = Font.new("rbxasset://fonts/families/SourceSansPro.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
ThrowingTab.TextSize = 20
ThrowingTab.Size = UDim2.new(0.00, 174.00, 0.00, 54.00)
ThrowingTab.TextColor3 = Color3.new(0.00, 0.00, 0.00)
ThrowingTab.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
ThrowingTab.Text = "Throwing"
ThrowingTab.Position = UDim2.new(0.03, 0.00, 0.61, 0.00)
ThrowingTab.Parent = TabSection

local UICorner_1 = Instance.new("UICorner")
UICorner_1.Parent = ThrowingTab

local ThrowingPage = Instance.new("Frame")
ThrowingPage.Name = "ThrowingPage"
ThrowingPage.Size = UDim2.new(0.00, 536.00, 0.00, 386.00)
ThrowingPage.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
ThrowingPage.Position = UDim2.new(1.25, 0.00, -4.91, 0.00)
ThrowingPage.BorderSizePixel = 0
ThrowingPage.BackgroundColor3 = Color3.new(0.07, 0.07, 0.11)
ThrowingPage.Parent = ThrowingTab

local TopBar = Instance.new("Frame")
TopBar.Name = "TopBar"
TopBar.Size = UDim2.new(0.00, 780.00, 0.00, 45.00)
TopBar.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
TopBar.Position = UDim2.new(-0.00, 0.00, -0.00, 0.00)
TopBar.BorderSizePixel = 0
TopBar.BackgroundColor3 = Color3.new(0.05, 0.05, 0.07)
TopBar.Parent = Frame

local Title = Instance.new("TextLabel")
Title.Name = "Title"
Title.BorderSizePixel = 0
Title.BackgroundColor3 = Color3.new(0.05, 0.05, 0.07)
Title.FontFace = Font.new("rbxasset://fonts/families/LuckiestGuy.json", Enum.FontWeight.Bold, Enum.FontStyle.Normal)
Title.TextSize = 34
Title.Size = UDim2.new(0.00, 200.00, 0.00, 37.00)
Title.BorderColor3 = Color3.new(0.00, 0.00, 0.00)
Title.Text = " Zxyllo Hub"
Title.TextColor3 = Color3.new(0.00, 0.67, 0.00)
Title.Position = UDim2.new(0.01, 0.00, 0.18, 0.00)
Title.Parent = TopBar

local LocalScript = Instance.new("LocalScript")
LocalScript.Parent = TopBar

local LocalScript_1 = Instance.new("LocalScript")
LocalScript_1.Parent = Frame

