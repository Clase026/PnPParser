This is the script that parses input for Virtual P&P.

Given a string with 'roll' in it, it will attempt to roll dice based on the text after that keyword.
If a string has effect in it, it will add the text after that keyword after the roll as a description
Any text that comes before either of these keywords is treated as the name of whatever action the player is taking.

Basic dice roll syntax: XDY, where X is the number of dice to be rolled, and Y is the number of facets on those dice.
For example, 2D6 means to roll 2 6-sided dice and add them together.

For instance: "Holy Smites ROLL 2d6 + 4 EFFECT burns the heretic with holy fury" would be parsed into
"Holy smites, rolls 11, and burns the heretic with holy fury"

Additional case-insensitive modifiers can be added to rolls
-"CRIT": A critical hit doubles the number of dice rolled for the whole roll
-"ADV": Advantage allows a set of dice to roll twice and take the higher value
-"DIS": Disadvantage forces a set of dice to roll twice and take the lower value
-"LUCKY": Luck allows a set of dice to re-roll and take the new roll if the initial roll was a 1
-"GREAT": Skill with great weapons allows a set of dice to re-roll and take the new roll if the initial roll was a 1 or 2
-"B": Brutal Criticals increase the number of dice rolled on a critical hit by the number of 'B's. This is applied after the doubling from the critical hit.
-"M10" : Long practice has ensured that even if a die rolls lower than this value, it at least takes this value, usually 10

Example Dice rolls and their effects:
"ROLL 1D20 Adv + 4" This will roll one 20-sided die twice, taking the higher value, and then adding four to that value.
"ROLL CRIT 2D6 BB + 1.5 * 5" This will roll 6 six-sided dice, since the critical hit double the base number,
 and the two Brutal ratings increase it by two more. It will then add 7 to the sum of the six dice, since you always round down.
"ROLL 1D20 Dis M10 + -2" This will roll two twenty-sided dice and take the lower value, then change it to 10 if that value
 is less than 10. It will then add negative two to that number.

