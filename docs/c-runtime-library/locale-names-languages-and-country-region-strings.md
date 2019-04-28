---
title: Názvy národních prostředí, jazyků a zemí / oblastí řetězců
ms.date: 12/10/2018
f1_keywords:
- c.strings
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
ms.openlocfilehash: f6df36aafde9a61a1fd590a7f60b3c17131aadbb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62342741"
---
# <a name="ucrt-locale-names-languages-and-countryregion-strings"></a>UCRT Locale names, jazyky a země/oblast řetězce

*Národní prostředí* argument [setlocale, \_wsetlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md), [ \_vytvořit\_národní prostředí](../c-runtime-library/reference/create-locale-wcreate-locale.md), a [ \_wcreate\_národní prostředí](../c-runtime-library/reference/create-locale-wcreate-locale.md) funkce lze nastavit pomocí názvů národního prostředí, jazyků, kódů země/oblasti a znakových stránek, které podporují rozhraní API Windows NLS. *Národní prostředí* argument má následující podobu:

> *národní prostředí* :: "*název národního prostředí*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "*jazyk*\[**\_**_zemí / oblastí_\[__.__ *znaková stránka*]] "<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "__.__  *znaková stránka*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "C"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| ""<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| NULL

*Název národního prostředí* formuláře je krátký, standardizované IETF řetězec, například `en-US` pro angličtinu (Spojené státy) nebo `bs-Cyrl-BA` pro Bosenština (cyrilice, Bosna a Hercegovina). Jsou upřednostňované. Seznam podporovaných názvech národních prostředí podle verze operačního systému Windows, najdete v článku **značku jazyka** sloupec tabulky v [dodatku A: Chování produktu](https://msdn.microsoft.com/library/cc233982.aspx) v [MS-LCID]: Odkaz na identifikátor (LCID) kód jazyka Windows. Tento materiál obsahuje seznam podporovaných částí názvů národních prostředí, jež udávají jazyk, způsob zápisu a oblast. Informace o názvech podporované národní prostředí, které mají jiné než výchozí pořadí řazení, naleznete **název národního prostředí** sloupec v [identifikátory pořadí řazení](/windows/desktop/Intl/sort-order-identifiers). V části Windows 10 nebo novější, národní prostředí názvy, které odpovídají na platný [BCP-47](https://tools.ietf.org/html/bcp47) jsou povolené značky jazyka. Například `jp-US` je platná značka BCP-47, ale to je v podstatě pouze `US` pro funkce národního prostředí.

*Jazyk*\[**\_**_zemí / oblastí_\[__.__ *znaková stránka*]] formuláře je uložen v nastavení národního prostředí pro kategorii v případě řetězec jazyka nebo řetězec jazyka a země nebo oblast řetězec se používá k vytvoření národního prostředí. Sada podporovaných řetězců jazyka je popsána v [Language Strings](../c-runtime-library/language-strings.md), a seznam podporovaných řetězců země a oblasti je uveden v [Country/Region Strings](../c-runtime-library/country-region-strings.md). Pokud zadaný jazyk není spojen se zadanou zemi nebo oblast, ukládají se v nastavení národního prostředí výchozí jazyk pro zadanou zemi nebo oblast. Tuto formu řetězců národního prostředí vložených do kódu nebo serializovaných do úložiště nedoporučujeme, protože tyto řetězce s větší pravděpodobností podlehnou změně při aktualizaci operačního systému než u formy s názvem národního prostředí.

*Znakovou stránku* je znaková stránka ANSI/OEM spojená s daným národním prostředím. Znakovou stránku za vás určíme, pokud zadáte národní prostředí pouze pomocí jazyka nebo jazyka a země či oblasti. Zvláštní hodnota `.ACP` Určuje znakovou stránku ANSI pro danou zemi nebo oblast. Zvláštní hodnota `.OCP` Určuje znakovou stránku OEM pro danou zemi nebo oblast. Pokud zadáte například `"Greek_Greece.ACP"` jako národní prostředí, národní prostředí, které se uloží jako `Greek_Greece.1253` (znaková stránka ANSI pro řečtinu), a pokud zadáte `"Greek_Greece.OCP"` jako národní prostředí, je uložena jako `Greek_Greece.737` (znaková stránka OEM pro řečtinu). Další informace o znakových stránkách naleznete v tématu [znakové stránky](../c-runtime-library/code-pages.md). Seznam znakových stránek podporovaných ve Windows najdete v tématu [identifikátory znakových stránek](/windows/desktop/Intl/code-page-identifiers).

Pokud používáte k určení národního prostředí, výchozí jazyk a zemi/oblast uživatele, jak je hlásí pouze znaková stránka [GetUserDefaultLocaleName](/windows/desktop/api/winnls/nf-winnls-getuserdefaultlocalename) se používají. Pokud zadáte například `".1254"` (turečtina ANSI) jako národní prostředí pro uživatele, který je nakonfigurován pro angličtinu (Spojené státy), je národní prostředí, která je uložena `English_United States.1254`. Tuto formu ukládání nedoporučujeme, protože může způsobit nekonzistentní chování.

A *národní prostředí* hodnotu argumentu `C` Určuje minimální prostředí vyhovující standardu ANSI pro překlad. `C` Národní prostředí předpokládá, že všechny **char** datový typ je 1 bajt a jejich hodnota je vždy menší než 256. Pokud *národní prostředí* odkazuje na prázdný řetězec, národní prostředí, které je definováno implementací nativního prostředí.

Všechny kategorie národního prostředí lze zadat ve stejnou dobu `setlocale` a `_wsetlocale` funkcí s použitím `LC_ALL` kategorie. Všechny kategorie mohou být nastaveny na stejné národní prostředí nebo můžete nastavit každou kategorii samostatně pomocí argumentu národního prostředí, který má tento tvar:

> *LC-ALL-specifier* :: *národního prostředí*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| \[**LC_COLLATE =**_národní prostředí_]\[**; LC_CTYPE =**_národní prostředí_]\[**; LC_MONETARY =**_národní prostředí_]\[**; LC_NUMERIC =**_národní prostředí_]\[**; LC_TIME =**_národní prostředí_]

Můžete zadat více typů kategorií oddělených středníky. Typy kategorií, které nejsou zadány, používají aktuální nastavení národního prostředí. Například tento fragment kódu nastaví aktuální národní prostředí pro všechny kategorie na `de-DE`a pak nastaví kategorie `LC_MONETARY` k `en-GB` a `LC_TIME` k `es-ES`:

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```

## <a name="see-also"></a>Viz také:

[Referenční dokumentace knihovny CRT](../c-runtime-library/c-run-time-library-reference.md)<br/>
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[Řetězce jazyků](../c-runtime-library/language-strings.md)<br/>
[Řetězce zemí/oblastí](../c-runtime-library/country-region-strings.md)
