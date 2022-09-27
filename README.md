# qb-interior-modern

# README

Naviagte to qb-interior/client/main.lua



# Replace This
```
exports('CreateApartmentFurnished', function(spawn)
	local objects = {}
    local POIOffsets = {}
	POIOffsets.exit = json.decode('{"x": -1.50, "y": 10.0, "z": 1.3, "h":358.50}')
	POIOffsets.clothes = json.decode('{"x": -6.028, "y": -9.5, "z": 1.2, "h":2.263}')
	POIOffsets.stash = json.decode('{"x": -7.305, "y": -3.922, "z": 0.5, "h":2.263}')
	POIOffsets.logout = json.decode('{"x": -0.8, "y": 1.0, "z": 1.0, "h":2.263}')
    DoScreenFadeOut(500)
    while not IsScreenFadedOut() do
        Wait(10)
    end
	RequestModel(`furnitured_midapart`)
	while not HasModelLoaded(`furnitured_midapart`) do
	    Wait(3)
	end
	local house = CreateObject(`furnitured_midapart`, spawn.x, spawn.y, spawn.z, false, false, false)
    FreezeEntityPosition(house, true)
    objects[#objects+1] = house
	TeleportToInterior(spawn.x + 1.5, spawn.y - 8.0, spawn.z, POIOffsets.exit.h)
	if IsNew then
		SetTimeout(750, function()
			TriggerEvent('qb-clothes:client:CreateFirstCharacter')
			IsNew = false
		end)
	end
    return { objects, POIOffsets }
end)```

# TO THIS
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
            --Add gift thingy here
            IsNew = false
        end)
    end
    return { objects, POIOffsets }
end)
 ```
