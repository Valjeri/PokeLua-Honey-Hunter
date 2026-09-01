#  PokeLua Honey Hunter

A Honey Tree RNG helper for Pokémon Platinum, built on top of PokeLua and tested with DeSmuME 0.9.13 x64.

Honey Hunter predicts which Pokémon species will be assigned to a Honey Tree when Honey is applied, automatically calculates the player's personal Munchlax Trees, and can be used together with PokeFinder for advanced RNG manipulation.

---

> [!IMPORTANT]
> ## Honey Hunter 1.0 works only with Munchlax Trees
>
> The species predictor in Honey Hunter 1.0 is designed specifically for the player's four personal Munchlax Trees.
>
> These are the four Honey Trees on which Munchlax can appear. Honey Hunter automatically calculates them from the current save's TID/SID and displays their locations at the bottom of the overlay:
>
>     Your Munchlax trees:
>     205 South / 207
>     211 East / 212 North
>
> Use the Honey Hunter species predictor only on these four displayed trees.
>
> The predictor is not designed for normal Honey Trees. If it displays Munchlax, Heracross, Aipom, or another species while you are using a normal Honey Tree, the actual encounter may be different.
>
> Normal Honey Trees are still useful when performing repeated manipulations. You can apply Honey to a different tree to reset the previous-tree state, then return to one of your four displayed Munchlax Trees for the next Honey Hunter manipulation.

---

# What is Honey Hunter?

Pokémon Platinum's Honey Tree system uses several separate RNG stages.

For our purposes, two of them are especially important:

1. Species selection — happens when Honey is applied to the tree.
2. Pokémon generation — happens later, when the encounter with the selected species begins.

These two stages are separate, which can make Honey Tree RNG confusing when using standard RNG tools.

Honey Hunter is primarily designed to handle the first stage — species selection on the player's four Munchlax Trees.

It reads the current RNG state and displays, in real time, which Pokémon species will be selected if Honey is applied to a Munchlax Tree at that moment.

For example:

    Honey Hunter 1.0

    NOW @154: Munchlax
    +1  @155: Combee
    +2  @156: Aipom
    +3  @157: Nothing
    +4  @158: Burmy
    +5  @159: Burmy

    Munchlax: +0 @154
    Heracross: +37 @191

Honey Hunter also automatically calculates the player's four personal Munchlax Trees from the current save's TID/SID and displays them directly in the overlay.

This means Honey Hunter can be used in two ways:

- By itself, to obtain a desired species from one of your Munchlax Trees.
- Together with PokeFinder, to obtain a specific Pokémon with selected characteristics.

---

# Features

- Real-time species prediction for the player's four Munchlax Trees
- Displays the currently predicted species
- Shows the next 5 predicted results
- Finds the next Munchlax advance
- Finds the next Heracross advance
- Automatically calculates the player's four personal Munchlax Trees from TID/SID
- Displays the Munchlax Tree locations directly in the overlay
- Runs inside the existing PokeLua Platinum overlay
- Does not modify the ROM or save file
- Can be used independently or together with PokeFinder

---

# Requirements

Tested configuration:

- Pokémon Platinum
- DeSmuME 0.9.13 x64
- Lua 5.1 (lua51.dll)

Other emulator versions may work, but have not been verified.

Honey Hunter is based on the Pokémon Platinum DeSmuME RNG script from PokeLua.

---

# Installation

1. Download Honey_Hunter_1.0.lua.
2. Make sure Lua 5.1 is working with DeSmuME.
3. If required, place lua51.dll next to the DeSmuME executable.
4. Start Pokémon Platinum in DeSmuME.
5. Open:

       Tools → Lua Scripting → New Lua Script Window

6. Load Honey_Hunter_1.0.lua.
7. Switch the PokeLua overlay to Capture mode if necessary.

Honey Hunter information will appear in the lower-right section of the PokeLua overlay.

The four Munchlax Trees calculated for the current save are displayed at the bottom of the Honey Hunter section.

---

# Basic Use — Finding the Pokémon You Want

If you simply want a Pokémon for your Pokédex or collection, PokeFinder is not required.

First, go to one of the four Munchlax Trees displayed by Honey Hunter.

Do not use the species predictor on a normal Honey Tree.

For example, if you want Munchlax:

1. Go to one of your displayed Munchlax Trees.
2. Watch the Honey Hunter predictor.
3. Advance the RNG until it displays:

       NOW @xxx: Munchlax

4. Apply Honey to the tree at that moment.

At this point, the species for the future encounter has already been selected.

---

# Important — Leave the Area After Applying Honey

After applying Honey, we recommend leaving the Honey Tree area, entering another route or area, and only then saving the game.

This is a precaution based on behavior repeatedly observed during testing with DeSmuME.

When remaining in the Honey Tree area during later RTC manipulation, the tree state — especially its shaking animation — could sometimes behave inconsistently.

Observed cases included:

- The tree stopped shaking even though the encounter was still available.
- The animation returned after leaving the area and coming back.
- Leaving and returning did not always restore the animation correctly.
- After entering an inconsistent state, the tree could sometimes continue behaving unpredictably.

For reliability, the recommended workflow is:

    Select the species with Honey Hunter
                  ↓
             Apply Honey
                  ↓
            Leave the area
                  ↓
       Save in another area
                  ↓
        Wait / advance the RTC
                  ↓
        Return to the Honey Tree

This does not mean that remaining in the area will always break the Honey Tree.

However, leaving the area after applying Honey proved more reliable during our testing, so this workflow is recommended.

The shaking animation should also not be treated as the only indication that an encounter is available.

---

# Honey Tree Waiting Time

In the tested DeSmuME 0.9.13 x64 configuration, the Pokémon became available on the Honey Tree after 6 hours.

Therefore, the minimum tested waiting time is 6 hours.

When manipulating the emulator RTC, advancing approximately 7–8 hours can be used as an additional safety margin.

After enough time has passed, return to the prepared Munchlax Tree and interact with it.

If Honey Hunter displayed:

    NOW @xxx: Munchlax

when Honey was applied, Munchlax was already selected during the Honey application stage.

For normal collection hunting, there is no need to hit a specific PokeFinder Seed, Delay, PID, or Advance.

Honey Hunter has already handled the species-selection stage.

---

# Advanced Use — Honey Hunter + PokeFinder

Honey Hunter can also be combined with PokeFinder.

This allows the two parts of a Honey Tree encounter to be controlled separately:

    Honey Hunter → determines which Pokémon species is selected

    PokeFinder   → determines what the generated Pokémon will be like

For example, Honey Hunter can first be used to assign Munchlax to one of your four Munchlax Trees.

PokeFinder can then be used to obtain a specific shiny Munchlax with the desired Nature, IVs, Ability, gender, Hidden Power, or other characteristics.

---

# Stage 1 — Choose Your Target in PokeFinder

First, find the Pokémon result you want in PokeFinder.

This may include:

- Shiny status
- Nature
- IVs
- Ability
- Gender
- Hidden Power
- Or simply any specific result you prefer

Note the required:

- Date and time
- Initial Seed
- Delay
- Advance

If your emulator setup has difficulty hitting odd Delays, selecting a result with an even Delay may make the manipulation easier.

You now know the time at which the final encounter needs to occur.

---

# Stage 2 — Prepare the Munchlax Tree in Advance

Using RunAsDate, start the game at a time at least 6 hours earlier than the final encounter time required by your PokeFinder target.

Starting even earlier is fine and can provide an additional time margin.
Go to one of the four Munchlax Trees displayed by Honey Hunter.

Use Honey Hunter to reach the desired species:

    NOW @xxx: Munchlax

Apply Honey at that RNG state.

The species is now assigned to the tree.

Then:

    Apply Honey
         ↓
    Leave the area
         ↓
    Enter another route/area
         ↓
    Save the game

The Munchlax Tree is now prepared, and the species-selection stage is complete.

---

# Stage 3 — Generate the Specific Pokémon

Once enough time has passed for the Honey Tree encounter to become available:

1. Use RunAsDate to set the date and time required by your selected PokeFinder result.
2. Start Pokémon Platinum.
3. Hit the required Initial Seed / Delay.
4. Advance the encounter RNG to the required Advance.
5. Return to the previously prepared Munchlax Tree.
6. Interact with the tree and begin the encounter.
7. Verify and catch the Pokémon.

If both stages were performed correctly, the result will combine:

- The species selected earlier with Honey Hunter
- The characteristics selected with PokeFinder

---

# The Main Concept

The entire workflow can be summarized with one simple rule:

> Honey Hunter determines WHO is waiting on the tree.
>
> PokeFinder determines WHAT that Pokémon will be like.

These operations happen during different RNG stages and can therefore be manipulated separately.

This makes Honey Hunter useful both for players who simply want rare Honey Tree Pokémon for their collection and for advanced RNG hunting of specific shiny Pokémon or Pokémon with selected characteristics.

---

# Personal Munchlax Trees

Pokémon Platinum assigns four special Munchlax Trees according to the player's TID and SID.

Honey Hunter calculates these automatically and displays them directly in the overlay.

Example:

    Your Munchlax trees:
    205 South / 207
    211 East / 212 North

The displayed locations depend on the current save's TID/SID.

These four displayed trees are the trees on which Honey Hunter 1.0's species predictor should be used.

The predictor should not be expected to give correct species results on normal Honey Trees.

---

# Resetting the Previous Tree

When repeatedly hunting on the same Munchlax Tree, the game's previous-tree behavior can interfere with a clean species prediction.

For more reliable manipulation:

1. Finish the encounter on your target Munchlax Tree.
2. Apply Honey to a different Honey Tree.
3. Leave that area.
4. Return to your target Munchlax Tree.
5. Perform the next Honey Hunter manipulation.

The second tree does not need to be another Munchlax Tree.

A normal Honey Tree can therefore be used simply to reset the previous-tree state before returning to your target Munchlax Tree.

---

# RTC Notes

During emulator testing, moving the RTC forward proved considerably more reliable than moving it backwards between different dates or times.

Moving the emulator RTC backwards could sometimes cause Honey Trees to enter an inconsistent state.

If a tree begins behaving incorrectly, restoring a known-good save from before the Honey Tree experiments may be necessary.

When possible, we recommend planning manipulations so that the emulated date and time move forward rather than backward.

These observations were made during emulator testing and should not be assumed to behave identically on retail Nintendo DS hardware.

---

# PokeFinder and Honey Tree Species

An important limitation should be understood when using PokeFinder with Honey Trees.

PokeFinder can predict characteristics of the Pokémon generated when the encounter begins, including:

- PID
- Shininess
- Nature
- Ability
- IVs
- Gender
- Hidden Power

However, the Honey Tree species-selection stage happens earlier, when Honey is applied.

Therefore, PokeFinder's final encounter result should not be used by itself to determine which species was assigned to the tree.

Use:

> Honey Hunter for species selection on your four Munchlax Trees.
>
> PokeFinder for the final generated Pokémon.

---

# Tested and Confirmed

Honey Hunter 1.0

Tested successfully on:

    DeSmuME 0.9.13 x64
    Pokémon Platinum

Confirmed during testing:

- Munchlax prediction
- Heracross prediction
- Other species prediction on personal Munchlax Trees
- Automatic personal Munchlax Tree calculation from TID/SID
- Different saves correctly producing different personal Munchlax Tree locations
- 6-hour Honey Tree readiness in the tested emulator setup
- Honey Hunter species manipulation combined with PokeFinder encounter RNG
- Species selection and final Pokémon generation functioning as separate RNG stages

---

# Credits and License

Honey Hunter is a derivative of Real96/PokeLua, specifically its Pokémon Platinum DeSmuME RNG script.

Original PokeLua code, RNG overlay functionality, game memory research, Pokémon information display, and emulator integration remain credited to the original PokeLua project and its contributors.

Honey Hunter adds:

- Munchlax Tree species prediction
- Real-time current and upcoming species display
- Munchlax and Heracross search
- Automatic personal Munchlax Tree calculation and display
- Honey Tree-specific RNG workflow and testing

Honey Hunter is distributed under the GNU General Public License v3.0, matching the upstream PokeLua license.

See the repository's LICENSE file for details.

Additional Honey Tree mechanics were cross-checked against existing Generation IV RNG research and community documentation.

---

# Disclaimer

This is an unofficial fan-made RNG research and tooling project.

Honey Hunter does not modify the Pokémon Platinum ROM or save file.

Pokémon and Pokémon Platinum are trademarks of their respective owners.
