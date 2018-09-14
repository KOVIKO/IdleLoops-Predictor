# IdleLoops Predictor

The IdleLoops Predictor is a userscript addon that modifies the action list UI of [IdleLoops](http://stopsign.github.io/idleLoops/). The modifications will show you the estimated amount of mana, gold, reputation, herbs, hide, potions, soulstone attempts, crafting guild segments, and adventure guild segments after every action in the action list based on your current talents and progress.

## Installation

You will need a userscript manager like [Tampermonkey for Chrome](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo) or [Greasemonkey for Firefox](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/) installed on your browser before using this script. The script is installed via one of these tools.

To install the script, click the `idleloops-predictor.user.js` in GitHub and then click the **`Raw`** button. Your userscript manager should automatically give you the option to install the script. Alternatively, you can just follow the link below:

**[»» Install IdleLoops Predictor ««](https://github.com/SerVamP/IdleLoops-Predictor/raw/master/idleloops-predictor.user.js)**

## The UI

![IdleLoops Predictor Action List](https://i.imgur.com/cGDodUk.png)

The UI additions of the addon are all contained in the Action List.

* **Estimated Total Mana Used**: To the right of the title "Action List," there is a number that shares its color with the default mana bar. This number represents the total amount of mana spent by the action list. This should help you to keep track of your mana efficiency.

* **Estimated Resources**: To the right of to the number of loops for any given action in the action list, there will be colored numbers. These numbers represent resources. The numbers for any given resource will only be visible if one of the actions in your action list affects that resource. If an action won't have enough mana to complete, the UI element will show all resources as red text.

  * **Mana**: Mana is shown as the same color as the default mana bar.
  * **Gold**: Gold is shown as an orange-ish gold.
  * **Reputation**: Reputation is shown as brown.
  * **Herbs**: Herbs are shown as green.
  * **Hide**: Hide is shown as dark brown.
  * **Potions**: Potions are shown as blue.
  * **Crafting Guild Segments**: Completed crafting guild segments are shown as grey.
  * **Adventure Guild Segments**: Completed adventure guild segments are shown as black.
  * **Soulstone Attempts**: Completed soulstone attempts are shown as purple.
  
The predictor does not attempt to predict the actual amount of soulstones you will receive, but rather the amount of chances you have at receiving soulstones.

![IdleLoops Predictor Tooltip](https://i.imgur.com/RnuFxmy.png)

* **Tooltips**: When you hover your cursor over an action in the action list, it will show the predicted level of stats and skills the IdleLoops Predictor expects you to have at the end of the action. This will display to the left of the action in a tooltip.

## How it works

This script is actually a simplified, barebones rebuild of the game loop, operating on an instanced set of progression attributes. Whenever the predictions are calculated, each individual tick is calculated in sequence. This calculation occurs every time that the game attempts to update the action list, which is most frequently while the user is setting up the action list.

The script keeps track of anything that can affect resources, both those that are visible in the section above and those that are not. Since the script only concerns itself with resources, it's able to ignore irrelevant things such as exploration progress, action validation, story progression, and anything with RNG aspects.

## Limitations

### Skills

The results that you see in the IdleLoops Predictor UI are predicted based on your current skills at the moment in which the UI was last updated. This means that if you are gaining skills in the middle of a loop, updating the action list will make a prediction as though you were about to press the Restart button at that specific moment.

### Tooltips

Currently, the only way to display tooltips without ruining scrolling of the action list is to overlap the left-side current action list. Due to this requirement, sometimes the left-side current action list will not be interactable immediately after displaying tooltips from the Action List. Just move your mouse outside of the Action List UI element and then return to it from the left side.

### Performance

If you notice lag whenever you make changes to the action list, I recommend taking the code from this userscript and pasting it directly into the console rather than using the userscript manager. Personally, I've found that Tampermonkey can cause some slight performance issues.

## License

IdleLoops Predictor is licensed under the MIT License. Refer to the [LICENSE](https://github.com/Koviko/IdleLoops-Predictor/blob/master/LICENSE) file.
