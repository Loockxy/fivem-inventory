# Menu

**Do not use these scripts if you are not comfortable with development.**
**If you have some issues with code, ask the community on the official [FiveM's topic](https://forum.fivem.net/t/preview-enhanced-hud/634217).**

## How to install

* Copy and paste ```target``` folder to ```resources```
* Add ```start target``` to your ```server.cfg``` file
* Copy and paste ```menu``` folder to ```resources```
* Add ```start menu``` to your ```server.cfg``` file

## Dependency
* [Target](https://github.com/Naikzer/HUD-GTAVRP/tree/master/target)

## Create menu

```index.html```
```html
<ul class="menu menu-user">
    <li>
        <a class="cheer" href="">
            <span class="emoji">👋</span>Cheer
        </a>
    </li>
    <li>
        <a class="[PUT FUNCTION RIGHT HERE]" href="">
            <span class="emoji">👋</span>Saluer
        </a>
    </li>
    (…)
</ul>
```

```script.js```
```javascript
$('.cheer').on('click', function(e){
    e.preventDefault();
    $.post('http://menu/cheer', JSON.stringify({
        id: idEnt
    }));
});
```

```client.lua``` (and server.lua if needed)
```javascript
RegisterNUICallback('cheer', function(data)
  playerPed = GetPlayerPed(-1);
    if(not IsPedInAnyVehicle(playerPed)) then
        if playerPed then
            if playing_emote == false then
                TaskStartScenarioInPlace(playerPed, 'WORLD_HUMAN_CHEERING', 0, true);
                playing_emote = true
            end
        end
    end
end)
```

*To understand the structure, check demos on source files*

## Files

* ```ui/index.html``` file to add new menu
* ```ui/script.js``` file to add new function
* ```ui/front.js``` JS for HTML interaction
* ```ui/styles.scss``` use this to edit CSS if you are comfortable with CSS pre-processor (must be compiled)

## Screen

![Inventory Screen](https://user-images.githubusercontent.com/52666643/61137488-e50f2b80-a4c5-11e9-8a87-c584f6fcd0a5.jpg)
