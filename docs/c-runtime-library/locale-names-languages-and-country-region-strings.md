---
title: Názvy národních prostředí, jazyků a řetězců zemí a oblastí
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
ms.openlocfilehash: 512eb589d964da9ef8e87f4193362c739b39b4b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500064"
---
# <a name="ucrt-locale-names-languages-and-countryregion-strings"></a>UCRT názvy národních prostředí, jazyků a zemí/oblastí

Argument *locale* pro funkce [setlocale, \_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md), [ \_Create\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)a [ \_wcreate\_národního](../c-runtime-library/reference/create-locale-wcreate-locale.md) prostředí lze nastavit pomocí názvů národních prostředí. jazyky, kódy zemí a oblastí a znakové stránky, které jsou podporovány rozhraním API Windows NLS. Argument *locale* má následující formát:

> *locale* :: "*locale-Name*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|"*jazyková*\[_země – oblast_ . **\_** \[ *znaková stránka*]] "<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|" __.__ *znaková stránka*"<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|R<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\| ""<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|PLATNOST

Forma *názvu národního prostředí* je krátký řetězec standardně IETF; například `en-US` pro angličtinu (USA) nebo `bs-Cyrl-BA` pro bosenština (cyrilice, Bosna a Hercegovina). Tyto formuláře jsou upřednostňovány. Seznam podporovaných názvů národního prostředí podle verze operačního systému Windows najdete v tabulce **značka jazyka** v tabulce v [příloze a: Chování](https://msdn.microsoft.com/library/cc233982.aspx) produktu v [MS-LCID]: Odkaz na identifikátor kódu jazyka systému Windows (LCID). Tento materiál obsahuje seznam podporovaných částí názvů národních prostředí, jež udávají jazyk, způsob zápisu a oblast. Informace o podporovaných názvech národního prostředí, které mají jiné než výchozí pořadí řazení, najdete ve sloupci **název národního prostředí** v části [identifikátory pořadí řazení](/windows/win32/Intl/sort-order-identifiers). V systému Windows 10 nebo novějších jsou povoleny názvy národních prostředí, které odpovídají platným značkám jazyka [BCP-47](https://tools.ietf.org/html/bcp47) . Například `jp-US` je platná značka BCP-47, ale je efektivně pouze `US` pro funkce národního prostředí.

*Jazyk*\[_země a oblasti_ . **\_** \[ *znaková stránka*]] formulář je uložen v nastavení národního prostředí pro kategorii, pokud se k vytvoření národního prostředí používá řetězec jazyka, řetězec jazyka a řetězec země nebo oblasti. Sada podporovaných řetězců jazyka je popsána v části [řetězce jazyka](../c-runtime-library/language-strings.md)a seznam podporovaných řetězců země a oblasti je uveden v řetězcích [země/oblasti](../c-runtime-library/country-region-strings.md). Pokud zadaný jazyk není přidružen k zadané zemi nebo oblasti, je výchozí jazyk pro zadanou zemi nebo oblast uložen v nastavení národního prostředí. Tuto formu řetězců národního prostředí vložených do kódu nebo serializovaných do úložiště nedoporučujeme, protože tyto řetězce s větší pravděpodobností podlehnou změně při aktualizaci operačního systému než u formy s názvem národního prostředí.

*Znaková stránka* je znaková stránka ANSI/OEM, která je přidružená k danému národnímu prostředí. Znakovou stránku za vás určíme, pokud zadáte národní prostředí pouze pomocí jazyka nebo jazyka a země či oblasti. Speciální hodnota `.ACP` určuje znakovou stránku ANSI pro danou zemi nebo oblast. Speciální hodnota `.OCP` určuje znakovou stránku OEM pro danou zemi nebo oblast. Pokud například zadáte `"Greek_Greece.ACP"` jako národní prostředí, národní prostředí je uloženo jako `Greek_Greece.1253` (znaková stránka ANSI pro řečtinu) a Pokud určíte `"Greek_Greece.OCP"` jako národní prostředí, bude uloženo jako `Greek_Greece.737` (znaková stránka OEM pro řečtinu). Další informace o znakových stránkách naleznete v tématu [Code Pages](../c-runtime-library/code-pages.md). Seznam podporovaných znakových stránek ve Windows najdete v tématu [identifikátory znakových stránek](/windows/win32/Intl/code-page-identifiers).

Použijete-li k určení národního prostředí pouze znakovou stránku, budou použity výchozí jazyky uživatele a země/oblast hlášené nástrojem [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename) . Pokud například zadáte `".1254"` (ANSI turečtiny) jako národní prostředí pro uživatele, který je nakonfigurován pro angličtinu (USA), národní prostředí, které je uloženo, `English_United States.1254`je. Tuto formu ukládání nedoporučujeme, protože může způsobit nekonzistentní chování.

Hodnota`C` argumentu *národního prostředí* určuje minimální prostředí vyhovující standardu ANSI pro překlad C. Národní prostředí předpokládá, že každý datový typ char je 1 bajt a jeho hodnota je vždy menší než 256. `C` Pokud *národní prostředí* odkazuje na prázdný řetězec, národní prostředí je nativní prostředí definované implementací.

Můžete zadat všechny kategorie národního prostředí ve stejnou dobu pro `setlocale` funkce a `_wsetlocale` pomocí `LC_ALL` kategorie. Všechny kategorie mohou být nastaveny na stejné národní prostředí nebo můžete nastavit každou kategorii samostatně pomocí argumentu národního prostředí, který má tento tvar:

> *LC-All-specifikátor* :: *locale*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;\|LC_COLLATE =_národní prostředí_] \[ \[ **; LC_CTYPE =** _locale_]\[ **; LC_MONETARY =** _locale_]\[ **; LC_NUMERIC =** _locale_]\[ **; LC_TIME =** _národní prostředí_]

Můžete zadat více typů kategorií oddělených středníky. Typy kategorií, které nejsou zadány, používají aktuální nastavení národního prostředí. Například tento fragment kódu nastaví aktuální národní prostředí pro všechny kategorie na `de-DE`a poté nastaví kategorie `LC_MONETARY` na `en-GB` a `LC_TIME`: `es-ES`

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
[Řetězce země/oblasti](../c-runtime-library/country-region-strings.md)
