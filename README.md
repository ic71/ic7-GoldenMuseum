# ic7-GoldenMuseum
Golden Museum robbery

# فيديو: https://streamable.com/l7etc7



# المتطلبات

* [qb-core](https://github.com/qbcore-framework/qb-core)
* [Memorygame](https://github.com/pushkart2/memorygame)
* [qb-target](https://github.com/qbcore-framework/qb-target)
* [ps-dispatch](https://github.com/Project-Sloth/ps-dispatch)
* [qb-doorlock](https://github.com/qbcore-framework/qb-doorlock)

# طريقة التركيب


*  1- ضيف هذا الكود في 
qb-core\shared\items.lua
```lua
--ic7
    ['ic7_burial'] 		 				 = {['name'] = 'ic7_burial', 						['label'] = 'قطعة اثرية مصرية', 					['weight'] = 1000, 	    ['type'] = 'item', 		['image'] = 'ic7_burial-mask.png', 				['unique'] = false, 	['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'قطعة اثرية مصرية من المتحف الذهبي'},
	['ic7_fishingchest'] 		 			 = {['name'] = 'ic7_fishingchest', 					['label'] = 'صندوق اثرية', 				['weight'] = 1000, 	    ['type'] = 'item', 		['image'] = 'ic7_fishingchest.png', 				['unique'] = false, 	['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'صندوق اثرية من المتحف الذهبي'},
	['ic7_greek'] 				 	 = {['name'] = 'ic7_greek', 			    	['label'] = 'االتمثال الفديم', 				['weight'] = 1000, 		['type'] = 'item', 		['image'] = 'ic7_greek-bust.png', 			['unique'] = false, 	['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'االتمثال القديم من المتحف الذهبي'},
	['ic7_jadeite'] 			 = {['name'] = 'ic7_jadeite', 			  	['label'] = 'الماسة خضراء', 				['weight'] = 1000, 	['type'] = 'item', 		['image'] = 'ic7_jadeite-stone.png', 		['unique'] = false, 	['useable'] = true, 	['shouldClose'] = true,	   ['combinable'] = nil,   ['description'] = 'الماسة خضراء من المتحف الذهبي'},
	['ic7_mask'] 			 = {['name'] = 'ic7_mask', 			['label'] = 'القناع الذهبي', 		['weight'] = 1000, 		['type'] = 'item', 		['image'] = 'ic7_vip_mask.png', 			['unique'] = false, 	['useable'] = false, 	['shouldClose'] = false,   ['combinable'] = nil,   ['description'] = 'القناع الذهبي من المتحف الذهبي'},
	['ic7_vanpogo'] 			 = {['name'] = 'ic7_vanpogo', 			['label'] = 'التمثال الذهبي', 		['weight'] = 1000, 		['type'] = 'item', 		['image'] = 'ic7_vanpogo.png', 			['unique'] = false, 	['useable'] = false, 	['shouldClose'] = false,   ['combinable'] = nil,   ['description'] = 'التمثال الذهبي من المتحف الذهبي'},
--ic7
```


* 2- ضيف ملف img في 
qb-inventory\html\images


* 3- ضيف هذا الكود في 
qb-doorlock/configs
```lua
Config.DoorList['ic7'] = {
    locked = true,
    authorizedJobs = { ['police'] = 0 },
    doorType = 'double',
    doorLabel = 'ic7',
    doors = {
        {objName = -881481405, objYaw = 0.0, objCoords = vec3(-554.572510, -617.887939, 35.073013)},
        {objName = -881481405, objYaw = 180.00001525879, objCoords = vec3(-556.532288, -617.896790, 35.078335)}
    },
    doorRate = 1.0,
    distance = 2,
    maxDistance = 2.5,
    lockpick = false,
    audioRemote = false,
    slides = false,
    --oldMethod = true,
    --audioLock = {['file'] = 'metal-locker.ogg', ['volume'] = 0.6},
    --audioUnlock = {['file'] = 'metallic-creak.ogg', ['volume'] = 0.7},
    --autoLock = 1000,
    --doorRate = 1.0,
    --showNUI = true
}
```


* 4- ضيف هذا الكود في 
ps-dispatch\client\cl_eventhandlers.lua
```lua
local function goldenmuseum()
    local currentPos = GetEntityCoords(PlayerPedId())
    local locationInfo = getStreetandZone(currentPos)
    local gender = GetPedGender()
    TriggerServerEvent("dispatch:server:notify",{
        dispatchcodename = "goldenmuseum", 
        dispatchCode = "10-90",
        firstStreet = locationInfo,
        gender = gender,
        model = nil,
        plate = nil,
        priority = 2, 
        firstColor = nil,
        automaticGunfire = false,
        origin = {
            x = currentPos.x,
            y = currentPos.y,
            z = currentPos.z
        },
        dispatchMessage = _U('Golden Museum Robbery'), 
        job = {"LEO", "police"} 
    })
end exports('goldenmuseum', goldenmuseum)
```
* 5- ضيف هذا الكود في 
ps-dispatch\server\sv_dispatchcodes.lua
```lua
["goldenmuseum"] =  {displayCode = '10-90', description = "Golden Museum Robbery In Progress", radius = 0, recipientList = {'LEO', 'police'}, blipSprite = 124, blipColour = 59, blipScale = 1.5, blipLength = 2, sound = "robberysound", offset = "false", blipflash = "false"},
```
تم انشاء هذا السكربت بواسطة : ic7

