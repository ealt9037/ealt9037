------------------------------------ FIX VIEWMODELS ------------------------------------
for i,v in pairs(game.ReplicatedStorage.Viewmodels:GetChildren()) do
    if v:FindFirstChild("HumanoidRootPart") and v.HumanoidRootPart.Transparency ~= 1 then
        v.HumanoidRootPart.Transparency = 1
    end
end
----------------------------------------------------------------------------------------
if game.CoreGui:FindFirstChild("Internal") then
    game.CoreGui["Internal"]:Destroy()
end
local cbClient = getsenv(game.Players.LocalPlayer.PlayerGui.Client)
local a = game:GetService("UserInputService")
local b = game:GetService("TweenService")
local c = game:GetService("HttpService")
local d = game:GetService("RunService")
local e = game:GetService("Players")
local f = game:GetService("Debris")
local g = e.LocalPlayer
local h = getsenv(g.PlayerGui.Client)
local i = workspace.CurrentCamera
local j = g:GetMouse()
local k = {}
local l = {Scrolling = false, options = {}}

function l:CreateUI()
    if not isfolder("pepsi") then
        makefolder("pepsi")
    end
    local m = Instance.new("ScreenGui")
    m.Name = "Internal.move"
    local n = Instance.new("ImageLabel")
    n.Name = "main"
    n.Size = UDim2.new(0, 320, 0, 365)
    n.Position = UDim2.new(0.5, -160, 0.5, -154)
    n.BackgroundColor3 = Color3.fromRGB(49, 49, 49)
    n.BorderSizePixel = 0
    n.ZIndex = 0
    n.Parent = m
    n.Image = "rbxassetid://6073763717"
    n.ImageColor3 = Color3.fromRGB(49, 49, 49)
    local o = Instance.new("Frame")
    o.Name = "back"
    o.Size = UDim2.new(1, 10, 1, 10)
    o.Position = UDim2.new(0, -5, 0, -5)
    o.BackgroundTransparency = 0.6
    o.BackgroundColor3 = Color3.fromRGB(0, 0, 0)
    o.BorderSizePixel = 2
    o.BorderColor3 = Color3.fromRGB(54, 54, 54)
    o.ZIndex = 0
    o.Parent = n
    local p = Instance.new("TextButton")
    p.Name = "unlock"
    p.Size = UDim2.new(0, 0, 0, 0)
    p.Text = ""
    p.BackgroundTransparency = 1
    p.Modal = true
    p.Parent = n
    local q = Instance.new("Frame")
    q.Name = "sidebar"
    q.Size = UDim2.new(0, 80, 1, 0)
    q.BackgroundColor3 = Color3.fromRGB(17, 17, 17)
    q.BorderSizePixel = 0
    q.ZIndex = 3
    q.Parent = n
    local r = Instance.new("TextLabel")
    r.Name = "name"
    r.Text = "Internal"
    r.TextColor3 = Color3.new(1, 1, 1)
    r.Size = UDim2.new(1, 0, 0, 20)
    r.BackgroundColor3 = Color3.fromRGB(24, 24, 24)
    r.BorderSizePixel = 0
    r.ZIndex = 3
    r.Font = Enum.Font.Code
    r.TextSize = 13
    r.Parent = q
    local s = Instance.new("Frame")
    s.Name = "cheatbuttons"
    s.Size = UDim2.new(1, 0, 1, -25)
    s.Position = UDim2.new(0, 0, 0, 25)
    s.BackgroundTransparency = 1
    s.Parent = q
    local t = Instance.new("UIListLayout")
    t.SortOrder = "LayoutOrder"
    t.Name = "cheatsorter"
    t.Padding = UDim.new(0, 4)
    t.Parent = s
    local u = Instance.new("Frame")
    u.Name = "cheattabs"
    u.Size = UDim2.new(0.75, 0, 1, 0)
    u.Position = UDim2.new(0.25, 0, 0, 0)
    u.BackgroundTransparency = 1
    s.ZIndex = 3
    u.Parent = n
    local v = Instance.new("ImageLabel")
    v.Name = "cursor"
    v.BackgroundTransparency = 1
    v.Size = UDim2.new(0, 17, 0, 17)
    v.Image = "rbxassetid://7205257578"
    v.ZIndex = 101
    v.Parent = m
    a.InputBegan:connect(
        function(w)
            if w.KeyCode == Enum.KeyCode.RightShift then
                n.Visible = not n.Visible
            end
        end
    )
    spawn(
        function()
            d.RenderStepped:connect(
                function()
                    v.Visible = n.Visible
                    v.Position = UDim2.new(0, j.X, 0, j.Y)
                end
            )
        end
    )
    local x = {}
    function x:CreateTab(y)
        local z = Instance.new("TextButton")
        z.Name = y .. "Tab"
        z.Size = UDim2.new(1, 0, 0, 15)
        z.BackgroundTransparency = 1
        z.TextColor3 = Color3.new(1, 1, 1)
        z.Font = Enum.Font.Code
        z.TextSize = 13
        z.ZIndex = 3
        z.Text = y
        z.Parent = s
        z.MouseEnter:Connect(function()
            z.TextSize = 14 
            z.TextColor3 = Color3.fromRGB(255, 0, 0)
        end)
        z.MouseLeave:Connect(function()
            z.TextSize = 13
            z.TextColor3 = Color3.new(1, 1, 1)
        end)
        local A = Instance.new("Frame")
        A.Name = y .. "tab"
        A.Size = UDim2.new(0.95, 0, 0.975, 0)
        A.Position = UDim2.new(0.05, 0, 0.025, 0)
        A.BackgroundTransparency = 1
        A.Visible = false
        A.Parent = u
        z.MouseButton1Click:connect(
            function()
                for B, C in next, u:GetChildren() do
                    C.Visible = false
                end
                A.Visible = true
            end
        )
        local D = Instance.new("UIListLayout")
        D.SortOrder = "LayoutOrder"
        D.Padding = UDim.new(0, 5)
        D.Parent = A
        local E = {}
        function E:CreateToggle(y, F)
            local G = false
            k[y] = false
            local H = Instance.new("TextButton")
            H.Name = y .. "togglebutton"
            H.Size = UDim2.new(0, 0, 0, 12)
            H.BackgroundTransparency = 1
            H.Text = ""
            H.Parent = A
            local I = Instance.new("Frame")
            I.Size = UDim2.new(0, 12, 0, 12)
            I.BackgroundColor3 = Color3.fromRGB(17, 17, 17)
            I.BorderSizePixel = 1
            I.BorderColor3 = Color3.new()
            I.Parent = H
            I.MouseEnter:Connect(function()
                I.BorderColor3 = Color3.fromRGB(255, 0, 0)
            end)
            I.MouseLeave:Connect(function()
                I.BorderColor3 = Color3.new()
            end)
            local J = Instance.new("TextLabel")
            J.Text = y
            J.BackgroundTransparency = 1
            J.Font = Enum.Font.Code
            J.TextColor3 = Color3.new(1, 1, 1)
            J.TextSize = 12
            J.Position = UDim2.new(1, 10, 0, 0)
            J.Parent = I
            J.Size = UDim2.new(0, J.TextBounds.X, 1, 0)
            J.MouseEnter:Connect(function()
                I.BorderColor3 = Color3.fromRGB(255, 0, 0)  
            end)
            J.MouseLeave:Connect(function()
                I.BorderColor3 = Color3.new()
            end)
            H.Size = UDim2.new(0, 22 + J.TextBounds.X, 0, 12)
            local function K()
                G = not G
                F(G)
                I.BackgroundColor3 = G and Color3.fromRGB(255, 0, 0) or Color3.fromRGB(17, 17, 17)
            end
            H.MouseButton1Click:connect(K)
            local L = {toggleFunction = K, Name = y, Type = "Toggle"}
            l.options[y] = L
        end
        function E:CreateLabel(Text)
            local Label = Instance.new("TextLabel")
            Label.Name = "Label"
            Label.Parent = A
            Label.BackgroundColor3 = Color3.new(1, 1, 1)
            Label.BackgroundTransparency = 1
            Label.Position = UDim2.new(1.67999995, 0, -0.0149999997, 0)
            Label.Size = UDim2.new(0, 199, 0, 11)
            Label.ZIndex = 2
            Label.Font = Enum.Font.Code
            Label.Text = Text
            Label.TextColor3 = Color3.new(1, 1, 1)
            Label.TextSize = 12
            Label.TextStrokeTransparency = 0.40000000596046
            Label.TextXAlignment = Enum.TextXAlignment.Left
        end
        function E:CreateSlider(y, M, N)
            local O = false
            local P = false
            local Q = 0
            k[y] = 0
            local R = Instance.new("TextButton")
            R.Name = y
            R.Size = UDim2.new(0, 100, 0, 12)
            R.BackgroundColor3 = Color3.fromRGB(17, 17, 17)
            R.BorderColor3 = Color3.new()
            R.AutoButtonColor = false
            R.Text = ""
            R.Parent = A
            R.MouseEnter:Connect(function()
                R.BorderColor3 = Color3.fromRGB(255, 0, 0)  
            end)
            R.MouseLeave:Connect(function()
                R.BorderColor3 = Color3.new()
            end)
            local S = Instance.new("Frame")
            S.Name = "fill"
            S.Size = UDim2.new(0, 1, 1, 0)
            S.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
            S.BorderSizePixel = 0
            S.Parent = R
            local T = Instance.new("TextLabel")
            T.Text = y
            T.BackgroundTransparency = 1
            T.Font = Enum.Font.Code
            T.TextColor3 = Color3.new(1, 1, 1)
            T.TextSize = 12
            T.Position = UDim2.new(1, 10, 0, 0)
            T.Parent = R
            T.Size = UDim2.new(0, T.TextBounds.X, 1, 0)
            local U = Instance.new("TextLabel")
            U.Text = 0
            U.BackgroundTransparency = 1
            U.Font = Enum.Font.Code
            U.TextColor3 = Color3.new(0.7, 0.7, 0.7)
            U.TextSize = 13
            U.Position = UDim2.new(0.5, 0, 0.5, 0)
            U.Size = UDim2.new(0, 0, 0, 0)
            U.Visible = false
            U.Parent = R
            local function V(W)
                if W ~= 0 then
                    S:TweenSize(UDim2.new(W / M, 0, 0, 12), Enum.EasingDirection.In, Enum.EasingStyle.Sine, 0.05)
                else
                    S:TweenSize(UDim2.new(0, 1, 0, 12), Enum.EasingDirection.In, Enum.EasingStyle.Sine, 0.05)
                end
                U.Text = W
                N(W)
            end
            local function X()
                if P or l.scrolling then
                    return
                end
                while a:IsMouseButtonPressed(Enum.UserInputType.MouseButton1) do
                    d.RenderStepped:Wait()
                    l.scrolling = true
                    U.Visible = true
                    P = true
                    local W = j.X - R.AbsolutePosition.X
                    W = W / 100 * M
                    if W < 0 then
                        W = 0
                    end
                    if W > M then
                        W = M
                    end
                    V(math.floor(W))
                end
                if P and not O then
                    U.Visible = false
                end
                P = false
                l.scrolling = false
            end
            R.MouseEnter:connect(
                function()
                    if P or O then
                        return
                    end
                    O = true
                    U.Visible = true
                    while O do
                        wait()
                        X()
                    end
                end
            )
            R.MouseLeave:connect(
                function()
                    O = false
                    U.Visible = false
                end
            )
            local Y = {changeValue = V, Name = y, Type = "Slider"}
            l.options[y] = Y
        end
        function E:CreateDropdown(y, Z, _)
            local a0 = Z
            k[y] = ""
            local a1 = Instance.new("TextButton")
            a1.Name = y
            a1.Size = UDim2.new(0, 100, 0, 12)
            a1.BackgroundColor3 = Color3.fromRGB(17, 17, 17)
            a1.BorderColor3 = Color3.new()
            a1.AutoButtonColor = false
            a1.Text = "none"
            a1.Font = Enum.Font.Code
            a1.TextColor3 = Color3.new(1, 1, 1)
            a1.TextWrapped = true
            a1.TextSize = 11
            a1.ZIndex = 99
            a1.Parent = A
            a1.MouseEnter:Connect(function()
                a1.BorderColor3 = Color3.fromRGB(255, 0, 0)  
            end)
            a1.MouseLeave:Connect(function()
                a1.BorderColor3 = Color3.new()
            end)
            local a2 = Instance.new("Frame")
            a2.Name = "list"
            a2.Size = UDim2.new(1, 0, 0, 0)
            a2.Position = UDim2.new(0, 0, 1, 1)
            a2.BackgroundColor3 = Color3.fromRGB(17, 17, 17)
            a2.BorderColor3 = Color3.new()
            a2.BorderSizePixel = #Z >= 1 and 1 or 0
            a2.ZIndex = 99
            a2.Visible = false
            a2.Parent = a1
            local a3 = Instance.new("UIListLayout")
            a3.SortOrder = "LayoutOrder"
            a3.Padding = UDim.new(0, 1)
            a3.Parent = a2
            local a4 = Instance.new("TextLabel")
            a4.Text = y
            a4.BackgroundTransparency = 1
            a4.Font = Enum.Font.Code
            a4.TextColor3 = Color3.new(1, 1, 1)
            a4.TextSize = 12
            a4.Position = UDim2.new(1, 10, 0, 0)
            a4.Parent = a1
            a4.Size = UDim2.new(0, a4.TextBounds.X, 1, 0)
            local function V(W)
                local G = false
                for B, C in next, a0 do
                    if a0[B] == W then
                        G = true
                    end
                end
                if G then
                    local a5, a6 = string.gsub(W, "pepsi\\", "")
                    a1.Text = a5
                    _(W)
                end
            end
            local function a7(W)
                for B, C in next, a2:GetChildren() do
                    if C:IsA("TextButton") then
                        C:Destroy()
                    end
                end
                a2.BorderSizePixel = #W >= 1 and 1 or 0
                a2.Size = UDim2.new(1, 0, 0, #W * 13)
                for B, C in next, W do
                    local a5, a6 = string.gsub(C, "pepsi\\", "")
                    local a8 = Instance.new("TextButton")
                    a8.Name = C
                    a8.Size = UDim2.new(0, 100, 0, 12)
                    a8.BackgroundTransparency = 1
                    a8.Font = Enum.Font.Code
                    a8.TextColor3 = Color3.new(1, 1, 1)
                    a8.TextSize = 11
                    a8.AutoButtonColor = false
                    a8.Text = a5
                    a8.TextWrapped = true
                    a8.Parent = a2
                    a8.ZIndex = 100
                    a8.MouseEnter:Connect(function()
                        a8.TextSize = 12 
                        a8.TextColor3 = Color3.fromRGB(255, 0, 0)
                    end)
                    a8.MouseLeave:Connect(function()
                        a8.TextSize = 11
                        a8.TextColor3 = Color3.fromRGB(255, 255, 255)
                    end)
                    a8.MouseButton1Click:connect(
                        function()
                            a2.Visible = false
                            V(C)
                        end
                    )
                end
                a0 = W
            end
            a1.MouseButton1Click:connect(
                function()
                    a2.Visible = not a2.Visible
                end
            )
            a7(Z)
            local a9 = {changeValue = V, updateList = a7, Name = y, Type = "Dropdown"}
            l.options[y] = a9
        end
        function E:CreateKeybind(y, aa, _)
            local G = false
            k[y] = aa
            local ab = Instance.new("TextButton")
            ab.Name = y
            ab.Size = UDim2.new(0, 100, 0, 12)
            ab.BackgroundColor3 = Color3.fromRGB(17, 17, 17)
            ab.BorderColor3 = Color3.new()
            ab.AutoButtonColor = false
            ab.Text = "none"
            ab.Font = Enum.Font.Code
            ab.TextColor3 = Color3.new(1, 1, 1)
            ab.TextSize = 11
            ab.ZIndex = 0
            ab.Parent = A
            ab.MouseEnter:Connect(function()
                ab.BorderColor3 = Color3.fromRGB(255, 0, 0)  
            end)
            ab.MouseLeave:Connect(function()
                ab.BorderColor3 = Color3.new()
            end)
            local ac = Instance.new("TextLabel")
            ac.Text = y
            ac.BackgroundTransparency = 1
            ac.Font = Enum.Font.Code
            ac.TextColor3 = Color3.new(1, 1, 1)
            ac.TextSize = 12
            ac.Position = UDim2.new(1, 10, 0, 0)
            ac.Parent = ab
            ac.Size = UDim2.new(0, ac.TextBounds.X, 1, 0)
            local function ad(w)
                return string.sub(tostring(w), string.find(tostring(w), "UserInputType") and 20 or 14)
            end
            local function V(ae)
                ab.Text = ad(ae)
                _(ae)
            end
            ab.MouseButton1Click:connect(
                function()
                    G = true
                    ab.Text = "..."
                end
            )
            a.InputBegan:connect(
                function(w)
                    if G then
                        G = false
                        V(w.KeyCode == Enum.KeyCode.Unknown and w.UserInputType or w.KeyCode)
                    end
                end
            )
            V(aa)
            local af = {changeValue = V, Name = y, Type = "Keybind"}
            l.options[y] = af
        end
        function E:Textbox(y, aa, _)
            local G = false
            k[y] = aa
            local ag = Instance.new("TextBox")
            ag.Name = y
            ag.Size = UDim2.new(0, 100, 0, 12)
            ag.BackgroundColor3 = Color3.fromRGB(17, 17, 17)
            ag.BorderColor3 = Color3.new()
            ag.Text = ""
            ag.PlaceholderColor3 = Color3.new(0.7, 0.7, 0.7)
            ag.PlaceholderText = "..."
            ag.Font = Enum.Font.Code
            ag.TextColor3 = Color3.new(1, 1, 1)
            ag.TextSize = 11
            ag.ZIndex = 0
            ag.ClearTextOnFocus = false
            ag.TextWrapped = true
            ag.Parent = A
            local ah = Instance.new("TextLabel")
            ah.Text = y
            ah.BackgroundTransparency = 1
            ah.Font = Enum.Font.Code
            ah.TextColor3 = Color3.new(1, 1, 1)
            ah.TextSize = 12
            ah.Position = UDim2.new(1, 10, 0, 0)
            ah.Parent = ag
            ah.Size = UDim2.new(0, ah.TextBounds.X, 1, 0)
            ah.MouseEnter:Connect(function()
                ah.TextSize = 14 
                ah.TextColor3 = Color3.fromRGB(255, 0, 0)
            end)
            ah.MouseLeave:Connect(function()
                ah.TextSize = 13
                ah.TextColor3 = Color3.new(1, 1, 1)
            end)
            return ag
        end
        function E:CreateButton(y, ai)
            local aj = Instance.new("TextButton")
            aj.Name = y
            aj.Size = UDim2.new(0, 100, 0, 12)
            aj.BackgroundColor3 = Color3.fromRGB(17, 17, 17)
            aj.BorderColor3 = Color3.fromRGB()
            aj.AutoButtonColor = false
            aj.Text = y
            aj.Font = Enum.Font.Code
            aj.TextColor3 = Color3.new(0.7, 0.7, 0.7)
            aj.TextSize = 11
            aj.ZIndex = 0
            aj.Parent = A
            aj.MouseButton1Click:connect(ai)
            aj.MouseEnter:Connect(function()
                aj.BorderColor3 = Color3.fromRGB(255, 0, 0)  
            end)
            aj.MouseLeave:Connect(function()
                aj.BorderColor3 = Color3.fromRGB(29, 29, 29)  
            end)
        end
        return E
    end
    m.Parent = game.CoreGui
    return x
end

function getNearest()
    local ak = math.huge
    local al = nil
    local am = nil
    for B, C in next, e:GetChildren() do
        if C ~= g and C.Team ~= g and C.Character and C.Character.PrimaryPart then
            local am, an = i:WorldToScreenPoint(C.Character["HumanoidRootPart"].Position)
            if an then
                local ao = (Vector2.new(j.X, j.Y) - Vector2.new(am.X, am.Y)).magnitude
                if ao < ak then
                    al = C
                    ak = ao
                end
            end
        end
    end
    return al, ak
end
local ap = Instance.new("Folder", game.CoreGui)
function chams(aq)
    pcall(
        function()
            if aq.Character then
                for B, C in next, aq.Character:GetChildren() do
                    if C:IsA "BasePart" and C.Name ~= "HumanoidRootPart" then
                        local ar = Instance.new("BoxHandleAdornment")
                        ar.Size = C.Size + Vector3.new(0.1, 0.1, 0.1)
                        ar.Transparency = k["Chams Transparency"] / 100
                        ar.ZIndex = 0
                        ar.AlwaysOnTop = true
                        ar.Visible = true
                        ar.Parent = ap
                        ar.Adornee = C
                        ar.Color3 = Color3.fromRGB(255, 0, 0)
                        if aq.Character:FindFirstChild("HumanoidRootPart") then
                            aq.Character.HumanoidRootPart.AncestryChanged:connect(
                                function()
                                    ar:Destroy()
                                end
                            )
                        end
                    end
                end
            end
        end
    )
end
local as = nil
local at = false
local au = getrawmetatable(game)
setreadonly(au, false)
local av = au.__namecall
local aw = au.__newindex
au.__newindex =
    newcclosure(
    function(self, ax, W)
        if ax == "WalkSpeed" and at then
            return
        end
        return aw(self, ax, W)
    end
)
au.__namecall =
    newcclosure(
    function(self, ...)
        local ay = getnamecallmethod()
        local az = {...}
        if string.find(ay, "IgnoreList") then
            if as and k["Silent aim"] then
                az[1] =
                    Ray.new(
                    workspace.CurrentCamera.CFrame.Position,
                    (as.CFrame.p +
                        Vector3.new(0, (workspace.CurrentCamera.CFrame.Position - as.CFrame.p).Magnitude / 500, 0) -
                        workspace.CurrentCamera.CFrame.Position).unit * 500
                )
            end
        end
        if tostring(ay) == "InvokeServer" and self.Name == "Hugh" then
            return wait(9e9)
        elseif tostring(ay) == "FireServer" and string.find(tostring(self.Name), "{") then
            return wait(9e9)
        end
        return av(self, unpack(az))
    end
)
function getNearest()
    local ak = math.huge
    local al = nil
    local am = nil
    for B, C in next, e:GetChildren() do
        if C ~= g and C.Team ~= g and C.Character and C.Character.PrimaryPart then
            local am, an = i:WorldToScreenPoint(C.Character["HumanoidRootPart"].Position)
            if an then
                local ao = (Vector2.new(j.X, j.Y) - Vector2.new(am.X, am.Y)).magnitude
                if ao < ak then
                    al = C
                    ak = ao
                end
            end
        end
    end
    return al, ak
end
local ap = Instance.new("Folder", game.CoreGui)
function chams(aq)
    pcall(
        function()
            if aq.Character then
                for B, C in next, aq.Character:GetChildren() do
                    if C:IsA "BasePart" and C.Name ~= "HumanoidRootPart" then
                        local ar = Instance.new("BoxHandleAdornment")
                        ar.Size = C.Size + Vector3.new(0.1, 0.1, 0.1)
                        ar.Transparency = k["Chams Transparency"] / 100
                        ar.ZIndex = 0
                        ar.AlwaysOnTop = true
                        ar.Visible = true
                        ar.Parent = ap
                        ar.Adornee = C
                        ar.Color3 = Color3.fromRGB(255, 0, 0)
                        if aq.Character:FindFirstChild("HumanoidRootPart") then
                            aq.Character.HumanoidRootPart.AncestryChanged:connect(
                                function()
                                    ar:Destroy()
                                end
                            )
                        end
                    end
                end
            end
        end
    )
end
local as = nil
local at = false
local au = getrawmetatable(game)
setreadonly(au, false)
local av = au.__namecall
local aw = au.__newindex
au.__newindex =
    newcclosure(
    function(self, ax, W)
        if ax == "WalkSpeed" and at then
            return
        end
        return aw(self, ax, W)
    end
)
au.__namecall =
    newcclosure(
    function(self, ...)
        local ay = getnamecallmethod()
        local az = {...}
        if string.find(ay, "IgnoreList") then
            if as and k["Silent aim"] then
                az[1] =
                    Ray.new(
                    workspace.CurrentCamera.CFrame.Position,
                    (as.CFrame.p +
                        Vector3.new(0, (workspace.CurrentCamera.CFrame.Position - as.CFrame.p).Magnitude / 500, 0) -
                        workspace.CurrentCamera.CFrame.Position).unit * 500
                )
            end
        end
        if tostring(ay) == "InvokeServer" and self.Name == "Hugh" then
            return wait(9e9)
        elseif tostring(ay) == "FireServer" and string.find(tostring(self.Name), "{") then
            return wait(9e9)
        end
        return av(self, unpack(az))
    end
)

------------------------------------ UI   ------------------------------------
local aA = l:CreateUI()
------------------------------------ TABS ------------------------------------
local aB = aA:CreateTab("aimbot")
local aC = aA:CreateTab("visuals")
local aD = aA:CreateTab("movement")
local aE = aA:CreateTab("other")
local aG = aA:CreateTab("skins")
local aH = aA:CreateTab("lua")
local aF = aA:CreateTab("config")

------------------------------------ AIMBOT ------------------------------------
aB:CreateLabel("Aimbot")

silentAim = aB:CreateToggle("Silent aim", function(K)
    k["Silent aim"] = K
    if K then
        spawn(
            function()
                d:BindToRenderStep(
                    "silentAim",
                    1,
                    function()
                        as = nil
                        if
                            a:IsMouseButtonPressed(Enum.UserInputType.MouseButton1) and g.Character and
                                g.Character.PrimaryPart
                        then
                            local aG, aH = getNearest()
                            if
                                aH <= k["Aimbot FOV"] and aG.Team ~= g.Team and aG.Character and
                                    aG.Character.PrimaryPart and
                                    aG.Character:FindFirstChild("Head")
                            then
                                local aI = 100 - k["Hit chance"] <= math.random(0, 99)
                                if aI then
                                    as = k["Body aim"] and aG.Character.PrimaryPart or aG.Character.Head
                                end
                            end
                        end
                    end)
                end)
        else
            d:UnbindFromRenderStep("silentAim")
        end
end)

silentAim = aB:CreateToggle("Body aim", function(K)
    k["Body aim"] = K
end)

hitChange = aB:CreateSlider("Hit chance", 100, function(W)
    k["Hit chance"] = W
end)

aimbotFOV = aB:CreateSlider("Aimbot FOV", 200, function(W)
    k["Aimbot FOV"] = W
end)

aB:CreateLabel("Gun mods")

noSpread = aB:CreateToggle("No Spread", function(K)
    k["NoSpread"] = K
end)

noRecoil = aB:CreateToggle("No Recoil", function(K)
    if K == true then
        game:GetService("RunService"):BindToRenderStep("NoRecoil", 100, function()
            cbClient.resetaccuracy()
            cbClient.RecoilX = 0
            cbClient.RecoilY = 0
        end)
    elseif K == false then
        game:GetService("RunService"):UnbindFromRenderStep("NoRecoil")
    end
end)

------------------------------------ VISUALS ------------------------------------
local bj = game:GetService("Players")
local bk = bj.LocalPlayer
local aV = bk:GetMouse()
local cam = workspace.CurrentCamera
local bl = getrawmetatable(game)
local bm = bl.__namecall
local bn = bl.__index
local bo = bl.__newindex

local bq = game:GetService("RunService")
local aW = game:GetService("UserInputService")
local bs = game:GetService("Lighting")
local boxCOlor = Color3.new(1,1,1)
local NameColor = Color3.new(1,1,1)
local WeaponCOLOR = Color3.new(1,1,1)
local HealthCOLOR = Color3.fromRGB(1,255,1)

local boxf = false
local activef = true
local healthf = false
local namesf = false
local weaponf = false
local Teammates = false
local Enemies = true
local cT = {}
local cU = {}
do
    cU.default = {
        Line = {Thickness = 1.5, Color = Color3.fromRGB(255, 255, 255), Visible = false},
        Text = {
            Size = 13,
            Center = true,
            Outline = true,
            Font = 0,
            Color = Color3.fromRGB(255, 255, 255),
            Visible = false
        },
    Square = {Thickness = 1.5, Filled = false, Color = Color3.fromRGB(255, 255, 255), Visible = false}
    }
    function cU.create(aq)
        local cV = Drawing.new(aq)
            for bc, j in pairs(cU.default[aq]) do
                cV[bc] = j
            end
            return cV
        end
        function cU.add(c0)
            if not cT[c0] then
                cT[c0] = {
                    Name = cU.create("Text"),
                    Weapon = cU.create("Text"),
                    BoxOutline = cU.create("Square"),
                    Box = cU.create("Square"),
                    HealthOutline = cU.create("Line"),
                    Health = cU.create("Line")
                }
            end
        end
        for af, c0 in pairs(bj:GetPlayers()) do
            if c0 ~= bk then
                cU.add(c0)
            end
        end
        bj.PlayerAdded:Connect(cU.add)
        bj.PlayerRemoving:Connect(
            function(c0)
                wait()
                if cT[c0] then
                    for bc, j in pairs(cT[c0]) do
                        for cW, cX in pairs(j) do
                            if j then
                                j:Remove()
                            end
                        end
                    end
                    cT[c0] = nil
                end
            end
        )
    end
    bq.RenderStepped:Connect(
        function()
            for af, c0 in pairs(bj:GetPlayers()) do
                local aA = cT[c0]
                if aA ~= nil then
                    if
                    c0 ~= bk and c0.Character and c0.Character:FindFirstChild("Humanoid") and
                    c0.Character:FindFirstChild("HumanoidRootPart") and
                    activef and c0.Team ~= bk.Team then
                        local bV = c0.Character.HumanoidRootPart
                        local c1, cY = cam:WorldToViewportPoint(bV.Position)
                        local a6 =
                        (cam:WorldToViewportPoint(bV.Position - Vector3.new(0, 3, 0)).Y -
                            cam:WorldToViewportPoint(bV.Position + Vector3.new(0, 2.6, 0)).Y) /
                        2
                        aA.Box.Color = boxCOlor
                        aA.Box.Size = Vector2.new(a6 * 1.5, a6 * 1.9)
                        aA.Box.Position = Vector2.new(c1.X - a6 * 1.5 / 2, c1.Y - a6 * 1.6 / 2)
                        aA.BoxOutline.Color = Color3.fromRGB(0, 0, 0)
                        aA.BoxOutline.Thickness = 3
                        aA.BoxOutline.Size = aA.Box.Size
                        aA.BoxOutline.Position = aA.Box.Position
                        aA.Health.Color = HealthCOLOR
                        aA.Health.From = Vector2.new(aA.Box.Position.X - 5, aA.Box.Position.Y + aA.Box.Size.Y)
                        aA.Health.To =
                        Vector2.new(
                            aA.Health.From.X,
                            aA.Health.From.Y -
                            c0.Character.Humanoid.Health / c0.Character.Humanoid.MaxHealth * aA.Box.Size.Y
                        )
                        aA.HealthOutline.Color = Color3.fromRGB(0, 0, 0)
                        aA.HealthOutline.Thickness = 3
                        aA.HealthOutline.From = Vector2.new(aA.Health.From.X, aA.Box.Position.Y + aA.Box.Size.Y + 1)
                        aA.HealthOutline.To = Vector2.new(aA.Health.From.X, aA.Health.From.Y - 1 * aA.Box.Size.Y - 1)
                        aA.Name.Color = NameColor
                        aA.Name.Text = c0.Name
                        aA.Name.Position = Vector2.new(aA.Box.Size.X / 2 + aA.Box.Position.X, aA.Box.Position.Y - 16)
                        aA.Name.Font = Drawing.Fonts.Plex
                        aA.Name.Outline = true
                        aA.Name.Size = 14
                        aA.Weapon.Color = WeaponCOLOR
                        aA.Weapon.Position =
                        Vector2.new(aA.Box.Size.X / 2 + aA.Box.Position.X, aA.Box.Size.Y + aA.Box.Position.Y + 1)
                        aA.Weapon.Font = Drawing.Fonts.Plex
                        aA.Weapon.Outline = true
                        aA.Weapon.Size = 14
                        if boxf then
                            aA.Box.Visible = cY
                            aA.BoxOutline.Visible = cY
                        else
                            aA.Box.Visible = false
                            aA.BoxOutline.Visible = false
                        end
                        if healthf then
                            aA.Health.Visible = cY
                            aA.HealthOutline.Visible = cY
                        else
                            aA.Health.Visible = false
                            aA.HealthOutline.Visible = false
                        end
                        aA.Name.Visible = namesf and cY or false
                        aA.Weapon.Visible = weaponf and cY or false
                        else
                            aA.Box.Visible = false
                            aA.BoxOutline.Visible = false
                            aA.HealthOutline.Visible = false
                            aA.Health.Visible = false
                            aA.Name.Visible = false
                            aA.Weapon.Visible = false
                        end
                end
        end
end)


aC:CreateLabel("ESP")

chamsToggle = aC:CreateToggle("Chams", function(K)
    if K ~= k["Chams"] then
        k["Chams"] = K
        if k["Chams"] then
            for B, C in next, e:GetPlayers() do
                if C ~= g and C.Team ~= g.Team and C.Character and C.Character.PrimaryPart then
                    chams(C)
                end
            end
        else
            ap:ClearAllChildren()
        end
    end
end)

chamsTransparency = aC:CreateSlider("Chams Transparency", 100, function(W)
    k["Chams Transparency"] = W
    for B, C in next, ap:GetChildren() do
        C.Transparency = 0 + k["Chams Transparency"] / 100
    end
end)

boxesToggle = aC:CreateToggle("Boxes", function(K)
    boxf = K
end)

healthToggle = aC:CreateToggle("Health", function(K)
    healthf = K
end)

nameToggle = aC:CreateToggle("Names", function(K)
    namesf = K
end)

aC:CreateLabel("World")

local b3 = Instance.new("ColorCorrectionEffect", game.Lighting)
Nightmode = aC:CreateToggle("Nightmode", function(K)
    k["Nightmode"] = K
    if K then
        b3.Brightness = -0.15
        game.Lighting.Brightness = 0
    else
        b3.Brightness = 0
        game.Lighting.Brightness = 1
    end
end)

local zuhnmode = Instance.new("ColorCorrectionEffect", workspace.CurrentCamera)
Zuhnmode = aC:CreateToggle("Zuhn Mode", function(K)
    if K == true then
        zuhnmode.Saturation = 1.2
    elseif K == false then
        zuhnmode.Saturation = 0
    end
end)

bettershadows = aC:CreateToggle("Better Shadows", function(K)
    k["Shadows"] = K
end)

noFlash = aC:CreateToggle("No Flash", function(K)
    if K == true then
        game.Players.LocalPlayer.PlayerGui.Blnd.Enabled = false
    elseif K == false then
        game.Players.LocalPlayer.PlayerGui.Blnd.Enabled = true
    end
end)

Skyboxes = {
    ["Purple Nebula"] = {
        ["SkyboxBk"] = "rbxassetid://159454299",
        ["SkyboxDn"] = "rbxassetid://159454296",
        ["SkyboxFt"] = "rbxassetid://159454293",
        ["SkyboxLf"] = "rbxassetid://159454286",
        ["SkyboxRt"] = "rbxassetid://159454300",
        ["SkyboxUp"] = "rbxassetid://159454288"
    },
    ["Red Night"] = {
        ["SkyboxBk"] = "rbxassetid://401664839",
        ["SkyboxDn"] = "rbxassetid://401664862",
        ["SkyboxFt"] = "rbxassetid://401664960",
        ["SkyboxLf"] = "rbxassetid://401664881",
        ["SkyboxRt"] = "rbxassetid://401664901",
        ["SkyboxUp"] = "rbxassetid://401664936"
    },
    ["Dusty Clouds"] = {
        ["SkyboxBk"] = "rbxassetid://252760981",
        ["SkyboxDn"] = "rbxassetid://252763035",
        ["SkyboxFt"] = "rbxassetid://252761439",
        ["SkyboxLf"] = "rbxassetid://252760980",
        ["SkyboxRt"] = "rbxassetid://252760986",
        ["SkyboxUp"] = "rbxassetid://252762652"
    },
    ["Night Sky"] = {
        ["SkyboxBk"] = "rbxassetid://12064107",
        ["SkyboxDn"] = "rbxassetid://12064152",
        ["SkyboxFt"] = "rbxassetid://12064121",
        ["SkyboxLf"] = "rbxassetid://12063984",
        ["SkyboxRt"] = "rbxassetid://12064115",
        ["SkyboxUp"] = "rbxassetid://12064131"
    },
    ["Pink Daylight"] = {
        ["SkyboxBk"] = "rbxassetid://271042516",
        ["SkyboxDn"] = "rbxassetid://271077243",
        ["SkyboxFt"] = "rbxassetid://271042556",
        ["SkyboxLf"] = "rbxassetid://271042310",
        ["SkyboxRt"] = "rbxassetid://271042467",
        ["SkyboxUp"] = "rbxassetid://271077958"
    }
}

local b5 = workspace.CurrentCamera
local b6 = Instance.new("SurfaceGui")
b6.CanvasSize = Vector2.new(200, 200)
b6.Name = "DropSurface"

local b7 = Instance.new("ImageLabel")
b7.BackgroundTransparency = 1
b7.ImageColor3 = Color3.new(121 / 255, 121 / 255, 121 / 255)
b7.Size = UDim2.new(0, 5, 0, 100)
b7.ImageTransparency = 0.75
b7.Image = "rbxassetid://221405600"

local b8 = Instance.new("Part")
b8.Transparency = 1
b8.Anchored = true
b8.CanCollide = false
b8.FormFactor = "Custom"

local b9 = Instance.new("SurfaceGui")
b9.CanvasSize = Vector2.new(200, 200)
b9.Face = "Top"
b9.Parent = b8
b9.Name = "DropleSurface"

local ba = Instance.new("ImageLabel", b9)
ba.Position = UDim2.new(0, 0, 0, 0)
ba.Size = UDim2.new(1, 0, 1, 0)
ba.BackgroundTransparency = 1
ba.Image = "rbxassetid://221657524"
ba.ImageColor3 = Color3.new(121 / 255, 121 / 255, 121 / 255)
ba.ImageTransparency = 0.75
ba.Name = "SplashImage"
local bb = 300
local bc = 900
local bd = {}
local be = {}

function randring(bf, bg)
    local bh = math.random() * math.pi * 2
    local bi = math.random() * (bg - bf) + bf
    return math.cos(bh) * bi, 0, math.sin(bh) * bi
end

function drople(b0)
    local bj = b8:Clone()
    bj.Parent = workspace.Debris
    local bk = math.random() * math.pi * 2
    table.insert(be, {part = bj, start = tick(), position = b0, label = bj.DropleSurface.SplashImage, angle = bk})
end

rainEnabled = aC:CreateToggle("Rain", function(K)
    k["Rain"] = K
    bd = {}
    be = {}
    if not k["Rain"] then
        workspace.Debris:ClearAllChildren()
    end
    spawn(
        function()
            while k["Rain"] do
                game["Run Service"].RenderStepped:wait()
                if #bd < 150 then
                    local bl = Instance.new("Part", workspace.Debris)
                    local bm = math.random(1, 3) == 1 and 24 or 8
                    local bn, bo, bp, bq = 0, 75, 3, 8
                    if math.random(1, 3) == 1 then
                        bn, bo, bp, bq = 75, 200, 9, 24
                    end
                    bl.CanCollide = false
                    bl.Transparency = 0.5
                    bl.Anchored = true
                    bl.FormFactor = "Custom"
                    bl.Size = Vector3.new(bq, bq, 0.2)
                    bl.Transparency = 1
                    local br = b6:Clone()
                    br.Parent = bl
                    br.CanvasSize = Vector2.new(200, 200)
                    for B = 1, bp do
                        local bs = b7:Clone()
                        bs.Position = UDim2.new(0, math.random() * 195, 0, math.random() * 100)
                        bs.Parent = br
                    end
                    bl.Position =
                        Vector3.new(
                        b5.CFrame.p.X + math.random(-100, 0),
                        b5.CFrame.p.Y + 100,
                        b5.CFrame.p.Z + math.random(-100, 100)
                    )
                    table.insert(
                        bd,
                        {
                            part = bl,
                            x = 0,
                            y = math.random(),
                            z = 0,
                            stop = -1,
                            close = bn,
                            far = bo,
                            labels = bl.DropSurface:GetChildren()
                        }
                    )
                end
                local b5 = workspace.CurrentCamera.CoordinateFrame
                local bt = b5.lookVector
                local bu = workspace.CurrentCamera.CoordinateFrame.p
                for bv, bw in pairs(bd) do
                    local bl, bx, by, bz = bw.part, bw.x, bw.y, bw.z
                    local C = Vector3.new(bx, by, bz)
                    local bA = b5:pointToObjectSpace(C)
                    local bB = bA.z < 0
                if by < bw.stop - 5 then
                        if bB and (Vector3.new(bx, bw.stop, bz) - workspace.CurrentCamera.CFrame.p).Magnitude >= 5 then
                            drople(Vector3.new(bx, bw.stop, bz))
                        end
                        bw.x, bv, bw.z = randring(bw.close, bw.far)
                        bw.x, bw.z = bw.x + bu.x, bw.z + bu.z
                        bw.y = bc
                        local b0 = Vector3.new(bw.x, bw.y, bw.z)
                        bl.CFrame = CFrame.new(b0, Vector3.new(bu.x, by, bu.z))
                        local aZ = Ray.new(b0, Vector3.new(0, -bc - bb, 0))
                        local bC, a_ = workspace.FindPartOnRay(workspace, aZ, home, true)
                        if bC then
                            bw.stop = a_.y
                        else
                            bw.stop = bb
                        end
                    else
                        bw.y = by - 2
                        if bB then
                            local bD = (by - bc + 50) * .25 / 50 + .75
                            if by < bw.stop - 1 then
                                bD = .75 + .25 / 5 * (bw.stop - 1 - by)
                            end
                            if by > bc - 50 or by < bw.stop then
                                for bv, bE in pairs(bw.labels) do
                                    bE.ImageTransparency = bD
                                end
                            end
                        end
                        bl.CFrame = CFrame.new(C, Vector3.new(bu.x, by, bu.z))
                    end
                end
                for bF = #be, 1, -1 do
                    local bG = be[bF]
                    local bh = (tick() - bG.start) * 3
                    if bh > 1 then
                        bG.part:Destroy()
                        table.remove(be, bF)
                    else
                        bG.label.ImageTransparency = bh
                        local bH = bh - bh * bh
                        bG.part.Size = Vector3.new(2 / 3 + bh, 0.2, 2 / 3 + bh)
                        bG.part.CFrame =
                            CFrame.new(bG.position + Vector3.new(0, bH * 2, 0)) * CFrame.Angles(0, bG.angle, 0)
                    end
                end
            end
        end)
end)


ForceCrosshairToggle = aC:CreateToggle("Force Crosshair", function(K)
    ForceCrosshairEnabled = K
end)

skyboxEnabled = aC:CreateToggle("Custom skybox", function(K)
    k["Custom skybox"] = K
end)

skyboxSelected = aC:CreateDropdown("Selected skybox", {"Night Sky", "Purple Nebula", "Pink Daylight", "Dusty Clouds", "Red Night"}, function(bI)
    k["Selected skybox"] = bI
    spawn(
        function()
            if not game.Lighting:FindFirstChild("customsky") then
                if k["Custom skybox"] then
                    local bJ = Instance.new("Sky", game.Lighting)
                    bJ.Name = "customsky"
                    if Skyboxes[bI] then
                        for B, C in next, Skyboxes[bI] do
                            game.Lighting.customsky[B] = C
                        end
                    end
                end
            end
            if Skyboxes[bI] and game.Lighting:FindFirstChild("customsky") then
                for B, C in next, Skyboxes[bI] do
                    game.Lighting.customsky[B] = C
                end
            end
            if not k["Custom skybox"] and game.Lighting:FindFirstChild("customsky") then
                game.Lighting.customsky:Destroy()
        end
    end)
end)

aC:CreateLabel("Viewmodel")

enabledViewmodel = aC:CreateToggle("Enabled Viewmodel", function(K)
    ViewmodelEnabled = K
end)

xViewmodel = aC:CreateSlider("X", 360, function(W)
    ViewmodelX = W
end)

yViewmodel = aC:CreateSlider("Y", 360, function(W)
    ViewmodelY = W
end)

zViewmodel = aC:CreateSlider("Z", 360, function(W)
    ViewmodelZ = W
end)
------------------------------------ MOVEMENT ------------------------------------
aD:CreateLabel("Movement")

local aJ = h.speedupdate
bunnyHop = aD:CreateToggle("Bunny hop", function(K)
    k["Bunny hop"] = K
        if K then
            spawn(
                function()
                    d:BindToRenderStep("bunnyHop", 1, function()
                            if
                                a:IsKeyDown(Enum.KeyCode.Space) and g.Character and
                                    g.Character:FindFirstChild("Humanoid")
                            then
                                at = false
                                g.Character.Humanoid.WalkSpeed = 20.5
                                at = true
                                g.Character.Humanoid.Jump = true
                                h.speedupdate = function()
                                end
                            else
                                at = false
                                h.speedupdate = aJ
                            end
                        end
                    )
                end
            )
        else
            h.speedupdate = aJ
            d:UnbindFromRenderStep("bunnyHop")
        end
    end
)

local aK = {}
local aL = workspace.CurrentCamera.ViewportSize.Y - 100
local aM = aL
local aN = 0
local aO = {
    Color3.fromRGB(85, 205, 252),
    Color3.fromRGB(85, 205, 252),
    Color3.fromRGB(247, 168, 184),
    Color3.fromRGB(247, 168, 184),
    Color3.fromRGB(255, 255, 255),
    Color3.fromRGB(255, 255, 255),
    Color3.fromRGB(247, 168, 184),
    Color3.fromRGB(247, 168, 184)
}

local aP = Drawing.new("Text")
aP.Text = ""
aP.Center = true
aP.Outline = true
aP.Color = Color3.new(1, 1, 1)
aP.Font = 3
aP.Position = Vector2.new(workspace.CurrentCamera.ViewportSize.X / 2, workspace.CurrentCamera.ViewportSize.Y - 90)
aP.Size = 20
aP.Visible = false

local aQ = Drawing.new("Text")
aQ.Text = "EB"
aQ.Center = true
aQ.Outline = true
aQ.Color = Color3.new(0.9, 0.2, 0.2)
aQ.Font = 3
aQ.Position = Vector2.new(workspace.CurrentCamera.ViewportSize.X / 2, workspace.CurrentCamera.ViewportSize.Y - 80)
aQ.Size = 18
aQ.Visible = false

local aR = Drawing.new("Text")
aR.Text = "JB"
aR.Center = true
aR.Outline = true
aR.Color = Color3.new(1, 1, 1)
aR.Font = 3
aR.Position = Vector2.new(workspace.CurrentCamera.ViewportSize.X / 2, workspace.CurrentCamera.ViewportSize.Y - 50)
aR.Size = 18
aR.Visible = false

local aS = {
    Edgebug = {
        Keybind = "Enum.KeyCode.E",
        XZModifier = 2.4,
        Debounce = false,
        NoDamage = false,
        YModifier = 0.2,
        Enabled = false,
        Held = false
    },
    Edgejump = {Held = false, Enabled = false, Debounce = false, Keybind = "Enum.KeyCode.LeftAlt"},
    VelocityGraph = {Enabled = false, SmoothMode = false, Color = "Normal", TransCount = 1, DebounceCount = 0},
    JumpBug = {Held = false, Enabled = false, Keybind = "Enum.KeyCode.T"},
    M9 = {Enabled = false}
}

EdgebugToggle = aD:CreateToggle("Edgebug", function(K)
    k["Edgebug"] = K
    aS.Edgebug.Enabled = not aS.Edgebug.Enabled
    aS.Edgebug.Held = false
    aQ.Visible = false
end)

EdgejumpToggle = aD:CreateToggle("Edgejump", function(K)
    k["Edgejump"] = K
    aS.Edgejump.Enabled = not aS.Edgejump.Enabled
    aS.Edgejump.Held = false
end)

EdgejumpToggle = aD:CreateToggle("Jumpbug", function(K)
    k["Jumpbug"] = K
    aS.JumpBug.Enabled = not aS.JumpBug.Enabled
    aS.JumpBug.Held = false
end)

aD:CreateLabel("Sounds")

local ebsfx = Instance.new("Sound")
ebsfx.Parent = game:GetService("SoundService")

ebSoundsDropdown = aD:CreateDropdown("EB Sound", {"Ownage", "Godlike", "Skeet", "Wow"}, function(K)
    if K == "Ownage" then
        ebsfx.SoundId = 'rbxassetid://6887181639'
    elseif K == "Godlike" then
        ebsfx.SoundId = 'rbxassetid://7463103082'
    elseif K == "Skeet" then
        ebsfx.SoundId = 'rbxassetid://5447626464'
    elseif K == "Wow" then
        ebsfx.SoundId = 'rbxassetid://7872233648'
    end
end)

aD:CreateLabel("Keybinds")

EdgebugKeybind = aD:CreateKeybind("Edgejump Keybind", Enum.KeyCode.LeftAlt, function(w)
    k["Edgejump Keybind"] = tostring(w)
    aS.Edgejump.Keybind = tostring(w)
    aS.Edgejump.Held = false
end)

EdgebugKeybind = aD:CreateKeybind("Edgebug Keybind", Enum.KeyCode.E, function(w)
    k["Edgebug Keybind"] = tostring(w)
    aS.Edgejump.Keybind = tostring(w)
    aS.Edgejump.Held = false
end)

JumpbugKeybind = aD:CreateKeybind("Jumpbug Keybind", Enum.KeyCode.T, function(w)
    k["Jumpbug Keybind"] = tostring(w)
    aS.JumpBug.Keybind = tostring(w)
    aS.JumpBug.Held = false
end)

local au = getrawmetatable(game)
setreadonly(au, false)
local av = au.__namecall
au.__namecall = newcclosure( function(self, ...)
    local ay = getnamecallmethod()
    local az = {...}
    if self.Name == "FallDamage" and aS.Edgebug.NoDamage then
        az[2] = 0
    end
    return av(self, unpack(az))
end)

a.InputBegan:connect(function(w)
    local aY = w.KeyCode == Enum.KeyCode.Unknown and tostring(w.UserInputType) or tostring(w.KeyCode)
    if aY == k["Edgebug Keybind"] and aS.Edgebug.Enabled then
        aQ.Visible = true
    end
    if aY == aS.JumpBug.Keybind and aS.JumpBug.Enabled then
        aR.Visible = true
        aS.JumpBug.Held = true
    end
    if aY == k["Edgebug Keybind"] and aS.Edgebug.Enabled then
        aS.Edgebug.Held = true
            spawn(
                function()
                    while aS.Edgebug.Held do
                        d.RenderStepped:Wait()
                        if g.Character and g.Character:FindFirstChild("Humanoid") and g.Character.PrimaryPart then
                            local aZ =
                                Ray.new(
                                g.Character.HumanoidRootPart.Position,
                                (g.Character.HumanoidRootPart.Position - g.Character.HumanoidRootPart.Position -
                                    Vector3.new(0, 1, 0)).unit * 500
                            )
                            local a_, b0, b1 = workspace:FindPartOnRayWithIgnoreList(aZ, {g.Character})
                            if
                                g.Character.HumanoidRootPart.Position.Y - 2.99 <= b0.Y + 2.5 and
                                    g.Character.Humanoid:GetState() == Enum.HumanoidStateType.Freefall and
                                    g.Character.HumanoidRootPart.Velocity.Y <= 0 and
                                    not aS.Edgebug.Debounce
                            then
                                aS.Edgebug.Debounce = true
                                aS.Edgebug.NoDamage = true
                                repeat
                                    wait()
                                until g.Character.Humanoid:GetState() ~= Enum.HumanoidStateType.Freefall
                                if g.Character.HumanoidRootPart.Position.Y - 3.49 <= b0.Y + 2.5 then
                                    aQ.Color = Color3.new(0.2, 0.9, 0.2)
                                    wait()
                                    game.StarterGui:SetCore("SendNotification", {
                                    Title = "Internal";
                                    Text = "edgebugged !";
                                    Icon = "rbxassetid://6910419016";
                                    Duration = 3;
                                    })
                                    ebsfx.Volume = 2
                                    ebsfx:Play()
                                    g.Character.HumanoidRootPart.Velocity =
                                        Vector3.new(
                                        g.Character.HumanoidRootPart.Velocity.X * aS.Edgebug.XZModifier,
                                        g.Character.HumanoidRootPart.Velocity.Y * aS.Edgebug.YModifier,
                                        g.Character.HumanoidRootPart.Velocity.Z * aS.Edgebug.XZModifier
                                    )
                                    getsenv(game.Players.LocalPlayer.PlayerGui.GUI.Main.Chats.DisplayChat).moveOldMessages()
                                    getsenv(game.Players.LocalPlayer.PlayerGui.GUI.Main.Chats.DisplayChat).createNewMessage(
                                        "Internal",
                                        "edgebugged",
                                        Color3.fromRGB(255,0,0), 
                                        Color3.new(1,1,1),
                                        .01
                                    )
                                    local b2 = g.Character.HumanoidRootPart.Velocity
                                    pcall(
                                        function()
                                            for B = 1, 3 do
                                                wait()
                                                g.Character.HumanoidRootPart.Velocity = b2 - Vector3.new(0, 20, 0)
                                            end
                                        end
                                    )
                                end
                                wait(0)
                                aQ.Color = Color3.new(0.9, 0.2, 0.2)
                                wait(0)
                                aS.Edgebug.Debounce = false
                                aS.Edgebug.NoDamage = false
                            end
                        end
                    end
                end)
        end
        if aY == aS.Edgejump.Keybind and aS.Edgejump.Enabled then
            aS.Edgejump.Held = true
            while aS.Edgejump.Held do
                d.RenderStepped:Wait()
                if g.Character and g.Character:FindFirstChild("Humanoid") and not aS.Edgejump.Debounce then
                    if g.Character.Humanoid:GetState() == Enum.HumanoidStateType.Freefall then
                        return
                    end
                    if g.Character.Humanoid:GetState() ~= Enum.HumanoidStateType.Freefall then
                        wait(0.05)
                        if g.Character.Humanoid:GetState() == Enum.HumanoidStateType.Freefall then
                            game.Players.LocalPlayer.Character.Humanoid:ChangeState("Jumping")
                            aS.Edgejump.Debounce = true
                            wait(0.5)
                            aS.Edgejump.Debounce = false
                        end
                    end
                end
            end
        end
    end
)

a.InputEnded:connect(
    function(w)
        local aY = w.KeyCode == Enum.KeyCode.Unknown and tostring(w.UserInputType) or tostring(w.KeyCode)
        if aY == k["Edgebug Keybind"] and aS.Edgebug.Enabled then
            aQ.Visible = false
        end
        if aY == k["Edgebug Keybind"] then
            aS.Edgebug.Held = false
        end
        if aY == aS.Edgejump.Keybind then
            aS.Edgejump.Held = false
        end
        if aY == aS.JumpBug.Keybind then
            aR.Visible = false
            aS.JumpBug.Held = false
        end
    end
)

d.Stepped:connect(
    function()
        if g.Character and g.Character:FindFirstChild("Humanoid") then
            if aS.JumpBug.Enabled and aS.JumpBug.Held then
                game.Players.LocalPlayer.Character.Humanoid.JumpPower = 23
            else
                game.Players.LocalPlayer.Character.Humanoid.JumpPower = 20
            end
        end
    end
)

aD:CreateLabel("Other")

infStamina = aD:CreateToggle("Inf Stamina", function(K)
    if K == true then
		game:GetService("RunService"):BindToRenderStep("Stamina", 100, function()
			if cbClient.crouchcooldown ~= 0 then
				cbClient.crouchcooldown = 0
			end
		end)
	elseif K == false then
		game:GetService("RunService"):UnbindFromRenderStep("Stamina")
	end
end)

keystrokesButton = aD:CreateToggle("Keystrokes", function(K)
    if K == true then
        local ScreenGui = Instance.new("ScreenGui")
        local Frame = Instance.new("Frame")
        local W = Instance.new("TextLabel")
        local S = Instance.new("TextLabel")
        local A = Instance.new("TextLabel")
        local D = Instance.new("TextLabel")
        local E = Instance.new("TextLabel")
        local R = Instance.new("TextLabel")
        local Space = Instance.new("TextLabel")
        
        ScreenGui.Parent = game.CoreGui
        ScreenGui.Name = "keystrokess"
        
        Frame.Parent = game.CoreGui.keystrokess
        Frame.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        Frame.BackgroundTransparency = 1.000
        Frame.Position = UDim2.new(0.453987718, 0, 0.738977075, 0)
        Frame.Size = UDim2.new(0, 72, 0, 75)
        
        W.Name = "W"
        W.Parent = Frame
        W.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        W.BackgroundTransparency = 1.000
        W.Position = UDim2.new(0.287764132, 0, -0.0102292299, 0)
        W.Size = UDim2.new(0, 29, 0, 28)
        W.Font = Enum.Font.Code
        W.Text = "_"
        W.TextColor3 = Color3.fromRGB(255, 255, 255)
        W.TextSize = 14.000
        W.TextStrokeTransparency = 0.000
        
        S.Name = "S"
        S.Parent = Frame
        S.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        S.BackgroundTransparency = 1.000
        S.Position = UDim2.new(0.287764132, 0, 0.35915342, 0)
        S.Size = UDim2.new(0, 29, 0, 28)
        S.Font = Enum.Font.Code
        S.Text = "_"
        S.TextColor3 = Color3.fromRGB(255, 255, 255)
        S.TextSize = 14.000
        S.TextStrokeTransparency = 0.000
        
        A.Name = "A"
        A.Parent = Frame
        A.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        A.BackgroundTransparency = 1.000
        A.Position = UDim2.new(-0.0950409099, 0, 0.35915345, 0)
        A.Size = UDim2.new(0, 29, 0, 28)
        A.Font = Enum.Font.Code
        A.Text = "_"
        A.TextColor3 = Color3.fromRGB(255, 255, 255)
        A.TextSize = 14.000
        A.TextStrokeTransparency = 0.000
        
        D.Name = "D"
        D.Parent = Frame
        D.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        D.BackgroundTransparency = 1.000
        D.Position = UDim2.new(0.684458077, 0, 0.35915342, 0)
        D.Size = UDim2.new(0, 29, 0, 28)
        D.Font = Enum.Font.Code
        D.Text = "_"
        D.TextColor3 = Color3.fromRGB(255, 255, 255)
        D.TextSize = 14.000
        D.TextStrokeTransparency = 0.000
        
        E.Name = "E"
        E.Parent = Frame
        E.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        E.BackgroundTransparency = 1.000
        E.Position = UDim2.new(-0.0950409099, 0, -0.0102293491, 0)
        E.Size = UDim2.new(0, 29, 0, 28)
        E.Font = Enum.Font.Code
        E.Text = "_"
        E.TextColor3 = Color3.fromRGB(255, 255, 255)
        E.TextSize = 14.000
        E.TextStrokeTransparency = 0.000
        
        R.Name = "R"
        R.Parent = Frame
        R.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        R.BackgroundTransparency = 1.000
        R.Position = UDim2.new(0.683231115, 0, -0.0102292895, 0)
        R.Size = UDim2.new(0, 29, 0, 28)
        R.Font = Enum.Font.Code
        R.Text = "_"
        R.TextColor3 = Color3.fromRGB(255, 255, 255)
        R.TextSize = 14.000
        R.TextStrokeTransparency = 0.000
        
        Space.Name = "Space"
        Space.Parent = Frame
        Space.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
        Space.BackgroundTransparency = 1.000
        Space.Position = UDim2.new(-0.104209319, 0, 0.620387971, 0)
        Space.Size = UDim2.new(0, 87, 0, 28)
        Space.Font = Enum.Font.Code
        Space.Text = "_"
        Space.TextColor3 = Color3.fromRGB(255, 255, 255)
        Space.TextSize = 14.000
        Space.TextStrokeTransparency = 0.000
        
        -- Scripts:
        
        local function SJBA_fake_script() -- Frame.LocalScript 
            local script = Instance.new('LocalScript', Frame)
            local gui = script.Parent
            gui.Draggable = true
            gui.Active = true
        end
        coroutine.wrap(SJBA_fake_script)()
        
        local function UTCCBQ_fake_script() -- Frame.LocalScript 
            local script = Instance.new('LocalScript', Frame)
            local UIS = game:GetService("UserInputService")
            local Sp = script.Parent.Space
            local W = script.Parent.W
            local A = script.Parent.A
            local S = script.Parent.S
            local D = script.Parent.D
            local E = script.Parent.E
            local R = script.Parent.R
        	
            UIS.InputBegan:Connect(function(key)
                if key.KeyCode == Enum.KeyCode.W then
                    W.Text = "W"
                elseif key.KeyCode == Enum.KeyCode.A then
                    A.Text = "A"
                elseif key.KeyCode == Enum.KeyCode.S then
                    S.Text = "S"
                elseif key.KeyCode == Enum.KeyCode.D then
                    D.Text = "D"
                elseif key.KeyCode == Enum.KeyCode.E then
                    E.Text = "E"
                elseif key.KeyCode == Enum.KeyCode.R then
                    R.Text = "R"
                elseif key.KeyCode == Enum.KeyCode.Space then
                    Sp.Text = "Space"
                end
            end)
            
            UIS.InputEnded:Connect(function(key)
                if key.KeyCode == Enum.KeyCode.W then
                    W.Text = "_"
                elseif key.KeyCode == Enum.KeyCode.A then
                    A.Text = "_"
                elseif key.KeyCode == Enum.KeyCode.S then
                    S.Text = "_"
                elseif key.KeyCode == Enum.KeyCode.D then
                    D.Text = "_"
                elseif key.KeyCode == Enum.KeyCode.E then
                    E.Text = "_"
                elseif key.KeyCode == Enum.KeyCode.R then
                    R.Text = "_"
                elseif key.KeyCode == Enum.KeyCode.Space then
                    Sp.Text = "_"
                end
            end)
        end
    coroutine.wrap(UTCCBQ_fake_script)()
    
    elseif K == false then
        game.CoreGui.keystrokess:Destroy()
    end
end)

PlrTrailToggle = aD:CreateToggle("Player Trail", function(K)
    if K == true then
        PlrTrail = game:GetService("RunService").RenderStepped:Connect(function()
            pcall(function()
                local player = game:GetService("Players").LocalPlayer
                local LFoot = Instance.new("Attachment",player.Character.LeftFoot)
                local RFoot = Instance.new("Attachment",player.Character.RightFoot)
                local Trail = Instance.new("Trail")
                Trail.Attachment0 = LFoot
                Trail.Attachment1 = RFoot
                Trail.Lifetime = 3
                Trail.Parent = LFoot.Parent
                Trail.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(255, 0, 4)), ColorSequenceKeypoint.new(0.24, Color3.fromRGB(243, 255, 0)), ColorSequenceKeypoint.new(0.42, Color3.fromRGB(4, 246, 0)), ColorSequenceKeypoint.new(0.65, Color3.fromRGB(0, 221, 255)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(255, 0, 209))}
            end)
        end)
    elseif K == false and PlrTrail then
        PlrTrail:Disconnect()
    end
end)

VelocityGraphToggle = aD:CreateToggle("Velocity Graph", function(K)
    k["Velocity Graph"] = K
    aS.VelocityGraph.Enabled = K
    aP.Visible = K
    spawn(
        function()
            while aS.VelocityGraph.Enabled do
                if aS.VelocityGraph.SmoothMode then
                    d.RenderStepped:Wait()
                else
                    d.RenderStepped:Wait()
                    d.RenderStepped:Wait()
                end
                    aL = workspace.CurrentCamera.ViewportSize.Y - 100
                    aQ.Position =
                        Vector2.new(
                        workspace.CurrentCamera.ViewportSize.X / 2,
                        workspace.CurrentCamera.ViewportSize.Y - 70
                    )
                    aR.Position =
                        Vector2.new(
                        workspace.CurrentCamera.ViewportSize.X / 2,
                        workspace.CurrentCamera.ViewportSize.Y - 50
                    )
                    aP.Position =
                        Vector2.new(
                        workspace.CurrentCamera.ViewportSize.X / 2,
                        workspace.CurrentCamera.ViewportSize.Y - 90
                    )
                if g.Character and g.Character.PrimaryPart then
                    if #aK >= 1 then
                        local M = 100
                        if #aK >= M then
                            aK[1]:Remove()
                            local aT = 0
                            for B = 2, 6 do
                                aT = aT + 1.8
                                aK[B].Transparency = 1 - aT / 10
                            end
                            aK[2].Transparency = 0.1
                            aK[3].Transparency = 0.2
                            aK[4].Transparency = 0.4
                            aK[5].Transparency = 0.6
                            aK[6].Transparency = 0.8
                            table.remove(aK, 1)
                        end
                        for B, C in ipairs(aK) do
                            C.To = C.To - Vector2.new(2, 0)
                            C.From = C.From - Vector2.new(2, 0)
                        end
                    end
                    local aU = (g.Character.PrimaryPart.Velocity * Vector3.new(1, 0, 1)).magnitude
                    local aV = aU * 14.85
                    if aV > 300 then
                        aV = 300
                    end
                    aP.Color = Color3.new(1, 1, 1)
                    if math.floor(aU) < aN then
                        aP.Color = Color3.new(1, 0.5, 0.3)
                    end
                    if math.floor(aU) > aN then
                        aP.Color = Color3.new(0.5, 1, 0.3)
                    end
                    if math.floor(aV) == 300 then
                        aP.Color = Color3.new(1, 0.3, 0.1)
                    end
                    local aW = Color3.new(1, 1, 1)
                    if aS.VelocityGraph.Color == "Rainbow" then
                        aW = Color3.fromHSV(tick() % 5 / 5, 1, 1)
                    elseif aS.VelocityGraph.Color == "Trans" then
                        aW = aO[aS.VelocityGraph.TransCount]
                        aS.VelocityGraph.DebounceCount =
                            aS.VelocityGraph.DebounceCount == 5 and 0 or aS.VelocityGraph.DebounceCount + 1
                    if aS.VelocityGraph.DebounceCount == 0 then
                        aS.VelocityGraph.TransCount =
                        aS.VelocityGraph.TransCount == #aO and 1 or aS.VelocityGraph.TransCount + 1
                        end
                    end
                    local aX = Drawing.new("Line")
                    table.insert(aK, aX)
                    aX.Color = aW
                    aX.Thickness = 1
                    aX.From = Vector2.new(workspace.CurrentCamera.ViewportSize.X / 2 + 98, aM)
                    aX.To = Vector2.new(workspace.CurrentCamera.ViewportSize.X / 2 + 100, aL - aV / 6.5)
                    aX.Transparency = 0
                    aX.Visible = true
                    if #aK >= 8 then
                        aK[#aK - 1].Transparency = aK[#aK - 1].Transparency + 0.2
                        aK[#aK - 2].Transparency = aK[#aK - 2].Transparency + 0.2
                        aK[#aK - 3].Transparency = aK[#aK - 3].Transparency + 0.2
                        aK[#aK - 4].Transparency = aK[#aK - 4].Transparency + 0.2
                        aK[#aK - 5].Transparency = aK[#aK - 5].Transparency + 0.2
                        aK[#aK - 7].Transparency = 1
                    end
                    aP.Text = tostring(math.floor(aV))
                    aM = aL - aV / 6.5
                    aN = math.floor(aU)
                end
            end
        end)
    for B, C in next, aK do
        C:Remove()
    end
    aK = {}
end)

SmoothVelocityGraph = aD:CreateToggle("Smoother Graph", function(K)
    k["Smoother Graph"] = K
    aS.VelocityGraph.SmoothMode = K
end)

SmoothVelocityGraph = aD:CreateDropdown("Graph Color", {"Rainbow", "Trans", "Normal"}, function(K)
    k["Graph Color"] = K
    aS.VelocityGraph.TransCount = 1
    aS.VelocityGraph.Color = K
end)

------------------------------------ CONFIGS ------------------------------------
aF:CreateLabel("Cfg")

configName = aF:Textbox("Config name")

Config = aF:CreateDropdown("Config", listfiles("pepsi"), function(bI)
    k.Config = bI
end)

createConfig = aF:CreateButton("Create config", function()
    local bM = {}
    for B, C in next, l.options do
        if l.options[B].Type == "KeyBind" then
            bM[B] = tostring(k[B])
        else
            bM[B] = k[B]
        end
    end
    writefile("pepsi\\" .. configName.Text .. ".pepsi", c:JSONEncode(bM))
    l.options.Config.updateList(listfiles("pepsi"))
end)

saveConfig = aF:CreateButton("Save config", function()
    local bM = {}
    if isfile(k.Config) then
        for B, C in next, l.options do
            if l.options[B].Type == "KeyBind" then
                bM[B] = tostring(k[B])
            else
                bM[B] = k[B]
            end
        end
        writefile(k.Config, c:JSONEncode(bM))
    end
    l.options.Config.updateList(listfiles("pepsi"))
end)

loadConfig = aF:CreateButton("Load config", function()
    if isfile(k.Config) then
        for B, C in next, c:JSONDecode(readfile(k.Config)) do
            if l.options[B] then
                local bN = l.options[B].Type
                if bN == "Toggle" and k[B] ~= C then
                    l.options[B].toggleFunction()
                elseif bN == "Slider" or bN == "Dropdown" then
                    l.options[B].changeValue(C)
                elseif bN == "Keybind" then
                    local bO = "return " .. C
                    l.options[B].changeValue(loadstring(bO)())
                end
            end
        end
    end
    l.options.Config.updateList(listfiles("pepsi"))
end)

refreshConfigs = aF:CreateButton("Refresh configs", function()
    l.options.Config.updateList(listfiles("pepsi"))
end)

------------------------------------ MISC ------------------------------------
aE:CreateLabel("UI")

aE:CreateToggle("Watermark", function(K)
    if K == true then
        local watermark = Instance.new("ScreenGui")
        local ScreenLabel = Instance.new("Frame")
        local Color = Instance.new("Frame")
        local UIGradient = Instance.new("UIGradient")
        local Container = Instance.new("Frame")
        local UIPadding = Instance.new("UIPadding")
        local Text = Instance.new("TextLabel")
        local Background = Instance.new("Frame")
        local UIGradient_2 = Instance.new("UIGradient")

        watermark.Name = "watermark"
        watermark.Parent = game.CoreGui

        ScreenLabel.Name = "ScreenLabel"
        ScreenLabel.Parent = watermark
        ScreenLabel.BackgroundColor3 = Color3.fromRGB(28, 28, 28)
        ScreenLabel.BackgroundTransparency = 1.000
        ScreenLabel.BorderColor3 = Color3.fromRGB(20, 20, 20)
        ScreenLabel.Position = UDim2.new(0, 12, 0, 7)
        ScreenLabel.Size = UDim2.new(0, 260, 0, 20)

        Color.Name = "Color"
        Color.Parent = ScreenLabel
        Color.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
        Color.BorderSizePixel = 0
        Color.Size = UDim2.new(1.25, 0, 0, 2)
        Color.ZIndex = 2

        UIGradient.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(255, 255, 255)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(60, 60, 60))}
        UIGradient.Rotation = 90
        UIGradient.Parent = Color

        Container.Name = "Container"
        Container.Parent = ScreenLabel
        Container.BackgroundTransparency = 1.000
        Container.BorderSizePixel = 0
        Container.Position = UDim2.new(0, 0, 0, 4)
        Container.Size = UDim2.new(1, 0, 0, 14)
        Container.ZIndex = 3

        UIPadding.Parent = Container
        UIPadding.PaddingLeft = UDim.new(0, 4)

        Text.Name = "Text"
        Text.Parent = Container
        Text.BackgroundTransparency = 1.000
        Text.Position = UDim2.new(0.0230769236, 0, 0, 0)
        Text.Size = UDim2.new(1, 0, 1, 0)
        Text.ZIndex = 4
        Text.Font = Enum.Font.RobotoMono
        Text.Text = "Internal.move | 00:00:00  | Oct. 17, 2021"
        Text.TextColor3 = Color3.fromRGB(65025, 65025, 65025)
        Text.TextSize = 14.000
        Text.TextStrokeTransparency = 0.000
        Text.TextXAlignment = Enum.TextXAlignment.Left

        Background.Name = "Background"
        Background.Parent = ScreenLabel
        Background.BackgroundColor3 = Color3.fromRGB(23, 23, 23)
        Background.BorderColor3 = Color3.fromRGB(20, 20, 20)
        Background.Size = UDim2.new(1.25, 0, 1, 0)

        UIGradient_2.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(255, 255, 255)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(90, 90, 90))}
        UIGradient_2.Rotation = 90
        UIGradient_2.Parent = Background

        local function UQHM_fake_script() -- Text.LocalScript 
            local script = Instance.new('LocalScript', Text)
            
            local mo = "A.M."
            local mont = nil
            while wait() do
                local l = math.fmod(tick(),86400)
                local h = math.floor(l/3600)
                local m = math.floor(l/60-h*60)
                local s = math.floor(math.fmod(l,60))
                local y = math.floor(1970+tick()/31579200)
                local mon = {{"January",31,31},{"February",59,28},{"March",90,31},{"April",120,30},{"May",151,31},{"June",181,30},{"July",212,31},{"August",243,31},{"September",273,30},{"October",304,31},{"November",334,30},{"December",365,31}}
                if y%4 == 0 then
                    mon[2][3] = 29
                    for i,v in pairs(mon) do
                        if i ~= 1 then
                            v[2] = v[2] + 1
                        end
                    end
                end
                local d = math.floor(tick()/86400%365.25+1)
                for i,v in pairs(mon) do
                    if v[2]-v[3]<=d then
                        mont = i
                    end
                end
                d = d + mon[mont][3]-mon[mont][2]
                if m <= 9 then
                    m = "0" ..m
                end
                if s <= 9 then
                    s = "0" ..s
                end
                if h >= 12 then
                    mo = "P.M."
                else
                    mo = "A.M."
                end
                if h > 12 then
                    h = h - 12
                end
                script.Parent.Text = "Internal| " ..h.. ":" ..m.. ":" ..s.. " " ..mo.. " | " ..mon[mont][1].. " " ..d.. ", " ..y
            end
        end

        coroutine.wrap(UQHM_fake_script)()
        local function QQXIOK_fake_script() -- ScreenLabel.LocalScript 
            local script = Instance.new('LocalScript', ScreenLabel)
            
            local gui = script.Parent
            gui.Draggable = true
            gui.Active = true
        end
        coroutine.wrap(QQXIOK_fake_script)()
    elseif K == false then
        game.CoreGui.watermark:Destroy()
    end
end)

aE:CreateToggle("Spectator List", function(K)
    if K ==  true then
        local SpectatorsList = Instance.new("ScreenGui")
        local Spectators = Instance.new("Frame")
        local Container = Instance.new("Frame")
        local UIPadding = Instance.new("UIPadding")
        local Text = Instance.new("TextLabel")
        local Players = Instance.new("TextLabel")
        local Background = Instance.new("Frame")
        local UIGradient = Instance.new("UIGradient")
        local Color = Instance.new("Frame")
        local UIGradient_2 = Instance.new("UIGradient")

        SpectatorsList.Parent = game.CoreGui
        SpectatorsList.Name = "SpectatorsList"
        SpectatorsList.Enabled = true

        Spectators.Name = "Spectators"
        Spectators.Parent = SpectatorsList
        Spectators.BackgroundColor3 = Color3.fromRGB(23, 23, 23)
        Spectators.BackgroundTransparency = 1.000
        Spectators.BorderColor3 = Color3.fromRGB(20, 20, 20)
        Spectators.Position = UDim2.new(0.00800000038, 0, 0.400000006, 49)
        Spectators.Size = UDim2.new(0, 200, 0, 20)

        Container.Name = "Container"
        Container.Parent = Spectators
        Container.BackgroundTransparency = 1.000
        Container.BorderSizePixel = 0
        Container.Position = UDim2.new(0, 0, 0, 4)
        Container.Size = UDim2.new(1, 0, 0, 14)
        Container.ZIndex = 3

        UIPadding.Parent = Container
        UIPadding.PaddingLeft = UDim.new(0, 4)

        Text.Name = "Text"
        Text.Parent = Container
        Text.BackgroundTransparency = 1.000
        Text.Size = UDim2.new(1, 0, 1, 0)
        Text.ZIndex = 4
        Text.Font = Enum.Font.Code
        Text.Text = "Spectators"
        Text.TextColor3 = Color3.fromRGB(65025, 65025, 65025)
        Text.TextSize = 14.000
        Text.TextStrokeTransparency = 0.000

        Players.Name = "Players"
        Players.Parent = Container
        Players.BackgroundTransparency = 1.000
        Players.Position = UDim2.new(0.0196080022, 0, 1.14285719, 0)
        Players.Size = UDim2.new(0.980391979, 0, 1.14285719, 0)
        Players.ZIndex = 4
        Players.Font = Enum.Font.Code
        Players.Text = "loading..."
        Players.TextColor3 = Color3.fromRGB(65025, 65025, 65025)
        Players.TextSize = 14.000
        Players.TextStrokeTransparency = 0.000
        Players.TextYAlignment = Enum.TextYAlignment.Top

        Background.Name = "Background"
        Background.Parent = Spectators
        Background.BackgroundColor3 = Color3.fromRGB(23, 23, 23)
        Background.BorderColor3 = Color3.fromRGB(20, 20, 20)
        Background.Size = UDim2.new(1, 0, 1, 0)

        UIGradient.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(255, 255, 255)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(90, 90, 90))}
        UIGradient.Rotation = 90
        UIGradient.Parent = Background

        Color.Name = "Color"
        Color.Parent = Spectators
        Color.BackgroundColor3 = Color3.fromRGB(255, 0, 0)
        Color.BorderSizePixel = 0
        Color.Size = UDim2.new(1, 0, 0, 2)
        Color.ZIndex = 2

        UIGradient_2.Color = ColorSequence.new{ColorSequenceKeypoint.new(0.00, Color3.fromRGB(255, 255, 255)), ColorSequenceKeypoint.new(1.00, Color3.fromRGB(60, 60, 60))}
        UIGradient_2.Rotation = 90
        UIGradient_2.Parent = Color

        function GetSpectators()
            local CurrentSpectators = ""
            for i,v in pairs(game.Players:GetChildren()) do 
                pcall(function()
                    if v ~= game.Players.LocalPlayer then
                        if not v.Character then 
                            if (v.CameraCF.Value.p - game.Workspace.CurrentCamera.CFrame.p).Magnitude < 10 then 
                                if CurrentSpectators == "" then
                                        CurrentSpectators = v.Name
                                    else
                                        CurrentSpectators = CurrentSpectators.. "\n" ..v.Name
                                    end
                                end
                            end
                        end
                    end)
                end
            return CurrentSpectators
        end

        spawn(function()
            while wait(0.1) do
                if SpectatorsList.Enabled then
                    Players.Text = GetSpectators()
                end
            end
        end)
    
        local function SCUAM_fake_script() -- Spectators.LocalScript 
            local script = Instance.new('LocalScript', Spectators)
            local gui = script.Parent
            gui.Draggable = true
            gui.Active = true
        end
        coroutine.wrap(SCUAM_fake_script)()
    
    elseif K ==  false then
        game.CoreGui.SpectatorsList:Destroy()
    end
end)

oldSounds = {}
for B, C in next, game.Players.LocalPlayer.PlayerGui.Music:GetDescendants() do
    if C:IsA("Sound") then
        if C.Name == "Lose" then
            oldSounds["Lose"] = C.SoundId
        elseif C.Name == "Win" then
            oldSounds["Win"] = C.SoundId
        elseif C.Name == "Bomb" then
            oldSounds["Bomb"] = C.SoundId
        elseif C.Name == "1" then
            if C.Parent.Name == "StartRound" then
                oldSounds["StartRound"] = C.SoundId
            end
        end
    end
end

aE:CreateLabel("Other")

aE:CreateToggle("Splatoon sound effects", function(K)
    k["Splatoon sound effects"] = K
    for B, C in next, game.Players.LocalPlayer.PlayerGui.Music:GetDescendants() do
        if C:IsA("Sound") then
            if C.Name == "Lose" then
                C.SoundId = K and "rbxassetid://5566798757" or oldSounds["Lose"]
            elseif C.Name == "Win" then
                C.SoundId = K and "rbxassetid://5566793224" or oldSounds["Win"]
            elseif C.Name == "Bomb" then
                C.SoundId = K and "rbxassetid://444115590" or oldSounds["Bomb"]
            elseif C.Name == "1" then
                if C.Parent.Name == "StartRound" then
                    C.SoundId = K and "rbxassetid://5566732319" or oldSounds["StartRound"]
                else
                    C.SoundId = "rbxassetid://"
                end
            end
        end
    end
end)

aE:CreateToggle("Headless horseman", function(K)
    k["Headless horseman"] = K
end)

aE:CreateToggle("Kill All", function(K)
    if K then
        KillAllLoop = game:GetService("RunService").RenderStepped:Connect(function()
            pcall(function()
                for i,v in pairs(game.Players:GetChildren()) do
					if v.Character and v.Character.Humanoid.Health > 0 and game.Players.LocalPlayer.Character.EquippedTool and v.Team ~= game.Players.LocalPlayer.Team then
						local Arguments = {
							[1] = v.Character.Head,
							[2] = v.Character.Head.Position,
							[3] = game.Players.LocalPlayer.Character.EquippedTool.Value,
							[4] = 100,
							[5] = game.Players.LocalPlayer.Character.Gun,
							[8] = 10, -- Damage Multiplier
							[9] = false,
							[10] = false, -- Is Wallbang
							[11] = Vector3.new(),
							[12] = 100,
							[13] = Vector3.new()
						}
						game.ReplicatedStorage.Events.HitPart:FireServer(unpack(Arguments))
					end
				end
			end)
		end)
	else
		KillAllLoop:Disconnect()
	end
end)

aE:CreateToggle("Anti Kick", function(K)
    if K == true then
        game.ReplicatedStorage.Events.SendMsg.OnClientEvent:Connect(function(message)
            local msg = string.split(message, " ")
            if game.Players:FindFirstChild(msg[1]) and msg[7] == "1" and msg[12] == game.Players.LocalPlayer.Name then
                game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, game.JobId, LocalPlayer)
            end
        end)
    end
end)

OldGunSounds = aE:CreateToggle("Old Gun Sounds", function(K)
if K == true then
    OldSounds = game:GetService("RunService").RenderStepped:Connect(function()
        pcall(function()
            if g.Character.EquippedTool.Value == "AK47" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://1112730119"
            end
            if g.Character.EquippedTool.Value == "M4A1" then
                g.Character.Gun.SShoot.SoundId = "rbxassetid://1665639883"
                g.Character.Gun.Shoot.SoundId = "rbxassetid://2515498997"
            end
            if g.Character.EquippedTool.Value == "Glock" then
				g.Character.Gun.Shoot.SoundId = "rbxassetid://1112951656"
			end
			if g.Character.EquippedTool.Value == "Galil" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://344800912"
			end
			if g.Character.EquippedTool.Value == "USP" then
                g.Character.Gun.SShoot.SoundId = "rbxassetid://1112952739"
                g.Character.Gun.Shoot.SoundId = "rbxassetid://2515499360"
			end
			if g.Character.EquippedTool.Value == "P2000" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://263589107"
            end
            if  g.Character.EquippedTool.Value == "P250" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://340365431"
            end
            if g.Character.EquippedTool.Value == "DesertEagle" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://202918645"
            end
            if g.Character.EquippedTool.Value == "MP9" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://222888810"
            end
            if g.Character.EquippedTool.Value == "UMP" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://206953341"
            end
            if g.Character.EquippedTool.Value == "Famas" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://206953280"
            end
            if g.Character.EquippedTool.Value == "Scout" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://1112858108"
            end
            if g.Character.EquippedTool.Value == "AUG" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://515215839"
            end
            if g.Character.EquippedTool.Value == "AWP" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://202918637"
            end
            if g.Character.EquippedTool.Value == "G3SG1" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://340365815"
            end
            if g.Character.EquippedTool.Value == "SG" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://347270113"
            end
            if g.Character.EquippedTool.Value == "M4A4" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://202918741"
            end
          	if g.Character.EquippedTool.Value == "Tec9" then
                g.Character.Gun.Shoot.SoundId = "rbxassetid://206953317"
                end
            end)
        end)
    elseif K == false then
        OldSounds:Disconnect()
    end
end)

aE:CreateButton("Remove Textures", function()
    workspace:FindFirstChildOfClass('Terrain').WaterWaveSize = 0
    workspace:FindFirstChildOfClass('Terrain').WaterWaveSpeed = 0
    workspace:FindFirstChildOfClass('Terrain').WaterReflectance = 0
	workspace:FindFirstChildOfClass('Terrain').WaterTransparency = 0
	for i,v in pairs(game:GetDescendants()) do
		if v:IsA("Part") or v:IsA("UnionOperation") or v:IsA("MeshPart") or v:IsA("CornerWedgePart") or v:IsA("TrussPart") then
			v.Material = "Plastic"
			v.Reflectance = 0
		elseif v:IsA("Decal") then
			v.Transparency = 1
		elseif v:IsA("Explosion") then
			v.BlastPressure = 1
			v.BlastRadius = 1
		end
	end
end)

aE:CreateToggle("Remove Killers", function(K)
    pcall(function()
        local Clips = workspace.Map.Clips; Clips.Name = "FAT"; Clips.Parent = nil
        local Killers = workspace.Map.Killers; Killers.Name = "FAT"; Killers.Parent = nil
        if K == true then
		    for i,v in pairs(Clips:GetChildren()) do
				if v:IsA("BasePart") then
					v:Remove()
				end
			end
			for i,v in pairs(Killers:GetChildren()) do
				if v:IsA("BasePart") then
					v:Remove()
				end
			end
		end
		Killers.Name = "Killers"; Killers.Parent = workspace.Map
		Clips.Name = "Clips"; Clips.Parent = workspace.Map
    end)
end)

aE:CreateButton("Rejoin", function()
    game:GetService("TeleportService"):TeleportToPlaceInstance(game.PlaceId, game.JobId, LocalPlayer)
end)

aE:CreateLabel("Damage Bypass")

aE:CreateToggle("No Fall Damage", function(K)
    k["NoFall"] = K
end)

aE:CreateToggle("No Fire Damage", function(K)
    k["NoFire"] = K
end)

aE:CreateLabel("On Hit")

aE:CreateToggle("Hit Sound", function(K)
    if K then
        game.Players.LocalPlayer.Additionals.TotalDamage.Changed:Connect(function()
			if game.Players.LocalPlayer.Additionals.TotalDamage.Value ~= 0 then
				spawn(function()
					local hitsound = Instance.new("Sound")
					hitsound.Parent = game:GetService("SoundService")
					hitsound.SoundId = "rbxassetid://6607339542"
					hitsound.Volume = 5
					hitsound:Play()
				end)
			end
        end)
	else
	    hitsound:Destroy()
    end
end)

aE:CreateToggle("Kill Sound", function(K)
    if K then
        game.Players.LocalPlayer.Status.Kills.Changed:Connect(function(val)
			if val ~= 0 then
				spawn(function()
					local death = Instance.new("Sound")
					death.Parent = game:GetService("SoundService")
					death.SoundId = "rbxassetid://5902468562"
					death.Volume = 4
					death:Play()
				end)
			end
        end)
	else
	    death:Destroy()
    end
end)

aE:CreateToggle("Hit Marker", function(K)
    if K then
        game.Players.LocalPlayer.Additionals.TotalDamage.Changed:Connect(function()
			if game.Players.LocalPlayer.Additionals.TotalDamage.Value ~= 0 then
				spawn(function()
                    local ScreenGui = Instance.new("ScreenGui")
                    local ImageLabel = Instance.new("ImageLabel")
                    ScreenGui.Parent = game.CoreGui
                    ImageLabel.Parent = ScreenGui
                    ImageLabel.BackgroundColor3 = Color3.fromRGB(255, 255, 255)
                    ImageLabel.BackgroundTransparency = 1.000
                    ImageLabel.Size = UDim2.new(0, 200, 0, 200)
                    ImageLabel.Image = "rbxassetid://7746729175"
                    ImageLabel.Visible = true
                    ImageLabel.AnchorPoint = Vector2.new(0.5, 0.6)
                    ImageLabel.Position = UDim2.new(0.5, 1.3, 0.5, 1.3)

                    wait(0.3)
                    ImageLabel.Visible = false
                end)
            else
                ScreenGui:Remove()
			end
        end)
    end
end)

bulletTracers = aE:CreateToggle("Bullet Tracers", function(K)
    if K == true then
        BulletTracersEnabled = true
    elseif K == false then
        BulletTracersEnabled = false
    end
end)
------------------------------------ LUAS. ------------------------------------
aH:CreateLabel("LUAs")

local trannyenabled = false
local socks = false

trannyLua = aH:CreateToggle("Tranny Mode", function(K)
    if K == true then
        trannyenabled = true
        socks = true
    elseif K == false then
        trannyenabled = false
        socks = false
    end
end)

local a = Instance.new("MeshPart",workspace)
a.Size = Vector3.new(1.35,1.4,1.35)
a.CanCollide = false
a.Anchored = true
a.MeshId = "rbxassetid://4249338569"
a.TextureID = "rbxassetid://4249293955"

game:GetService("RunService").RenderStepped:connect(function()
    if game.Players.LocalPlayer.Character and game.Players.LocalPlayer.Character:FindFirstChild("LowerTorso") and trannyenabled then
        a.Position = game.Players.LocalPlayer.Character.LowerTorso.Position
        a.Rotation = game.Players.LocalPlayer.Character.LowerTorso.Rotation
    end
    if socks and game.Players.LocalPlayer.Character then
        if game.Players.LocalPlayer.Character:FindFirstChild("Pants") then
            game.Players.LocalPlayer.Character.Pants.PantsTemplate = "rbxassetid://5381345577"
        end
    end
    a.Transparency = trannyenabled and 0 or 1
end)

aH:CreateLabel("More coming soon.")
------------------------------------ SKINS ------------------------------------
aG:CreateLabel("Knives")

meleeDropdown = aG:CreateDropdown("Custom Melee", {"Shadow Daggers", "Talon", "$19 Fortnite Card", "RemRem", "Skeleton", "Bowie", "Diamond Pickaxe", "Classic"}, function(K)
    if K == "Shadow Daggers" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/deaddigi/pepsi.club/main/skins/shadowdaggers", true))()
    elseif K == "Talon" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/deaddigi/pepsi.club/main/skins/talon", true))()
    elseif K == "$19 Fortnite Card" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/deaddigi/pepsi.club/main/skins/fortnitecard", true))()
    elseif K == "RemRem" then
        loadstring(game:HttpGet("https://pastebin.com/raw/0V9dNtNM", true))()
    elseif K == "Skeleton" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/deaddigi/pepsi.club/main/skins/skeleton", true))()
    elseif K == "Bowie" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/deaddigi/pepsi.club/main/skins/bowie", true))()
    elseif K == "Diamond Pickaxe" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/deaddigi/pepsi.club/main/skins/diamondpickaxe", true))()
    elseif K == "Classic" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/deaddigi/pepsi.club/main/skins/classic", true))()
    end
end)

m9Dropdown = aG:CreateDropdown("M9 Bayonet Skin", {"Vanilla", "Lore", "GammaDoppler2", "GammaDoppler4", "Fade", "Sapphire", "Ruby", "Crimson Web", "Lighting Strike"}, function(K)
    if K == "Vanilla" then
        game.ReplicatedStorage.Weapons.Bayonet.Model.Handle.MeshId = "rbxassetid://6473522916"
        game.ReplicatedStorage.Viewmodels["v_Bayonet"].Handle.MeshId = "rbxassetid://6473522916"
        game.Players.LocalPlayer.PlayerGui.Client.Images["Bayonet"]["Splattered"].Value = "rbxassetid://7874426119"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].WorldModel.Main.Value = "rbxassetid://6355243957"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].Handle.Value = "rbxassetid://6355243957"
    elseif K == "Lore" then
        game.ReplicatedStorage.Weapons.Bayonet.Model.Handle.MeshId = "rbxassetid://6473522916"
        game.ReplicatedStorage.Viewmodels["v_Bayonet"].Handle.MeshId = "rbxassetid://6473522916"
        game.Players.LocalPlayer.PlayerGui.Client.Images["Bayonet"]["Splattered"].Value = "rbxassetid://7874426119"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].WorldModel.Main.Value = "rbxassetid://6355247035"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].Handle.Value = "rbxassetid://6355247035"
    elseif K == "GammaDoppler2" then
        game.ReplicatedStorage.Weapons.Bayonet.Model.Handle.MeshId = "rbxassetid://6473522916"
        game.ReplicatedStorage.Viewmodels["v_Bayonet"].Handle.MeshId = "rbxassetid://6473522916"
        game.Players.LocalPlayer.PlayerGui.Client.Images["Bayonet"]["Splattered"].Value = "rbxassetid://7874426119"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].WorldModel.Main.Value = "rbxassetid://7891965871"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].Handle.Value = "rbxassetid://7891965871"
    elseif K == "GammaDoppler4" then
        game.ReplicatedStorage.Weapons.Bayonet.Model.Handle.MeshId = "rbxassetid://6473522916"
        game.ReplicatedStorage.Viewmodels["v_Bayonet"].Handle.MeshId = "rbxassetid://6473522916"
        game.Players.LocalPlayer.PlayerGui.Client.Images["Bayonet"]["Splattered"].Value = "rbxassetid://7874426119"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].WorldModel.Main.Value = "rbxassetid://7891968316"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].Handle.Value = "rbxassetid://7891968316"
    elseif K == "Fade" then
        game.ReplicatedStorage.Weapons.Bayonet.Model.Handle.MeshId = "rbxassetid://6473522916"
        game.ReplicatedStorage.Viewmodels["v_Bayonet"].Handle.MeshId = "rbxassetid://6473522916"
        game.Players.LocalPlayer.PlayerGui.Client.Images["Bayonet"]["Splattered"].Value = "rbxassetid://7874426119"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].WorldModel.Main.Value = "rbxassetid://6355237475"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].Handle.Value = "rbxassetid://6355237475"
    elseif K == "Sapphire" then
        game.ReplicatedStorage.Weapons.Bayonet.Model.Handle.MeshId = "rbxassetid://6473522916"
        game.ReplicatedStorage.Viewmodels["v_Bayonet"].Handle.MeshId = "rbxassetid://6473522916"
        game.Players.LocalPlayer.PlayerGui.Client.Images["Bayonet"]["Splattered"].Value = "rbxassetid://7874426119"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].WorldModel.Main.Value = "rbxassetid://6355236981"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].Handle.Value = "rbxassetid://6355236981"
    elseif K == "Ruby" then
        game.ReplicatedStorage.Weapons.Bayonet.Model.Handle.MeshId = "rbxassetid://6473522916"
        game.ReplicatedStorage.Viewmodels["v_Bayonet"].Handle.MeshId = "rbxassetid://6473522916"
        game.Players.LocalPlayer.PlayerGui.Client.Images["Bayonet"]["Splattered"].Value = "rbxassetid://7874426119"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].WorldModel.Main.Value = "rbxassetid://6355236588"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].Handle.Value = "rbxassetid://6355236588"
    elseif K == "Crimson Web" then
        game.ReplicatedStorage.Weapons.Bayonet.Model.Handle.MeshId = "rbxassetid://6473522916"
        game.ReplicatedStorage.Viewmodels["v_Bayonet"].Handle.MeshId = "rbxassetid://6473522916"
        game.Players.LocalPlayer.PlayerGui.Client.Images["Bayonet"]["Splattered"].Value = "rbxassetid://7874426119"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].WorldModel.Main.Value = "rbxassetid://6355235916"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].Handle.Value = "rbxassetid://6355235916"
    elseif K == "Lighting Strike" then
        game.ReplicatedStorage.Weapons.Bayonet.Model.Handle.MeshId = "rbxassetid://6473522916"
        game.ReplicatedStorage.Viewmodels["v_Bayonet"].Handle.MeshId = "rbxassetid://6473522916"
        game.Players.LocalPlayer.PlayerGui.Client.Images["Bayonet"]["Splattered"].Value = "rbxassetid://7874426119"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].WorldModel.Main.Value = "rbxassetid://6355234343"
        game.ReplicatedStorage.Skins["Bayonet"]["Splattered"].Handle.Value = "rbxassetid://6355234343"
    end
end)

otherDropdown = aG:CreateDropdown("Other", {"Reset Viewmodels", "Unlock Inv"}, function(K)
    if K == "Reset Viewmodels" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/deaddigi/pepsi.club/main/skins/resetviewmodels", true))()
    elseif K == "Unlock Inv" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/6segs/millionware/main/inv", true))()
    end
end)

--[[
    M9Toggle = aG:CreateToggle("M9 Bayonet", function(K)
        k["M9 Bayonet"] = K
        aS.M9.Enabled = K
        spawn(
            function()
                while aS.M9.Enabled do
                    d.RenderStepped:Wait()
                    pcall(
                        function()
                            if
                                g.Character and g.Character:FindFirstChild("EquippedTool") and
                                    game.ReplicatedStorage.Weapons:FindFirstChild(g.Character.EquippedTool.Value):FindFirstChild(
                                        "Melee"
                                    ) and
                                    workspace.Camera:FindFirstChild("Arms") and
                                    workspace.Camera.Arms:FindFirstChild("Handle2")
                                then
                                    workspace.Camera.Arms.Handle.MeshId = "rbxassetid://5524010796"
                                    workspace.Camera.Arms.Handle.TextureID = "rbxassetid://5521767392"
                                end
                        end)
                    end
            end)
    end)
--]]

unlockInv = aG:CreateButton("Bayonet", function()
    local bK = "v_Bayonet"
    for bv, C in pairs(game:GetDescendants()) do
        if C.Name == "v_T Knife" or C.Name == "v_CT Knife" then
            C.Name = "hdf"
        end
    end
    local bj = game.ReplicatedStorage.Viewmodels[bK]
    bj:Clone().Parent = game.ReplicatedStorage.Viewmodels
    local bL = bj:Clone()
    local bh = bj:Clone()
    bL.Name = "v_CT Knife"
    bh.Name = "v_T Knife"
    bL.Parent = game.ReplicatedStorage.Viewmodels
    bh.Parent = game.ReplicatedStorage.Viewmodels
end)

aG:CreateLabel("Arms")

armsDropdown = aG:CreateDropdown("Arms", {"Anarchia", "Snake", "Steve"}, function(K)
    if K == "Anarchia" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/deaddigi/pepsi.club/main/skins/anarchiaarms", true))()
    elseif K == "Snake" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/deaddigi/pepsi.club/main/skins/snakearms", true))()
    elseif K == "Steve" then
        loadstring(game:HttpGet("https://raw.githubusercontent.com/deaddigi/pepsi.club/main/skins/stevearms", true))()
    end
end)

removeSleeves = aG:CreateToggle("Remove Sleeves", function(K)
    if K == true then
		game.ReplicatedStorage.Viewmodels.GIGNArms["Left Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.GIGNArms["Right Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.SASArms["Left Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.SASArms["Right Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.IDFArms["Left Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.IDFArms["Right Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.UTArms["Left Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.UTArms["Right Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.BDSArms["Left Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.BDSArms["Right Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.GSGArms["Left Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.GSGArms["Right Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.SPArms["Left Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.SPArms["Right Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.WDArms["Left Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.WDArms["Right Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.AAArms["Left Arm"].Sleeve.Transparency = 1
		game.ReplicatedStorage.Viewmodels.AAArms["Right Arm"].Sleeve.Transparency = 1
	elseif K == false then
		game.ReplicatedStorage.Viewmodels.GIGNArms["Left Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.GIGNArms["Right Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.SASArms["Left Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.SASArms["Right Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.IDFArms["Left Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.IDFArms["Right Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.UTArms["Left Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.UTArms["Right Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.BDSArms["Left Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.BDSArms["Right Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.GSGArms["Left Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.GSGArms["Right Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.SPArms["Left Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.SPArms["Right Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.WDArms["Left Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.WDArms["Right Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.AAArms["Left Arm"].Sleeve.Transparency = 0
		game.ReplicatedStorage.Viewmodels.AAArms["Right Arm"].Sleeve.Transparency = 0
	end
end)

removeGloves = aG:CreateToggle("Remove Gloves", function(K)
	if K == true then
		game.ReplicatedStorage.Viewmodels.ECArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.ECArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.GIGNArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.GIGNArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.SASArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.SASArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.IDFArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.IDFArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.UTArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.UTArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.GCTArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.GCTArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.PCArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.PCArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.BDSArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.BDSArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.GSGArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.GSGArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.SPArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.SPArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.WDArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.WDArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.GTArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.GTArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.PTArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.PTArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.AAArms["Left Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Viewmodels.AAArms["Right Arm"].Glove.Transparency = 1
		game.ReplicatedStorage.Gloves.Models["Sports Glove"].LGlove.Transparency = 1
		game.ReplicatedStorage.Gloves.Models["Sports Glove"].RGlove.Transparency = 1
		game.ReplicatedStorage.Gloves.Models["Handwraps"].LGlove.Transparency = 1
		game.ReplicatedStorage.Gloves.Models["Handwraps"].RGlove.Transparency = 1
		game.ReplicatedStorage.Gloves.Models["Fingerless Glove"].LGlove.Transparency = 1
		game.ReplicatedStorage.Gloves.Models["Fingerless Glove"].RGlove.Transparency = 1
		game.ReplicatedStorage.Gloves.Models["Strapped Glove"].LGlove.Transparency = 1
		game.ReplicatedStorage.Gloves.Models["Strapped Glove"].RGlove.Transparency = 1
	elseif K == false then
		game.ReplicatedStorage.Viewmodels.ECArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.ECArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.GIGNArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.GIGNArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.SASArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.SASArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.IDFArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.IDFArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.UTArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.UTArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.GCTArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.GCTArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.PCArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.PCArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.BDSArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.BDSArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.GSGArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.GSGArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.SPArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.SPArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.WDArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.WDArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.GTArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.GTArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.PTArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.PTArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.AAArms["Left Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Viewmodels.AAArms["Right Arm"].Glove.Transparency = 0
		game.ReplicatedStorage.Gloves.Models["Sports Glove"].LGlove.Transparency = 0
		game.ReplicatedStorage.Gloves.Models["Sports Glove"].RGlove.Transparency = 0
		game.ReplicatedStorage.Gloves.Models["Handwraps"].LGlove.Transparency = 0
		game.ReplicatedStorage.Gloves.Models["Handwraps"].RGlove.Transparency = 0
		game.ReplicatedStorage.Gloves.Models["Fingerless Glove"].LGlove.Transparency = 0
		game.ReplicatedStorage.Gloves.Models["Fingerless Glove"].RGlove.Transparency = 0
		game.ReplicatedStorage.Gloves.Models["Strapped Glove"].LGlove.Transparency = 0
		game.ReplicatedStorage.Gloves.Models["Strapped Glove"].RGlove.Transparency = 0
	end
end)

aG:CreateLabel("Custom Skin")

awpSkin = aG:CreateDropdown("AWP Skin", {"Neo-Noir", "Gugnir", "Hyper Beast", "Dragon Lore", "Atheris", "Asiimov"}, function(K)
    if K == "Neo-Noir" then
        game.ReplicatedStorage.Viewmodels["v_AWP"].Handle.TextureID = "rbxassetid://6585612923"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Scope.TextureID = "rbxassetid://6559601090"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Mag.TextureID = "rbxassetid://6585612923"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Slide.TextureID = "rbxassetid://6585612923"
        game.ReplicatedStorage.Viewmodels["v_AWP"]["Slide 2"].TextureID = "rbxassetid://6585612923"
    elseif K == "Gugnir" then
        game.ReplicatedStorage.Viewmodels["v_AWP"].Handle.TextureID = "rbxassetid://6559063434"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Scope.TextureID = "rbxassetid://6561080965"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Mag.TextureID = "rbxassetid://2471931220"
    elseif K == "Hyper Beast" then
        game.ReplicatedStorage.Viewmodels["v_AWP"].Handle.TextureID = "rbxassetid://6585630605"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Scope.TextureID = "rbxassetid://6585630875"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Mag.TextureID = "rbxassetid://6585630605"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Slide.TextureID = "rbxassetid://6585630605"
        game.ReplicatedStorage.Viewmodels["v_AWP"]["Slide 2"].TextureID = "rbxassetid://6585630605"
    elseif K == "Dragon Lore" then
        game.ReplicatedStorage.Viewmodels["v_AWP"].Handle.TextureID = "rbxassetid://6451539744"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Scope.TextureID = "rbxassetid://6451541040"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Mag.TextureID = "rbxassetid://2471931220"
    elseif K == "Atheris" then
        game.ReplicatedStorage.Viewmodels["v_AWP"].Handle.TextureID = "rbxassetid://6580844725"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Scope.TextureID = "rbxassetid://6580845315"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Mag.TextureID = "rbxassetid://6580844725"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Slide.TextureID = "rbxassetid://6580844725"
        game.ReplicatedStorage.Viewmodels["v_AWP"]["Slide 2"].TextureID = "rbxassetid://6580844725"
    elseif K == "Asiimov" then
        game.ReplicatedStorage.Viewmodels["v_AWP"].Handle.TextureID = "rbxassetid://6581974020"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Scope.TextureID = "rbxassetid://6581974687"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Mag.TextureID = "rbxassetid://6581974020"
        game.ReplicatedStorage.Viewmodels["v_AWP"].Slide.TextureID = "rbxassetid://6581974020"
        game.ReplicatedStorage.Viewmodels["v_AWP"]["Slide 2"].TextureID = "rbxassetid://6581974020"
    end
end)

deagleSkin = aG:CreateDropdown("Deagle Skin", {"City", "Code Red", "Printstream"}, function(K)
    if K == "City" then
        game.ReplicatedStorage.Viewmodels["v_DesertEagle"].Handle.TextureID = "rbxassetid://6458222794"
        game.ReplicatedStorage.Viewmodels["v_DesertEagle"].Mag.TextureID = "rbxassetid://6458222794"
        game.ReplicatedStorage.Viewmodels["v_DesertEagle"].Slide.TextureID = "rbxassetid://6458222794"
    elseif K == "Code Red" then
        game.ReplicatedStorage.Viewmodels["v_DesertEagle"].Handle.TextureID = "rbxassetid://6451093913"
        game.ReplicatedStorage.Viewmodels["v_DesertEagle"].Mag.TextureID = "rbxassetid://6451093913"
        game.ReplicatedStorage.Viewmodels["v_DesertEagle"].Slide.TextureID = "rbxassetid://6451093913"
    elseif K == "Printstream" then
        game.ReplicatedStorage.Viewmodels["v_DesertEagle"].Handle.TextureID = "rbxassetid://6442505045"
        game.ReplicatedStorage.Viewmodels["v_DesertEagle"].Mag.TextureID = "rbxassetid://6442505045"
        game.ReplicatedStorage.Viewmodels["v_DesertEagle"].Slide.TextureID = "rbxassetid://6451245869"
    end
end)

for B, C in next, game.Players.LocalPlayer.PlayerGui.GUI.SuitZoom:GetDescendants() do
    C.Visible = false
end
for B, C in next, e:GetPlayers() do
    C.CharacterAdded:Connect(
        function(aq)
            wait(1)
            if C ~= g and g.Team ~= C.Team and k["Chams"] then
                chams(C)
            end
        end
    )
end
e.PlayerAdded:Connect(
    function(C)
        C.CharacterAdded:Connect(
            function(aq)
                wait(1)
                if C ~= g and C.Team ~= g.Team and k["Chams"] then
                    chams(C)
                end
            end
        )
    end
)
for B, C in next, game.Teams:GetChildren() do
    C.PlayerAdded:connect(
        function(aq)
            if aq == g then
                ap:ClearAllChildren()
                wait(0.5)
                if k["Chams"] then
                    for B, C in next, e:GetPlayers() do
                        if
                            C ~= g and C.Team ~= g.Team and C.Character and C.Character:FindFirstChild("Humanoid") and
                                C.Character.Humanoid.Health > 0
                         then
                            chams(C)
                        end
                    end
                end
            end
        end
    )
end
spawn(
    function()
        while wait(5) do
            if game.Lighting:FindFirstChild("customsky") then
                game.Lighting.customsky:Destroy()
            end
        end
    end
)
game:GetService("RunService").Stepped:connect(
    function()
        if not game.Lighting:FindFirstChild("customsky") and k["Custom skybox"] then
            local bJ = Instance.new("Sky", game.Lighting)
            bJ.Name = "customsky"
            local a5 = k["Selected skybox"]
            if Skyboxes[a5] then
                for B, C in next, Skyboxes[a5] do
                    game.Lighting.customsky[B] = C
                end
            end
        end
        pcall(
            function()
                if game.Lighting:FindFirstChild("SunRays") then
                    game.Lighting.SunRays.Intensity = k["Nightmode"] and 0 or 0.11
                end
                game.Lighting.TimeOfDay = k["Nightmode"] and 17 or 14
                game.Lighting.FogEnd = k["Fog"] and 175 or 9e9
                if k["Shadows"] then
                    game.Lighting.GlobalShadows = true
                else
                    game.Lighting.GlobalShadows = false
                end
                
                if g.Character and k["Headless horseman"] and g.Character:FindFirstChild("Shirt") then
                    for B, C in next, game.Players.LocalPlayer.Character:GetDescendants() do
                        if
                            C.ClassName == "Accessory" or C.Name == "Shirt" or C.Name == "Pants" or C.Name == "Mesh" or
                                C.Name == "FakeHead" or
                                C.Name == "HeadHB"
                         then
                            C:Destroy()
                        end
                    end
                end
                game.Players.LocalPlayer.PlayerGui.GUI.SuitZoom.Visible = false
                game.Players.LocalPlayer.PlayerGui.GUI.SuitZoom.BackgroundTransparency = 1
            end)
        end)

-- btracers Settings
local Other = {
    Camera = workspace.CurrentCamera,
    BeamPart = Instance.new("Part", workspace)
}

Other.BeamPart.Name = "BeamPart"
Other.BeamPart.Transparency = 1

local Settings = {
    StartColor = Color3.new(1, 1, 1),
    EndColor = Color3.new(1, 0, 0),
    StartWidth = 0.1,
    EndWidth = 0.05,
    ShowImpactPoint = false,
    ImpactTransparency = 0.5,
    ImpactColor = Color3.new(1, 1, 1),
    Time = 1,
}

local funcs = {}

function funcs:Beam(v1, v2)
    local colorSequence = ColorSequence.new({
    ColorSequenceKeypoint.new(0, Settings.StartColor),
    ColorSequenceKeypoint.new(1, Settings.EndColor),
    })
    -- main part
    local Part = Instance.new("Part", Other.BeamPart)
    Part.Size = Vector3.new(1, 1, 1)
    Part.Transparency = 1
    Part.CanCollide = false
    Part.CFrame = CFrame.new(v1)
    Part.Anchored = true
    -- attachment
    local Attachment = Instance.new("Attachment", Part)
    -- part 2
    local Part2 = Instance.new("Part", Other.BeamPart)
    Part2.Size = Vector3.new(1, 1, 1)
    Part2.Transparency = ShowImpactPoint and Settings.ImpactTransparency or 1
    Part2.CanCollide = false
    Part2.CFrame = CFrame.new(v2)
    Part2.Anchored = true
    Part2.Color = Settings.ImpactColor
    -- another attachment
    local Attachment2 = Instance.new("Attachment", Part2)
    -- beam
    local Beam = Instance.new("Beam", Part)
    Beam.FaceCamera = true
    Beam.Color = colorSequence
    Beam.Attachment0 = Attachment
    Beam.Attachment1 = Attachment2
    Beam.LightEmission = 6
    Beam.LightInfluence = 1
    Beam.Width0 = Settings.StartWidth
    Beam.Width1 = Settings.EndWidth
    delay(Settings.Time, function()
    for i = 0.5, 1, 0.02 do
    wait()
    Beam.Transparency = NumberSequence.new(i)
    end
    Part:Destroy()
    Part2:Destroy()
    end)
end

local mt = getrawmetatable(game)
local oldNamecall = mt.__namecall

setreadonly(mt, false)

mt.__namecall = newcclosure(function(self, ...)
    local method = getnamecallmethod()
    local callingscript = getcallingscript()
    local args = {...}
	
	if not checkcaller() then
		if method == "SetPrimaryPartCFrame" and self.Name == "Arms" and ViewmodelEnabled == true then
			args[1] = args[1] * CFrame.new(Vector3.new(math.rad(ViewmodelX-180), math.rad(ViewmodelY-180), math.rad(ViewmodelZ-180)))
		elseif method == "FireServer" and self.Name == "HitPart" then
			spawn(function()
				if BulletTracersEnabled == true then
					local beam = funcs:Beam(game.workspace.Camera.Arms.Flash.CFrame.p, args[2])
				end
			end)
		elseif method == "InvokeServer" and self.Name == "Moolah" then
			return wait(99e99)
		elseif method == "Kick" then
			return
		elseif self.Name == "BURNME" and k["NoFire"] == true then
            return
		elseif self.Name == "FallDamage" and k["NoFall"] == true then
            return
		elseif method == "FireServer" and self.Name == "ControlTurn" and SECHS == true then
			return
		end
	end
    return oldNamecall(self, unpack(args))
end)

oldIndex = hookfunc(getrawmetatable(game.Players.LocalPlayer.PlayerGui.Client).__index, newcclosure(function(self, idx, val)
	if idx == "Value" then
		if (self.Name == "Spread" or self.Parent.Name == "Spread") and k["NoSpread"] == true then
			return 0
		elseif (self.Name == "AccuracyDivisor" or self.Name == "AccuracyOffset") and k["NoSpread"] == true then
			return 0.001
		end
	end
    return oldIndex(self, idx)
end))

    oldNewIndex = hookfunc(getrawmetatable(game.Players.LocalPlayer.PlayerGui.Client).__newindex, newcclosure(function(self, idx, val)
	if not checkcaller() then
		if self.Name == "Crosshair" and idx == "Visible" and val == false and game.Players.LocalPlayer.PlayerGui.GUI.Crosshairs.Scope.Visible == false and ForceCrosshairEnabled == true then
			val = true
		end
	end
	
    return oldNewIndex(self, idx, val)
end))
