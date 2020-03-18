---
title: Názvy národních prostředí, jazyků a řetězců zemí a oblastí
ms.date: 12/10/2018
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
ms.openlocfilehash: d9baf3622064a7f035d0eb2b096916ae81a3bd50
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443122"
---
# <a name="ucrt-locale-names-languages-and-countryregion-strings"></a>UCRT názvy národních prostředí, jazyků a zemí/oblastí

Argument *locale* pro [setlocali, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md), [\_Create\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)a [\_funkce národního prostředí wcreate\_](../c-runtime-library/reference/create-locale-wcreate-locale.md) lze nastavit pomocí názvů národních prostředí, jazyků, kódů zemí a oblastí a znakových stránek, které jsou podporovány rozhraním Windows NLS API. Argument *locale* má následující formát:

> *locale* :: "*locale-Name*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "*language*\[ **\_** _země-region_\[ __.__ *znaková stránka*]] "<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| " __.__ *znaková stránka*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| "C"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| ""<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| NULL

Forma *názvu národního prostředí* je krátký řetězec standardně IETF; například `en-US` pro angličtinu (USA) nebo `bs-Cyrl-BA` pro bosenština (cyrilice, Bosna a Hercegovina). Tyto formuláře jsou upřednostňovány. Seznam podporovaných názvů národního prostředí podle verze operačního systému Windows naleznete v části sloupec **značka jazyka** v tabulce v [příloze a: chování produktu](https://msdn.microsoft.com/library/cc233982.aspx) v [MS-LCID]: odkaz na identifikátor kódu jazyka Windows (LCID). Tento materiál obsahuje seznam podporovaných částí názvů národních prostředí, jež udávají jazyk, způsob zápisu a oblast. Informace o podporovaných názvech národního prostředí, které mají jiné než výchozí pořadí řazení, najdete ve sloupci **název národního prostředí** v části [identifikátory pořadí řazení](/windows/win32/Intl/sort-order-identifiers). V systému Windows 10 nebo novějších jsou povoleny názvy národních prostředí, které odpovídají platným značkám jazyka [BCP-47](https://tools.ietf.org/html/bcp47) . Například `jp-US` je platná značka BCP-47, ale je efektivně `US` pouze pro funkce národního prostředí.

*Jazyk*\[ **\_** \[_oblasti země_ __.__ *znaková stránka*]] formulář je uložen v nastavení národního prostředí pro kategorii, pokud se k vytvoření národního prostředí používá řetězec jazyka, řetězec jazyka a řetězec země nebo oblasti. Sada podporovaných řetězců jazyka je popsána v části [řetězce jazyka](../c-runtime-library/language-strings.md)a seznam podporovaných řetězců země a oblasti je uveden v [řetězcích země/oblasti](../c-runtime-library/country-region-strings.md). Pokud zadaný jazyk není přidružen k zadané zemi nebo oblasti, je výchozí jazyk pro zadanou zemi nebo oblast uložen v nastavení národního prostředí. Tuto formu řetězců národního prostředí vložených do kódu nebo serializovaných do úložiště nedoporučujeme, protože tyto řetězce s větší pravděpodobností podlehnou změně při aktualizaci operačního systému než u formy s názvem národního prostředí.

*Znaková stránka* je znaková stránka ANSI/OEM, která je přidružená k danému národnímu prostředí. Znakovou stránku za vás určíme, pokud zadáte národní prostředí pouze pomocí jazyka nebo jazyka a země či oblasti. Speciální hodnota `.ACP` určuje znakovou stránku ANSI pro zemi nebo oblast. Speciální hodnota `.OCP` určuje znakovou stránku OEM pro danou zemi nebo oblast. Pokud například zadáte `"Greek_Greece.ACP"` jako národní prostředí, národní prostředí je uloženo jako `Greek_Greece.1253` (znaková stránka ANSI pro řečtinu) a pokud zadáte `"Greek_Greece.OCP"` jako národní prostředí, bude uloženo jako `Greek_Greece.737` (znaková stránka OEM pro řečtinu). Další informace o znakových stránkách naleznete v tématu [Code Pages](../c-runtime-library/code-pages.md). Seznam podporovaných znakových stránek ve Windows najdete v tématu [identifikátory znakových stránek](/windows/win32/Intl/code-page-identifiers).

Použijete-li k určení národního prostředí pouze znakovou stránku, budou použity výchozí jazyky uživatele a země/oblast hlášené nástrojem [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename) . Pokud například zadáte `".1254"` (ANSI turečtiny) jako národní prostředí pro uživatele, který je nakonfigurován pro angličtinu (USA), je uložené národní prostředí `English_United States.1254`. Tuto formu ukládání nedoporučujeme, protože může způsobit nekonzistentní chování.

Hodnota argumentu *národního prostředí* `C` určuje minimální prostředí vyhovující standardu ANSI pro překlad C. Národní prostředí `C` předpokládá, že každý datový typ **char** je 1 bajt a jeho hodnota je vždy menší než 256. Pokud *národní prostředí* odkazuje na prázdný řetězec, národní prostředí je nativní prostředí definované implementací.

Pro funkce `setlocale` a `_wsetlocale` můžete zadat všechny kategorie národního prostředí ve stejnou dobu pomocí kategorie `LC_ALL`. Všechny kategorie mohou být nastaveny na stejné národní prostředí nebo můžete nastavit každou kategorii samostatně pomocí argumentu národního prostředí, který má tento tvar:

> *LC-All-specifikátor* :: *locale*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| \[**LC_COLLATE =** _locale_]\[ **; LC_CTYPE =** _locale_]\[ **; LC_MONETARY =** _locale_]\[ **; LC_NUMERIC =** _locale_]\[ **; LC_TIME =** _národní prostředí_]

Můžete zadat více typů kategorií oddělených středníky. Typy kategorií, které nejsou zadány, používají aktuální nastavení národního prostředí. Například tento fragment kódu nastaví aktuální národní prostředí pro všechny kategorie na `de-DE`a poté nastaví kategorie `LC_MONETARY` na `en-GB` a `LC_TIME` na `es-ES`:

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```

## <a name="see-also"></a>Viz také

[Referenční dokumentace knihovny CRT](../c-runtime-library/c-run-time-library-reference.md)<br/>
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[Řetězce jazyků](../c-runtime-library/language-strings.md)<br/>
[Řetězce země/oblasti](../c-runtime-library/country-region-strings.md)
