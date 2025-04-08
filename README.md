local v12 = {
    GUI = {
        GUIButton = true,
        GUIToggleKey = Enum.KeyCode.RightShift
    },
    AimBot = {
        Enabled = true,
        TeamCheck = false,
        WallCheck = true,
        StickyAim = true,
        Prediction = false,
        PredictionAmmount = 1,
        UseMouse = true,
        MouseBind = 'MouseButton2',
        Keybind = Enum.KeyCode.E,
        ShowFov = false,
        Fov = 360,
        Smoothing = 0.3,
        AimPart = 'Head',
        Thickness = 1,
        FovFillColor = Color3.fromRGB(100, 0, 100),
        FovColor = Color3.fromRGB(100, 0, 100),
        FovFillTransparency = 1,
        FovTransparenct = 0,
        IsAimKeyDown = false,
        Target = nil,
        CameraTween = nil
    },
    esp = {
        Enabled = false,
        TeamCheck = false,
        MaxDistance = 4E3,
        CharacterSize = Vector2.new(5, 6),
        Box = {
            Box = false,
            Name = false,
            Distance = false,
            Health = false,
            HealthBar = false,
            Color = Color3.fromRGB(255, 255, 255),
            Outline = false,
            OutlineColor = Color3.fromRGB(0, 0, 0)
        },
        Tracer = {
            TeamColor = false,
            Tracer = false,
            Color = Color3.fromRGB(255, 255, 255),
            Outline = false,
            OutlineColor = Color3.fromRGB(0, 0, 0)
        },
        Hilights = {
            Hilights = false,
            AllWaysVisible = false,
            OutlineTransparency = 0.5,
            FillTransparency = 0.5,
            OutlineColor = Color3.fromRGB(255, 0, 0),
            FillColor = Color3.fromRGB(255, 255, 255)
        }
    }
};
local v13 = game.Players;
local v14 = v13.LocalPlayer;
local v15 = game.Workspace.CurrentCamera;
local v16 = game.TweenService;
local v17 = game.UserInputService;
local v18 = v17.GetMouseLocation;
local v19 = game:FindFirstChild('CoreGui');
function library()
    local v61 = 0;
    local v62;
    local v63;
    local v64;
    local v65;
    local v66;
    while true do
        if (v61 == 1) then
            v64 = game:FindFirstChild('CoreGui');
            v65 = game:GetService('TextService');
            v61 = 2;
        end
        if (0 == v61) then
            v62 = {
                flags = {},
                items = {}
            };
            v63 = game.Players.LocalPlayer.PlayerGui;
            v61 = 1;
        end
        if ((3) == v61) then
            v62.CreateWindow = function(v253, v254, v255)
                local v256 = {};
                v256.keybind = v254 or Enum.KeyCode.RightShift ;
                v256.name = v255 or 'XIT RBN BETA' ;
                v256.ScreenGui = Instance.new('ScreenGui');
                v256.ScreenGui.Parent = v64 or v63 ;
                v256.ScreenGui.ResetOnSpawn = false;
                v256.ScreenGui.DisplayOrder = 10;
                local v263, v264, v265, v266;
                game:GetService('UserInputService').InputChanged:Connect(function(v321)
                    if ((v321 == v264) and v263) then
                        local v465 = v321.Position - v265 ;
                        v256.Main.Position = UDim2.new(v266.X.Scale, v266.X.Offset + v465.X, v266.Y.Scale, v266.Y.Offset + v465.Y);
                    end
                end);
                local v267 = function(v322)
                    if ((v322.UserInputType == Enum.UserInputType.MouseButton1) or (v322.UserInputType == Enum.UserInputType.Touch)) then
                        local v467 = 0;
                        while true do
                            if (v467 == 0) then
                                v263 = true;
                                v265 = v322.Position;
                                v467 = 1;
                            end
                            if (v467 == (1)) then
                                v266 = v256.Main.Position;
                                v322.Changed:Connect(function()
                                    if (v322.UserInputState == Enum.UserInputState.End) then
                                        v263 = false;
                                    end
                                end);
                                break
                            end
                        end
                    end
                end;
                local v268 = function(v323)
                    if ((v323.UserInputType == Enum.UserInputType.MouseMovement) or (v323.UserInputType == Enum.UserInputType.Touch)) then
                        v264 = v323;
                    end
                end;
                v256.Main = Instance.new('TextButton', v256.ScreenGui);
                v256.Main.Size = UDim2.fromOffset(800, 450);
                v256.Main.BackgroundColor3 = v62.theme.BackGround;
                v256.Main.BorderSizePixel = 1;
                v256.Main.BorderColor3 = v62.theme.Border;
                v256.Main.Active = true;
                v256.Main.AutoButtonColor = false;
                v256.Main.Text = "";
                v256.Main.InputBegan:Connect(v267);
                v256.Main.InputChanged:Connect(v268);
                v256.RightSide = Instance.new('Frame', v256.Main);
                v256.RightSide.BackgroundColor3 = v62.theme.BackGround2;
                v256.RightSide.Size = UDim2.fromOffset(150, 450);
                v256.RightSide.BorderSizePixel = 0;
                v256.TabsHolder = Instance.new('Frame', v256.Main);
                v256.TabsHolder.Position = UDim2.fromScale(3.1E-2, 0.1069999999999709);
                v256.TabsHolder.Size = UDim2.fromOffset(100, 389);
                v256.TabsHolder.BackgroundTransparency = 1;
                v256.UIListLayout = Instance.new('UIListLayout', v256.TabsHolder);
                v256.UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center;
                v256.UIListLayout.Padding = UDim.new(0, 10);
                v256.UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder;
                v256.line = Instance.new('Frame', v256.Main);
                v256.line.Position = UDim2.fromScale(0.188, 0);
                v256.line.Size = UDim2.fromOffset(1, 450);
                v256.line.BorderSizePixel = 0;
                v256.line.BackgroundColor3 = v62.theme.Border;
                v256.Title = Instance.new('TextLabel', v256.Main);
                v256.Title.Position = UDim2.fromScale(0.016, 1.6E-2);
                v256.Title.Size = UDim2.fromOffset(123, 34);
                v256.Title.Text = v256.name;
                v256.Title.Font = v62.theme.Font;
                v256.Title.TextSize = 19;
                v256.Title.BackgroundTransparency = 1;
                v256.Title.TextColor3 = v62.theme.TextColor;
                local v309 = v256.Title.FontFace;
                v309.Weight = Enum.FontWeight.Bold;
                v256.Title.FontFace = v309;
                game:GetService('UserInputService').InputBegan:Connect(function(v324)
                    if (v324.KeyCode == v256.keybind) then
                        v256.Main.Visible = not v256.Main.Visible;
                    end
                end);
                v256.Tabs = {};
                v256.OpenedColorPickers = {};
                v256.UpdateKeyBind = function(v325, v326)
                    v256.keybind = v326;
                end;
                v256.CreateToggleButton = function(v328)
                    local v329 = 0;
                    local v330;
                    while true do
                        if (v329 == 2) then
                            v330.Frame.BorderColor3 = v62.theme.Border;
                            v330.Button = Instance.new('TextButton', v330.Frame);
                            v330.Button.Size = UDim2.fromOffset(141, 26);
                            v330.Button.Position = UDim2.fromScale(0, 0.316);
                            v329 = 3;
                        end
                        if (v329 == 5) then
                            game:GetService('UserInputService').InputBegan:Connect(function(v1004)
                                if (v1004.KeyCode == v256.keybind) then
                                    v330.Button.Text = (v256.Main.Visible and 'Close') or 'Open' ;
                                end
                            end);
                            v330.Update = function(v1005, v1006)
                                v330.Frame.Visible = v1006;
                            end;
                            return v330
                        end
                        if (v329 == 4) then
                            v330.Button.BackgroundColor3 = v62.theme.BackGround2;
                            v330.Button.BorderSizePixel = 0;
                            v330.Button.BorderColor3 = v62.theme.Border;
                            v330.Button.MouseButton1Click:Connect(function()
                                v256.Main.Visible = not v256.Main.Visible;
                                v330.Button.Text = (v256.Main.Visible and 'Close') or (not v256.Main.Visible and 'Open') ;
                            end);
                            v329 = 5;
                        end
                        if (v329 == (3)) then
                            v330.Button.Text = 'Close';
                            v330.Button.TextColor3 = v62.theme.TextColor;
                            v330.Button.Font = v62.theme.Font;
                            v330.Button.TextSize = v62.theme.TextSize;
                            v329 = 4;
                        end
                        if (v329 == (1)) then
                            v330.Frame.Draggable = true;
                            v330.Frame.Active = true;
                            v330.Frame.BackgroundColor3 = v62.theme.BackGround;
                            v330.Frame.BorderSizePixel = 1;
                            v329 = 2;
                        end
                        if (0 == v329) then
                            v330 = {};
                            v330.Frame = Instance.new('Frame', v256.ScreenGui);
                            v330.Frame.Size = UDim2.fromOffset(141, 38);
                            v330.Frame.Position = UDim2.fromScale(0.466, 0.15);
                            v329 = 1;
                        end
                    end
                end;
                v256.CreateTab = function(v331, v332)
                    local v333 = {};
                    v333.Button = Instance.new('TextButton', v256.TabsHolder);
                    v333.Button.Size = UDim2.fromOffset(137, 33);
                    v333.Button.BackgroundColor3 = v62.theme.BackGround;
                    v333.Button.Text = v332;
                    v333.Button.TextColor3 = v62.theme.TextColor;
                    v333.Button.Font = v62.theme.Font;
                    v333.Button.TextSize = v62.theme.TextSize;
                    v333.Button.BorderSizePixel = 0;
                    v333.Window = Instance.new('ScrollingFrame', v256.Main);
                    v333.Window.Name = v332 .. 'Tab' ;
                    v333.Window.BackgroundTransparency = 1;
                    v333.Window.Visible = false;
                    v333.Window.Size = UDim2.fromOffset(650, 450);
                    v333.Window.Position = UDim2.fromOffset(150, 0);
                    v333.Window.ScrollBarThickness = 0;
                    v333.Left = Instance.new('Frame', v333.Window);
                    v333.Left.Size = UDim2.fromOffset(100, 428);
                    v333.Left.Position = UDim2.fromOffset(120, 18);
                    v333.Left.BackgroundTransparency = 1;
                    v333.UiListLayout = Instance.new('UIListLayout', v333.Left);
                    v333.UiListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center;
                    v333.UiListLayout.Padding = UDim.new(0, 7);
                    v333.UiListLayout.SortOrder = Enum.SortOrder.LayoutOrder;
                    v333.Right = Instance.new('Frame', v333.Window);
                    v333.Right.Size = UDim2.fromOffset(100, 428);
                    v333.Right.Position = UDim2.fromOffset(430, 18);
                    v333.Right.BackgroundTransparency = 1;
                    v333.UiListLayout1 = Instance.new('UIListLayout', v333.Right);
                    v333.UiListLayout1.HorizontalAlignment = Enum.HorizontalAlignment.Center;
                    v333.UiListLayout1.Padding = UDim.new(0, 7);
                    v333.UiListLayout1.SortOrder = Enum.SortOrder.LayoutOrder;
                    local v371 = false;
                    v333.SelectTab = function(v400)
                        local v401 = 0;
                        while true do
                            if (v401 == 0) then
                                repeat
                                    wait();
                                until v371 == false
                                v371 = true;
                                v401 = 1;
                            end
                            if (v401 == 3) then
                                v371 = false;
                                break
                            end
                            if (1 == v401) then
                                for v1028, v1029 in pairs(v256.Tabs) do
                                    if ((v1029 ~= v333) or (v1029.ClassName ~= 'TextLabel')) then
                                        v1029.Button.BackgroundColor3 = v62.theme.BackGround;
                                        v1029.Button.Name = 'Tab';
                                        v1029.Window.Visible = false;
                                    end
                                end
                                v333.Button.BackgroundColor3 = v62.theme.Selected;
                                v401 = 2;
                            end
                            if (2 == v401) then
                                v333.Button.Name = 'SelectedTab';
                                v333.Window.Visible = true;
                                v401 = 3;
                            end
                        end
                    end;
                    if (# v256.Tabs == 0) then
                        v333:SelectTab();
                    end
                    v333.Button.MouseButton1Down:Connect(function()
                        v333:SelectTab();
                    end);
                    v333.SectorsLeft = {};
                    v333.SectorsRight = {};
                    v333.CreateSector = function(v402, v403, v404)
                        local v405 = {};
                        v405.side = v404:lower() or 'left' ;
                        v405.name = v403 or "" ;
                        v405.Main = Instance.new('Frame', ((v405.side == 'left') and v333.Left) or v333.Right);
                        v405.Main.BackgroundColor3 = v62.theme.BackGround2;
                        v405.Main.BorderSizePixel = 0;
                        v405.Main.Name = v405.name:gsub(" ", "") .. 'Sector' ;
                        v405.Main.Size = UDim2.fromOffset(265, 50);
                        v405.UICorner = Instance.new('UICorner', v405.Main);
                        v405.UICorner.CornerRadius = UDim.new(0, 9);
                        v405.Items = Instance.new('Frame', v405.Main);
                        v405.Items.Position = UDim2.fromScale(0.434, 0);
                        v405.Items.Size = UDim2.fromOffset(34, 50);
                        v405.Items.AutomaticSize = Enum.AutomaticSize.Y;
                        v405.Items.BackgroundTransparency = 1;
                        v405.UIListLayout = Instance.new('UIListLayout', v405.Items);
                        v405.UIListLayout.SortOrder = Enum.SortOrder.LayoutOrder;
                        v405.UIListLayout.HorizontalAlignment = Enum.HorizontalAlignment.Center;
                        v405.UIListLayout.Padding = UDim.new(0, 7);
                        v405.Name = Instance.new('TextLabel', v405.Items);
                        v405.Name.BackgroundTransparency = 1;
                        v405.Name.Size = UDim2.fromOffset(20, 20);
                        v405.Name.Text = v403;
                        v405.Name.TextColor3 = v62.theme.TextColor;
                        v405.Name.Font = v62.theme.Font;
                        v405.Name.TextSize = v62.theme.TextSize;
                        v405.Name.TextYAlignment = Enum.TextYAlignment.Bottom;
                        v405.Divider = Instance.new('Frame', v405.Items);
                        v405.Divider.Size = UDim2.fromOffset(230, 2);
                        v405.Divider.BorderSizePixel = 0;
                        v405.Divider.BackgroundColor3 = v62.theme.BackGround;
                        table.insert(((v405.side:lower() == 'left') and v333.SectorsLeft) or v333.SectorsRight, v405);
                        v405.FixSize = function(v469)
                            local v470 = 0;
                            local v471;
                            local v472;
                            local v473;
                            while true do
                                if ((0) == v470) then
                                    v471 = 0;
                                    v472 = nil;
                                    v470 = 1;
                                end
                                if (v470 == (1)) then
                                    v473 = nil;
                                    while true do
                                        if (v471 == (0)) then
                                            v405.Main.Size = UDim2.fromOffset(250, v405.UIListLayout.AbsoluteContentSize.Y + 12);
                                            v472, v473 = 0, 0;
                                            v471 = 1;
                                        end
                                        if (v471 == 2) then
                                            v333.Window.CanvasSize = ((v472 > v473) and UDim2.fromOffset(650, v472 + 100)) or UDim2.fromOffset(650, v473 + (100)) ;
                                            break
                                        end
                                        if (v471 == (1)) then
                                            for v1165, v1166 in pairs(v333.SectorsLeft) do
                                                v472 = v472 + v1166.Main.AbsoluteSize.Y ;
                                            end
                                            for v1167, v1168 in pairs(v333.SectorsRight) do
                                                v473 = v473 + v1168.Main.AbsoluteSize.Y ;
                                            end
                                            v471 = 2;
                                        end
                                    end
                                    break
                                end
                            end
                        end;
                        v405.CreateToggle = function(v474, v475, v476, v477, v478)
                            local v479 = {};
                            v479.text = v475 or "" ;
                            v479.default = v476 or false ;
                            v479.callback = v477 or function(v905)
                            end ;
                            v479.flag = v478 or v475 or "" ;
                            v479.value = v479.default;
                            v479.Main = Instance.new('TextButton', v405.Items);
                            v479.Main.Size = UDim2.fromOffset(240, 35);
                            v479.Main.BackgroundColor3 = v62.theme.BackGround;
                            v479.Main.AutoButtonColor = false;
                            v479.Main.Text = "";
                            v479.UICorner = Instance.new('UICorner', v479.Main);
                            v479.UICorner.CornerRadius = UDim.new(0, 8);
                            v479.Text = Instance.new('TextLabel', v479.Main);
                            v479.Text.Position = UDim2.fromScale(0.046, 0);
                            v479.Text.Size = UDim2.fromOffset(125, 35);
                            v479.Text.Text = v475;
                            v479.Text.TextColor3 = v62.theme.TextColor;
                            v479.Text.Font = v62.theme.Font;
                            v479.Text.TextSize = v62.theme.TextSize;
                            v479.Text.BackgroundTransparency = 1;
                            v479.Text.TextXAlignment = Enum.TextXAlignment.Left;
                            v479.Indicator = Instance.new('Frame', v479.Main);
                            v479.Indicator.Position = UDim2.fromScale(0.875, 0.229);
                            v479.Indicator.Size = UDim2.fromOffset(18, 18);
                            v479.Indicator.BackgroundColor3 = v62.theme.Toggle;
                            v479.Indicator.BorderSizePixel = 0;
                            if (v479.flag and (v479.flag ~= "")) then
                                v62.flags[v479.flag] = v479.default or false ;
                            end
                            v479.Set = function(v906, v907)
                                if v907 then
                                    v479.Indicator.BackgroundColor3 = v62.theme.Selected;
                                else
                                    v479.Indicator.BackgroundColor3 = v62.theme.Toggle;
                                end
                                v479.value = v907;
                                v479.Indicator.BackgroundColor3 = (v907 and v62.theme.Selected) or v62.theme.Toggle ;
                                if (v479.flag and (v479.flag ~= "")) then
                                    v62.flags[v479.flag] = v479.value;
                                end
                                pcall(v479.callback, v907);
                            end;
                            v479.Main.MouseButton1Down:Connect(function()
                                v479:Set(not (((v479.Indicator.BackgroundColor3 == v62.theme.Selected) and true) or ((v479.Indicator.BackgroundColor3 == v62.theme.Toggle) and false)));
                            end);
                            v479:Set(v479.default);
                            v405:FixSize();
                            table.insert(v62.items, v479);
                            return v479
                        end;
                        v405.CreateSlider = function(v513, v514, v515, v516, v517, v518, v519, v520)
                            local v521 = {};
                            v521.text = v514 or "" ;
                            v521.callback = v519 or function(v910)
                            end ;
                            v521.min = v515 or (0) ;
                            v521.max = v517 or (100) ;
                            v521.decimals = v518 or (1) ;
                            v521.default = v516 or v521.min ;
                            v521.flag = v520 or v514 or "" ;
                            v521.value = v521.default;
                            local v530 = false;
                            v521.Mainback = Instance.new('Frame', v405.Items);
                            v521.Mainback.Size = UDim2.fromOffset(240, 35);
                            v521.Mainback.BackgroundColor3 = v62.theme.BackGround;
                            v521.Mainback.BorderSizePixel = 0;
                            v521.UICorner = Instance.new('UICorner', v521.Mainback);
                            v521.UICorner.CornerRadius = UDim.new(0, 8);
                            v521.Text = Instance.new('TextLabel', v521.Mainback);
                            v521.Text.Position = UDim2.fromScale(0.046, 0);
                            v521.Text.Size = UDim2.fromOffset(125, 35);
                            v521.Text.Text = v514;
                            v521.Text.TextColor3 = v62.theme.TextColor;
                            v521.Text.Font = v62.theme.Font;
                            v521.Text.TextSize = v62.theme.TextSize;
                            v521.Text.BackgroundTransparency = 1;
                            v521.Text.TextXAlignment = Enum.TextXAlignment.Left;
                            v521.Main = Instance.new('TextButton', v521.Mainback);
                            v521.Main.BackgroundColor3 = v62.theme.Toggle;
                            v521.Main.Text = "";
                            v521.Main.Position = UDim2.fromScale(0.533, 0.22900000000004184);
                            v521.Main.Size = UDim2.fromOffset(100, 18);
                            v521.Main.BorderSizePixel = 0;
                            v521.Main.AutoButtonColor = false;
                            v521.Slider = Instance.new('Frame', v521.Main);
                            v521.Slider.BackgroundColor3 = v62.theme.Selected;
                            v521.Slider.BorderSizePixel = 0;
                            v521.Slider.Position = UDim2.fromScale(0, 0);
                            v521.Slider.Size = UDim2.fromOffset(50, 18);
                            v521.OutPutText = Instance.new('TextLabel', v521.Main);
                            v521.OutPutText.Position = UDim2.fromScale(0, 0);
                            v521.OutPutText.Size = UDim2.fromOffset(100, 18);
                            v521.OutPutText.BackgroundTransparency = 1;
                            v521.OutPutText.Font = v62.theme.Font;
                            v521.OutPutText.TextColor3 = v62.theme.TextColor;
                            v521.OutPutText.TextSize = v62.theme.TextSize;
                            v521.OutPutText.Text = v521.value;
                            if (v521.flag and (v521.flag ~= "")) then
                                v62.flags[v521.flag] = v521.default or v521.min or (0) ;
                            end
                            v521.Get = function(v911)
                                return v521.value
                            end;
                            v521.Set = function(v912, v913)
                                local v914 = 0;
                                local v915;
                                while true do
                                    if (v914 == 2) then
                                        v521.OutPutText.Text = v521.value;
                                        pcall(v521.callback, v521.value);
                                        break
                                    end
                                    if (v914 == 0) then
                                        v521.value = math.clamp(math.round(v913 * v521.decimals) / v521.decimals, v521.min, v521.max);
                                        v915 = 1 - ((v521.max - v521.value) / (v521.max - v521.min)) ;
                                        v914 = 1;
                                    end
                                    if (v914 == 1) then
                                        if (v521.flag and (v521.flag ~= "")) then
                                            v62.flags[v521.flag] = v521.value;
                                        end
                                        v521.Slider:TweenSize(UDim2.fromOffset(v915 * v521.Main.AbsoluteSize.X, v521.Main.AbsoluteSize.Y), Enum.EasingDirection.In, Enum.EasingStyle.Sine, 7.000000000005002E-2);
                                        v914 = 2;
                                    end
                                end
                            end;
                            v521:Set(v521.default);
                            v521.Refresh = function(v916)
                                local v917 = 0;
                                local v918;
                                local v919;
                                local v920;
                                while true do
                                    if (v917 == 2) then
                                        v521:Set(v920);
                                        break
                                    end
                                    if (v917 == (0)) then
                                        v918 = game.Workspace.CurrentCamera:WorldToViewportPoint(game.Players.LocalPlayer:GetMouse().Hit.p);
                                        v919 = math.clamp(v918.X - v521.Slider.AbsolutePosition.X, 0, v521.Main.AbsoluteSize.X) / v521.Main.AbsoluteSize.X ;
                                        v917 = 1;
                                    end
                                    if (v917 == (1)) then
                                        local v1080 = 0;
                                        while true do
                                            if (v1080 == (0)) then
                                                v920 = math.floor((v521.min + ((v521.max - v521.min) * v919)) * v521.decimals) / v521.decimals ;
                                                v920 = math.clamp(v920, v521.min, v521.max);
                                                v1080 = 1;
                                            end
                                            if (1 == v1080) then
                                                v917 = 2;
                                                break
                                            end
                                        end
                                    end
                                end
                            end;
                            v521.Slider.InputBegan:Connect(function(v921)
                                if (v921.UserInputType == Enum.UserInputType.MouseButton1) then
                                    local v1036 = 0;
                                    local v1037;
                                    while true do
                                        if (v1036 == (0)) then
                                            v1037 = 0;
                                            while true do
                                                if (v1037 == (0)) then
                                                    v530 = true;
                                                    v521:Refresh();
                                                    break
                                                end
                                            end
                                            break
                                        end
                                    end
                                end
                            end);
                            v521.Slider.InputEnded:Connect(function(v922)
                                if (v922.UserInputType == Enum.UserInputType.MouseButton1) then
                                    v530 = false;
                                end
                            end);
                            v521.Main.InputBegan:Connect(function(v923)
                                if (v923.UserInputType == Enum.UserInputType.MouseButton1) then
                                    v530 = true;
                                    v521:Refresh();
                                end
                            end);
                            v521.Main.InputEnded:Connect(function(v924)
                                if (v924.UserInputType == Enum.UserInputType.MouseButton1) then
                                    v530 = false;
                                end
                            end);
                            game:GetService('UserInputService').InputChanged:Connect(function(v925)
                                if (v530 and (v925.UserInputType == Enum.UserInputType.MouseMovement)) then
                                    v521:Refresh();
                                end
                            end);
                            v405:FixSize();
                            table.insert(v62.items, v521);
                            return v521
                        end;
                        v405.CreateDropDown = function(v576, v577, v578, v579, v580, v581, v582)
                            local v583 = {};
                            v583.text = v577 or "" ;
                            v583.defaultitems = v578 or {} ;
                            v583.default = v579;
                            v583.callback = v581 or function()
                            end ;
                            v583.multichoice = v580 or false ;
                            v583.values = {};
                            v583.flag = v582 or v577 or "" ;
                            v583.MainBack = Instance.new('TextButton', v405.Items);
                            v583.MainBack.BackgroundColor3 = v62.theme.BackGround;
                            v583.MainBack.AutoButtonColor = false;
                            v583.MainBack.Size = UDim2.fromOffset(240, 35);
                            v583.MainBack.Text = "";
                            v583.UICorner = Instance.new('UICorner', v583.MainBack);
                            v583.UICorner.CornerRadius = UDim.new(0, 8);
                            v583.TextLabel = Instance.new('TextLabel', v583.MainBack);
                            v583.TextLabel.Text = v583.text;
                            v583.TextLabel.BackgroundTransparency = 1;
                            v583.TextLabel.TextColor3 = v62.theme.TextColor;
                            v583.TextLabel.TextSize = v62.theme.TextSize;
                            v583.TextLabel.Font = v62.theme.Font;
                            v583.TextLabel.Size = UDim2.fromOffset(125, 35);
                            v583.TextLabel.Position = UDim2.fromScale(0.046, 0);
                            v583.TextLabel.TextXAlignment = Enum.TextXAlignment.Left;
                            v583.Main = Instance.new('TextButton', v583.MainBack);
                            v583.Main.BackgroundColor3 = v62.theme.Toggle;
                            v583.Main.BorderSizePixel = 0;
                            v583.Main.Position = UDim2.fromScale(0.496, 0.229);
                            v583.Main.Size = UDim2.fromOffset(109, 18);
                            v583.Main.TextSize = v62.theme.TextSize;
                            v583.Main.TextColor3 = v62.theme.TextColor;
                            v583.Main.Font = v62.theme.Font;
                            v583.Main.AutoButtonColor = false;
                            v583.Main.Text = "";
                            v583.SelectedLable = Instance.new('TextLabel', v583.Main);
                            v583.SelectedLable.Position = UDim2.fromOffset(0, 0);
                            v583.SelectedLable.Size = UDim2.fromOffset(108, 18);
                            v583.SelectedLable.BackgroundTransparency = 1;
                            v583.SelectedLable.TextSize = v62.theme.TextSize;
                            v583.SelectedLable.TextColor3 = v62.theme.TextColor;
                            v583.SelectedLable.Font = v62.theme.Font;
                            v583.SelectedLable.Text = v583.text;
                            v583.Arrow = Instance.new('TextLabel', v583.Main);
                            v583.Arrow.Position = UDim2.fromScale(0.826, 0);
                            v583.Arrow.Size = UDim2.fromOffset(18, 18);
                            v583.Arrow.BackgroundTransparency = 1;
                            v583.Arrow.TextSize = v62.theme.TextSize;
                            v583.Arrow.TextColor3 = v62.theme.TextColor;
                            v583.Arrow.Font = v62.theme.Font;
                            v583.Arrow.Text = "<";
                            v583.Arrow.Rotation = - 90;
                            v583.Itemsframe = Instance.new('ScrollingFrame', v583.Main);
                            v583.Itemsframe.BorderSizePixel = 0;
                            v583.Itemsframe.BackgroundColor3 = v62.theme.BackGround;
                            v583.Itemsframe.Position = UDim2.fromOffset(0, v583.Main.Size.Y.Offset + 8);
                            v583.Itemsframe.ScrollBarThickness = 2;
                            v583.Itemsframe.ZIndex = 8;
                            v583.Itemsframe.ScrollingDirection = "Y";
                            v583.Itemsframe.Visible = false;
                            v583.Itemsframe.CanvasSize = UDim2.fromOffset(v583.Main.AbsoluteSize.X, 0);
                            v583.UIList = Instance.new('UIListLayout', v583.Itemsframe);
                            v583.UIList.FillDirection = Enum.FillDirection.Vertical;
                            v583.UIList.SortOrder = Enum.SortOrder.LayoutOrder;
                            v583.IgnoreBackButtons = Instance.new('TextButton', v583.Main);
                            v583.IgnoreBackButtons.BackgroundTransparency = 1;
                            v583.IgnoreBackButtons.BorderSizePixel = 0;
                            v583.IgnoreBackButtons.Position = UDim2.fromOffset(0, v583.Main.Size.Y.Offset + 8);
                            v583.IgnoreBackButtons.Size = UDim2.new(0, 0, 0, 0);
                            v583.IgnoreBackButtons.ZIndex = 7;
                            v583.IgnoreBackButtons.Text = "";
                            v583.IgnoreBackButtons.Visible = false;
                            v583.IgnoreBackButtons.AutoButtonColor = false;
                            if (v583.flag and (v583.flag ~= "")) then
                                v62.flags[v583.flag] = (v583.multichoice and {
                                    v583.default or v583.defaultitems[1] or ""
                                }) or v583.default or v583.defaultitems[1] or "" ;
                            end
                            v583.isSelected = function(v926, v927)
                                local v928 = 0;
                                while true do
                                    if (v928 == (0)) then
                                        for v1097, v1098 in pairs(v583.values) do
                                            if (v1098 == v927) then
                                                return true
                                            end
                                        end
                                        return false
                                    end
                                end
                            end;
                            v583.GetOptions = function(v929)
                                return v583.values
                            end;
                            v583.updateText = function(v930, v931)
                                if (# v931 >= (27)) then
                                    v931 = v931:sub(1, 25) .. '..' ;
                                end
                                v583.SelectedLable.Text = v931;
                            end;
                            v583.Changed = Instance.new('BindableEvent');
                            v583.Set = function(v933, v934)
                                local v935 = 0;
                                while true do
                                    if (v935 == 0) then
                                        if (type(v934) == 'table') then
                                            v583.values = v934;
                                            v583:updateText(table.concat(v934, ', '));
                                            pcall(v583.callback, v934);
                                        else
                                            local v1107 = 0;
                                            while true do
                                                if (v1107 == 0) then
                                                    v583:updateText(v934);
                                                    v583.values = {
                                                        v934
                                                    };
                                                    v1107 = 1;
                                                end
                                                if (v1107 == (1)) then
                                                    pcall(v583.callback, v934);
                                                    break
                                                end
                                            end
                                        end
                                        v583.Changed:Fire(v934);
                                        v935 = 1;
                                    end
                                    if (v935 == (1)) then
                                        if (v583.flag and (v583.flag ~= "")) then
                                            v62.flags[v583.flag] = (v583.multichoice and v583.values) or v583.values[1] ;
                                        end
                                        break
                                    end
                                end
                            end;
                            v583.Get = function(v936)
                                return (v583.multichoice and v583.values) or v583.values[1]
                            end;
                            v583.items = {};
                            v583.Add = function(v937, v938)
                                local v939 = Instance.new('TextButton', v583.Itemsframe);
                                v939.BackgroundColor3 = v62.theme.Toggle;
                                v939.TextColor3 = v62.theme.TextColor;
                                v939.BorderSizePixel = 0;
                                v939.Position = UDim2.fromOffset(0, 0);
                                v939.Size = UDim2.fromOffset(180, 20);
                                v939.BackgroundTransparency = 0;
                                v939.ZIndex = 9;
                                v939.Text = v938;
                                v939.Name = v938;
                                v939.AutoButtonColor = false;
                                v939.Font = v62.theme.Font;
                                v939.TextSize = v62.theme.TextSize;
                                v939.TextXAlignment = Enum.TextXAlignment.Left;
                                v939.MouseButton1Down:Connect(function()
                                    local v1017 = 0;
                                    local v1018;
                                    while true do
                                        if (v1017 == (0)) then
                                            v1018 = 0;
                                            while true do
                                                if (v1018 == (0)) then
                                                    if v583.multichoice then
                                                        if v583:isSelected(v938) then
                                                            for v1380, v1381 in pairs(v583.values) do
                                                                if (v1381 == v938) then
                                                                    table.remove(v583.values, v1380);
                                                                end
                                                            end
                                                            v583:Set(v583.values);
                                                        else
                                                            local v1335 = 0;
                                                            while true do
                                                                if (v1335 == (0)) then
                                                                    table.insert(v583.values, v938);
                                                                    v583:Set(v583.values);
                                                                    break
                                                                end
                                                            end
                                                        end
                                                        return
                                                    else
                                                        local v1320 = 0;
                                                        while true do
                                                            if (v1320 == (0)) then
                                                                v583.Itemsframe.Visible = false;
                                                                v583.Itemsframe.Active = false;
                                                                v1320 = 1;
                                                            end
                                                            if (v1320 == (1)) then
                                                                v583.IgnoreBackButtons.Visible = false;
                                                                v583.IgnoreBackButtons.Active = false;
                                                                break
                                                            end
                                                        end
                                                    end
                                                    v583:Set(v938);
                                                    v1018 = 1;
                                                end
                                                if ((1) == v1018) then
                                                    return
                                                end
                                            end
                                            break
                                        end
                                    end
                                end);
                                game:GetService('RunService').RenderStepped:Connect(function()
                                    if ((v583.multichoice and v583:isSelected(v938)) or (v583.values[1] == v938)) then
                                        v939.BackgroundColor3 = v62.theme.Selected;
                                        v939.Text = v938;
                                    else
                                        v939.BackgroundColor3 = v62.theme.BackGround2;
                                        v939.Text = v938;
                                    end
                                end);
                                table.insert(v583.items, v938);
                                v583.Itemsframe.Size = UDim2.fromOffset(v583.Main.Size.X.Offset, math.clamp(# v583.items * v939.AbsoluteSize.Y, 20, 156) + 2 + 2);
                                v583.Itemsframe.CanvasSize = UDim2.fromOffset(v583.Itemsframe.AbsoluteSize.X, (# v583.items * v939.AbsoluteSize.Y) + 4);
                                v583.IgnoreBackButtons.Size = v583.Itemsframe.Size;
                            end;
                            v583.Remove = function(v961, v962)
                                local v963 = 0;
                                local v964;
                                while true do
                                    if (v963 == (0)) then
                                        v964 = v583.Itemsframe:FindFirstChild(v962);
                                        if v964 then
                                            local v1109 = 0;
                                            while true do
                                                if (v1109 == 1) then
                                                    v583.Itemsframe.CanvasSize = UDim2.fromOffset(v583.Itemsframe.AbsoluteSize.X, (# v583.items * v964.AbsoluteSize.Y) + (4));
                                                    v583.IgnoreBackButtons.Size = v583.Itemsframe.Size;
                                                    v1109 = 2;
                                                end
                                                if (v1109 == (2)) then
                                                    v964:Remove();
                                                    break
                                                end
                                                if (0 == v1109) then
                                                    for v1321, v1322 in pairs(v583.items) do
                                                        if (v1322 == v962) then
                                                            table.remove(v583.items, v1321);
                                                        end
                                                    end
                                                    v583.Itemsframe.Size = UDim2.fromOffset(v583.Main.Size.X.Offset, math.clamp(# v583.items * v964.AbsoluteSize.Y, 20, 156) + 4);
                                                    v1109 = 1;
                                                end
                                            end
                                        end
                                        break
                                    end
                                end
                            end;
                            for v965, v966 in pairs(v583.defaultitems) do
                                v583:Add(v966);
                            end
                            if v583.default then
                                v583:Set(v583.default);
                            end
                            local v672 = function()
                                if not v583.Itemsframe.Visible then
                                    if (v583.items and (# v583.items ~= 0)) then
                                        local v1099 = 0;
                                        while true do
                                            if (v1099 == (1)) then
                                                v583.Itemsframe.Visible = true;
                                                v583.Itemsframe.Active = true;
                                                v1099 = 2;
                                            end
                                            if (v1099 == (2)) then
                                                v583.IgnoreBackButtons.Visible = true;
                                                v583.IgnoreBackButtons.Active = true;
                                                break
                                            end
                                            if ((0) == v1099) then
                                                v583.Arrow.Rotation = 90;
                                                v583.Itemsframe.ScrollingEnabled = true;
                                                v1099 = 1;
                                            end
                                        end
                                    end
                                else
                                    v583.Arrow.Rotation = - 90;
                                    v583.Itemsframe.ScrollingEnabled = false;
                                    v583.Itemsframe.Visible = false;
                                    v583.Itemsframe.Active = false;
                                    v583.IgnoreBackButtons.Visible = false;
                                    v583.IgnoreBackButtons.Active = false;
                                end
                            end;
                            v583.MainBack.MouseButton1Down:Connect(v672);
                            v583.Main.MouseButton1Down:Connect(v672);
                            v405:FixSize();
                            table.insert(v62.items, v583);
                            return v583
                        end;
                        v405.CreateColorPicker = function(v673, v674, v675, v676, v677)
                            local v678 = {};
                            v678.callback = v676 or function()
                            end ;
                            v678.default = v675 or Color3.fromRGB(255, 255, 255) ;
                            v678.value = v678.default;
                            v678.flag = v677 or v674 or "" ;
                            v678.MainBack = Instance.new('TextButton', v405.Items);
                            v678.MainBack.BackgroundColor3 = v62.theme.BackGround;
                            v678.MainBack.AutoButtonColor = false;
                            v678.MainBack.Size = UDim2.fromOffset(240, 35);
                            v678.MainBack.Text = "";
                            v678.UiCorner = Instance.new('UICorner', v678.MainBack);
                            v678.UiCorner.CornerRadius = UDim.new(0, 8);
                            v678.Indicator = Instance.new('Frame', v678.MainBack);
                            v678.Indicator.Position = UDim2.fromScale(0.875, 0.229);
                            v678.Indicator.Size = UDim2.fromOffset(18, 18);
                            v678.Indicator.BackgroundColor3 = v678.default;
                            v678.Indicator.BorderSizePixel = 0;
                            v678.TextLabel = Instance.new('TextLabel', v678.MainBack);
                            v678.TextLabel.Text = v674;
                            v678.TextLabel.BackgroundTransparency = 1;
                            v678.TextLabel.TextColor3 = v62.theme.TextColor;
                            v678.TextLabel.TextSize = v62.theme.TextSize;
                            v678.TextLabel.Font = v62.theme.Font;
                            v678.TextLabel.Size = UDim2.fromOffset(125, 35);
                            v678.TextLabel.Position = UDim2.fromScale(4.6E-2, 0);
                            v678.TextLabel.TextXAlignment = Enum.TextXAlignment.Left;
                            v678.MainPicker = Instance.new('TextButton', v678.MainBack);
                            v678.MainPicker.Name = 'picker';
                            v678.MainPicker.ZIndex = 100;
                            v678.MainPicker.Visible = false;
                            v678.MainPicker.AutoButtonColor = false;
                            v678.MainPicker.Text = "";
                            v678.MainPicker.Size = UDim2.fromOffset(180, 196);
                            v678.MainPicker.BorderSizePixel = 0;
                            v678.MainPicker.BackgroundColor3 = Color3.fromRGB(40, 40, 40);
                            v678.MainPicker.Rotation = 1E-15;
                            v678.MainPicker.Position = UDim2.fromOffset(- v678.MainPicker.AbsoluteSize.X + v678.MainBack.AbsoluteSize.X, 17);
                            v256.OpenedColorPickers[v678.MainPicker] = false;
                            v678.hue = Instance.new('ImageLabel', v678.MainPicker);
                            v678.hue.ZIndex = 101;
                            v678.hue.Position = UDim2.new(0, 3, 0, 3);
                            v678.hue.Size = UDim2.new(0, 172, 0, 172);
                            v678.hue.Image = 'rbxassetid://4155801252';
                            v678.hue.ScaleType = Enum.ScaleType.Stretch;
                            v678.hue.BackgroundColor3 = Color3.new(1, 0, 0);
                            v678.hue.BorderColor3 = v62.theme.Border;
                            v678.hueselectorpointer = Instance.new('ImageLabel', v678.MainPicker);
                            v678.hueselectorpointer.ZIndex = 101;
                            v678.hueselectorpointer.BackgroundTransparency = 1;
                            v678.hueselectorpointer.BorderSizePixel = 0;
                            v678.hueselectorpointer.Position = UDim2.new(0, 0, 0, 0);
                            v678.hueselectorpointer.Size = UDim2.new(0, 7, 0, 7);
                            v678.hueselectorpointer.Image = 'rbxassetid://6885856475';
                            v678.selector = Instance.new('TextLabel', v678.MainPicker);
                            v678.selector.ZIndex = 100;
                            v678.selector.Position = UDim2.new(0, 3, 0, 181);
                            v678.selector.Size = UDim2.new(0, 173, 0, 10);
                            v678.selector.BackgroundColor3 = Color3.fromRGB(255, 255, 255);
                            v678.selector.BorderColor3 = v62.theme.Border;
                            v678.selector.Text = "";
                            v678.gradient = Instance.new('UIGradient', v678.selector);
                            v678.gradient.Color = ColorSequence.new({
                                ColorSequenceKeypoint.new(0, Color3.new(1, 0, 0)),
                                ColorSequenceKeypoint.new(0.17, Color3.new(1, 0, 1)),
                                ColorSequenceKeypoint.new(0.33, Color3.new(0, 0, 1)),
                                ColorSequenceKeypoint.new(0.5, Color3.new(0, 1, 1)),
                                ColorSequenceKeypoint.new(0.6700000000000017, Color3.new(0, 1, 0)),
                                ColorSequenceKeypoint.new(0.83, Color3.new(1, 1, 0)),
                                ColorSequenceKeypoint.new(1, Color3.new(1, 0, 0))
                            });
                            v678.pointer = Instance.new('Frame', v678.selector);
                            v678.pointer.ZIndex = 101;
                            v678.pointer.BackgroundColor3 = v62.theme.Border;
                            v678.pointer.Position = UDim2.new(0, 0, 0, 0);
                            v678.pointer.Size = UDim2.new(0, 2, 0, 10);
                            v678.pointer.BorderColor3 = v62.theme.BackGround;
                            if (v678.flag and (v678.flag ~= "")) then
                                v62.flags[v678.flag] = v678.default;
                            end
                            v678.RefreshHue = function(v967)
                                local v968 = 0;
                                local v969;
                                local v970;
                                while true do
                                    if ((1) == v968) then
                                        v678.hueselectorpointer:TweenPosition(UDim2.new(math.clamp(v969 * v678.hue.AbsoluteSize.X, 0.5, (0.952) * v678.hue.AbsoluteSize.X) / v678.hue.AbsoluteSize.X, 0, math.clamp(v970 * v678.hue.AbsoluteSize.Y, 0.5, 0.885 * v678.hue.AbsoluteSize.Y) / v678.hue.AbsoluteSize.Y, 0), Enum.EasingDirection.In, Enum.EasingStyle.Sine, 5E-2);
                                        v678:Set(Color3.fromHSV(v678.color, math.clamp(v969 * v678.hue.AbsoluteSize.X, 0.5, (1) * v678.hue.AbsoluteSize.X) / v678.hue.AbsoluteSize.X, 1 - (math.clamp(v970 * v678.hue.AbsoluteSize.Y, 0.5, (1) * v678.hue.AbsoluteSize.Y) / v678.hue.AbsoluteSize.Y)));
                                        break
                                    end
                                    if (v968 == (0)) then
                                        local v1087 = 0;
                                        while true do
                                            if (v1087 == 1) then
                                                v968 = 1;
                                                break
                                            end
                                            if ((0) == v1087) then
                                                v969 = (game.Players.LocalPlayer:GetMouse().X - v678.hue.AbsolutePosition.X) / v678.hue.AbsoluteSize.X ;
                                                v970 = (game.Players.LocalPlayer:GetMouse().Y - v678.hue.AbsolutePosition.Y) / v678.hue.AbsoluteSize.Y ;
                                                v1087 = 1;
                                            end
                                        end
                                    end
                                end
                            end;
                            v678.RefreshSelector = function(v971)
                                local v972 = 0;
                                local v973;
                                local v974;
                                local v975;
                                while true do
                                    if (v972 == (2)) then
                                        v974 = (v678.hueselectorpointer.AbsolutePosition.X - v678.hue.AbsolutePosition.X) / v678.hue.AbsoluteSize.X ;
                                        v975 = (v678.hueselectorpointer.AbsolutePosition.Y - v678.hue.AbsolutePosition.Y) / v678.hue.AbsoluteSize.Y ;
                                        v972 = 3;
                                    end
                                    if (v972 == 3) then
                                        v678:Set(Color3.fromHSV(v678.color, math.clamp(v974 * v678.hue.AbsoluteSize.X, 0.5, (1) * v678.hue.AbsoluteSize.X) / v678.hue.AbsoluteSize.X, (1) - (math.clamp(v975 * v678.hue.AbsoluteSize.Y, 0.5, (1) * v678.hue.AbsoluteSize.Y) / v678.hue.AbsoluteSize.Y)));
                                        break
                                    end
                                    if ((1) == v972) then
                                        v678.pointer:TweenPosition(UDim2.new(v973, 0, 0, 0), Enum.EasingDirection.In, Enum.EasingStyle.Sine, 5E-2);
                                        v678.hue.BackgroundColor3 = Color3.fromHSV((1) - v973, 1, 1);
                                        v972 = 2;
                                    end
                                    if (v972 == (0)) then
                                        local v1089 = 0;
                                        while true do
                                            if (v1089 == (1)) then
                                                v972 = 1;
                                                break
                                            end
                                            if (v1089 == (0)) then
                                                v973 = math.clamp((game.Players.LocalPlayer:GetMouse().X - v678.hue.AbsolutePosition.X) / v678.hue.AbsoluteSize.X, 0, 1);
                                                v678.color = 1 - v973 ;
                                                v1089 = 1;
                                            end
                                        end
                                    end
                                end
                            end;
                            v678.Set = function(v976, v977)
                                local v978 = 0;
                                local v979;
                                local v980;
                                while true do
                                    if (v978 == 2) then
                                        v678.Indicator.BackgroundColor3 = v979;
                                        pcall(v678.callback, v979);
                                        break
                                    end
                                    if (v978 == (1)) then
                                        if (v678.flag and (v678.flag ~= "")) then
                                            v62.flags[v678.flag] = v979;
                                        end
                                        v980 = Color3.new(math.clamp(v979.R / 1.7, 0, 1), math.clamp(v979.G / (1.7), 0, 1), math.clamp(v979.B / 1.7, 0, 1));
                                        v978 = 2;
                                    end
                                    if (v978 == 0) then
                                        v979 = Color3.new(math.clamp(v977.r, 0, 1), math.clamp(v977.g, 0, 1), math.clamp(v977.b, 0, 1));
                                        v678.value = v979;
                                        v978 = 1;
                                    end
                                end
                            end;
                            v678.Get = function(v981, v982)
                                return v678.value
                            end;
                            v678:Set(v678.default);
                            local v757 = false;
                            local v758 = false;
                            v678.selector.InputBegan:Connect(function(v983)
                                if (v983.UserInputType == Enum.UserInputType.MouseButton1) then
                                    local v1044 = 0;
                                    while true do
                                        if (v1044 == (0)) then
                                            v757 = true;
                                            v678:RefreshSelector();
                                            break
                                        end
                                    end
                                end
                            end);
                            v678.selector.InputEnded:Connect(function(v984)
                                if (v984.UserInputType == Enum.UserInputType.MouseButton1) then
                                    v757 = false;
                                    v678:RefreshSelector();
                                end
                            end);
                            v678.hue.InputBegan:Connect(function(v985)
                                if (v985.UserInputType == Enum.UserInputType.MouseButton1) then
                                    local v1045 = 0;
                                    while true do
                                        if (v1045 == 0) then
                                            v758 = true;
                                            v678:RefreshHue();
                                            break
                                        end
                                    end
                                end
                            end);
                            v678.hue.InputEnded:Connect(function(v986)
                                if (v986.UserInputType == Enum.UserInputType.MouseButton1) then
                                    local v1046 = 0;
                                    while true do
                                        if (v1046 == 0) then
                                            v758 = false;
                                            v678:RefreshHue();
                                            break
                                        end
                                    end
                                end
                            end);
                            game:GetService('UserInputService').InputChanged:Connect(function(v987)
                                local v988 = 0;
                                local v989;
                                while true do
                                    if (v988 == (0)) then
                                        v989 = 0;
                                        while true do
                                            if (0 == v989) then
                                                if (v757 and (v987.UserInputType == Enum.UserInputType.MouseMovement)) then
                                                    v678:RefreshSelector();
                                                end
                                                if (v758 and (v987.UserInputType == Enum.UserInputType.MouseMovement)) then
                                                    v678:RefreshHue();
                                                end
                                                break
                                            end
                                        end
                                        break
                                    end
                                end
                            end);
                            local v759 = function(v990)
                                if (v990.UserInputType == Enum.UserInputType.MouseButton1) then
                                    local v1047 = 0;
                                    local v1048;
                                    while true do
                                        if (v1047 == (0)) then
                                            v1048 = 0;
                                            while true do
                                                if (v1048 == 0) then
                                                    for v1323, v1324 in pairs(v256.OpenedColorPickers) do
                                                        if (v1324 and (v1323 ~= v678.MainPicker)) then
                                                            local v1336 = 0;
                                                            local v1337;
                                                            while true do
                                                                if (v1336 == 0) then
                                                                    v1337 = 0;
                                                                    while true do
                                                                        if (v1337 == (0)) then
                                                                            v1323.Visible = false;
                                                                            v256.OpenedColorPickers[v1323] = false;
                                                                            break
                                                                        end
                                                                    end
                                                                    break
                                                                end
                                                            end
                                                        end
                                                    end
                                                    v678.MainPicker.Visible = not v678.MainPicker.Visible;
                                                    v1048 = 1;
                                                end
                                                if (v1048 == (1)) then
                                                    v256.OpenedColorPickers[v678.MainPicker] = v678.MainPicker.Visible;
                                                    break
                                                end
                                            end
                                            break
                                        end
                                    end
                                end
                            end;
                            v678.MainBack.InputBegan:Connect(v759);
                            v678.MainPicker.InputBegan:Connect(v759);
                            v678.MainPicker.InputBegan:Connect(v759);
                            v405:FixSize();
                            table.insert(v62.items, v678);
                            return v678
                        end;
                        v405.CreateKeyBind = function(v760, v761, v762, v763, v764)
                            local v765 = {};
                            v765.text = v761 or "" ;
                            v765.default = v762 or 'None' ;
                            v765.value = v765.default;
                            v765.callback = v763 or function()
                            end ;
                            v765.flag = v764 or v761 or "" ;
                            local v771 = {
                                LeftShift = 'LSHIFT',
                                RightShift = 'RSHIFT',
                                LeftControl = 'LCTRL',
                                RightControl = 'RCTRL',
                                LeftAlt = 'LALT',
                                RightAlt = 'RALT'
                            };
                            local v772 = ((v765.default == 'None') and 'None') or v771[v765.default.Name] or v765.default.Name ;
                            v765.MainBack = Instance.new('TextButton', v405.Items);
                            v765.MainBack.BackgroundColor3 = v62.theme.BackGround;
                            v765.MainBack.AutoButtonColor = false;
                            v765.MainBack.Size = UDim2.fromOffset(240, 35);
                            v765.MainBack.Text = "";
                            v765.UICorner = Instance.new('UICorner', v765.MainBack);
                            v765.UICorner.CornerRadius = UDim.new(0, 8);
                            v765.TextLabel = Instance.new('TextLabel', v765.MainBack);
                            v765.TextLabel.Text = v765.text;
                            v765.TextLabel.BackgroundTransparency = 1;
                            v765.TextLabel.TextColor3 = v62.theme.TextColor;
                            v765.TextLabel.TextSize = v62.theme.TextSize;
                            v765.TextLabel.Font = v62.theme.Font;
                            v765.TextLabel.Size = UDim2.fromOffset(125, 35);
                            v765.TextLabel.Position = UDim2.fromScale(4.6E-2, 0);
                            v765.TextLabel.TextXAlignment = Enum.TextXAlignment.Left;
                            v765.Main = Instance.new('TextButton', v765.MainBack);
                            v765.Main.BorderSizePixel = 0;
                            v765.Main.BackgroundColor3 = v62.theme.Toggle;
                            v765.Main.Size = UDim2.fromOffset(109, 18);
                            v765.Main.Position = UDim2.fromScale(0.4959999999999809, 0.229);
                            v765.Main.Text = v772;
                            v765.Main.Font = v62.theme.Font;
                            v765.Main.TextColor3 = v62.theme.TextColor;
                            v765.Main.TextSize = v62.theme.TextSize;
                            v765.Main.TextXAlignment = Enum.TextXAlignment.Center;
                            v765.Main.MouseButton1Down:Connect(function()
                                v765.Main.Text = '...';
                            end);
                            if (v765.flag and (v765.flag ~= "")) then
                                v62.flags[v765.flag] = v765.default;
                            end
                            v765.Set = function(v992, v993)
                                if (v993 == 'None') then
                                    local v1049 = 0;
                                    while true do
                                        if (v1049 == (0)) then
                                            v765.Main.Text = v993;
                                            v765.value = v993;
                                            v1049 = 1;
                                        end
                                        if (v1049 == (1)) then
                                            if (v765.flag and (v765.flag ~= "")) then
                                                v62.flags[v765.flag] = v993;
                                            end
                                            break
                                        end
                                    end
                                end
                                v765.Main.Text = v771[v993.Name] or v993.Name ;
                                v765.value = v993;
                                if (v765.flag and (v765.flag ~= "")) then
                                    v62.flags[v765.flag] = v765.value;
                                end
                            end;
                            v765.Get = function(v996)
                                return v765.value
                            end;
                            game:GetService('UserInputService').InputBegan:Connect(function(v997, v998)
                                if not v998 then
                                    if (v765.Main.Text == '...') then
                                        if ((v997.UserInputType == Enum.UserInputType.Keyboard) and (v997.KeyCode ~= Enum.KeyCode.Backspace)) then
                                            local v1170 = 0;
                                            while true do
                                                if (v1170 == (0)) then
                                                    v765:Set(v997.KeyCode);
                                                    pcall(v765.callback, v765.value);
                                                    break
                                                end
                                            end
                                        else
                                            v765:Set('None');
                                        end
                                    end
                                end
                            end);
                            v405:FixSize();
                            table.insert(v62.items, v765);
                            return v765
                        end;
                        v405.CreateCoppyText = function(v808, v809)
                            local v810 = {};
                            v810.MainBack = Instance.new('TextButton', v405.Items);
                            v810.MainBack.BackgroundColor3 = v62.theme.BackGround;
                            v810.MainBack.AutoButtonColor = false;
                            v810.MainBack.Size = UDim2.fromOffset(240, 35);
                            v810.MainBack.Text = "";
                            v810.UICorner = Instance.new('UICorner', v810.MainBack);
                            v810.UICorner.CornerRadius = UDim.new(0, 8);
                            v810.TextLabel = Instance.new('TextBox', v810.MainBack);
                            v810.TextLabel.Text = v809;
                            v810.TextLabel.ClearTextOnFocus = false;
                            v810.TextLabel.Interactable = true;
                            v810.TextLabel.TextEditable = false;
                            v810.TextLabel.Active = false;
                            v810.TextLabel.BackgroundTransparency = 1;
                            v810.TextLabel.TextColor3 = v62.theme.TextColor;
                            v810.TextLabel.TextSize = v62.theme.TextSize;
                            v810.TextLabel.Font = v62.theme.Font;
                            v810.TextLabel.Size = UDim2.fromOffset(240, 35);
                            v810.TextLabel.Position = UDim2.fromScale(0, 0);
                            v810.TextLabel.TextXAlignment = Enum.TextXAlignment.Center;
                            v405:FixSize();
                            table.insert(v62.items, v810);
                            return v810
                        end;
                        v405.CreateLable = function(v836, v837)
                            local v838 = 0;
                            local v839;
                            while true do
                                if (v838 == (3)) then
                                    v839.TextLabel.TextSize = v62.theme.TextSize;
                                    v839.TextLabel.Font = v62.theme.Font;
                                    v839.TextLabel.Size = UDim2.fromOffset(125, 35);
                                    v839.TextLabel.Position = UDim2.fromScale(0.046, 0);
                                    v838 = 4;
                                end
                                if (v838 == 0) then
                                    v839 = {};
                                    v839.MainBack = Instance.new('TextButton', v405.Items);
                                    v839.MainBack.BackgroundColor3 = v62.theme.BackGround;
                                    v839.MainBack.AutoButtonColor = false;
                                    v838 = 1;
                                end
                                if (v838 == 1) then
                                    v839.MainBack.Size = UDim2.fromOffset(240, 35);
                                    v839.MainBack.Text = "";
                                    v839.UICorner = Instance.new('UICorner', v839.MainBack);
                                    v839.UICorner.CornerRadius = UDim.new(0, 8);
                                    v838 = 2;
                                end
                                if (v838 == (2)) then
                                    v839.TextLabel = Instance.new('TextLabel', v839.MainBack);
                                    v839.TextLabel.Text = v839.text;
                                    v839.TextLabel.BackgroundTransparency = 1;
                                    v839.TextLabel.TextColor3 = v62.theme.TextColor;
                                    v838 = 3;
                                end
                                if (v838 == (4)) then
                                    v839.TextLabel.TextXAlignment = Enum.TextXAlignment.Left;
                                    v405:FixSize();
                                    table.insert(v62.items, v839);
                                    return v839
                                end
                            end
                        end;
                        v405.CreateTextBox = function(v840, v841, v842, v843, v844)
                            local v845 = 0;
                            local v846;
                            while true do
                                local v999 = 0;
                                while true do
                                    if (2 == v999) then
                                        if (v845 == 4) then
                                            v846.TextLabel.Position = UDim2.fromScale(0.046, 0);
                                            v846.TextLabel.TextXAlignment = Enum.TextXAlignment.Left;
                                            v846.Main = Instance.new('TextBox', v846.MainBack);
                                            v846.Main.Position = UDim2.fromScale(0.496, 0.22900000000004184);
                                            v846.Main.Size = UDim2.fromOffset(109, 18);
                                            v845 = 5;
                                        end
                                        if (v845 == 6) then
                                            local v1119 = 0;
                                            while true do
                                                if (v1119 == (2)) then
                                                    v846.Get = function(v1325)
                                                        return v846.value
                                                    end;
                                                    v845 = 7;
                                                    break
                                                end
                                                if ((0) == v1119) then
                                                    v846.Main.TextSize = v62.theme.TextSize;
                                                    v846.Main.ClearTextOnFocus = false;
                                                    v1119 = 1;
                                                end
                                                if (v1119 == (1)) then
                                                    if (v846.flag and (v846.flag ~= "")) then
                                                        v62.flags[v846.flag] = v846.default or "" ;
                                                    end
                                                    v846.Set = function(v1326, v1327)
                                                        local v1328 = 0;
                                                        while true do
                                                            if (v1328 == (0)) then
                                                                v846.value = v1327;
                                                                v846.Main.Text = v1327;
                                                                v1328 = 1;
                                                            end
                                                            if (v1328 == (1)) then
                                                                if (v846.flag and (v846.flag ~= "")) then
                                                                    v62.flags[v846.flag] = v1327;
                                                                end
                                                                pcall(v846.callback, v1327);
                                                                break
                                                            end
                                                        end
                                                    end;
                                                    v1119 = 2;
                                                end
                                            end
                                        end
                                        v999 = 3;
                                    end
                                    if (v999 == (3)) then
                                        if (v845 == (7)) then
                                            local v1120 = 0;
                                            while true do
                                                if (v1120 == (2)) then
                                                    return v846
                                                end
                                                if ((0) == v1120) then
                                                    if v846.default then
                                                        v846:Set(v846.default);
                                                    end
                                                    v846.Main.FocusLost:Connect(function()
                                                        v846:Set(v846.Main.Text);
                                                    end);
                                                    v1120 = 1;
                                                end
                                                if (v1120 == (1)) then
                                                    v405:FixSize();
                                                    table.insert(v62.items, v846);
                                                    v1120 = 2;
                                                end
                                            end
                                        end
                                        if (v845 == (2)) then
                                            v846.MainBack.Text = "";
                                            v846.UICorner = Instance.new('UICorner', v846.MainBack);
                                            v846.UICorner.CornerRadius = UDim.new(0, 8);
                                            v846.TextLabel = Instance.new('TextLabel', v846.MainBack);
                                            v846.TextLabel.Text = v846.text;
                                            v845 = 3;
                                        end
                                        break
                                    end
                                    if ((0) == v999) then
                                        if (v845 == (5)) then
                                            local v1127 = 0;
                                            while true do
                                                if (v1127 == (2)) then
                                                    v846.Main.Font = v62.theme.Font;
                                                    v845 = 6;
                                                    break
                                                end
                                                if (v1127 == (1)) then
                                                    v846.Main.Text = "";
                                                    v846.Main.TextColor3 = v62.theme.TextColor;
                                                    v1127 = 2;
                                                end
                                                if (v1127 == (0)) then
                                                    v846.Main.BackgroundColor3 = v62.theme.Toggle;
                                                    v846.Main.BorderSizePixel = 0;
                                                    v1127 = 1;
                                                end
                                            end
                                        end
                                        if (v845 == (1)) then
                                            v846.flag = v844 or v841 or "" ;
                                            v846.MainBack = Instance.new('TextButton', v405.Items);
                                            v846.MainBack.BackgroundColor3 = v62.theme.BackGround;
                                            v846.MainBack.AutoButtonColor = false;
                                            v846.MainBack.Size = UDim2.fromOffset(240, 35);
                                            v845 = 2;
                                        end
                                        v999 = 1;
                                    end
                                    if (v999 == 1) then
                                        if ((0) == v845) then
                                            v846 = {};
                                            v846.text = v841 or "" ;
                                            v846.callback = v843 or function()
                                            end ;
                                            v846.default = v842;
                                            v846.value = "";
                                            v845 = 1;
                                        end
                                        if (v845 == (3)) then
                                            v846.TextLabel.BackgroundTransparency = 1;
                                            v846.TextLabel.TextColor3 = v62.theme.TextColor;
                                            v846.TextLabel.TextSize = v62.theme.TextSize;
                                            v846.TextLabel.Font = v62.theme.Font;
                                            v846.TextLabel.Size = UDim2.fromOffset(125, 35);
                                            v845 = 4;
                                        end
                                        v999 = 2;
                                    end
                                end
                            end
                        end;
                        v405.CreateButton = function(v847, v848, v849)
                            local v850 = 0;
                            local v851;
                            while true do
                                local v1000 = 0;
                                while true do
                                    if (v1000 == (0)) then
                                        if (v850 == (0)) then
                                            local v1146 = 0;
                                            while true do
                                                if (v1146 == (0)) then
                                                    v851 = {};
                                                    v851.text = v848 or "" ;
                                                    v1146 = 1;
                                                end
                                                if (v1146 == 1) then
                                                    v851.callback = v849 or function()
                                                    end ;
                                                    v850 = 1;
                                                    break
                                                end
                                            end
                                        end
                                        if (v850 == (2)) then
                                            v851.MainBack.Size = UDim2.fromOffset(240, 35);
                                            v851.MainBack.Text = "";
                                            v851.MainBack.Text = v851.text;
                                            v850 = 3;
                                        end
                                        v1000 = 1;
                                    end
                                    if (v1000 == 1) then
                                        if (v850 == (4)) then
                                            v851.MainBack.MouseButton1Click:Connect(v851.callback);
                                            v851.UICorner = Instance.new('UICorner', v851.MainBack);
                                            v851.UICorner.CornerRadius = UDim.new(0, 8);
                                            v850 = 5;
                                        end
                                        if (v850 == (1)) then
                                            v851.MainBack = Instance.new('TextButton', v405.Items);
                                            v851.MainBack.BackgroundColor3 = v62.theme.BackGround;
                                            v851.MainBack.AutoButtonColor = false;
                                            v850 = 2;
                                        end
                                        v1000 = 2;
                                    end
                                    if ((2) == v1000) then
                                        if ((3) == v850) then
                                            local v1156 = 0;
                                            while true do
                                                if (v1156 == (0)) then
                                                    v851.MainBack.Font = v62.theme.Font;
                                                    v851.MainBack.TextColor3 = v62.theme.TextColor;
                                                    v1156 = 1;
                                                end
                                                if (v1156 == (1)) then
                                                    v851.MainBack.TextSize = v62.theme.TextSize;
                                                    v850 = 4;
                                                    break
                                                end
                                            end
                                        end
                                        if (v850 == 5) then
                                            v405:FixSize();
                                            return v851
                                        end
                                        break
                                    end
                                end
                            end
                        end;
                        return v405
                    end;
                    v333.CreateConfig = function(v455, v456)
                        local v457 = 0;
                        local v458;
                        while true do
                            if (v457 == (0)) then
                                v458 = {};
                                v458.configFolder = v256.name;
                                v457 = 1;
                            end
                            if (v457 == (1)) then
                                local v1025 = 0;
                                while true do
                                    if (v1025 == (0)) then
                                        pcall(function()
                                            if (isfolder and makefolder and listfiles and writefile and readfile and delfile) then
                                                if not isfolder(v458.configFolder) then
                                                    makefolder(v458.configFolder);
                                                end
                                                v458.sector = v333:CreateSector('Configs', v456 or 'left');
                                                local v1181 = v458.sector:CreateTextBox('Config Name', "", ConfigName, function()
                                                end, "");
                                                local v1182 = tostring(listfiles(v458.configFolder)[1] or ""):gsub(v458.configFolder .. "\\", ""):gsub('.txt', "");
                                                local v1183 = v458.sector:CreateDropDown('Configs', {}, v1182, false, function()
                                                end, "");
                                                for v1235, v1236 in pairs(listfiles(v458.configFolder)) do
                                                    if v1236:find('.txt') then
                                                        v1183:Add(tostring(v1236):gsub(v458.configFolder .. "\\", ""):gsub('.txt', ""));
                                                    end
                                                end
                                                v458.Create = v458.sector:CreateButton('Create', function()
                                                    local v1237 = 0;
                                                    while true do
                                                        if (v1237 == (0)) then
                                                            for v1388, v1389 in pairs(listfiles(v458.configFolder)) do
                                                                v1183:Remove(tostring(v1389):gsub(v458.configFolder .. "\\", ""):gsub('.txt', ""));
                                                            end
                                                            if (v1181:Get() and (v1181:Get() ~= "")) then
                                                                local v1407 = 0;
                                                                local v1408;
                                                                while true do
                                                                    if (v1407 == (0)) then
                                                                        v1408 = {};
                                                                        for v1427, v1428 in pairs(v62.flags) do
                                                                            if ((v1428 ~= nil) and (v1428 ~= "")) then
                                                                                if (typeof(v1428) == 'Color3') then
                                                                                    v1408[v1427] = {
                                                                                        v1428.R,
                                                                                        v1428.G,
                                                                                        v1428.B
                                                                                    };
                                                                                elseif (tostring(v1428):find('Enum.KeyCode')) then
                                                                                    v1408[v1427] = v1428.Name;
                                                                                elseif (typeof(v1428) == 'table') then
                                                                                    v1408[v1427] = {
                                                                                        v1428
                                                                                    };
                                                                                else
                                                                                    v1408[v1427] = v1428;
                                                                                end
                                                                            end
                                                                        end
                                                                        v1407 = 1;
                                                                    end
                                                                    if (v1407 == (1)) then
                                                                        writefile(v458.configFolder .. "/" .. v1181:Get() .. '.txt', v66:JSONEncode(v1408));
                                                                        for v1429, v1430 in pairs(listfiles(v458.configFolder)) do
                                                                            if v1430:find('.txt') then
                                                                                v1183:Add(tostring(v1430):gsub(v458.configFolder .. "\\", ""):gsub('.txt', ""));
                                                                            end
                                                                        end
                                                                        break
                                                                    end
                                                                end
                                                            end
                                                            break
                                                        end
                                                    end
                                                end);
                                                v458.Save = v458.sector:CreateButton('Save', function()
                                                    local v1238 = {};
                                                    if (v1183:Get() and (v1183:Get() ~= "")) then
                                                        for v1338, v1339 in pairs(v62.flags) do
                                                            if ((v1339 ~= nil) and (v1339 ~= "")) then
                                                                if (typeof(v1339) == 'Color3') then
                                                                    v1238[v1338] = {
                                                                        v1339.R,
                                                                        v1339.G,
                                                                        v1339.B
                                                                    };
                                                                elseif (tostring(v1339):find('Enum.KeyCode')) then
                                                                    v1238[v1338] = 'Enum.KeyCode.' .. v1339.Name ;
                                                                elseif (typeof(v1339) == 'table') then
                                                                    v1238[v1338] = {
                                                                        v1339
                                                                    };
                                                                else
                                                                    v1238[v1338] = v1339;
                                                                end
                                                            end
                                                        end
                                                        writefile(v458.configFolder .. "/" .. v1181:Get() .. '.txt', v66:JSONEncode(v1238));
                                                    end
                                                end);
                                                v458.Load = v458.sector:CreateButton('Load', function()
                                                    local v1239 = pcall(readfile, v458.configFolder .. "/" .. v1183:Get() .. '.txt');
                                                    if v1239 then
                                                        pcall(function()
                                                            local v1340 = 0;
                                                            local v1341;
                                                            local v1342;
                                                            while true do
                                                                if (v1340 == (1)) then
                                                                    for v1419, v1420 in pairs(v1341) do
                                                                        if (typeof(v1420) == 'table') then
                                                                            if (typeof(v1420[1]) == 'number') then
                                                                                v1342[v1419] = Color3.new(v1420[1], v1420[2], v1420[3]);
                                                                            elseif (typeof(v1420[1]) == 'table') then
                                                                                v1342[v1419] = v1420[1];
                                                                            end
                                                                        elseif (tostring(v1420):find('Enum.KeyCode.')) then
                                                                            v1342[v1419] = Enum.KeyCode[tostring(v1420):gsub('Enum.KeyCode.', "")];
                                                                        else
                                                                            v1342[v1419] = v1420;
                                                                        end
                                                                    end
                                                                    v62.flags = v1342;
                                                                    v1340 = 2;
                                                                end
                                                                if ((0) == v1340) then
                                                                    v1341 = v66:JSONDecode(readfile(v458.configFolder .. "/" .. v1183:Get() .. '.txt'));
                                                                    v1342 = {};
                                                                    v1340 = 1;
                                                                end
                                                                if (v1340 == 2) then
                                                                    for v1421, v1422 in pairs(v62.flags) do
                                                                        for v1423, v1424 in pairs(v62.items) do
                                                                            if ((v1421 ~= nil) and (v1421 ~= "") and (v1421 ~= 'Configs_Name') and (v1421 ~= 'Configs') and (v1424.flag ~= nil)) then
                                                                                if (v1424.flag == v1421) then
                                                                                    pcall(function()
                                                                                        v1424:Set(v1422);
                                                                                    end);
                                                                                end
                                                                            end
                                                                        end
                                                                    end
                                                                    break
                                                                end
                                                            end
                                                        end);
                                                    end
                                                end);
                                                v458.Delete = v458.sector:CreateButton('Delete', function()
                                                    for v1329, v1330 in pairs(listfiles(v458.configFolder)) do
                                                        v1183:Remove(tostring(v1330):gsub(v458.configFolder .. "\\", ""):gsub('.txt', ""));
                                                    end
                                                    if (not v1183:Get() or (v1183:Get() == "")) then
                                                        return
                                                    end
                                                    if not isfile(v458.configFolder .. "/" .. v1183:Get() .. '.txt') then
                                                        return
                                                    end
                                                    delfile(v458.configFolder .. "/" .. v1183:Get() .. '.txt');
                                                    for v1331, v1332 in pairs(listfiles(v458.configFolder)) do
                                                        if v1332:find('.txt') then
                                                            v1183:Add(tostring(v1332):gsub(v458.configFolder .. "\\", ""):gsub('.txt', ""));
                                                        end
                                                    end
                                                end);
                                            else
                                                local v1188 = 0;
                                                while true do
                                                    if (v1188 == 0) then
                                                        v458.sector = v333:CreateSector('Configs', v456 or 'left');
                                                        v458.sector:CreateLable('Your Executor Is Not Supported');
                                                        break
                                                    end
                                                end
                                            end
                                        end);
                                        return v458
                                    end
                                end
                            end
                        end
                    end;
                    table.insert(v256.Tabs, v333);
                    return v333
                end;
                return v256
            end;
            return v62
        end
        if ((2) == v61) then
            v66 = game:GetService('HttpService');
            v62.theme = {
                BackGround = Color3.fromRGB(30, 30, 30),
                BackGround2 = Color3.fromRGB(38, 38, 38),
                Border = Color3.fromRGB(0, 0, 0),
                Toggle = Color3.fromRGB(62, 62, 62),
                Selected = Color3.fromRGB(85, 0, 255),
                Font = Enum.Font.Ubuntu,
                TextSize = 14,
                TextColor = Color3.fromRGB(255, 255, 255)
            };
            v61 = 3;
        end
    end
end
local v20 = false;
if (game.PlaceId == (286090429)) then
    v20 = true;
end
local v21 = library();
local v22 = v21:CreateWindow(v12.GUI.GUIToggleKey, 'XIT RBN BETA');
local v23 = v22:CreateToggleButton();
local v24 = v22:CreateTab('Aim Bot');
local v25 = v24:CreateSector('Main', 'Left');
v25:CreateToggle('Enable', v12.AimBot.Enabled, function(v67)
    v12.AimBot.Enabled = v67;
end);
v25:CreateToggle('Team Check', v12.AimBot.TeamCheck, function(v69)
    v12.AimBot.TeamCheck = v69;
end);
v25:CreateToggle('Wall Check', v12.AimBot.WallCheck, function(v71)
    v12.AimBot.WallCheck = v71;
end);
v25:CreateDropDown('Hit Scan', {
    'Head',
    'HumanoidRootPart'
}, v12.AimBot.AimPart, false, function(v73)
    v12.AimBot.AimPart = v73;
end);
local v26 = v24:CreateSector('FOV Circle', 'Left');
v26:CreateToggle('Show Fov', v12.AimBot.ShowFov, function(v75)
    v12.AimBot.ShowFov = v75;
end);
v26:CreateSlider('Circle Radius', 0, v12.AimBot.Fov, 1500, 1, function(v77)
    v12.AimBot.Fov = v77;
end);
local v27 = v24:CreateSector('Other', 'Right');
v27:CreateToggle('Prediction', v12.AimBot.Prediction, function(v79)
    v12.AimBot.Prediction = v79;
end);
v27:CreateSlider('Prediction Ammount', 100, v12.AimBot.PredictionAmmount * (100), 1000, 1, function(v81)
    v12.AimBot.PredictionAmmount = v81 / 100 ;
end);
v27:CreateToggle('Sticky Aim', v12.AimBot.StickyAim, function(v83)
    v12.AimBot.StickyAim = v83;
end);
v27:CreateSlider('Smoothing', 3, v12.AimBot.Smoothing * 100, 50, 1, function(v85)
    v12.AimBot.Smoothing = v85 / 100 ;
end);
v27:CreateKeyBind('Key Bind', v12.AimBot.Keybind, function(v87)
    v12.AimBot.Keybind = v87;
end);
v27:CreateToggle('Use Mouse', v12.AimBot.UseMouse, function(v89)
    v12.AimBot.UseMouse = v89;
end);
v27:CreateDropDown('Mouse Bind', {
    'MouseButton1',
    'MouseButton2'
}, v12.AimBot.MouseBind, false, function(v91)
    v12.AimBot.MouseBind = v91;
end);
local v28 = v22:CreateTab('ESP');
local v29 = v28:CreateSector('ESP', 'Left');
v29:CreateToggle('Enable', v12.esp.Enabled, function(v93)
    v12.esp.Enabled = v93;
end);
v29:CreateToggle('Team Check', v12.esp.Box.TeamCheck, function(v95)
    v12.esp.TeamCheck = v95;
end);
v29:CreateToggle('Box', v12.esp.Box.Box, function(v97)
    v12.esp.Box.Box = v97;
end);
v29:CreateToggle('Tracer', v12.esp.Tracer.Tracer, function(v99)
    v12.esp.Tracer.Tracer = v99;
end);
v29:CreateToggle('Health', v12.esp.Box.Health, function(v101)
    v12.esp.Box.Health = v101;
end);
v29:CreateToggle('Name', v12.esp.Box.Name, function(v103)
    v12.esp.Box.Name = v103;
end);
v29:CreateToggle('Distance', v12.esp.Box.Distance, function(v105)
    v12.esp.Box.Distance = v105;
end);
v29:CreateToggle('Health Bar', v12.esp.Box.HealthBar, function(v107)
    v12.esp.Box.HealthBar = v107;
end);
if not v20 then
    local v232 = 0;
    while true do
        if (v232 == (0)) then
            v29:CreateToggle('Hilights', v12.esp.Hilights.Hilights, function(v377)
                v12.esp.Hilights.Hilights = v377;
            end);
            v29:CreateToggle('Show Hilight Through Walls', v12.esp.Hilights.AllWaysVisible, function(v379)
                v12.esp.Hilights.AllWaysVisible = v379;
            end);
            break
        end
    end
end
local v30 = v28:CreateSector('Settings', 'Right');
v30:CreateSlider('Max Distance', 0, v12.esp.MaxDistance, 4E3, 1, function(v109)
    v12.esp.MaxDistance = v109;
end);
v30:CreateToggle('Outlines', v12.esp.Box.Outline, function(v111)
    local v112 = 0;
    while true do
        if (v112 == 0) then
            v12.esp.Box.Outline = v111;
            v12.esp.Tracer.Outline = v111;
            break
        end
    end
end);
v30:CreateColorPicker('Outline Color', v12.esp.Box.OutlineColor, function(v113)
    v12.esp.Box.OutlineColor = v113;
    v12.esp.Tracer.OutlineColor = v113;
end);
v30:CreateColorPicker('ESP Color', v12.esp.Box.Color, function(v116)
    local v117 = 0;
    local v118;
    while true do
        if ((0) == v117) then
            v118 = 0;
            while true do
                if (v118 == 0) then
                    v12.esp.Box.Color = v116;
                    v12.esp.Tracer.Color = v116;
                    break
                end
            end
            break
        end
    end
end);
if not v20 then
    local v233 = 0;
    while true do
        if ((1) == v233) then
            v30:CreateSlider('Hilight Outline', 0, v12.esp.Hilights.OutlineTransparency * (100), 100, 1, function(v381)
                v12.esp.Hilights.OutlineTransparency = v381 / 100 ;
            end);
            v30:CreateSlider('Hilight Fill', 0, v12.esp.Hilights.FillTransparency * 100, 100, 1, function(v383)
                v12.esp.Hilights.FillTransparency = v383 / 100 ;
            end);
            break
        end
        if ((0) == v233) then
            v30:CreateColorPicker('Hilight Outline', v12.esp.Hilights.OutlineColor, function(v385)
                v12.esp.Hilights.OutlineColor = v385;
            end);
            v30:CreateColorPicker('Hilight Fill', v12.esp.Hilights.FillColor, function(v387)
                v12.esp.Hilights.FillColor = v387;
            end);
            v233 = 1;
        end
    end
end
local v31 = v22:CreateTab('Settings');
local v32 = v31:CreateSector('Info', 'Left');
v32:CreateCoppyText('XIT RBN BETA');
v32:CreateCoppyText('VERSAO BETA');
v31:CreateConfig('Right');
local v33 = v31:CreateSector('GUI Settigns', 'Left');
v33:CreateToggle('UI Toggle Button', v12.GUI.GUIButton, function(v119)
    v12.GUI.GUIButton = v119;
    v23:Update(v119);
end);
v33:CreateKeyBind('UI Key Bind', v12.GUI.GUIToggleKey, function(v121)
    local v122 = 0;
    local v123;
    while true do
        if (v122 == (0)) then
            v123 = 0;
            while true do
                if (v123 == 0) then
                    v12.GUI.GUIToggleKey = v121;
                    v22:UpdateKeyBind(v121);
                    break
                end
            end
            break
        end
    end
end);
local v34 = Instance.new('Folder', v19 or v14.PlayerGui);
local v35 = Instance.new('ScreenGui', v19 or v14.PlayerGui);
v35.Name = 'Fov';
v35.ZIndexBehavior = Enum.ZIndexBehavior.Sibling;
v35.ResetOnSpawn = false;
local v40 = Instance.new('Frame');
v40.Parent = v35;
v40.Name = 'FOVFFrame';
v40.BackgroundColor3 = Color3.fromRGB(255, 255, 255);
v40.BorderColor3 = Color3.fromRGB(0, 0, 0);
v40.BorderSizePixel = 0;
v40.BackgroundTransparency = 1;
v40.AnchorPoint = Vector2.new(0.5, 0.5);
v40.Position = UDim2.new(0.5, 0, 0.5, 0);
v40.Size = UDim2.new(0, v12.AimBot.Fov, 0, v12.AimBot.Fov);
v40.BackgroundTransparency = 1;
local v50 = Instance.new('UICorner');
v50.CornerRadius = UDim.new(1, 0);
v50.Parent = v40;
local v53 = Instance.new('UIStroke');
v53.Color = Color3.fromRGB(100, 0, 100);
v53.Parent = v40;
v53.Thickness = 1;
v53.ApplyStrokeMode = 'Border';
game:GetService('StarterGui'):SetCore('SendNotification', {
    Title = 'https://discord.gg/7wFXQRMYHc',
    Text = 'The Discord For More!'
});
local function v58(v124)
    if (v124 and v124.Character and (v124.Character:FindFirstChild('HumanoidRootPart') ~= nil) and (v124.Character:FindFirstChild('Humanoid') ~= nil) and ((v20 and (v13[v124.Character.Name].NRPBS.Health.Value > 0)) or (not v20 and (v124.Character.Humanoid.Health > (0))))) then
        return true
    end
    return false
end
local function v59(v125)
    if not game.Players.LocalPlayer.Neutral then
        return game.Teams[v125.Team.Name]
    end
    return true
end
function isVisible(v126, ...)
    if not (v12.AimBot.WallCheck == true) then
        return true
    end
    return # v15:GetPartsObscuringTarget({
        v126
    }, {
        v15,
        v14.Character,
        ...
    }) == (0)
end
function CameraGetClosestToMouse()
    local v127 = 0;
    local v128;
    local v129;
    while true do
        local v234 = 0;
        while true do
            if (v234 == (0)) then
                if (v127 == (1)) then
                    for v852, v853 in pairs(game:GetService('Players'):GetPlayers()) do
                        if (v853 ~= v14) then
                            if ((v12.AimBot.TeamCheck ~= true) or (v59(v853) ~= v59(v14))) then
                                if v58(v853) then
                                    local v1157 = 0;
                                    local v1158;
                                    local v1159;
                                    local v1160;
                                    local v1161;
                                    local v1162;
                                    while true do
                                        if (v1157 == (0)) then
                                            v1158 = 0;
                                            v1159 = nil;
                                            v1157 = 1;
                                        end
                                        if (v1157 == (2)) then
                                            v1162 = nil;
                                            while true do
                                                if (v1158 == (1)) then
                                                    v1162 = (v1161 - v18(v17)).Magnitude;
                                                    if (v1160 and (v1162 < v128) and isVisible(v853.Character[v12.AimBot.AimPart].Position, v853.Character.Head.Parent)) then
                                                        v128 = v1162;
                                                        v129 = v853;
                                                    end
                                                    break
                                                end
                                                if (v1158 == (0)) then
                                                    local v1344 = 0;
                                                    while true do
                                                        if (v1344 == (0)) then
                                                            v1159, v1160 = v15:WorldToViewportPoint(v853.Character[v12.AimBot.AimPart].Position);
                                                            v1161 = Vector2.new(v1159.X, v1159.Y);
                                                            v1344 = 1;
                                                        end
                                                        if (v1344 == (1)) then
                                                            v1158 = 1;
                                                            break
                                                        end
                                                    end
                                                end
                                            end
                                            break
                                        end
                                        if (v1157 == 1) then
                                            v1160 = nil;
                                            v1161 = nil;
                                            v1157 = 2;
                                        end
                                    end
                                end
                            end
                        end
                    end
                    return v129
                end
                if (v127 == 0) then
                    v128 = v12.AimBot.Fov;
                    v129 = nil;
                    v127 = 1;
                end
                break
            end
        end
    end
end
local function v60(v130)
    local v131 = Instance.new('Folder', v34);
    v131.Name = v130.Name .. 'ESP' ;
    local v133 = Instance.new('ScreenGui', v131);
    v133.Name = 'Box';
    v133.DisplayOrder = 2;
    local v136 = Instance.new('ScreenGui', v131);
    v136.Name = 'Tracer';
    local v138 = Instance.new('Folder', v131);
    v138.Name = 'Hilight';
    local v140 = Instance.new('Frame', v133);
    v140.BackgroundColor3 = v12.esp.Box.OutlineColor;
    v140.Visible = false;
    v140.BorderSizePixel = 1;
    local v145 = Instance.new('Frame', v133);
    v145.BackgroundColor3 = v12.esp.Box.OutlineColor;
    v145.Visible = false;
    v145.BorderSizePixel = 1;
    local v149 = Instance.new('Frame', v133);
    v149.BackgroundColor3 = v12.esp.Box.OutlineColor;
    v149.Visible = false;
    v149.BorderSizePixel = 1;
    local v153 = Instance.new('Frame', v133);
    v153.BackgroundColor3 = v12.esp.Box.OutlineColor;
    v153.Visible = false;
    v153.BorderSizePixel = 1;
    local v157 = Instance.new('Frame', v133);
    v157.BackgroundColor3 = v12.esp.Box.Color;
    v157.Visible = false;
    v157.BorderSizePixel = 0;
    local v162 = Instance.new('Frame', v133);
    v162.BackgroundColor3 = v12.esp.Box.Color;
    v162.Visible = false;
    v162.BorderSizePixel = 0;
    local v166 = Instance.new('Frame', v133);
    v166.BackgroundColor3 = v12.esp.Box.Color;
    v166.Visible = false;
    v166.BorderSizePixel = 0;
    local v170 = Instance.new('Frame', v133);
    v170.BackgroundColor3 = v12.esp.Box.Color;
    v170.Visible = false;
    v170.BorderSizePixel = 0;
    local v174 = Instance.new('TextLabel', v133);
    v174.BackgroundTransparency = 1;
    v174.Text = v130.Name;
    v174.Visible = false;
    v174.AnchorPoint = Vector2.new(0.5, 0.5);
    v174.TextSize = 12;
    v174.Font = 2;
    v174.TextColor3 = Color3.fromRGB(255, 255, 255);
    v174.TextStrokeTransparency = 0;
    local v184 = Instance.new('TextLabel', v133);
    v184.BackgroundTransparency = 1;
    if v58(v130) then
        v184.Text = math.floor(0.5 + (v15.CFrame.Position - v130.Character.HumanoidRootPart.Position).magnitude);
    end
    v184.Visible = false;
    v184.AnchorPoint = Vector2.new(0.5, 0.5);
    v184.TextSize = 12;
    v184.Font = 2;
    v184.TextColor3 = Color3.fromRGB(255, 255, 255);
    v184.TextStrokeTransparency = 0;
    local v192 = Instance.new('Frame', v133);
    v192.Visible = false;
    v192.BorderSizePixel = 1;
    v192.BorderColor3 = v12.esp.Box.OutlineColor;
    local v196 = Instance.new('Frame', v133);
    v196.Visible = false;
    v196.BorderSizePixel = 0;
    v196.BackgroundColor3 = Color3.fromRGB(0, 255, 0);
    local v200 = Instance.new('TextLabel', v133);
    v200.BackgroundTransparency = 1;
    if v58(v130) then
        v200.Text = (v20 and v13[v130.Character.Name].NRPBS.Health.Value) or v130.Character.Humanoid.Health ;
    end
    v200.Visible = false;
    v200.AnchorPoint = Vector2.new(0.5, 0.5);
    v200.TextSize = 12;
    v200.Font = 2;
    v200.TextColor3 = Color3.fromRGB(255, 255, 255);
    v200.TextStrokeTransparency = 0;
    local v208 = Instance.new('Frame', v136);
    v208.BackgroundColor3 = v12.esp.Tracer.OutlineColor;
    v208.Visible = false;
    v208.BorderSizePixel = 1;
    v208.AnchorPoint = Vector2.new(0.5, 0.5);
    local v214 = Instance.new('Frame', v136);
    v214.BackgroundColor3 = v12.esp.Tracer.Color;
    v214.Visible = false;
    v214.BorderSizePixel = 0;
    v214.AnchorPoint = Vector2.new(0.5, 0.5);
    local v220 = Instance.new('Highlight', v138);
    v220.Enabled = false;
    local v222 = coroutine.create(function()
        local v235 = 0;
        while true do
            if (v235 == (0)) then
                game:GetService('RunService').RenderStepped:Connect(function()
                    if (v58(v130) and (v12.esp.Box.Box or v12.esp.Box.HealthBar or v12.esp.Box.Name or v12.esp.Box.Health or v12.esp.Tracer.Tracer or v12.esp.Hilights.Hilights)) then
                        local v854 = 0;
                        local v855;
                        local v856;
                        local v857;
                        local v858;
                        local v859;
                        while true do
                            if (v854 == (1)) then
                                v858 = (v15.ViewportSize.Y / v857) * v12.esp.CharacterSize ;
                                v859 = Vector2.new(v855.X, v855.Y) - ((v858 / (2)) - (Vector2.new(0, v858.Y) / 20)) ;
                                v854 = 2;
                            end
                            if (v854 == (0)) then
                                v855, v856 = v15:WorldToScreenPoint(v130.Character.HumanoidRootPart.Position);
                                v857 = math.tan(math.rad(v15.FieldOfView * (0.5))) * (2) * v855.Z ;
                                v854 = 1;
                            end
                            if (v854 == 2) then
                                if (v856 and ((v12.esp.TeamCheck ~= true) or (v59(v130) ~= v59(v14))) and v12.esp.Enabled) then
                                    local v1100 = math.floor(0.5 + (v15.CFrame.Position - v130.Character.HumanoidRootPart.Position).magnitude);
                                    if (v12.esp.MaxDistance > v1100) then
                                        if v12.esp.Box.Box then
                                            v140.Visible = v12.esp.Box.Box and v12.esp.Box.Outline ;
                                            v145.Visible = v12.esp.Box.Box and v12.esp.Box.Outline ;
                                            v149.Visible = v12.esp.Box.Box and v12.esp.Box.Outline ;
                                            v153.Visible = v12.esp.Box.Box and v12.esp.Box.Outline ;
                                            v157.Position = UDim2.fromOffset(v859.X, v859.Y);
                                            v162.Position = UDim2.fromOffset(v859.X, (v859.Y + v858.Y) - (1));
                                            v166.Position = UDim2.fromOffset(v859.X, v859.Y);
                                            v170.Position = UDim2.fromOffset((v859.X + v858.X) - (1), v859.Y);
                                            v140.Position = v157.Position;
                                            v145.Position = v162.Position;
                                            v149.Position = v166.Position;
                                            v153.Position = v170.Position;
                                            v157.Visible = v12.esp.Box.Box;
                                            v162.Visible = v12.esp.Box.Box;
                                            v166.Visible = v12.esp.Box.Box;
                                            v170.Visible = v12.esp.Box.Box;
                                            v157.Size = UDim2.fromOffset(v858.X, 1);
                                            v162.Size = UDim2.fromOffset(v858.X, 1);
                                            v166.Size = UDim2.fromOffset(1, v858.Y);
                                            v170.Size = UDim2.fromOffset(1, v858.Y);
                                            v140.Size = v157.Size;
                                            v145.Size = v162.Size;
                                            v149.Size = v166.Size;
                                            v153.Size = v170.Size;
                                            v140.BorderColor3 = v12.esp.Box.OutlineColor;
                                            v145.BorderColor3 = v12.esp.Box.OutlineColor;
                                            v149.BorderColor3 = v12.esp.Box.OutlineColor;
                                            v153.BorderColor3 = v12.esp.Box.OutlineColor;
                                            v157.BackgroundColor3 = v12.esp.Box.Color;
                                            v162.BackgroundColor3 = v12.esp.Box.Color;
                                            v166.BackgroundColor3 = v12.esp.Box.Color;
                                            v170.BackgroundColor3 = v12.esp.Box.Color;
                                            v140.BackgroundColor3 = v12.esp.Box.Color;
                                            v145.BackgroundColor3 = v12.esp.Box.Color;
                                            v149.BackgroundColor3 = v12.esp.Box.Color;
                                            v153.BackgroundColor3 = v12.esp.Box.Color;
                                        else
                                            v140.Visible = false;
                                            v145.Visible = false;
                                            v149.Visible = false;
                                            v153.Visible = false;
                                            v157.Visible = false;
                                            v162.Visible = false;
                                            v166.Visible = false;
                                            v170.Visible = false;
                                        end
                                        if v12.esp.Box.HealthBar then
                                            local v1287 = 0;
                                            local v1288;
                                            local v1289;
                                            local v1290;
                                            while true do
                                                if (v1287 == (2)) then
                                                    local v1345 = 0;
                                                    while true do
                                                        if (v1345 == (0)) then
                                                            v196.Size = UDim2.fromOffset(2, - v1290);
                                                            v192.Position = UDim2.fromOffset(v859.X - (8), v859.Y);
                                                            v1345 = 1;
                                                        end
                                                        if (v1345 == (1)) then
                                                            v196.Position = UDim2.fromOffset(v859.x - (7), v859.y + v858.Y);
                                                            v1287 = 3;
                                                            break
                                                        end
                                                    end
                                                end
                                                if (v1287 == (3)) then
                                                    v192.BackgroundColor3 = v12.esp.Box.OutlineColor;
                                                    v192.BorderColor3 = v12.esp.Box.OutlineColor;
                                                    break
                                                end
                                                if (v1287 == 1) then
                                                    v192.Visible = v12.esp.Box.HealthBar;
                                                    v196.Visible = v12.esp.Box.HealthBar;
                                                    v192.Size = UDim2.fromOffset(4, v858.Y);
                                                    v1287 = 2;
                                                end
                                                if (v1287 == (0)) then
                                                    local v1353 = 0;
                                                    while true do
                                                        if (v1353 == (0)) then
                                                            v1288 = (v20 and v13[v130.Character.Name].NRPBS.Health.Value) or v130.Character.Humanoid.Health ;
                                                            v1289 = (v20 and (v1288 / v13[v130.Character.Name].NRPBS.MaxHealth.Value)) or (v1288 / v130.Character.Humanoid.MaxHealth) ;
                                                            v1353 = 1;
                                                        end
                                                        if ((1) == v1353) then
                                                            v1290 = v858.Y * v1289 ;
                                                            v1287 = 1;
                                                            break
                                                        end
                                                    end
                                                end
                                            end
                                        else
                                            local v1291 = 0;
                                            while true do
                                                if (v1291 == (0)) then
                                                    v192.Visible = false;
                                                    v196.Visible = false;
                                                    break
                                                end
                                            end
                                        end
                                        if v12.esp.Box.Health then
                                            local v1292 = 0;
                                            local v1293;
                                            local v1294;
                                            local v1295;
                                            while true do
                                                if (v1292 == 1) then
                                                    v1295 = v858.Y * v1294 ;
                                                    v200.Visible = v12.esp.Box.Health;
                                                    v1292 = 2;
                                                end
                                                if (v1292 == 0) then
                                                    v1293 = (v20 and v13[v130.Character.Name].NRPBS.Health.Value) or v130.Character.Humanoid.Health ;
                                                    v1294 = (v20 and (v1293 / v13[v130.Character.Name].NRPBS.MaxHealth.Value)) or (v1293 / v130.Character.Humanoid.MaxHealth) ;
                                                    v1292 = 1;
                                                end
                                                if (v1292 == (2)) then
                                                    v200.Position = (v12.esp.Box.HealthBar and UDim2.fromOffset(v859.X - (25), v859.y + v858.Y + - v1295)) or UDim2.fromOffset(v859.X - 25, v859.Y + v858.Y) ;
                                                    v200.Text = (v20 and math.floor(v13[v130.Character.Name].NRPBS.Health.Value)) or math.floor(v130.Character.Humanoid.Health) ;
                                                    break
                                                end
                                            end
                                        else
                                            v200.Visible = false;
                                        end
                                        if (v12.esp.Box.Distance or v12.esp.Box.Name) then
                                            local v1297 = 0;
                                            while true do
                                                if (v1297 == (0)) then
                                                    v174.Visible = v12.esp.Box.Name;
                                                    v184.Visible = v12.esp.Box.Distance and not v12.esp.Box.Name ;
                                                    v1297 = 1;
                                                end
                                                if (v1297 == (2)) then
                                                    v184.Text = math.floor(0.5 + (v15.CFrame.Position - v130.Character.HumanoidRootPart.Position).magnitude);
                                                    v174.Text = (v12.esp.Box.Name and v12.esp.Box.Distance and (v130.Name .. ' [' .. math.floor((0.5) + ((v15.CFrame.Position - v130.Character.HumanoidRootPart.Position).magnitude / 3.5714285714)) .. "]")) or v130.Name ;
                                                    break
                                                end
                                                if (v1297 == 1) then
                                                    v174.Position = UDim2.fromOffset(v855.X, v855.Y - ((v858.Y + v174.TextBounds.Y + 14) / 2));
                                                    v184.Position = UDim2.fromOffset(v855.X, v855.Y - ((v858.Y + v174.TextBounds.Y + 14 + 0) / (2)));
                                                    v1297 = 2;
                                                end
                                            end
                                        else
                                            local v1298 = 0;
                                            while true do
                                                if ((0) == v1298) then
                                                    v174.Visible = false;
                                                    v184.Visible = false;
                                                    break
                                                end
                                            end
                                        end
                                        if v12.esp.Tracer.Tracer then
                                            local v1299 = Vector2.new(v855.X, v855.Y + (v858.Y / (2)) + (v858.Y / 20));
                                            local v1300 = Vector2.new(v15.ViewportSize.X / 2, v15.ViewportSize.Y - 1);
                                            local v1301 = (v1300 + v1299) / 2 ;
                                            v208.Visible = v12.esp.Tracer.Outline and v12.esp.Tracer.Tracer ;
                                            v214.Visible = v12.esp.Tracer.Tracer;
                                            v214.Rotation = math.deg(math.atan2(v1299.Y - v1300.Y, v1299.X - v1300.X));
                                            v214.Position = UDim2.new(0, v1301.X, 0, v1301.Y);
                                            v214.Size = UDim2.fromOffset((v1300 - v1299).Magnitude, 1);
                                            v208.Rotation = v214.Rotation;
                                            v208.Position = v214.Position;
                                            v208.Size = v214.Size;
                                            v208.BorderColor3 = v12.esp.Tracer.OutlineColor;
                                            v214.BackgroundColor3 = v12.esp.Tracer.Color;
                                        else
                                            v208.Visible = false;
                                            v214.Visible = false;
                                        end
                                        if v12.esp.Hilights.Hilights then
                                            local v1317 = 0;
                                            while true do
                                                if (v1317 == (2)) then
                                                    v220.FillTransparency = v12.esp.Hilights.FillTransparency;
                                                    v220.OutlineTransparency = v12.esp.Hilights.OutlineTransparency;
                                                    v1317 = 3;
                                                end
                                                if ((1) == v1317) then
                                                    v220.OutlineColor = v12.esp.Hilights.OutlineColor;
                                                    v220.FillColor = v12.esp.Hilights.FillColor;
                                                    v1317 = 2;
                                                end
                                                if (v1317 == 3) then
                                                    v220.DepthMode = (v12.esp.Hilights.AllWaysVisible and 'AlwaysOnTop') or (not v12.esp.Hilights.AllWaysVisible and 'Occluded') ;
                                                    break
                                                end
                                                if (v1317 == (0)) then
                                                    v220.Enabled = v12.esp.Hilights.Hilights;
                                                    if not v20 then
                                                        v220.Adornee = v130.Character;
                                                    end
                                                    v1317 = 1;
                                                end
                                            end
                                        else
                                            local v1318 = 0;
                                            local v1319;
                                            while true do
                                                if (v1318 == (0)) then
                                                    v1319 = 0;
                                                    while true do
                                                        if (v1319 == (0)) then
                                                            v220.Enabled = false;
                                                            v220.Adornee = nil;
                                                            break
                                                        end
                                                    end
                                                    break
                                                end
                                            end
                                        end
                                    else
                                        local v1171 = 0;
                                        local v1172;
                                        while true do
                                            if (v1171 == (0)) then
                                                v1172 = 0;
                                                while true do
                                                    if (v1172 == (3)) then
                                                        v192.Visible = false;
                                                        v196.Visible = false;
                                                        v200.Visible = false;
                                                        v220.Enabled = false;
                                                        v1172 = 4;
                                                    end
                                                    if (v1172 == 0) then
                                                        v140.Visible = false;
                                                        v145.Visible = false;
                                                        v149.Visible = false;
                                                        v153.Visible = false;
                                                        v1172 = 1;
                                                    end
                                                    if (v1172 == (4)) then
                                                        v220.Adornee = nil;
                                                        break
                                                    end
                                                    if ((2) == v1172) then
                                                        v208.Visible = false;
                                                        v214.Visible = false;
                                                        v174.Visible = false;
                                                        v184.Visible = false;
                                                        v1172 = 3;
                                                    end
                                                    if (v1172 == 1) then
                                                        v157.Visible = false;
                                                        v162.Visible = false;
                                                        v166.Visible = false;
                                                        v170.Visible = false;
                                                        v1172 = 2;
                                                    end
                                                end
                                                break
                                            end
                                        end
                                    end
                                else
                                    local v1101 = 0;
                                    while true do
                                        if (v1101 == (2)) then
                                            v208.Visible = false;
                                            v214.Visible = false;
                                            v174.Visible = false;
                                            v184.Visible = false;
                                            v1101 = 3;
                                        end
                                        if (v1101 == (3)) then
                                            v192.Visible = false;
                                            v196.Visible = false;
                                            v200.Visible = false;
                                            v220.Enabled = false;
                                            v1101 = 4;
                                        end
                                        if (v1101 == (1)) then
                                            v157.Visible = false;
                                            v162.Visible = false;
                                            v166.Visible = false;
                                            v170.Visible = false;
                                            v1101 = 2;
                                        end
                                        if (v1101 == (0)) then
                                            v140.Visible = false;
                                            v145.Visible = false;
                                            v149.Visible = false;
                                            v153.Visible = false;
                                            v1101 = 1;
                                        end
                                        if (v1101 == 4) then
                                            v220.Adornee = nil;
                                            break
                                        end
                                    end
                                end
                                break
                            end
                        end
                    else
                        v140.Visible = false;
                        v145.Visible = false;
                        v149.Visible = false;
                        v153.Visible = false;
                        v157.Visible = false;
                        v162.Visible = false;
                        v166.Visible = false;
                        v170.Visible = false;
                        v208.Visible = false;
                        v214.Visible = false;
                        v174.Visible = false;
                        v184.Visible = false;
                        v192.Visible = false;
                        v196.Visible = false;
                        v200.Visible = false;
                        v220.Enabled = false;
                        v220.Adornee = nil;
                    end
                end);
                if not v13:FindFirstChild(v130.Name) then
                    v131:Destroy();
                    coroutine.yield();
                end
                break
            end
        end
    end);
    coroutine.resume(v222);
end
for v223, v224 in pairs(v13:GetChildren()) do
    if (v224 ~= v14) then
        v60(v224);
    end
end
v13.PlayerAdded:Connect(function(v225)
    if (v225 ~= v14) then
        v60(v225);
    end
end);
v17.InputBegan:Connect(function(v226)
    if ((v226.KeyCode == v12.AimBot.Keybind) and not v12.AimBot.UseMouse) then
        local v238 = 0;
        while true do
            if (v238 == (0)) then
                v12.AimBot.Target = CameraGetClosestToMouse();
                v12.AimBot.IsAimKeyDown = true;
                break
            end
        end
    end
end);
v17.InputEnded:Connect(function(v227)
    if ((v227.KeyCode == v12.AimBot.Keybind) and not v12.AimBot.UseMouse) then
        local v239 = 0;
        while true do
            if (v239 == (0)) then
                v12.AimBot.Target = CameraGetClosestToMouse();
                v12.AimBot.IsAimKeyDown = false;
                v239 = 1;
            end
            if (v239 == (1)) then
                if (v12.AimBot.CameraTween ~= nil) then
                    v12.AimBot.CameraTween:Cancel();
                end
                break
            end
        end
    end
end);
v14:GetMouse().Button1Down:Connect(function(v228)
    if ((v12.AimBot.MouseBind == 'MouseButton1') and v12.AimBot.UseMouse) then
        if v12.AimBot.IsAimKeyDown then
            v12.AimBot.Target = CameraGetClosestToMouse();
            v12.AimBot.IsAimKeyDown = false;
            if (v12.AimBot.CameraTween ~= nil) then
                v12.AimBot.CameraTween:Cancel();
            end
        else
            local v320 = 0;
            while true do
                if (v320 == (0)) then
                    v12.AimBot.Target = CameraGetClosestToMouse();
                    v12.AimBot.IsAimKeyDown = true;
                    break
                end
            end
        end
    end
end);
v14:GetMouse().Button1Up:Connect(function(v229)
    if ((v12.AimBot.MouseBind == 'MouseButton1') and v12.AimBot.UseMouse) then
        local v240 = 0;
        while true do
            if (v240 == 0) then
                v12.AimBot.Target = CameraGetClosestToMouse();
                v12.AimBot.IsAimKeyDown = false;
                v240 = 1;
            end
            if (v240 == 1) then
                if (v12.AimBot.CameraTween ~= nil) then
                    v12.AimBot.CameraTween:Cancel();
                end
                break
            end
        end
    end
end);
v14:GetMouse().Button2Down:Connect(function(v230)
    if ((v12.AimBot.MouseBind == 'MouseButton2') and v12.AimBot.UseMouse) then
        v12.AimBot.Target = CameraGetClosestToMouse();
        v12.AimBot.IsAimKeyDown = true;
    end
end);
v14:GetMouse().Button2Up:Connect(function(v231)
    if ((v12.AimBot.MouseBind == 'MouseButton2') and v12.AimBot.UseMouse) then
        local v243 = 0;
        local v244;
        while true do
            if (v243 == (0)) then
                v244 = 0;
                while true do
                    if (v244 == (0)) then
                        v12.AimBot.Target = CameraGetClosestToMouse();
                        v12.AimBot.IsAimKeyDown = false;
                        v244 = 1;
                    end
                    if (v244 == (1)) then
                        if (v12.AimBot.CameraTween ~= nil) then
                            v12.AimBot.CameraTween:Cancel();
                        end
                        break
                    end
                end
                break
            end
        end
    end
end);
game:GetService('RunService').Heartbeat:Connect(function()
    if (v12.AimBot.Enabled and v12.AimBot.ShowFov) then
        local v245 = 0;
        local v246;
        while true do
            if ((2) == v245) then
                v40.Size = UDim2.fromOffset(v12.AimBot.Fov * (1.5), v12.AimBot.Fov * (1.5));
                break
            end
            if (v245 == (0)) then
                v53.Enabled = true;
                v53.Color = v12.AimBot.FovColor;
                v245 = 1;
            end
            if (v245 == 1) then
                v246 = v17:GetMouseLocation();
                v40.Position = UDim2.new(0, v246.X, 0, v246.Y - (36));
                v245 = 2;
            end
        end
    else
        v53.Enabled = false;
    end
    if v12.AimBot.Enabled then
        if v12.AimBot.IsAimKeyDown then
            if v12.AimBot.StickyAim then
                if (v12.AimBot.Target ~= nil) then
                    if not v58(v12.AimBot.Target) then
                        local v1074 = 0;
                        local v1075;
                        while true do
                            if (v1074 == (0)) then
                                v1075 = CameraGetClosestToMouse();
                                v12.AimBot.Target = v1075;
                                v1074 = 1;
                            end
                            if (v1074 == 1) then
                                v12.AimBot.CameraTween = v16:Create(v15, TweenInfo.new(v12.AimBot.Smoothing, Enum.EasingStyle.Sine, Enum.EasingDirection.Out), {
                                    CFrame = CFrame.new(v15.CFrame.Position, v1075.Character[v12.AimBot.AimPart].Position + ((v12.AimBot.Prediction and (v12.AimBot.target.Character[v12.AimBot.AimPart].Velocity * v14:GetNetworkPing() * v12.AimBot.PredictionAmmount)) or Vector3.new()))
                                });
                                v12.AimBot.CameraTween:Play();
                                break
                            end
                        end
                    end
                    v12.AimBot.CameraTween = v16:Create(v15, TweenInfo.new(v12.AimBot.Smoothing, Enum.EasingStyle.Sine, Enum.EasingDirection.Out), {
                        CFrame = CFrame.new(v15.CFrame.Position, v12.AimBot.Target.Character[v12.AimBot.AimPart].Position + ((v12.AimBot.Prediction and (v12.AimBot.Target.Character[v12.AimBot.AimPart].Velocity * v14:GetNetworkPing() * v12.AimBot.PredictionAmmount)) or Vector3.new()))
                    });
                    v12.AimBot.CameraTween:Play();
                end
            else
                local v463 = 0;
                local v464;
                while true do
                    if (v463 == 0) then
                        v464 = CameraGetClosestToMouse();
                        if (v464 ~= nil) then
                            v12.AimBot.CameraTween = v16:Create(v15, TweenInfo.new(v12.AimBot.Smoothing, Enum.EasingStyle.Sine, Enum.EasingDirection.Out), {
                                CFrame = CFrame.new(v15.CFrame.Position, v464.Character[v12.AimBot.AimPart].Position + ((v12.AimBot.Prediction and (v464.Character[v12.AimBot.AimPart].Velocity * v14:GetNetworkPing() * v12.AimBot.PredictionAmmount)) or Vector3.new()))
                            });
                            v12.AimBot.CameraTween:Play();
                        elseif (v12.AimBot.CameraTween ~= nil) then
                            v12.AimBot.CameraTween:Cancel();
                        end
                        break
                    end
                end
            end
        end
    end
end);
game.StarterGui:SetCore('SendNotification', {
    Title = 'XIT RBN BETA ',
    Text = 'XIT RBN BETA, ' .. game.Players.LocalPlayer.DisplayName .. ".",
    Duration = 4
});
