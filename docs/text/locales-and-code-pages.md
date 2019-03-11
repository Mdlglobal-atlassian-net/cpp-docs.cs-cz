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
ms.openlocfilehash: c0cfc7f192b65738984feb1933ea720fdf18fc6d
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750712"
---
# <a name="locales-and-code-pages"></a>Národní prostředí a kódové stránky

ID národního prostředí odráží místní konvence a jazyk pro konkrétní zeměpisné oblasti. Daný jazyk může být používán ve více než jedné zemi nebo oblasti. Například portugalsky se hovoří v Brazílii stejně jako v Portugalsku. Naopak země nebo oblast může používat více než jeden úřední jazyk. Například Kanada používá dva jazyky: Angličtinu a francouzštinu. Kanada má tedy dvě odlišná národní prostředí: Kanadské s angličtinou a Kanadské s francouzštinou. Ke kategoriím závislým na národním prostředí patří formátování dat nebo zobrazovací formát pro peněžní hodnoty.

Jazyk určuje konvence formátování textu a data, zatímco země nebo oblast určuje místní konvence. Každý jazyk má jedinečný mapování reprezentována znakových stránek, který obsahuje jiné znaky než ty v abecedě (například čísla a interpunkční znaménka). Znaková stránka je znaková sada a má vztah k jazyku. V důsledku toho [národní prostředí](../c-runtime-library/locale.md) je jedinečná kombinace jazyka, země/oblast a znakovou stránku. Stránka nastavení národního prostředí a kód může změnit za běhu pomocí volání [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) funkce.

Různé jazyky mohou používat různé znakové stránky. Například ANSI znakovou stránkou 1252 se používá pro angličtinu a většinu evropských jazyků a ANSI znakovou stránku 932 se používá pro japonské Kanji. Téměř všechny znakové stránky sdílet znaku standardu ASCII, nastavte pro nejnižší 128 znaků (0x00 do 0x7F).

Jakékoli jednobajtové znakové stránky můžou vyjádřeny v tabulce (s 256 položky) jako mapování bajtových hodnot znaků (včetně čísla a interpunkční znaménka), nebo glyfů. Žádné vícebajtové znakové stránky můžou být vyjádřeny i jako velmi velké tabulky (s položkami 64 kB) hodnot dvoubajtové znaky. V praxi ale jsou obvykle reprezentovány jako tabulku pro prvních 256 znaků (single bajty) a rozsahy adres pro hodnoty dvoubajtové.

Další informace o znakových stránkách naleznete v tématu [znakové stránky](../c-runtime-library/code-pages.md).

Knihovny runtime jazyka C obsahují dva typy vnitřních znakových stránek: národní prostředí a vícebajtové. Při provádění programu můžete změnit aktuální znakové stránce (naleznete v dokumentaci k [setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) a [_setmbcp](../c-runtime-library/reference/setmbcp.md) funkce). Knihovny run-time může také získat a používat hodnotu znakovou stránku operačního systému, což je konstantní po dobu trvání provádění programu.

Znaková stránka národního prostředí změny, chování závislé na národním prostředí sadu funkcí změny, které závisí na zvoleném znakovou stránku. Ve výchozím nastavení všechny závislé na národním prostředí funkce zahájit provádění s znaková stránka národního prostředí jedinečná pro národní prostředí "C". Znaková stránka národního prostředí vnitřní (stejně jako ostatní vlastnosti specifické pro národní prostředí) můžete změnit pomocí volání `setlocale` funkce. Volání `setlocale`(LC_ALL, "") nastaví národní prostředí, které udávají národní prostředí operačního systému uživatele.

Podobně, když je vícebajtová znaková stránka změní, chování vícebajtové funkce změny, které závisí na zvoleném znakovou stránku. Ve výchozím nastavení všechny funkce vícebajtové začínat vícebajtové znakové stránky odpovídající operační systém výchozí znaková stránka provádění. Interní vícebajtové znakové stránce lze změnit pomocí volání `_setmbcp` funkce.

Funkci run-time C `setlocale` nastaví, změní nebo dotazuje některých nebo všech informací o národním prostředí aktuálního programu. [_Wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) rutina je verze širokého znaku `setlocale`; argumenty a vrácené hodnoty `_wsetlocale` jsou širokoznaké řetězce.

## <a name="see-also"></a>Viz také:

[Unicode a MBCS](../text/unicode-and-mbcs.md)<br/>
[Výhody přenositelnosti znakové sady](../text/benefits-of-character-set-portability.md)
