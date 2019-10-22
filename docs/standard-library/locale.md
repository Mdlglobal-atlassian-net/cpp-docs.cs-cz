---
title: '&lt;locale &gt;'
ms.date: 11/04/2016
f1_keywords:
- <locale>
- locale/std::<locale>
- std::<locale>
helpviewer_keywords:
- locale header
ms.assetid: ca56f9d2-7128-44da-8df1-f4c78c17fbf2
ms.openlocfilehash: 71182f4a527fba0ef2c91dc84be5a8faad9fc99f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687802"
---
# <a name="ltlocalegt"></a>&lt;locale &gt;

Definuje šablony tříd a funkce, C++ které můžou programy použít k zapouzdření a manipulaci s různými kulturami, které se týkají reprezentace a formátování číselných, měnových a kalendářních dat, včetně podpory pro mezinárodní účely. pro klasifikaci znaků a kolaci řetězců.

## <a name="syntax"></a>Syntaxe

```cpp
#include <locale>
```

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[has_facet](../standard-library/locale-functions.md#has_facet)|Ověřuje, zda je v zadaném národním prostředí uložena konkrétní omezující vlastnost.|
|[isalnum](../standard-library/locale-functions.md#isalnum)|Ověřuje, zda je prvek v národním prostředí abecední, nebo číselný znak.|
|[v-alfa](../standard-library/locale-functions.md#isalpha)|Ověřuje, zda je prvek v národním prostředí abecední znak.|
|[iscntrl](../standard-library/locale-functions.md#iscntrl)|Ověřuje, zda je prvek v národním prostředí řídicí znak.|
|[IsDigit](../standard-library/locale-functions.md#isdigit)|Ověřuje, zda je prvek v národním prostředí číselný znak.|
|[graf](../standard-library/locale-functions.md#isgraph)|Ověřuje, zda je prvek v národním prostředí alfanumerický znak nebo znak interpunkce.|
|[snížit](../standard-library/locale-functions.md#islower)|Ověřuje, zda je prvek v národním prostředí malé písmeno.|
|[Tisk](../standard-library/locale-functions.md#isprint)|Ověřuje, zda je prvek v národním prostředí znak, který lze vytisknout.|
|[ispunct](../standard-library/locale-functions.md#ispunct)|Ověřuje, zda je prvek v národním prostředí znak interpunkce.|
|[místo](../standard-library/locale-functions.md#isspace)|Ověřuje, zda je prvek v národním prostředí prázdný znak.|
|[– horní](../standard-library/locale-functions.md#isupper)|Ověřuje, zda je prvek v národním prostředí velké písmeno.|
|[isxdigit](../standard-library/locale-functions.md#isxdigit)|Ověřuje, zda je prvek v národním prostředí znak používaný ke znázornění šestnáctkového čísla.|
|[ToLower](../standard-library/locale-functions.md#tolower)|Převede znak na malé písmeno.|
|[ToUpper](../standard-library/locale-functions.md#toupper)|Převede znak na velké písmeno.|
|[use_facet](../standard-library/locale-functions.md#use_facet)|Vrátí odkaz na omezující vlastnost určitého typu uloženou v národním prostředí.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[codecvt](../standard-library/codecvt-class.md)|Šablona třídy, která poskytuje omezující vlastnost, která slouží k převodu mezi interními a externími kódováními znaků.|
|[codecvt_base](../standard-library/codecvt-base-class.md)|Základní třída pro třídu codecvt, která se používá k definování typu výčtu označovaného jako `result`, použit jako návratový typ pro členské funkce omezující podmínky k indikaci výsledku převodu.|
|[codecvt_byname](../standard-library/codecvt-byname-class.md)|Šablona odvozené třídy popisující objekt, který může sloužit jako omezující vlastnost COLLATE daného národního prostředí a který umožňuje načtení informací specifických pro kulturní oblast týkající se převodů.|
|[COLLATE](../standard-library/collate-class.md)|Šablona třídy kompletování, která poskytuje omezující vlastnost, která zpracovává konvence řazení řetězců.|
|[collate_byname](../standard-library/collate-byname-class.md)|Šablona odvozené třídy popisující objekt, který může sloužit jako omezující vlastnost COLLATE daného národního prostředí a který umožňuje načtení informací specifických pro kulturní oblast týkající se konvencí řazení řetězců.|
|[CType](../standard-library/ctype-class.md)|Šablona třídy, která poskytuje omezující vlastnost, která se používá ke klasifikaci znaků, převodu z velkých a malých písmen a mezi nativní znakovou sadou a sadou, kterou používá národní prostředí.|
|[CType \<char >](../standard-library/ctype-char-class.md)|Třída, která je explicitní specializací šablony třídy `ctype<CharType>` k typu **char**, popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro charakterizaci různých vlastností znaku typu **char**.|
|[ctype_base](../standard-library/ctype-base-class.md)|Základní třída pro třídu ctype, která se používá k definování typů výčtu použitých ke klasifikaci nebo testování znaků buď jednotlivě, nebo v rámci celých rozsahů.|
|[ctype_byname](../standard-library/ctype-byname-class.md)|Šablona odvozené třídy, která popisuje objekt, který může sloužit jako omezující vlastnost CType daného národního prostředí, umožňující klasifikaci znaků a převod znaků mezi velikostmi písmen a nativním a národním systémem zadaným znakovým sadám.|
|[jazyka](../standard-library/locale-class.md)|Třída, která popisuje místní objekt, který zapouzdří informace specifické pro jazykovou verzi jako sadu omezujících vlastností, jež společně definují určité lokalizované prostředí.|
|[zprávy](../standard-library/messages-class.md)|Šablona třídy popisující objekt, který může sloužit jako omezující vlastnost národního prostředí k načítání lokalizovaných zpráv z katalogu mezinárodních zpráv pro dané národní prostředí.|
|[messages_base](../standard-library/messages-base-class.md)|Základní třída, která popisuje typ **int** pro katalog zpráv.|
|[messages_byname](../standard-library/messages-byname-class.md)|Šablona odvozené třídy popisující objekt, který může sloužit jako omezující vlastnost zprávy daného národního prostředí a který umožňuje načtení lokalizovaných zpráv.|
|[money_base](../standard-library/money-base-class.md)|Základní třída pro třídu ctype, která se používá k definování typů výčtu použitých ke klasifikaci nebo testování znaků buď jednotlivě, nebo v rámci celých rozsahů.|
|[money_get](../standard-library/money-get-class.md)|Šablona třídy popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodů sekvencí typu **CharType** na peněžní hodnoty.|
|[money_put](../standard-library/money-put-class.md)|Šablona třídy popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu peněžních hodnot na sekvence typu **CharType**.|
|[moneypunct](../standard-library/moneypunct-class.md)|Šablona třídy, která popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro popis sekvencí typu **CharType** , který představuje peněžní vstupní pole nebo pole s peněžním výstupem.|
|[moneypunct_byname](../standard-library/moneypunct-byname-class.md)|Šablona odvozené třídy popisující objekt, který může sloužit jako omezující vlastnost moneypunct daného národního prostředí a který povoluje formátování peněžních vstupních nebo výstupních polí.|
|[num_get](../standard-library/num-get-class.md)|Šablona třídy popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodů sekvencí typu **CharType** na číselné hodnoty.|
|[num_put](../standard-library/num-put-class.md)|Šablona třídy popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu číselných hodnot na sekvence typu **CharType**.|
|[numpunct](../standard-library/numpunct-class.md)|Šablona třídy popisující objekt, který může sloužit jako místní omezující vlastnost pro popis sekvencí typu **CharType** používaných k reprezentaci informací o formátování a interpunkci číselných a logických výrazů.|
|[numpunct_byname](../standard-library/numpunct-byname-class.md)|Šablona odvozené třídy popisující objekt, který může sloužit jako omezující vlastnost moneypunct daného národního prostředí a který umožňuje formátování a interpunkci číselných a logických výrazů.|
|[time_base](../standard-library/time-base-class.md)|Třída, která slouží jako základní třída pro omezující vlastnosti třídy Template time_get, definující pouze Výčtový typ výčtu a několik konstant tohoto typu.|
|[time_get](../standard-library/time-get-class.md)|Šablona třídy popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodů sekvencí typu **CharType** na hodnoty času.|
|[time_get_byname](../standard-library/time-get-byname-class.md)|Šablona odvozené třídy popisující objekt, který může sloužit jako omezující vlastnost národního prostředí typu time_get \<**CharType**, **InputIterator**>.|
|[time_put](../standard-library/time-put-class.md)|Šablona třídy popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení převodu časových hodnot na sekvence typu **CharType**.|
|[time_put_byname](../standard-library/time-put-byname-class.md)|Šablona odvozené třídy popisující objekt, který může sloužit jako omezující vlastnost národního prostředí typu `time_put` \<**CharType**, **OutputIterator**>.|
|[wbuffer_convert – třída](../standard-library/wbuffer-convert-class.md)|Popisuje vyrovnávací paměť datového proudu, která řídí přenos prvků do a z vyrovnávací paměti datového proudu bajtů.|
|[wstring_convert – třída](../standard-library/wstring-convert-class.md)|Šablona třídy, která provádí převody mezi šířkou řetězce a bajtovým řetězcem.|

## <a name="see-also"></a>Viz také:

[Znakové stránky](../c-runtime-library/code-pages.md) \
[Názvy národních prostředí, jazyky a řetězce země/oblasti](../c-runtime-library/locale-names-languages-and-country-region-strings.md) \
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
