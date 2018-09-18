---
title: Trigraphs | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb65bf8cf2f9585ff12ba0a098d9ca441310933f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101929"
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