---
title: Znakové stránky
ms.date: 11/04/2016
f1_keywords:
- c.international
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
ms.openlocfilehash: 707aec51b0a244fe305205b9b098f3f67a90de1b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50521053"
---
# <a name="code-pages"></a>Znakové stránky

A *znakovou stránku* je znaková sada, která může obsahovat čísla, interpunkční znaménka a dalších glyfy. Různé jazyky a národní prostředí může použít různé znakové stránky. Například ANSI znakovou stránkou 1252 slouží pro angličtinu a většina evropských jazyků; Výrobce OEM znakovou stránku 932 se používá pro japonské Kanji.

Znaková stránka může být reprezentován v tabulce jako mapování pro hodnoty jednobajtové nebo vícebajtové znaky. Mnoho stránek kód sdílet sadu pro znaky v rozsahu 0x00 – 0x7F znaků ASCII.

Běhové knihovny Microsoft používá tyto druhy znakových stránek:

- Systému výchozí ANSI znakovou stránku. Ve výchozím nastavení při spuštění systému za běhu automaticky nastaví vícebajtovou znakovou stránku na znakovou stránku ANSI výchozí systémové hodnoty, která se získá z operačního systému. Volání:

    ```C
    setlocale ( LC_ALL, "" );
    ```

   také nastaví národní prostředí systému výchozí ANSI znakovou stránku.

- Znaková stránka národního prostředí. Chování počet běhové rutiny je závislá na aktuální nastavení národního prostředí, která zahrnuje znaková stránka národního prostředí. (Další informace najdete v tématu [rutiny závislé na národním prostředí](../c-runtime-library/locale.md).) Ve výchozím nastavení používají všechny rutiny závislé na národním prostředí v knihovně Microsoft za běhu znakovou stránku, která odpovídá na národní prostředí "C". Při spuštění můžete změnit nebo dotazovat znaková stránka národního prostředí používané pro volání [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

- Vícebajtové znakové stránky. Chování většina rutin vícebajtového znaku v knihovně runtime závisí na aktuální nastavení vícebajtové znakové stránky. Ve výchozím nastavení použijte tyto rutiny systému výchozí ANSI znakovou stránku. V době běhu můžete zadávat dotazy a změnit vícebajtovou znakovou stránku s [_getmbcp](../c-runtime-library/reference/getmbcp.md) a [_setmbcp](../c-runtime-library/reference/setmbcp.md)v uvedeném pořadí.

- ANSI tak, aby odpovídaly národní prostředí, ve kterém jste spustili tradičně programů jazyka C je definována národní prostředí "C". Znaková stránka národního prostředí "C" ("C" znaková stránka) odpovídá znakové sady ASCII. Například v národním prostředí "C" **islower** vrací hodnotu true pro hodnoty 0x61 - 0x7A pouze. V jiném národním prostředí **islower** může vrátit hodnotu true pro tyto stejně jako ostatní hodnoty dle toto národní prostředí.

## <a name="see-also"></a>Viz také

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>