---
title: '&lt;Národní prostředí&gt;'
ms.date: 11/04/2016
f1_keywords:
- <locale>
- locale/std::<locale>
- std::<locale>
helpviewer_keywords:
- locale header
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
ms.openlocfilehash: 54d6f5306f4517c6450f36051df51385d8d8f578
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494301"
---
# <a name="ltlocalegt"></a>&lt;Národní prostředí&gt;

Definuje třídy a funkce šablon, které mohou programy v jazyce C++ použít k zapouzdření a manipulaci s různými kulturními konvencemi v souvislosti se znázorněním a formátováním číselných, finančních a kalendářních dat, včetně podpory iternacionalizace pro klasifikaci znaků a řazení řetězců.

## <a name="syntax"></a>Syntaxe

```cpp
#include <locale>

```

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[has_facet](../standard-library/locale-functions.md#has_facet)|Ověřuje, zda je v zadaném národním prostředí uložena konkrétní omezující vlastnost.|
|[isalnum](../standard-library/locale-functions.md#isalnum)|Ověřuje, zda je prvek v národním prostředí abecední, nebo číselný znak.|
|[isalpha](../standard-library/locale-functions.md#isalpha)|Ověřuje, zda je prvek v národním prostředí abecední znak.|
|[iscntrl](../standard-library/locale-functions.md#iscntrl)|Ověřuje, zda je prvek v národním prostředí řídicí znak.|
|[IsDigit](../standard-library/locale-functions.md#isdigit)|Ověřuje, zda je prvek v národním prostředí číselný znak.|
|[isgraph](../standard-library/locale-functions.md#isgraph)|Ověřuje, zda je prvek v národním prostředí alfanumerický znak nebo znak interpunkce.|
|[islower](../standard-library/locale-functions.md#islower)|Ověřuje, zda je prvek v národním prostředí malé písmeno.|
|[isprint](../standard-library/locale-functions.md#isprint)|Ověřuje, zda je prvek v národním prostředí znak, který lze vytisknout.|
|[ispunct](../standard-library/locale-functions.md#ispunct)|Ověřuje, zda je prvek v národním prostředí znak interpunkce.|
|[isspace](../standard-library/locale-functions.md#isspace)|Ověřuje, zda je prvek v národním prostředí prázdný znak.|
|[isupper](../standard-library/locale-functions.md#isupper)|Ověřuje, zda je prvek v národním prostředí velké písmeno.|
|[isxdigit](../standard-library/locale-functions.md#isxdigit)|Ověřuje, zda je prvek v národním prostředí znak používaný ke znázornění šestnáctkového čísla.|
|[ToLower](../standard-library/locale-functions.md#tolower)|Převede znak na malé písmeno.|
|[ToUpper](../standard-library/locale-functions.md#toupper)|Převede znak na velké písmeno.|
|[use_facet](../standard-library/locale-functions.md#use_facet)|Vrátí odkaz na omezující vlastnost určitého typu uloženou v národním prostředí.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[codecvt –](../standard-library/codecvt-class.md)|Třída šablony poskytující omezující vlastnost potřebnou k převodu mezi interním a externím kódováním znaků.|
|[codecvt_base](../standard-library/codecvt-base-class.md)|Základní třída pro třídu codecvt, která slouží k definování typu výčtu uvedené jako `result`, která se používá jako návratový typ členských funkcí omezující vlastnosti k určení výsledku převodu.|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|Odvozená třída šablony popisující objekt, který může sloužit jako omezující vlastnost kolace daného národního prostředí a který umožňuje načtení informací specifických pro kulturní oblast v případě převodů.|
|[COLLATE –](../standard-library/collate-class.md)|Třída šablony kolace poskytující omezující vlastnost, která zpracovává konvence řazení řetězců.|
|[collate_byname](../standard-library/collate-byname-class.md)|Odvozená třída šablony popisující objekt, který může sloužit jako omezující vlastnost kolace daného národního prostředí a který umožňuje načtení informací specifických pro kulturní oblast v případě konvencí řazení řetězců.|
|[ctype](../standard-library/ctype-class.md)|Třída šablony poskytující omezující vlastnost, která se používá ke klasifikaci znaků, převodu z velkých a malých písmen a převodu mezi nativní znakovou sadou a sadou používanou národním prostředím.|
|[ctype\<char >](../standard-library/ctype-char-class.md)|Třída, která je explicitní specializací třídy šablony `ctype<CharType>` na typ **char**, popisující objekt, který může sloužit jako omezující vlastnost národního prostředí k charakterizaci různých vlastností znaku typu **char**.|
|[ctype_base](../standard-library/ctype-base-class.md)|Základní třída pro třídu ctype, která se používá k definování typů výčtu použitých ke klasifikaci nebo testování znaků buď jednotlivě, nebo v rámci celých rozsahů.|
|[ctype_byname](../standard-library/ctype-byname-class.md)|Odvozená třída šablony popisující objekt, který může sloužit jako omezující vlastnost ctype daného národního prostředí a který umožňuje klasifikaci znaků a převod znaků mezi velkými a malými písmeny a nativními znakovými sadami a znakovými sadami určenými pro národní prostředí.|
|[Národní prostředí](../standard-library/locale-class.md)|Třída, která popisuje místní objekt, který zapouzdří informace specifické pro jazykovou verzi jako sadu omezujících vlastností, jež společně definují určité lokalizované prostředí.|
|[Zprávy](../standard-library/messages-class.md)|Třída šablony popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí k načítání lokalizovaných zpráv z katalogu internacionalizovaných zpráv pro dané národní prostředí.|
|[messages_base](../standard-library/messages-base-class.md)|Základní třída, která popisuje **int** typ pro katalog zpráv.|
|[messages_byname](../standard-library/messages-byname-class.md)|Odvozená třída šablony popisující objekt, který může sloužit jako omezující vlastnost zprávy daného národního prostředí a který umožňuje načtení lokalizovaných zpráv.|
|[money_base](../standard-library/money-base-class.md)|Základní třída pro třídu ctype, která se používá k definování typů výčtu použitých ke klasifikaci nebo testování znaků buď jednotlivě, nebo v rámci celých rozsahů.|
|[money_get](../standard-library/money-get-class.md)|Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu sekvencí typu **CharType** na finanční hodnoty.|
|[money_put](../standard-library/money-put-class.md)|Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodů finančních hodnot na sekvence typu **CharType**.|
|[moneypunct –](../standard-library/moneypunct-class.md)|Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro popis sekvencí typu **CharType** používaných ke znázornění vstupního nebo peněžní výstupního pole.|
|[moneypunct_byname –](../standard-library/moneypunct-byname-class.md)|Odvozená třída šablony popisující objekt, který může sloužit jako omezující vlastnost moneypunct daného národního prostředí a který umožňuje formátování vstupních nebo výstupních polí pro finanční hodnoty.|
|[num_get](../standard-library/num-get-class.md)|Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu sekvencí typu **CharType** na číselné hodnoty.|
|[num_put](../standard-library/num-put-class.md)|Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu číselných hodnot na sekvence typu **CharType**.|
|[numpunct –](../standard-library/numpunct-class.md)|Třída šablony popisující objekt, který může sloužit jako místní omezující vlastnost pro popis sekvencí typu **CharType** používaných ke znázornění informací o formátování a interpunkci numerických a logických výrazů.|
|[numpunct_byname –](../standard-library/numpunct-byname-class.md)|Odvozená třída šablony popisující objekt, který může sloužit jako omezující vlastnost moneypunct daného národního prostředí a který umožňuje formátování a interpunkci numerických a logických výrazů.|
|[time_base](../standard-library/time-base-class.md)|Třída, která slouží jako základní třída pro omezující vlastnosti třídy šablony time_get, definující pouze pořadí dat typu výčtu a několik konstant tohoto typu.|
|[time_get](../standard-library/time-get-class.md)|Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu sekvencí typu **CharType** na hodnoty času.|
|[time_get_byname](../standard-library/time-get-byname-class.md)|Odvozená třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí typu time_get\<**CharType**, **InputIterator**>.|
|[time_put](../standard-library/time-put-class.md)|Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodů hodnot času na sekvence typu **CharType**.|
|[time_put_byname](../standard-library/time-put-byname-class.md)|Odvozená třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí typu `time_put` \< **CharType**, **OutputIterator**>.|
|[wbuffer_convert – třída](../standard-library/wbuffer-convert-class.md)|Popisuje vyrovnávací paměť datového proudu, který řídí přenosu prvky do a z vyrovnávací paměti datového proudu bajtů.|
|[wstring_convert – třída](../standard-library/wstring-convert-class.md)|Třída šablony, který provádí převody mezi širokého řetězce a řetězec bajtů.|

## <a name="see-also"></a>Viz také:

[Znakové stránky](../c-runtime-library/code-pages.md)<br/>
[Názvy národních prostředí, jazyků a Country/Region Strings](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
