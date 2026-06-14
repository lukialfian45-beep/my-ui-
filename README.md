-- ==============================================
-- MUAT WINDUI
-- ==============================================
local Players = game:GetService("Players")
local LocalPlayer = Players.LocalPlayer

local success, WindUI = pcall(function()
    return loadstring(game:HttpGet("https://github.com/Footagesus/WindUI/releases/latest/download/main.lua"))()
end)

if not success or not WindUI then
    warn("❌ Gagal memuat WindUI")
    return
end

-- ==============================================
-- JENDELA UTAMA
-- ==============================================
local Window = WindUI:CreateWindow({
    Title   = "KIRIZ SCRIPT",
    Icon    = "door-open",
    Author  = "by Lvky",
    Folder  = "Kiriz",

    Size            = UDim2.fromOffset(580, 460),
    MinSize         = Vector2.new(560, 350),
    MaxSize         = Vector2.new(850, 560),
    Transparent     = true,
    Theme           = "Dark",
    Resizable       = true,
    SideBarWidth    = 200,
    HideSearchBar   = true,
    ScrollBarEnabled = false,

    BackgroundImageTransparency = 0.40,
    Background = "rbxassetid://1120738435",

    User = {
        Enabled   = true,
        Anonymous = false,
        Name      = LocalPlayer.Name,
        Subtitle  = "Pengguna Aktif",
        Avatar    = "rbxthumb://type=AvatarHeadShot&id="..LocalPlayer.UserId.."&w=150&h=150",
        Callback  = function()
            WindUI:Notify({Title = "Halo!", Content = "Selamat datang "..LocalPlayer.Name.."!"})
        end
    }
})

-- ==============================================
-- POPUP DIPERBAIKI
-- ==============================================
local Popup = WindUI:Popup({
    Title   = "KIRIZ SCRIPT",
    Icon    = "smile",
    Content = "WELCOME TO MY SCRIPT :D",

    -- ✅ PENGATURAN POSISI TENGAH
    TitleAlignment = Enum.TextXAlignment.Center,
    ContentAlignment = Enum.TextXAlignment.Center,

    -- ✅ HANYA SATU TOMBOL CONTINUE, CANCEL DIHAPUS
    Buttons = {
        {
            Title    = "Continue",
            Icon     = "arrow-right",
            Variant  = "Primary",
            Callback = function()
                Popup:Close()
                print("Lanjut ke menu utama")
            end
        }
    }
})