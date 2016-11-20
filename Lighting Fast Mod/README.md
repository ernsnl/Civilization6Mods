# Lighting Snail Speed Mod

## Introduction

Initial game speed options are somewhat limited in the new Civilization 6.

| Game Speed | Cost  Multiplier | Ancient  | Classical | Medieval | Renaissance | Industrial | Modern | Atomic | Information|
| :--------: | :--------------- | :------- |:--------- |:-------- |:----------- | :--------- | :----- | :----- | :--------- |
| Marathon   | 300              | 180/100  | 120/300   |  60/170  | 24/201      | 12/129     | 6/180  | 3/264  | 1/156      |
| Epic       | 150              | 300/140  | 180/90    |  120/40  | 60/90       | 24/70      | 12/100 | 6/264  | ????       |
| Standard   | 100              | 480/75   | 300/60    |  240/25  | 120/50      | 60/60      | 24/50  | 12/120 | 6/60       |
| Quick      | 67               | 720/50   | 480/30    |  360/20  | 240/30      | 120/25     | 60/40  | 24/65  | 12/70      |
| Online     | 50               | 960/35   | 600/30    |  480/20  | 240/20      | 120/30     | 48/25  | 24/60  | 12/30      |

These are given speed options of the Civilization game. As you can see when the cost multiplier decreased game becomes much faster. If you want to make much more faster or much more slower only have to do is change the value of the cost multiplier.

For that purpose, I added two different speed option. One is making the game run much faster (Lighting), other one makes the run game much slower (Snail). For others who want to create their own speed version please click [here](#How-to-Create-Own-Speed-Option)

| Game Speed | Cost  Multiplier | Ancient  | Classical | Medieval | Renaissance | Industrial | Modern | Atomic | Information|
| :--------: | :--------------- | :------- |:--------- |:-------- |:----------- | :--------- | :----- | :----- | :--------- |
| Snail      | 500              | 50/250   | 75/450    |  40/220  | 12/320      | 8/180      | 3/500  | 2/360  | 1/300      |
| Lighting   | 25               | 1920/18  | 1200/15   |  960/10  | 480/15      | 240/15     | 96/12  | 48/30  | 24/60      |

## <h2 id="How-to-Install">How to Install</h2>

First of all, use that mod at your own risk.

1. Even though modified files are stored in here, please please get a backup of your current Civilization 6 directory.
2. Download the folder (as a zip) by clicking the Download button at the top-right corner (Clone or Download).
3. Extract files.
4. Locate your Civilization 6 directory. Each modified files is located in their corresponding position
  1. If you are using steam, Civilization 6 is located under "~\Steam\steamapps\common\Sid Meier's Civilization VI".
5. Each changed file is located under their corresponding directory.
  1. For example, If you found GameSpeeds.xml under "Base\Assets\Configurtaion\Data\", file is located under "YOUR_CIV_6_DIR\Base\Assets\Configurtaion\Data\".
6. Copy each modified file to corresponding directory.
7. You are done!. Enjoy your increased speed options.

## <h2 id="How-to-Create-Own-Speed-Option">How to Create Own Speed Option</h2>

So, you want to customize your speed option. First of all, backup your Civilization 6 directory.

1. Locate your Civ 6 directory.
2. Find the following folders.
  1. GameSpeeds.xml => Located under "YOUR_CIV_6_DIR\Base\Assets\Configuration\Data"
  2. FrontEndText.xml => Located under "YOUR_CIV_6_DIR\Base\Assets\Text\en_US"
  3. Types_Text.xml => Located under "YOUR_CIV_6_DIR\Base\Assets\Text\en_US"
  4. GameSpeeds.xml => Located under "YOUR_CIV_6_DIR\Base\Assets\Gameplay\Data"
3. After you located the files, open the GameSpeeds.xml (Configuration/Data)
  1. In this file, there is a GameSpeeds tag and under that tag, there are familiar game speed options.
  2. To add your custom speed option, please select a name like GandhiNukesMuchFaster. Important note: Selected name must be unique.
  3. Copy given the row and paste it under the GameSpeeds tag .
   ```xml
   <Row GameSpeedType="GAMESPEED_%YOUR_OPTION%" Name="LOC_GAMESPEED_%YOUR_OPTION%_NAME" Description="LOC_GAMESPEED_%YOUR_OPTION%_HELP" SortIndex="%YOUR_OPTION_LOCATION%" />
   ```
  4. Change %YOUR_OPTION% with custom game speed name.
  5. Order for the custom game speed option. Insert any number that is bigger 0.
    1. For much more refined ordering of the game speed options, remember that Higher values means option will be presented at the top of the list. Vice versa.
    2. If you want to create a game speed option which is faster than Standard and slower than Quick. Your SortIndex value should be between Standard SortIndex Value and Quick SortIndex Value. (According to original values=> Standard SortIndex: 30, Quick SortIndex: 20).
4. Open FrontEndText.xml
    1. This file is responsible for tooltip of the setting.
    2. Please locate "Game Speed Descriptions"
    3. Add the following after "Game Speed Descriptions"
    ```xml
    <Row Tag="LOC_GAMESPEED_%YOUR_OPTION%_HELP">
			<Text>%EXPLAIN_YOUR_SPEED%</Text>
		</Row>
    ```
    4. Change %YOUR_OPTION% with custom game speed name.
    5. Change %EXPLAIN_YOUR_SPEED% with short description of the game speed.
5. Open Types_Text.xml
  1. This file is responsible for name of the game speed settings and more.
  2. Please locate "Game Speeds".
  3. Add the following after "Game Speeds"
  ```xml
  <Row Tag="LOC_GAMESPEED_%YOUR_OPTION%_NAME">
			<Text>%YOUR_OPTION%</Text>
		</Row>
  ```
  4. Change %YOUR_OPTION% with custom game speed name.
6. Open the GameSpeeds.xml (GamePlay/Data)
   1. This file is responsible for how the game speed setting will play out through ages.
   2. Please locate the "Types" tag.
   3. Add the following into Types Tag.
   ```xml
   	<Row Type="GAMESPEED_%YOUR_OPTION%" Kind="KIND_GAMESPEED"/>
   ```
   4. Change %YOUR_OPTION% with custom game speed name.
   5. Please locate GameSpeed tag.
   6. Add the following to the GameSpeeds tag.
   ```xml
   <Row>
			<GameSpeedType>GAMESPEED_%YOUR_OPTION%</GameSpeedType>
			<Name>LOC_GAMESPEED_%YOUR_OPTION%_NAME</Name>
			<Description>LOC_GAMESPEED_%YOUR_OPTION%_HELP</Description>
			<CostMultiplier>%YOUR_OPTION_COST%</CostMultiplier>
			<CivicUnlockMaxCost>%YOUR_OPTION_CIVIC_MAX%</CivicUnlockMaxCost>
			<CivicUnlockPerTurnDrop>%YOUR_OPTION_CIVIC_DROP_RATE%</CivicUnlockPerTurnDrop>
			<CivicUnlockMinCost>%YOUR_OPTION_CIVIC_MIN_COST%</CivicUnlockMinCost>
		</Row>
    ```
    7. Change %YOUR_OPTION% with custom game speed name.
    8. Change %YOUR_OPTION_COST% with any number that is bigger than 1.
     1. Note that, When the number becomes large, game speed will decrease. Vice versa.
    9. Change %YOUR_OPTION_CIVIC_MIN_COST% with any number that is bigger than 1.
     1. Note: This represents minimum value for a Civic. Meaning that a civic requirement research time cannot be lower than this value (Before Euraka moments).
    10. Change %YOUR_OPTION_CIVIC_MAX% with any number that is bigger than %YOUR_OPTION_CIVIC_MIN_COST%
     1. Note: This represents maximum value for a Civic. When a civic is available to research this number will be the highest possible value (Before Euraka moments).
    11. Change %YOUR_OPTION_CIVIC_DROP_RATE% with any number that is bigger than 1.
     1. Note: This represents amount of drop.
    12. Please locate the GameSpeed_Turns tag.
    13. Add the following to the GameSpeed_Turns tag.
    ```xml
    <Row>
			<GameSpeedType>GAMESPEED_%YOUR_OPTION%</GameSpeedType>
			<MonthIncrement>%ERA%</MonthIncrement>
			<TurnsPerIncrement>%ERA%</TurnsPerIncrement>
		</Row>
		<Row>
			<GameSpeedType>GAMESPEED_%YOUR_OPTION%</GameSpeedType>
      <MonthIncrement>%ERA%</MonthIncrement>
			<TurnsPerIncrement>%ERA%</TurnsPerIncrement>
		</Row>
		<Row>
			<GameSpeedType>GAMESPEED_%YOUR_OPTION%</GameSpeedType>
      <MonthIncrement>%ERA%</MonthIncrement>
      <TurnsPerIncrement>%ERA%</TurnsPerIncrement>
		</Row>
		<Row>
			<GameSpeedType>GAMESPEED_%YOUR_OPTION%</GameSpeedType>
      <MonthIncrement>%ERA%</MonthIncrement>
			<TurnsPerIncrement>%ERA%</TurnsPerIncrement>
		</Row>
		<Row>
			<GameSpeedType>GAMESPEED_%YOUR_OPTION%</GameSpeedType>
      <MonthIncrement>%ERA%</MonthIncrement>
      <TurnsPerIncrement>%ERA%</TurnsPerIncrement>
		</Row>
		<Row>
			<GameSpeedType>GAMESPEED_%YOUR_OPTION%</GameSpeedType>
      <MonthIncrement>%ERA%</MonthIncrement>
			<TurnsPerIncrement>%ERA%</TurnsPerIncrement>
		</Row>
		<Row>
			<GameSpeedType>GAMESPEED_%YOUR_OPTION%</GameSpeedType>
      <MonthIncrement>%ERA%</MonthIncrement>
      <TurnsPerIncrement>%ERA%</TurnsPerIncrement>
		</Row>
		<Row>
			<GameSpeedType>GAMESPEED_%YOUR_OPTION%</GameSpeedType>
      <MonthIncrement>%ERA%</MonthIncrement>
			<TurnsPerIncrement>%ERA%</TurnsPerIncrement>
		</Row>
    ```
    14. Change %YOUR_OPTION% with custom game speed name.
    15. You might ask why there are seven same Row tag. Let me explain each of those row is represents an era. First row being the Ancient Era and last one being the Information Era.
    16. For each era, please fill the %ERA% with a number bigger than 1.
      1. According the initial files, when the game speed increases, MonthIncrement increases and TurnsPerIncremen decreases
7. You are done. Enjoy your custom game speed setting.
