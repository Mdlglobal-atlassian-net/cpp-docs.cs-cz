---
title: Trigraphs
ms.date: 11/04/2016
helpviewer_keywords:
- ??) trigraph
- ??- trigraph
- question mark, in trigraphs
- ??= trigraph
- ?? trigraph
- ??< trigraph
- ??/ trigraph
- trigraphs
- '? symbol, trigraph'
- ??> trigraph
- ??! trigraph
- ??' trigraph
ms.assetid: 617f76ec-b8e8-4cfe-916c-4bc32cbd9aeb
ms.openlocfilehash: 2106f7dda6ecc71478b29cfad3f15dfee0483025
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523897"
---
# <a name="trigraphs"></a>Trigraphs

Zdroj znakové sady zdrojových programů jazyka C je obsažen v 7bitové znakové sadě ASCII, ale je nadmnožinou invariantní znakové sady standardu ISO 646-1983. Sekvence trigrafů umožňuje, aby programy jazyka C byly zapsány pouze pomocí invariantní znakové sady standardu ISO (International Standards Organization). Trigrafy jsou sekvence tří znaků (uvedené dvěma po sobě jdoucími otazníky), které kompilátor nahradí jejich odpovídajícími znaky interpunkce. Trigrafy lze použít ve zdrojových souborech jazyka C, které používají znakovou sadu, která neobsahuje vhodné grafické reprezentace pro některá interpunkční znaménka.

C ++ 17 odebere trigraphs od jazyka. Implementace může nadále podporovat trigraphs jako součást mapování definované implementací fyzický zdrojový soubor, který *základní sada zdrojových znaků*, i když standardní může vést ke vzniku implementace není k tomu. Pomocí C ++ 14 jsou podporovány trigraphs stejně jako v jazyce C.

Visual C++ i nadále podporuje náhrada trigraph, ale je ve výchozím nastavení zakázána. Informace o tom, jak povolit náhrada trigraph najdete v tématu [/Zc: trigraphs (náhrada trigraph)](../build/reference/zc-trigraphs-trigraphs-substitution.md).

Následující tabulka obsahuje devět sekvencí trigrafů. Všechny výskyty znaků interpunkce v prvním sloupci ve zdrojovém souboru jsou nahrazeny odpovídajícím znakem ve druhém sloupci.

### <a name="trigraph-sequences"></a>Sekvence trigraf

|Trigraf|Znak interpunkce|
|--------------|---------------------------|
|??=|#|
|??(|[|
|??/|\|
|??)|]|
|??'|^|
|??\<|{|
|??!|&#124;|
|??>|}|
|??-|~|

Trigraf je vždy považován za jediný zdrojový znak. Převod trigrafů probíhá v první [fáze překladu](../preprocessor/phases-of-translation.md), před rozpoznáním řídicích znaků v řetězcových literálech a znakových konstantách. V tabulce výše je rozpoznáno pouze devět trigrafů. Všechny ostatní sekvence znaků zůstanou nepřevedeny.

Řídicí sekvence znaku  **\\?**, zabraňuje špatnému vyhodnocení sekvencí znaků podobných. (Informace o řídicích sekvencích naleznete v tématu [řídicí sekvence](../c-language/escape-sequences.md).) Například, pokud se pokusíte vypsat řetězec `What??!` pomocí tohoto příkazu `printf`

```
printf( "What??!\n" );
```

Vypíše se řetězec `What|` protože `??!` je sekvence trigrafu, která je nahrazena `|` znak. Chcete-li tento řetězec vypsat správně, napište příkaz takto:

```
printf( "What?\?!\n" );
```

V tomto příkazu `printf` řídicí znak zpětného lomítka před druhým otazníkem zabraňuje špatnému vyhodnocení `??!` jako trigrafu.

## <a name="see-also"></a>Viz také

[/Zc:trigraphs (náhrada spřežky tří znaků)](../build/reference/zc-trigraphs-trigraphs-substitution.md)<br/>
[Identifikátory jazyka C](../c-language/c-identifiers.md)