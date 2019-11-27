---
title: Národní prostředí a kódové stránky
ms.date: 11/04/2016
helpviewer_keywords:
- locales [C++], about locales
- locale IDs [C++]
- locales [C++]
- code pages [C++]
- code pages [C++], dynamically changing
- character sets [C++], code pages
- multibyte code pages [C++]
- character sets [C++], locales
- localization [C++], code pages
- localization [C++], locales
- code pages [C++], locales
- conventions [C++], international character support
ms.assetid: bd937361-b6d3-4c98-af95-beb7c903187b
ms.openlocfilehash: 5821048363d92911f2902a580cb11f5b349f5e7c
ms.sourcegitcommit: 4f15b69e35dd112001b24fe9dc836dd5d6902465
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2019
ms.locfileid: "74474067"
---
# <a name="locales-and-code-pages"></a>Národní prostředí a kódové stránky

ID národního prostředí odráží místní konvence a jazyk pro konkrétní geografickou oblast. Daný jazyk může být používán ve více než jedné zemi nebo oblasti. Například portugalsky se hovoří v Brazílii stejně jako v Portugalsku. Naopak země nebo oblast může používat více než jeden úřední jazyk. Například Kanada používá dva jazyky: angličtinu a francouzštinu. Kanada má tedy dvě odlišná národní prostředí: kanadské s angličtinou a kanadské s francouzštinou. Ke kategoriím závislým na národním prostředí patří formátování dat nebo zobrazovací formát pro peněžní hodnoty.

Jazyk určuje konvence formátování textu a data, zatímco země nebo oblast určuje místní konvence. Každý jazyk má jedinečné mapování reprezentované kódovými stránkami, které obsahují znaky jiné než abecedy (jako jsou například interpunkční znaménka a čísla). Kódová stránka je znaková sada, která se vztahuje k jazyku. V takovém případě je [národní prostředí](../c-runtime-library/locale.md) jedinečnou kombinací jazyka, země nebo oblasti a znakové stránky. Nastavení národního prostředí a znakové stránky lze v době běhu změnit voláním funkce [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) .

Různé jazyky mohou používat různé znakové stránky. Například znaková stránka ANSI 1252 se používá pro angličtinu a většinu evropských jazyků a znaková stránka ANSI 932 se používá pro japonské kanji. Prakticky všechny znakové stránky sdílí znakovou sadu ASCII pro nejnižší 128 znaků (0x00 do 0x7F).

Každá bajtová znaková stránka může být reprezentována v tabulce (s 256 položkami) jako mapování bajtových hodnot na znaky (včetně čísel a interpunkčních znamének) nebo glyfů. Jakákoli Vícebajtová znaková stránka může být také reprezentovaná jako velmi velká tabulka (s 64 tisíci položkami) dvoubajtové hodnoty na znaky. V praxi je však obvykle reprezentován jako tabulka pro první 256 (jednobajtové) znaky a jako rozsahy pro dvoubajtové hodnoty.

Další informace o znakových stránkách naleznete v tématu [Code Pages](../c-runtime-library/code-pages.md).

Knihovny runtime jazyka C obsahují dva typy vnitřních znakových stránek: národní prostředí a vícebajtové. Aktuální znakovou stránku můžete změnit během provádění programu (informace naleznete v dokumentaci k funkcím [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) a [_setmbcp](../c-runtime-library/reference/setmbcp.md) ). Běhová knihovna také může získat a použít hodnotu znakové stránky operačního systému, což je konstanta po dobu trvání spuštění programu.

Když se změní znaková stránka národního prostředí, chování sady funkcí závislých na národním prostředí se změní na hodnotu, kterou určuje vybraná znaková stránka. Ve výchozím nastavení se všechny funkce závislé na národním prostředí začnou spouštět pomocí znakové stránky národního prostředí, které jsou jedinečné pro národní prostředí "C". Můžete změnit vnitřní znakovou stránku národního prostředí (stejně jako jiné vlastnosti specifické pro národní prostředí) voláním funkce `setlocale`. Volání `setlocale`(LC_ALL, "") nastaví národní prostředí na hodnotu určenou národním prostředím uživatele operačního systému.

Podobně při změně vícebajtové kódové stránky se chování vícebajtových funkcí změní na, který je určen zvolenou znakovou stránkou. Ve výchozím nastavení všechny vícebajtové funkce zahájí provádění na vícebajtové znakové stránce, která odpovídá výchozí znakové stránce operačního systému. Vnitřní vícebajtovou znakovou stránku lze změnit voláním funkce `_setmbcp`.

Běhová funkce jazyka C `setlocale` sady, změny nebo dotazy na některé nebo všechny informace o národním prostředí aktuálního programu. Rutina [_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) je verze `setlocale`s velkým znakem; argumenty a návratové hodnoty `_wsetlocale` jsou řetězce s velkým počtem znaků.

## <a name="see-also"></a>Viz také:

[Unicode a MBCS](../text/unicode-and-mbcs.md)<br/>
[Výhody přenositelnosti znakové sady](../text/benefits-of-character-set-portability.md)
