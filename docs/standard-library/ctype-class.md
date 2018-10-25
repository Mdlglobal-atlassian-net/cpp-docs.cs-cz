---
title: ctype – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocale/std::ctype
- xlocale/std::ctype::char_type
- xlocale/std::ctype::do_is
- xlocale/std::ctype::do_narrow
- xlocale/std::ctype::do_scan_is
- xlocale/std::ctype::do_scan_not
- xlocale/std::ctype::do_tolower
- xlocale/std::ctype::do_toupper
- xlocale/std::ctype::do_widen
- xlocale/std::ctype::is
- xlocale/std::ctype::narrow
- xlocale/std::ctype::scan_is
- xlocale/std::ctype::scan_not
- xlocale/std::ctype::tolower
- xlocale/std::ctype::toupper
- xlocale/std::ctype::widen
dev_langs:
- C++
helpviewer_keywords:
- std::ctype [C++]
- std::ctype [C++], char_type
- std::ctype [C++], do_is
- std::ctype [C++], do_narrow
- std::ctype [C++], do_scan_is
- std::ctype [C++], do_scan_not
- std::ctype [C++], do_tolower
- std::ctype [C++], do_toupper
- std::ctype [C++], do_widen
- std::ctype [C++], is
- std::ctype [C++], narrow
- std::ctype [C++], scan_is
- std::ctype [C++], scan_not
- std::ctype [C++], tolower
- std::ctype [C++], toupper
- std::ctype [C++], widen
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1ccd20476d7888f687d077a3356ac51f2f1a529
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50082551"
---
# <a name="ctype-class"></a>ctype – třída

Třída poskytující omezující vlastnost, která se používá ke klasifikaci znaků, převodu z velkých a malých písmen a převodu mezi nativní znakovou sadou a sadou používanou národním prostředím.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ používaný v rámci programu ke kódování znaků.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložené hodnotě uloží jedinečnou kladnou hodnotu v `id`. Klasifikační kritéria mají k dispozici vnořený typ bitové masky v základní třídě ctype_base.

Standardní knihovny C++ definuje dvě explicitní specializace této třídy šablony:

- `ctype<char>`, jehož rozdíly jsou popsány odděleně explicitní specializace. Další informace najdete v tématu [ctype&lt;char&gt; třídy](../standard-library/ctype-char-class.md).

- `ctype<wchar_t>`, které považuje za prvky širokých znaků.

Ostatní specializace třídy šablony `ctype<CharType>`:

- Převést hodnotu *ch* typu *CharType* na hodnotu typu **char** s výrazem `(char)ch`.

- Převést hodnotu *bajtů* typu **char** na hodnotu typu *CharType* s výrazem `CharType(byte)`.

Všechny ostatní operace jsou prováděny na **char** hodnoty stejným způsobem jako pro explicitní specializaci `ctype<char>`.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ctype](#ctype)|Konstruktor pro objekty třídy `ctype` , který bude sloužit jako omezující vlastnosti národního prostředí pro znaky.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který popisuje znak používaný národním prostředním.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_is](#do_is)|Virtuální funkce volaná k ověření, zda má jeden znak konkrétní atribut, nebo ke klasifikaci atributů v jednotlivých kontejnerech v rozsahu a jejich uložení v poli.|
|[do_narrow](#do_narrow)|Virtuální funkce volaná k převodu znaku typu `CharType` používaný národním prostředím na odpovídající znak typu **char** v nativní znakové nastavit.|
|[do_scan_is](#do_scan_is)|Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který odpovídá zadané masce.|
|[do_scan_not](#do_scan_not)|Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který neodpovídá zadané masce.|
|[do_tolower](#do_tolower)|Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na malá písmena.|
|[do_toupper](#do_toupper)|Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na velká písmena.|
|[do_widen](#do_widen)|Virtuální funkce volaná k převodu znaku typu **char** v nativní znakové sadě na odpovídající znak typu `CharType` používaný národním prostředím.|
|[is](#is)|Ověřuje, zda má jeden znak konkrétní atribut, nebo klasifikuje atributy v jednotlivých kontejnerech v rozsahu a uloží je v poli.|
|[Upřesněte](#narrow)|Převede znak typu `CharType` používaný národním prostředím na odpovídající znak typu char v nativní znakové sadě.|
|[scan_is](#scan_is)|Vyhledá první znak v rozsahu, který odpovídá zadané masce.|
|[scan_not](#scan_not)|Vyhledá první znak v rozsahu, který neodpovídá zadané masce.|
|[ToLower](#tolower)|Převede znak nebo rozsah znaků na malá písmena.|
|[ToUpper](#toupper)|Převede znak nebo rozsah znaků na velká písmena.|
|[widen](#widen)|Převede znak typu **char** v nativní znakové sadě na odpovídající znak typu `CharType` používaný národním prostředím.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="char_type"></a>  ctype::char_type

Typ, který popisuje znak používaný národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *CharType*.

### <a name="example"></a>Příklad

Naleznete v členské funkci [rozšířit](#widen) příklad, který používá `char_type` jako návratovou hodnotu.

## <a name="ctype"></a>  ctype::ctype

Konstruktor pro objekty třídy ctype, která bude sloužit jako omezující vlastnosti národního prostředí pro znaky.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*<br/>
Celočíselná hodnota určuje typ Správa paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* parametrů a jejich význam:

- 0: Životnost objektu se spravuje přes národní prostředí, které je obsahují.

- 1: doba života objektu je nutné ručně spravovat.

- \> 1: tyto hodnoty nejsou definovány.

Žádné přímé příklady je to možné, protože destruktor je chráněn.

Konstruktor inicializuje jeho `locale::facet` základního objektu s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="do_is"></a>  ctype::do_is

Virtuální funkce volaná k ověření, zda má jeden znak konkrétní atribut, nebo ke klasifikaci atributů v jednotlivých kontejnerech v rozsahu a jejich uložení v poli.

```cpp
virtual bool do_is(
    mask maskVal,
    CharType ch) const;

virtual const CharType *do_is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parametry

*maskVal*<br/>
Hodnota masky, pro kterou je znak, který má být testována.

*ch*<br/>
Znak, jejichž atributy jsou má být testována.

*první*<br/>
Ukazatel na první znak v rozsahu, jejichž atributy jsou klasifikaci.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu, jejichž atributy jsou klasifikaci.

*cíl*<br/>
Ukazatel na začátku pole, kde jsou hodnoty masky charakterizuje atributy znaky mají být uloženy.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí logickou hodnotu, která je **true** Pokud znak testování má atribut popsal hodnota masky; **false** , pokud se mají atribut nepodaří.

Druhá členská funkce vrátí pole obsahující hodnoty masky charakterizuje atributy každý znak v rozsahu.

### <a name="remarks"></a>Poznámky

Hodnoty masky klasifikaci atributů znaky jsou k dispozici prostřednictvím třídy [ctype_base –](../standard-library/ctype-base-class.md), ze které ctype je odvozena. První členská funkce může přijmout výrazy pro její první parametr uvedené jako bitové masky a z kombinace hodnoty masky tvořen logické bitové operátory (&#124; &, ^, ~).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [je](#is), který volá `do_is`.

## <a name="do_narrow"></a>  ctype::do_narrow

Virtuální funkce volaná k převodu znaku typu `CharType` používaný národním prostředím na odpovídající znak typu **char** v nativní znakové nastavit.

```cpp
virtual char do_narrow(
    CharType ch,
    char default = '\0') const;

virtual const CharType* do_narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak typu `Chartype` používá národní prostředí, které má být převeden.

*default*<br/>
Výchozí hodnota pro přiřazení pomocí členské funkce znaky typu `CharType` , které nemají protějšek znaky typu **char**.

*první*<br/>
Ukazatel na první znak v rozsahu znaků, které mají být převedeny.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu znaků, které mají být převedeny.

*cíl*<br/>
Konstantní ukazatel na první znak typu **char** v cílovém rozsahu, který ukládá převedený rozsahu znaků.

### <a name="return-value"></a>Návratová hodnota

První chráněné členská funkce vrátí nativní znak typu char, který odpovídá znaku parametr typu `CharType` nebo *výchozí* Pokud není definován žádný protějšky.

Druhá chráněné členská funkce vrátí ukazatel do cílového rozsahu nativní znaků převést z znaky typu `CharType`.

### <a name="remarks"></a>Poznámky

Druhá chráněný člen šablony funkce úložiště v `dest`[ `I`] hodnota `do_narrow`( `first` [ `I`], `default`), pro `I` v intervalu [0, `last`  -  `first`).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [zúžit](#narrow), který volá `do_narrow`.

## <a name="do_scan_is"></a>  ctype::do_scan_is

Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který odpovídá zadané masce.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*<br/>
Hodnota masky k porovnání s znak.

*první*<br/>
Ukazatel na první znak v rozsahu ke kontrole.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu ke kontrole.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, který neodpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce hodnotu *poslední*.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce vrátí ukazatel na nejmenší `ptr` v rozsahu [ `first`, `last`) pro kterou [do_is –](#do_is)( `maskVal`, \* `ptr`) má hodnotu true.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [scan_is –](#scan_is), který volá `do_scan_is`.

## <a name="do_scan_not"></a>  ctype::do_scan_not

Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který neodpovídá zadané masce.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*<br/>
Hodnota masky není k porovnání s znak.

*první*<br/>
Ukazatel na první znak v rozsahu ke kontrole.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu ke kontrole.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, který neodpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce hodnotu *poslední*.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce vrátí ukazatel na nejmenší `ptr` v rozsahu [ `first`, `last`) pro kterou [do_is –](#do_is)( `maskVal`, \* `ptr`) má hodnotu false.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [scan_not –](#scan_not), který volá `do_scan_not`.

## <a name="do_tolower"></a>  ctype::do_tolower

Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na malá písmena.

```cpp
virtual CharType do_tolower(CharType ch) const;

virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak, který má být převeden na malá písmena.

*první*<br/>
Ukazatel na první znak v rozsahu znaků, jehož případy jsou má být převeden.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu znaků, jehož případy jsou má být převeden.

### <a name="return-value"></a>Návratová hodnota

První chráněná členská funkce vrátí malá formulář parametru *ch*. Pokud neexistuje žádný malá formulář, vrátí *ch*. Druhá chráněné členské funkce vrátí *poslední*.

### <a name="remarks"></a>Poznámky

Druhá funkce šablony chráněný člen nahradí každý prvek `first` [ `I`], pro `I` v intervalu [0, `last`  -  `first`), s `do_tolower`( `first` [ `I`]).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [tolower](#tolower), který volá `do_tolower`.

## <a name="do_toupper"></a>  ctype::do_toupper

Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na velká písmena.

```cpp
virtual CharType do_toupper(CharType ch) const;

virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak, který má být převeden na velká písmena.

*první*<br/>
Ukazatel na první znak v rozsahu znaků, jehož případy jsou má být převeden.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu znaků, jehož případy jsou má být převeden.

### <a name="return-value"></a>Návratová hodnota

První chráněná členská funkce vrátí velká formulář parametru *ch*. Pokud neexistuje žádný velká formulář, vrátí *ch*. Druhá chráněné členské funkce vrátí *poslední*.

### <a name="remarks"></a>Poznámky

Druhá funkce šablony chráněný člen nahradí každý prvek `first` [ `I`], pro `I` v intervalu [0, `last`  -  `first`), s `do_toupper`( `first` [ `I`]).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [toupper](#toupper), který volá `do_toupper`.

## <a name="do_widen"></a>  ctype::do_widen

Virtuální funkce volaná k převodu znaku typu **char** v nativní znakové sadě na odpovídající znak typu `CharType` používaný národním prostředím.

```cpp
virtual CharType do_widen(char byte) const;

virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Parametry

*byte*<br/>
Znak typu **char** v nativní znakové sadě má být převeden.

*první*<br/>
Ukazatel na první znak v rozsahu znaků, které mají být převedeny.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu znaků, které mají být převedeny.

*cíl*<br/>
Ukazatel na první znak typu `CharType` v cílovém rozsahu, který ukládá převedený rozsahu znaků.

### <a name="return-value"></a>Návratová hodnota

První chráněná členská funkce vrátí znak typu `CharType` , který odpovídá znaku parametr nativního typu **char**.

Druhá chráněné členská funkce vrátí ukazatel do cílového rozsahu znaků typu `CharType` používaný národním prostředím převést z nativní znaky typu **char**.

### <a name="remarks"></a>Poznámky

Druhá chráněný člen šablony funkce úložiště v `dest`[ `I`] hodnota `do_widen`( `first`[ `I`]), pro `I` v intervalu [0, `last`  -  `first`).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rozšířit](#widen), který volá `do_widen`.

## <a name="is"></a>  ctype::is

Ověřuje, zda jeden znak konkrétní atribut nebo klasifikuje atributy v jednotlivých kontejnerech v rozsahu a uloží je v poli.

```cpp
bool is(mask maskVal, CharType ch) const;

const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parametry

*maskVal*<br/>
Hodnota masky, pro kterou je znak, který má být testována.

*ch*<br/>
Znak, jejichž atributy jsou má být testována.

*první*<br/>
Ukazatel na první znak v rozsahu, jejichž atributy jsou klasifikaci.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu, jejichž atributy jsou klasifikaci.

*cíl*<br/>
Ukazatel na začátku pole, kde jsou hodnoty masky charakterizuje atributy znaky mají být uloženy.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí **true** Pokud znak testování má atribut popsal hodnota masky; **false** , pokud se mají atribut nepodaří.

Druhá členská funkce vrátí ukazatel na poslední znak v rozsahu, jejichž atributy se zařazují.

### <a name="remarks"></a>Poznámky

Hodnoty masky klasifikaci atributů znaky jsou k dispozici prostřednictvím třídy [ctype_base – třída](../standard-library/ctype-base-class.md), ze které ctype je odvozena. První členská funkce může přijmout výrazy pro její první parametr uvedené jako bitové masky a z kombinace hodnoty masky tvořen logické bitové operátory (&#124; &, ^, ~).

### <a name="example"></a>Příklad

```cpp
// ctype_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main() {
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );

   if (use_facet<ctype<char> > ( loc1 ).is( ctype_base::alpha, 'a' ))
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if (use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!' ))
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;

   char *string = "Hello, my name is John!";
   ctype<char>::mask maskarray[30];
   use_facet<ctype<char> > ( loc2 ).is(
      string, string + strlen(string), maskarray );
   for (unsigned int i = 0; i < strlen(string); i++) {
      cout << string[i] << ": "
           << (maskarray[i] & ctype_base::alpha  "alpha"
                                                : "not alpha")
           << endl;;
   };
}
```

## <a name="narrow"></a>  ctype::Narrow

Převede znaky typu `CharType` používaný národním prostředím na odpovídající znaky typu **char** v nativní znakové nastavit.

```cpp
char narrow(CharType ch, char default = '\0') const;

const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak typu `Chartype` používá národní prostředí, které má být převeden.

*default*<br/>
Výchozí hodnota pro přiřazení pomocí členské funkce znaky typu `CharType` , které nemají protějšek znaky typu **char**.

*první*<br/>
Ukazatel na první znak v rozsahu znaků, které mají být převedeny.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu znaků, které mají být převedeny.

*cíl*<br/>
Konstantní ukazatel na první znak typu **char** v cílovém rozsahu, který ukládá převedený rozsahu znaků.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí znak nativního typu **char** , který odpovídá znaku parametr typu `CharType default` Pokud není protějšek není definován.

Druhá členská funkce vrátí ukazatel do cílového rozsahu nativní znaků převést z znaky typu `CharType`.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [do_narrow –](#do_narrow)(`ch`, `default`). Druhá členská funkce vrátí [do_narrow –](#do_narrow) (`first`, `last`, `default`, `dest`). Je zaručeno, že pouze znaky základní zdroj jedinečný inverzní image obsahují `CharType` pod `narrow`. Pro tyto znaky základní zdroj obsahuje následující invariantní: `narrow` ( [rozšířit](#widen) ( **c** ), 0) == **c**.

### <a name="example"></a>Příklad

```cpp
// ctype_narrow.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "english" );
   wchar_t *str1 = L"\x0392fhello everyone";
   char str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).narrow
      ( str1, str1 + wcslen(str1), 'X', &str2[0] ) != 0);  // C4996
   str2[wcslen(str1)] = '\0';
   wcout << str1 << endl;
   cout << &str2[0] << endl;
}
```

```Output
Xhello everyone
```

## <a name="scan_is"></a>  ctype::scan_is

Vyhledá první znak v rozsahu, který odpovídá zadané masce.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*<br/>
Hodnota masky k porovnání s znak.

*první*<br/>
Ukazatel na první znak v rozsahu ke kontrole.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu ke kontrole.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, který neodpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce hodnotu *poslední*.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_scan_is –](#do_scan_is)(`maskVal`, `first`, `last`).

### <a name="example"></a>Příklad

```cpp
// ctype_scan_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_is
      ( ctype_base::punct, string, string + strlen(string) );
   cout << "The first punctuation is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
The first punctuation is "," at position: 5
```

## <a name="scan_not"></a>  ctype::scan_not

Vyhledá první znak v rozsahu, který neodpovídá zadané masce.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal*<br/>
Hodnota masky není k porovnání s znak.

*první*<br/>
Ukazatel na první znak v rozsahu ke kontrole.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu ke kontrole.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, který neodpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce hodnotu *poslední*.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_scan_not –](#do_scan_not)(`maskVal`, `first`, `last`).

### <a name="example"></a>Příklad

```cpp
// ctype_scan_not.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_not
      ( ctype_base::alpha, string, string + strlen(string) );
   cout << "First nonalpha character is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
First nonalpha character is "," at position: 5
```

## <a name="tolower"></a>  ctype::ToLower

Převede znak nebo rozsah znaků na malá písmena.

```cpp
CharType tolower(CharType ch) const;

const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak, který má být převeden na malá písmena.

*první*<br/>
Ukazatel na první znak v rozsahu znaků, jehož případy jsou má být převeden.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu znaků, jehož případy jsou má být převeden.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí malá forma parametru *ch*. Pokud neexistuje žádný malá formulář, vrátí *ch*.

Druhá členská funkce vrátí *poslední*.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [do_tolower –](#do_tolower)(`ch`). Druhá členská funkce vrátí [do_tolower –](#do_tolower)(`first`, `last`).

### <a name="example"></a>Příklad

```cpp
// ctype_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "HELLO, MY NAME IS JOHN";

   use_facet<ctype<char> > ( loc1 ).tolower
      ( string, string + strlen(string) );
   cout << "The lowercase string is: " << string << endl;
}
```

```Output
The lowercase string is: hello, my name is john
```

## <a name="toupper"></a>  ctype::ToUpper

Převede znak nebo rozsah znaků na velká písmena.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak, který má být převeden na velká písmena.

*první*<br/>
Ukazatel na první znak v rozsahu znaků, jehož případy jsou má být převeden.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu znaků, jehož případy jsou má být převeden.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí velká forma parametru *ch*. Pokud neexistuje žádný velká formulář, vrátí *ch*.

Druhá členská funkce vrátí *poslední*.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [do_toupper –](#do_toupper)(`ch`). Druhá členská funkce vrátí [do_toupper –](#do_toupper)( `first`, `last`).

### <a name="example"></a>Příklad

```cpp
// ctype_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "Hello, my name is John";

   use_facet<ctype<char> > ( loc1 ).toupper
      ( string, string + strlen(string) );
   cout << "The uppercase string is: " << string << endl;
}
```

```Output
The uppercase string is: HELLO, MY NAME IS JOHN
```

## <a name="widen"></a>  ctype::widen

Převede znak typu **char** v nativní znakové sadě na odpovídající znak typu `CharType` používaný národním prostředím.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Parametry

*byte*<br/>
Znak typu char v nativní znakové nastavit má být převeden.

*první*<br/>
Ukazatel na první znak v rozsahu znaků, které mají být převedeny.

*poslední*<br/>
Ukazatel na znak hned za poslední znak v rozsahu znaků, které mají být převedeny.

*cíl*<br/>
Ukazatel na první znak typu `CharType` v cílovém rozsahu, který ukládá převedený rozsahu znaků.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí znak typu `CharType` , který odpovídá znaku parametr nativního typu **char**.

Druhá členská funkce vrátí ukazatel do cílového rozsahu znaků typu `CharType` používaný národním prostředím převést z nativní znaky typu **char**.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [do_widen –](#do_widen)(`byte`). Druhá členská funkce vrátí [do_widen –](#do_widen)(`first`, `last`, `dest`).

### <a name="example"></a>Příklad

```cpp
// ctype_widen.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "English" );
   char *str1 = "Hello everyone!";
   wchar_t str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).widen
      ( str1, str1 + strlen(str1), &str2[0] ) != 0);  // C4996
   str2[strlen(str1)] = '\0';
   cout << str1 << endl;
   wcout << &str2[0] << endl;

   ctype<wchar_t>::char_type charT;
   charT = use_facet<ctype<char> > ( loc1 ).widen( 'a' );
}
```

```Output
Hello everyone!
Hello everyone!
```

## <a name="see-also"></a>Viz také:

[\<národní prostředí >](../standard-library/locale.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
