# TattleLogMod
Vanilla paper mario with a tattle log added

To add new enemies:<br/>
change these to add more pages in `modDirectory/globals/TattleLogv2/mainTattleLog.patch`<br/>
`#export .commonPageTotal 3 %real total is .commonPageTotal + 1` <br/>
`#export .bossPageTotal 2 %real total is .bossPageTotal + 1`<br/>
<br/>
In `modDirectory/globals/TattleLogv2/tattleLogv2Data.patch` there is a pointer to each menu, then the pages that each menu has<br/>
```
#export:Data $commonPageStructs {
    $commonPage0Struct
    $commonPage1Struct
    $commonPage2Struct
    $commonPage3Struct
}
```
This defines menu `$commonPageStructs` with the pages `commonPageXStruct` which there are 4 of<br/>
Next is creating/change the actual pages. The struct is as follows:
```
typedef struct enemyEntry {
/* 0x00 */ char* enemyName;
/* 0x04 */ char* enemyDescription; //can also be a text ID
/* 0x08 */ s32 actorType;
/* 0x0C */ s16 xOffsetForImage;
/* 0x0E */ s16 yOffsetForImage;
/* 0x10 */ s32* imageData;
} enemyEntry; //sizeof 0x14
```
```$blueGoombaName     002F0004    90  35`s    8`s     $BlueGoombaBroData```<br/>
This is an example for blue goomba, it has <br/>
enemyName `$blueGoombaName`<br/>
enemyDescription `002F0004`<br/>
actorType `0x90`<br/>
xOffsetForImage `35`<br/>
yOffsetForImage `8`<br/>
imageData `$BlueGoombaBroData`<br/>
