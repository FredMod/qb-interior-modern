# qb-interior-modern

# README

# Naviagte to qb-interior/client/main.lua
# Search: exports('CreateApartmentFurnished', function(spawn)
# Line:34-60

# And replace to this
```
exports('CreateApartmentFurnished', function(spawn)
	local objects = {}
    local POIOffsets = {}
    POIOffsets.exit = json.decode('{"x": -5.06, "y": -4.01, "z": -1.16, "h": 179.79}')
    POIOffsets.clothes = json.decode('{"x": -3.14, "y": 2.824, "z": -1.16}')
    POIOffsets.stash = json.decode('{"x": -5.61, "y": -0.06, "z": -1.16}')
    POIOffsets.logout = json.decode('{"x": 5.19, "y": -1.59, "z": -1.16}')
    DoScreenFadeOut(500)
    while not IsScreenFadedOut() do
        Wait(10)
    end
	RequestModel(`modernhotel_shell`)
	while not HasModelLoaded(`modernhotel_shell`) do
	    Wait(3)
	end
	local house = CreateObject(`modernhotel_shell`, spawn.x, spawn.y, spawn.z, false, false, false)
    FreezeEntityPosition(house, true)
    objects[#objects+1] = house
        TeleportToInterior(spawn.x - -5.06, spawn.y - -4.01, spawn.z + 1.16, POIOffsets.exit.h)
	if IsNew then
		SetTimeout(750, function()
			TriggerEvent('qb-clothes:client:CreateFirstCharacter')
			IsNew = false
		end)
	end
    return { objects, POIOffsets }
end)



