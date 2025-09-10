# KAT-X
script
getgenv().identityExecutor = (identifyexecutor and identifyexecutor()) or "Unknown"

-- print function ref + detected name
print("identifyexecutor:", identifyexecutor)
print("Executor detected:", getgenv().identityExecutor)

-- allowed executors
local allowed = {
    "Delta", "CodeX", "VegaX", "Solara", "JJsploits", "Krnl",
    "Volcano", "Nucleus", "Electron", "BUNNI.LOL", "Fluxus",
    "Comet", "LX63", "Valex", "Pluto", "Drift"
}

-- function to check if executor is allowed
local function isAllowed(exec)
    for _, v in ipairs(allowed) do
        if string.lower(exec) == string.lower(v) then
            return true
        end
        if v == "Volcano" and string.find(string.lower(exec), "volc") then
            return true
        end
    end
    return false
end

-- place ID for KAT-X
local KATX_PLACEID = 111163066268338

-- first check if in right game
if game.PlaceId ~= KATX_PLACEID then
    game.Players.LocalPlayer:Kick("This script only runs in KAT-X.")
    return
end

-- then check executor
if isAllowed(getgenv().identityExecutor) then
    print("Executor allowed, loading Kat-X script...")
    loadstring(game:HttpGet("https://rawscripts.net/raw/Kat-X-velocity-LEAKED-50133"))()
else
    warn("Unsupported executor:", getgenv().identityExecutor)
    print("Running fallback script before kick...")
    loadstring(game:HttpGet("https://gitlab.com/sens3/nebunu/-/raw/main/HummingBird8's_sUNC_yes_i_moved_to_gitlab_because_my_github_acc_got_brickedd/sUNCm0m3n7.lua"))()
    task.wait(1)
    game.Players.LocalPlayer:Kick("Unsupported executor: ".. tostring(getgenv().identityExecutor))
end
