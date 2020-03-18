---
title: Znakové stránky
ms.date: 11/04/2016
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
ms.openlocfilehash: 13b31b7d7750158caf498d92db67fd3e61856c5c
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443497"
---
# <a name="code-pages"></a>Znakové stránky

Znaková *Stránka* je znaková sada, která může obsahovat čísla, interpunkční znaménka a další glyfy. Různé jazyky a národní prostředí mohou používat různé znakové stránky. Například znaková stránka ANSI 1252 se používá pro angličtinu a většinu evropských jazyků. Pro japonštinu kanji se používá znaková stránka OEM 932.

Znaková stránka může být reprezentována v tabulce jako mapování znaků na jednobajtové hodnoty nebo vícebajtové hodnoty. Mnoho kódových stránek sdílí znakovou sadu ASCII pro znaky v rozsahu 0x00-0x7F.

Knihovna run-time společnosti Microsoft používá následující typy znakových stránek:

- Systémová – výchozí znaková stránka ANSI. Ve výchozím nastavení při spuštění systém za běhu automaticky nastaví vícebajtovou znakovou stránku na znakovou stránku ANSI, která se získá z operačního systému. Volání:

    ```C
    setlocale ( LC_ALL, "" );
    ```

   také nastaví národní prostředí na znakovou stránku ANSI systému výchozí.

- Znaková stránka národního prostředí. Chování řady běhových rutin závisí na aktuálním nastavení národního prostředí, které zahrnuje znakovou stránku národního prostředí. (Další informace najdete v tématu [rutiny závislé na národním prostředí](../c-runtime-library/locale.md).) Ve výchozím nastavení používají všechny rutiny závislé na národním prostředí v knihovně modulu Microsoft run-time znakovou stránku, která odpovídá národnímu prostředí "C". V době běhu můžete změnit nebo zadat dotaz na znakovou stránku národního prostředí, která se používá, voláním [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md).

- Vícebajtová znaková stránka. Chování většiny rutin vícebajtových znaků v knihovně run-time závisí na aktuálním nastavení vícebajtové znakové stránky. Ve výchozím nastavení tyto rutiny používají standardní znakovou stránku ANSI systému. V době běhu můžete zadávat dotazy a měnit vícebajtovou znakovou stránku pomocí [_getmbcp](../c-runtime-library/reference/getmbcp.md) a [_setmbcp](../c-runtime-library/reference/setmbcp.md), v uvedeném pořadí.

- Národní prostředí "C" je definováno standardem ANSI, aby odpovídalo národnímu prostředí, ve kterém byly tradičně spouštěny programy jazyka C. Znaková stránka národního prostředí "C" ("C" Code ") odpovídá znakové sadě ASCII. Například v národním prostředí "C" vrátí příkaz **Lower** hodnotu true pro hodnoty 0X61-0x7A. V jiném národním prostředí **může naopak** vracet hodnotu true pro tyto i jiné hodnoty, jak je definováno tímto národním prostředím.

## <a name="see-also"></a>Viz také

[Internacionalizace](../c-runtime-library/internationalization.md)<br/>
[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
