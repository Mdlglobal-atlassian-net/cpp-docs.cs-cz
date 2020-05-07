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
ms.openlocfilehash: 001eb90b5cb4dda933571fd053598995d3ef613e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345313"
---
# <a name="trigraphs"></a>Trigraphs

Zdroj znakové sady zdrojových programů jazyka C je obsažen v 7bitové znakové sadě ASCII, ale je nadmnožinou invariantní znakové sady standardu ISO 646-1983. Sekvence trigrafů umožňuje, aby programy jazyka C byly zapsány pouze pomocí invariantní znakové sady standardu ISO (International Standards Organization). Trigrafy jsou sekvence tří znaků (uvedené dvěma po sobě jdoucími otazníky), které kompilátor nahradí jejich odpovídajícími znaky interpunkce. Trigrafy lze použít ve zdrojových souborech jazyka C, které používají znakovou sadu, která neobsahuje vhodné grafické reprezentace pro některá interpunkční znaménka.

C++ 17 odebere trigraphs z jazyka. Implementace mohou nadále podporovat trigraphs jako součást mapování definovaná implementací z fyzického zdrojového souboru do *základní zdrojové znakové sady*, i když standard podporuje implementace, které nejsou v takovém případě. V jazyce C++ 14 jsou trigraphs podporovány jako v jazyce C.

Visual C++ nadále podporuje substituci trigraph, ale ve výchozím nastavení je zakázaná. Informace o tom, jak povolit substituci trigraph, najdete v tématu [/Zc: trigraphs (trigraphs Substitution)](../build/reference/zc-trigraphs-trigraphs-substitution.md).

Následující tabulka obsahuje devět sekvencí trigrafů. Všechny výskyty znaků interpunkce v prvním sloupci ve zdrojovém souboru jsou nahrazeny odpovídajícím znakem ve druhém sloupci.

### <a name="trigraph-sequences"></a>Sekvence trigraf

| Trigraf | Znak interpunkce |
|----------|-----------------------|
| ??= | # |
| ??( | \[ |
| ??/ | \\ |
| ??) | ] |
| ??' | ^ |
| ??\< | { |
| ??! | &#124; |
| ?? > | } |
| ??- | ~ |

Trigraf je vždy považován za jediný zdrojový znak. Překlad trigraphs probíhá v první [fázi překladu](../preprocessor/phases-of-translation.md)před rozpoznáváním řídicích znaků v literálech řetězce a znakových konstant. V tabulce výše je rozpoznáno pouze devět trigrafů. Všechny ostatní sekvence znaků zůstanou nepřevedeny.

Znaková řídicí sekvence, ** \\?**, zabraňuje špatné interpretaci znakových sekvencí trigraph podobných. (Informace o řídicích sekvencích naleznete v tématu [řídicí sekvence](../c-language/escape-sequences.md).) Například pokud se pokusíte řetězec `What??!` vytisknout pomocí tohoto příkazu `printf`

```C
printf( "What??!\n" );
```

řetězec, který je `What|` vytištěn `??!` , je trigraph sekvence, která je nahrazena `|` znakem. Chcete-li tento řetězec vypsat správně, napište příkaz takto:

```C
printf( "What?\?!\n" );
```

V tomto příkazu `printf` řídicí znak zpětného lomítka před druhým otazníkem zabraňuje špatnému vyhodnocení `??!` jako trigrafu.

## <a name="see-also"></a>Viz také

[/Zc:trigraphs (náhrada spřežky tří znaků)](../build/reference/zc-trigraphs-trigraphs-substitution.md)<br/>
[Identifikátory jazyka C](../c-language/c-identifiers.md)
