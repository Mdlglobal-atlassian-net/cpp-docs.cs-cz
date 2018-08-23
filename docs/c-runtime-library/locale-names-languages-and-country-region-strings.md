---
title: Názvy národních prostředí, jazyků a zemí / oblastí řetězce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/13/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.strings
dev_langs:
- C++
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c072074c24466458ebd19e1335f49169c5c22bd5
ms.sourcegitcommit: 3b78ddea5fd3e22b7c5cd2d787ec71a518a52223
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2018
ms.locfileid: "42465570"
---
# <a name="locale-names-languages-and-countryregion-strings"></a>Řetězce s názvy národních prostředí, jazyků a zemí/oblastí

*Národní prostředí* argument `setlocale` a `_create_locale` funkce lze nastavit pomocí názvů národního prostředí, jazyků, kódů země/oblasti a znakových stránek, které podporují rozhraní API Windows NLS. *Národní prostředí* argument má následující podobu:

> *národní prostředí* :: "*locale_name*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "*jazyk*\[\_*zemí / oblastí*]\[. *code_page*]] "  
&nbsp;&nbsp;&nbsp;&nbsp;| ". *code_page*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "C"  
&nbsp;&nbsp;&nbsp;&nbsp;| ""  
&nbsp;&nbsp;&nbsp;&nbsp;| HODNOTU NULL  

Upřednostňována forma názvu národního prostředí; například použít `en-US` pro angličtinu (Spojené státy) nebo `bs-Cyrl-BA` pro Bosenština (cyrilice, Bosna a Hercegovina). Sada názvů národních prostředí je popsána v [názvy národních prostředí](/windows/desktop/Intl/locale-names). Seznam podporovaných názvech národních prostředí podle verze operačního systému Windows, najdete v článku **značku jazyka** sloupec tabulky v [chování produktu dodatku A:](https://msdn.microsoft.com/library/cc233982.aspx) v [MS-LCID]: Windows identifikátor pro kód jazyka (LCID) Referenční dokumentace. Tento materiál obsahuje seznam podporovaných částí názvů národních prostředí, jež udávají jazyk, způsob zápisu a oblast. Informace o názvech podporované národní prostředí, které mají jiné než výchozí pořadí řazení, naleznete **název národního prostředí** sloupec v [identifikátory pořadí řazení](/windows/desktop/Intl/sort-order-identifiers). V části Windows 10 nebo novější jsou povolené názvy národních prostředí, které odpovídají platné značky jazyka BCP 47. Například `jp-US` je platná značka BCP-47, ale to je v podstatě pouze `US` pro funkce národního prostředí.

*Jazyk*[*_country_region*[. *code_page*]] formuláře je uložen v nastavení národního prostředí pro kategorii v případě řetězec jazyka nebo řetězec jazyka a řetězec země/oblast se používá k vytvoření národního prostředí. Sada podporovaných řetězců jazyka je popsána v [Language Strings](../c-runtime-library/language-strings.md), a seznam řetězců podporované země/oblasti, které je uvedené v [Country/Region Strings](../c-runtime-library/country-region-strings.md). Pokud zadaný jazyk není spojen se zadanou zemí nebo oblastí, uloží se v nastavení národního prostředí výchozí jazyk pro zadanou zemi nebo oblast. Tuto formu řetězců národního prostředí vložených do kódu nebo serializovaných do úložiště nedoporučujeme, protože tyto řetězce s větší pravděpodobností podlehnou změně při aktualizaci operačního systému než u formy s názvem národního prostředí.

Znaková stránka je znaková stránka ANSI/OEM spojená s daným národním prostředím. Znakovou stránku za vás určíme, pokud zadáte národní prostředí pouze pomocí jazyka nebo jazyka a země či oblasti. Zvláštní hodnota `.ACP` Určuje znakovou stránku ANSI pro danou zemi nebo oblast. Zvláštní hodnota `.OCP` Určuje znakovou stránku OEM pro danou zemi nebo oblast. Pokud zadáte například `"Greek_Greece.ACP"` jako národní prostředí, národní prostředí, které se uloží jako `Greek_Greece.1253` (znaková stránka ANSI pro řečtinu), a pokud zadáte `"Greek_Greece.OCP"` jako národní prostředí, je uložena jako `Greek_Greece.737` (znaková stránka OEM pro řečtinu). Další informace o znakových stránkách naleznete v tématu [znakové stránky](../c-runtime-library/code-pages.md). Seznam znakových stránek podporovaných ve Windows najdete v tématu [identifikátory znakových stránek](/windows/desktop/Intl/code-page-identifiers).

Pokud používáte k určení národního prostředí, výchozí jazyk a zemi/oblast uživatele, jak je hlásí pouze znaková stránka [GetUserDefaultLocaleName](/windows/desktop/api/winnls/nf-winnls-getuserdefaultlocalename) se používají. Pokud zadáte například `".1254"` (turečtina ANSI) jako národní prostředí pro uživatele, který je nakonfigurován pro angličtinu (Spojené státy), je národní prostředí, která je uložena `English_United States.1254`. Tuto formu ukládání nedoporučujeme, protože může způsobit nekonzistentní chování.

A *národní prostředí* hodnotu argumentu `C` Určuje minimální prostředí vyhovující standardu ANSI pro překlad. `C` Národní prostředí předpokládá, že všechny **char** datový typ je 1 bajt a jejich hodnota je vždy menší než 256. Pokud *národní prostředí* odkazuje na prázdný řetězec, národní prostředí, které je definováno implementací nativního prostředí.

Všechny kategorie národního prostředí lze zadat ve stejnou dobu `setlocale` a `_wsetlocale` funkcí s použitím `LC_ALL` kategorie. Všechny kategorie mohou být nastaveny na stejné národní prostředí nebo můžete nastavit každou kategorii samostatně pomocí argumentu národního prostředí, který má tento tvar:

> LC_ALL_specifier:: národního prostředí  
&nbsp;&nbsp;&nbsp;&nbsp;| [LC_COLLATE národní prostředí =] [; LC_CTYPE národní prostředí =] [; LC_MONETARY národní prostředí =] [; LC_NUMERIC národní prostředí =] [; LC_TIME národní prostředí =]

Můžete zadat více typů kategorií oddělených středníky. Typy kategorií, které nejsou zadány, používají aktuální nastavení národního prostředí. Například tento fragment kódu nastaví aktuální národní prostředí pro všechny kategorie na `de-DE`a pak nastaví kategorie `LC_MONETARY` k `en-GB` a `LC_TIME` k `es-ES`:

```C
_wsetlocale(LC_ALL, L"de-DE");
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");
```

## <a name="see-also"></a>Viz také:

[Referenční dokumentace knihovny CRT](../c-runtime-library/c-run-time-library-reference.md)  
[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)  
[setlocale, _wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)  
[_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)  
[Řetězce jazyků](../c-runtime-library/language-strings.md)  
[Řetězce zemí/oblastí](../c-runtime-library/country-region-strings.md)  
