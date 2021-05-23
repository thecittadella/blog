---
title: "Настройка уровней клавиатуры в Linux"
date: 2020-05-24T15:32:23+04:00
tags:
  - linux
  - mapping
  - keyboard
  - config
categories:
  - Linux
draft: false
---
Поделюсь моими настройками клавиатуры в X. Я отказался от циклического переключения между раскладками. Долгое время я использовал сочетание правого и левого `Shift`:

```
key <LFSH> { [ Shift_L, ISO_Last_Group ] };
key <RTSH> { [ Shift_R, ISO_First_Group ] };
```
Раскладки переключались в зависимости от `Shift` нажатого последним.
<!--more-->

После с помощью утилиты [`xcape`](https://github.com/alols/xcape) я настроил нажитие левого `Shift` на переключение к английской раскладке и правого `Shift` к русской. В комбинациях с другими клавишами функции `Shift` сохраняются:
```
xcape -t 500 -e 'Shift_L=ISO_First_Group;Shift_R=ISO_Last_Group;Alt_L=Delete'
```
Левый `Alt` я использую как `Delete` клавишу, если нажат отдельно (без комбинаций с другими клавишами).\
*UPD: Переключение раскладки одной клавишей `Shift` не прошло проверку временем. Я вернулся к комбинациям правого и левого `Shift`.*

Правый `Alt` настроен на 3-й уровень раскладки и клавиша `Menu` на Compose:

```
include "pc+us+ru:2+inet(evdev)+level3(ralt_switch)+compose(menu)"
```
Третий и четвертый уровени обеих раскладок сходны с раскладкой Ильи Бирмана. Вот маппинг для английской раскладки:
```
// 1st keyboard row
key <TLDE> { [         grave,        asciitilde,              NoSymbol,             dead_grave  ] }; // "~"
key <AE01> { [             1,            exclam,           onesuperior,             exclamdown  ] }; // "1""
key <AE02> { [             2,                at,           twosuperior,                onehalf  ] }; // "2"
key <AE03> { [             3,        numbersign,         threesuperior,               onethird  ] }; // "3"
key <AE04> { [             4,            dollar,                dollar,             onequarter  ] }; // "4"
key <AE05> { [             5,           percent,                 U2030,               NoSymbol  ] }; // "5" // U+2030 PER MILLE SIGN (‰)
key <AE06> { [             6,       asciicircum,               uparrow,        dead_circumflex  ] }; // "6"
key <AE07> { [             7,         ampersand,             ampersand,           questiondown  ] }; // "7" // +&
key <AE08> { [             8,          asterisk,              infinity,              oneeighth  ] }; // "8" // +S⅛
key <AE09> { [             9,         parenleft,             leftarrow,               NoSymbol  ] }; // "9"
key <AE10> { [             0,        parenright,            rightarrow,               NoSymbol  ] }; // "0"
key <AE11> { [         minus,        underscore,                emdash,                 endash  ] }; // "-"
key <AE12> { [         equal,              plus,              notequal,              plusminus  ] }; // "="

// 2nd keyboard row
key <AD01> { [             q,                 Q,              NoSymbol,             dead_breve  ] }; // "q"
key <AD02> { [             w,                 W,              NoSymbol,               NoSymbol  ] }; // "w"
key <AD03> { [             e,                 E,              EuroSign,               NoSymbol  ] }; // "e"
key <AD04> { [             r,                 R,            registered,         dead_abovering  ] }; // "r"
key <AD05> { [             t,                 T,             trademark,               NoSymbol  ] }; // "t"
key <AD06> { [             y,                 Y,                 U0463,                  U0462  ] }; // "y" // U+0463 CYRILLIC SMALL LETTER YAT 
                                                                                                            // U+0462 CYRILLIC CAPITAL LETTER YAT
key <AD07> { [             u,                 U,                 U0475,                  U0474  ] }; // "u" // U+0475 CYRILLIC SMALL LETTER IZHITSA 
                                                                                                            // U+0474 CYRILLIC CAPITAL LETTER IZHITSA
key <AD08> { [             i,                 I,           Ukrainian_i,            Ukrainian_I  ] }; // "i"
key <AD09> { [             o,                 O,                 U0473,                  U0472  ] }; // "o" // U+0473 CYRILLIC SMALL LETTER FITA 
                                                                                                            // U+0472 CYRILLIC CAPITAL LETTER FITA
key <AD10> { [             p,                 P,                 acute,            doubleacute  ] }; // "p"
key <AD11> { [   bracketleft,         braceleft,           bracketleft,              braceleft  ] }; // "["
key <AD12> { [  bracketright,        braceright,          bracketright,             braceright  ] }; // "]"

// 3rd keyboard row
key <AC01> { [              a,                 A,                 U2248,                 U2318  ] }; // "a" // U+2248 ALMOST EQUAL TO 
                                                                                                     // U+2318 PLACE OF INTEREST SIGN
key <AC02> { [              s,                 S,               section,              NoSymbol  ] }; // "s"
key <AC03> { [              d,                 D,                degree,                 U2300  ] }; // "d" // U+2300 DIAMETER SIGN
key <AC04> { [              f,                 F,              sterling,              NoSymbol  ] }; // "f"
key <AC05> { [              g,                 G,                 U20B4,              NoSymbol  ] }; // "g" // +₴ // U+20b4 UKRAINIAN HRIVNYA
key <AC06> { [              h,                 H,                 U20BD,              NoSymbol  ] }; // "h" // U+20BD RUSSIAN RUBLE
key <AC07> { [              j,                 J,    doublelowquotemark,    singlelowquotemark  ] }; // "j" // +S‚
key <AC08> { [              k,                 K,   leftdoublequotemark,   leftsinglequotemark  ] }; // "k"
key <AC09> { [              l,                 L,  rightdoublequotemark,  rightsinglequotemark  ] }; // "l"
key <AC10> { [      semicolon,             colon,   leftsinglequotemark,        dead_diaeresis  ] }; // ";"
key <AC11> { [     apostrophe,          quotedbl,  rightsinglequotemark,              NoSymbol  ] }; // "'"
key <LSGT> { [      backslash,               bar,              NoSymbol,              NoSymbol  ] }; // "\"

// 4th keyboard row
key <BKSL> { [      backslash,               bar,              NoSymbol,              NoSymbol  ] };
key <AB01> { [              z,                 Z,              NoSymbol,          dead_cedilla  ] }; // "z"
key <AB02> { [              x,                 X,              multiply,                 U22C5  ] }; // "x" // U+22C5 DOT OPERATOR (·)
key <AB03> { [              c,                 C,             copyright,                  cent  ] }; // "c"
key <AB04> { [              v,                 V,             downarrow,            dead_caron  ] }; // "v"
key <AB05> { [              b,                 B,                 U03B2,                 U03B1  ] }; // "b" // +β +Sα 
                                                                                                     // U+03B2 GREEK SMALL LETTER BETA 
                                                                                                     // U+03B1 GREEK SMALL LETTER ALPHA
key <AB06> { [              n,                 N,              NoSymbol,            dead_tilde  ] }; // "n"
key <AB07> { [              m,                 M,                 U2212,    enfilledcircbullet  ] }; // "m" // U+2212 MINUS SIGN (−)
key <AB08> { [          comma,              less,         guillemotleft,    doublelowquotemark  ] }; // "," // +S<
key <AB09> { [         period,           greater,        guillemotright,  rightdoublequotemark  ] }; // "." // +S>
key <AB10> { [          slash,          question,              division,            dead_acute  ] }; // "/" // +÷

// 5th keyboard row
key <SPCE> { [          space,         BackSpace,          nobreakspace,          nobreakspace  ] }; // " "
```
Схожий 3-й и 4-й уровень я использую в русской раскладке.
