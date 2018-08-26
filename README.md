# IdleLoops Predictor

The IdleLoops Predictor is a userscript addon that modifies the action list UI of IdleLoops. The modifications will show you the estimated amount of mana, gold, reputation, herbs, hide, potions, and soulstone attempts after every action in the action list based on your current talents and progress.

## Installation

You will need a userscript manager like [Tampermonkey for Chrome](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo) or [Greasemonkey for Firefox](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/) installed on your browser before using this script. The script is installed via one of these tools.

To install the script, click the `idleloops-predictor.user.js` in GitHub and then click the **`Raw`** button. Your userscript manager should automatically give you the option to install the script. Alternatively, you can just follow the link below:

**[»» Install IdleLoops Predictor ««](https://github.com/Koviko/IdleLoops-Predictor/raw/master/idleloops-predictor.user.js)**

## The UI

![IdleLoops Predictor Action List](https://i.imgur.com/cGDodUk.png)

The UI additions of the addon are all contained in the Action List.

* **Estimated Total Mana Used**: To the right of the title "Action List," there is a blue number. This number represents the total amount of mana spent by the action list. This should help you to keep track of your mana efficiency.

* **Estimated Resources**: To the right of to the number of loops for any given action in the action list, there will be colored numbers. These numbers represent resources. The numbers for any given resource will only be visible if one of the actions in your action list affects that resource. If an action won't have enough mana to complete, the UI element will show all resources as red text.

  * **Mana**: Mana is shown as a light blue.
  * **Gold**: Gold is shown as an orange-ish gold.
  * **Reputation**: Reputation is shown as brown.
  * **Herbs**: Herbs are shown as green.
  * **Hide**: Hide is shown as a dark brown.
  * **Potions**: Potions are shown as a blue.
  * **Soulstone Attempts**: Soulstone attempts are shown as purple.
  
The predictor does not attempt to predict the actual amount of soulstones you will receive, but rather the amount of chances you have at receiving soulstones.

## How it works

This script is actually a simplified, barebones rebuild of the game loop. Whenever the predictions are calculated, each individual tick is calculated in sequence. This calculation occurs every time that the game attempts to update the action list, which is most frequently while the user is setting up the action list.

The script keeps track of anything that can affect resources, both those that are visible in the section above and those that are not. Since the script only concerns itself with resources, it's able to ignore irrelevant things such as exploration progress, action validation, story progression, and anything with RNG aspects.

## Limitations

When an action in your action list will cause a permanent attribute of your character to increase in level in the middle of a loop, this will not be accounted for. This includes things such as Combat skill, Magic skill, or Hermit Knowledge which can all affect subsequent actions in the action list. Instead, you'll simply see the update in the next loop.

## License

IdleLoops Predictor is licensed under the MIT License. Refer to the [LICENSE](https://github.com/Koviko/IdleLoops-Predictor/blob/master/LICENSE) file.