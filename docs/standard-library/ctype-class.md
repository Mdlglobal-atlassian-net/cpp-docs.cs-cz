---
title: ctype – třída | Microsoft Docs
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
ms.openlocfilehash: 0668e10bb1e9ccb54e356451b7d4efb1a75b5ac8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="ctype-class"></a>ctype – třída

Třída poskytující omezující vlastnost, která se používá ke klasifikaci znaků, převodu z velkých a malých písmen a převodu mezi nativní znakovou sadou a sadou používanou národním prostředím.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Parametry

`CharType` Typ v rámci programu použitá ke kódování znaků.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty **id.** Klasifikační kritéria mají k dispozici vnořený typ bitové masky v základní třídě ctype_base.

Standardní knihovna C++ definuje dvě explicitní specializací třídy tuto šablonu:

- [ctype](../standard-library/ctype-char-class.md)< `char`>, explicitní specializace, jejichž rozdíly jsou popsány samostatně.

- **ctype**< `wchar_t`>, která zpracovává elementy jako široké znaky.

Dalších specializací třídy šablony **ctype** \< **CharType**>:

- Převést hodnotu ***ch*** typu **CharType** na hodnotu typu `char` s výraz ( `char`) **ch**.

- Převést hodnotu ***bajtů*** typu `char` na hodnotu typu **CharType** s výraz **CharType** ( **bajtů**).

Všechny ostatní operace se provádí na `char` hodnoty stejným způsobem jako u explicitní specializace **ctype**< `char`>.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[ctype](#ctype)|Konstruktor pro objekty třídy `ctype` , sloužit jako národní prostředí omezující vlastnosti pro znaků.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který popisuje znak používaný národním prostředním.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_is](#do_is)|Virtuální funkce volaná k ověření, zda má jeden znak konkrétní atribut, nebo ke klasifikaci atributů v jednotlivých kontejnerech v rozsahu a jejich uložení v poli.|
|[do_narrow](#do_narrow)|Virtuální funkce volána převést znak typu `CharType` používá národní prostředí odpovídající znaku typ `char` nativní znakem nastavit.|
|[do_scan_is](#do_scan_is)|Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který odpovídá zadané masce.|
|[do_scan_not](#do_scan_not)|Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který neodpovídá zadané masce.|
|[do_tolower](#do_tolower)|Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na malá písmena.|
|[do_toupper](#do_toupper)|Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na velká písmena.|
|[do_widen](#do_widen)|Virtuální funkce volat za účelem převádí znak typu `char` v nativní znakovou sadu odpovídající znaku typ `CharType` používané v národním prostředí.|
|[is](#is)|Ověřuje, zda má jeden znak konkrétní atribut, nebo klasifikuje atributy v jednotlivých kontejnerech v rozsahu a uloží je v poli.|
|[zúžit](#narrow)|Převádí znak typu `CharType` používá národní prostředí odpovídající znaku znakový typ nativní znakovou sadu.|
|[scan_is](#scan_is)|Vyhledá první znak v rozsahu, který odpovídá zadané masce.|
|[scan_not](#scan_not)|Vyhledá první znak v rozsahu, který neodpovídá zadané masce.|
|[ToLower](#tolower)|Převede znak nebo rozsah znaků na malá písmena.|
|[ToUpper](#toupper)|Převede znak nebo rozsah znaků na velká písmena.|
|[widen](#widen)|Převádí znak typu `char` v nativní znakovou sadu odpovídající znaku typ `CharType` používané v národním prostředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="char_type"></a>  ctype::char_type

Typ, který popisuje znak používaný národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

### <a name="example"></a>Příklad

V tématu – členská funkce [widen](#widen) pro příklad, který používá `char_type` jako návratová hodnota.

## <a name="ctype"></a>  ctype::ctype

Konstruktor pro objekty třídy ctype, které slouží jako národní prostředí omezující vlastnosti pro znaky.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

`_Refs` Celočíselná hodnota určuje typ správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty `_Refs` parametrů a jejich významu jsou:

- 0: doba života objektu spravuje národní prostředí, které je obsahují.

- 1: doba života objektu, se musí ručně spravovat.

- \> 1: tyto hodnoty nejsou definovány.

Žádné přímé příklady je možné, protože je chráněn destruktoru.

Konstruktor inicializuje jeho `locale::facet` základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)( `_Refs`).

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

`maskVal` Hodnota masky, pro kterou má být testována znak.

`ch` Znak, jehož atributy jsou má být testována.

`first` Ukazatel na první znak v rozsahu, jejichž atributy se zařazují.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu, jejichž atributy se zařazují.

`dest` Ukazatel na začátek pole, kde jsou hodnoty masky charakterizuje atributy jednotlivých znaky k uložení.

### <a name="return-value"></a>Návratová hodnota

Vrátí logickou hodnotu, která je první členská funkce **true** Pokud testována znak má atribut popsaného hodnotu masky; **false** Pokud se nepodaří mají atribut.

Druhý členská funkce vrátí pole obsahující hodnoty masky charakterizuje atributy všechny znaky v rozsahu.

### <a name="remarks"></a>Poznámky

Hodnoty masky klasifikace atributy znaky jsou poskytovány třída [ctype_base](../standard-library/ctype-base-class.md), ze které ctype odvozena. První člen funkce může přijmout výrazy pro její první parametr označuje jako bitové masky a vytvořen z kombinace hodnoty masky tak logické bitové operátory (&#124; &, ^, ~).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [je](#is), který volá `do_is`.

## <a name="do_narrow"></a>  ctype::do_narrow

Virtuální funkce volána převést znak typu `CharType` používá národní prostředí odpovídající znaku typ `char` nativní znakem nastavit.

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

`ch` Znak typu `Chartype` používá národní prostředí má být převeden.

`default` Výchozí hodnota pro přiřazení funkcí člen znaků typu `CharType` které nemají protějšku znaky typu `char`.

`first` Ukazatel na první znak v rozsahu znaků, který má být převeden.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu znaků, který má být převeden.

`dest` Const ukazatel na první znak typu `char` v cílovém rozsahu, který ukládá převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

Vrátí první funkce chráněného člena nativní znak znakový typ, který odpovídá parametr znaku typ `CharType` nebo `default` Pokud je definována žádná protějšku.

Funkce second chráněného člena vrací ukazatel na cílový rozsah nativní znaků převést z znaky typu `CharType`.

### <a name="remarks"></a>Poznámky

Druhý chráněný člen šablony funkce úložiště v `dest`[ `I`] hodnota `do_narrow`( `first` [ `I`], `default`), pro `I` v intervalu [0, `last`  -  `first`).

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

`maskVal` Hodnota masky lze porovnat znakem.

`first` Ukazatel na první znak v rozsahu ke skenování.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu ke skenování.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, který bude odpovídat zadaná maska. Pokud žádná taková hodnota existuje, vrátí funkce `last.`

### <a name="remarks"></a>Poznámky

Vrátí nejmenší ukazatel funkce chráněného člena `ptr` v rozsahu [ `first`, `last`) pro kterou [do_is –](#do_is)( `maskVal`, * `ptr`) hodnotu true.

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

`maskVal` Hodnota masky tak, aby odpovídala znak.

`first` Ukazatel na první znak v rozsahu ke skenování.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu ke skenování.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, která neodpovídá zadané masky. Pokud žádná taková hodnota existuje, vrátí funkce `last`.

### <a name="remarks"></a>Poznámky

Vrátí nejmenší ukazatel funkce chráněného člena `ptr` v rozsahu [ `first`, `last`) pro kterou [do_is –](#do_is)( `maskVal`, * `ptr`) je hodnota false.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [scan_not –](#scan_not), který volá `do_scan_not`.

## <a name="do_tolower"></a>  ctype::do_tolower

Virtuální funkce volat za účelem převodu znak nebo rozsah znaků na malá písmena.

```cpp
virtual CharType do_tolower(CharType ch) const;


virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

`ch` Znak, který má být převeden na malá písmena.

`first` Ukazatel na první znak v rozsahu znaků, jejichž případech se převedou.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu znaků, jejichž případech se převedou.

### <a name="return-value"></a>Návratová hodnota

Vrátí první funkce chráněného člena malá formu parametr `ch`. Pokud neexistuje žádný malá formulář, vrátí `ch`. Druhý chráněný člen funkce vrátí `last`.

### <a name="remarks"></a>Poznámky

Druhý funkce šablony chráněného člena nahradí každý element `first` [ `I`], pro `I` v intervalu [0, `last`  -  `first`), s `do_tolower`( `first` [ `I`]).

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

`ch` Znak, který má být převeden na velká písmena.

`first` Ukazatel na první znak v rozsahu znaků, jejichž případech se převedou.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu znaků, jejichž případech se převedou.

### <a name="return-value"></a>Návratová hodnota

Vrátí první funkce chráněného člena velká formu parametr `ch`. Pokud neexistuje žádný velká formulář, vrátí `ch`. Druhý chráněný člen funkce vrátí `last`.

### <a name="remarks"></a>Poznámky

Druhý funkce šablony chráněného člena nahradí každý element `first` [ `I`], pro `I` v intervalu [0, `last`  -  `first`), s `do_toupper`( `first` [ `I`]).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [toupper](#toupper), který volá `do_toupper`.

## <a name="do_widen"></a>  ctype::do_widen

Virtuální funkce volat za účelem převádí znak typu `char` v nativní znakovou sadu odpovídající znaku typ `CharType` používané v národním prostředí.

```cpp
virtual CharType do_widen(char byte) const;


virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Parametry

`byte` Znak typu `char` v nativní znakovou sadu má být převeden.

`first` Ukazatel na první znak v rozsahu znaků, který má být převeden.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu znaků, který má být převeden.

`dest` Ukazatel na první znak typu `CharType` v cílovém rozsahu, který ukládá převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

První chráněného člena funkce vrátí znak typu `CharType` odpovídající parametr znaku nativní typ `char`.

Funkce second chráněného člena vrací ukazatel na cílový rozsah znaků typu `CharType` používané v národním prostředí převést z nativní znaky typu `char`.

### <a name="remarks"></a>Poznámky

Druhý chráněný člen šablony funkce úložiště v `dest`[ `I`] hodnota `do_widen`( `first`[ `I`]), pro `I` v intervalu [0, `last`  -  `first`).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [widen](#widen), který volá `do_widen`.

## <a name="is"></a>  ctype::is

Ověřuje, zda má konkrétní atribut nebo klasifikuje atributy každý znak v rozsahu a ukládá je do pole jednoho znaku.

```cpp
bool is(mask maskVal, CharType ch) const;


const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parametry

`maskVal` Hodnota masky, pro kterou má být testována znak.

`ch` Znak, jehož atributy jsou má být testována.

`first` Ukazatel na první znak v rozsahu, jejichž atributy se zařazují.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu, jejichž atributy se zařazují.

`dest` Ukazatel na začátek pole, kde jsou hodnoty masky charakterizuje atributy jednotlivých znaky k uložení.

### <a name="return-value"></a>Návratová hodnota

Vrátí první členská funkce `true` Pokud testována znak má atribut popsaného hodnotu masky; `false` Pokud se nepodaří mají atribut.

Druhý členská funkce vrátí poslední znak v rozsahu, jejichž atributy se zařazují ukazatel.

### <a name="remarks"></a>Poznámky

Hodnoty masky klasifikace atributy znaky jsou poskytovány třída [ctype_base – třída](../standard-library/ctype-base-class.md), ze které ctype odvozena. První člen funkce může přijmout výrazy pro její první parametr označuje jako bitové masky a vytvořen z kombinace hodnoty masky tak logické bitové operátory (&#124; &, ^, ~).

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

Převede znaky typu `CharType` používá národní prostředí odpovídající znaky typu `char` nativní znakem nastavit.

```cpp
char narrow(CharType ch, char default = '\0') const;


const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parametry

`ch` Znak typu `Chartype` používá národní prostředí má být převeden.

`default` Výchozí hodnota pro přiřazení funkcí člen znaků typu `CharType` které nemají protějšku znaky typu `char`.

`first` Ukazatel na první znak v rozsahu znaků, který má být převeden.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu znaků, který má být převeden.

`dest` Const ukazatel na první znak typu `char` v cílovém rozsahu, který ukládá převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

První člen funkce vrátí znak nativní typu `char` odpovídající parametr znaku typ `CharType default` Pokud protějšku není definovaná.

Druhý členská funkce vrátí ukazatel na cílový rozsah nativní znaků převést z znaky typu `CharType`.

### <a name="remarks"></a>Poznámky

Vrátí první členská funkce [do_narrow –](#do_narrow)( `ch`, `default`). Vrátí druhou členská funkce [do_narrow –](#do_narrow) ( `first`, `last`, `default`, `dest`). Pouze znaky základní zdroj kombinace obsahuje bitovou kopii jedinečný inverzní `CharType` pod `narrow`. Pro tyto znaky základní zdroj obsahuje následující neutrální: `narrow` ( [widen](#widen) ( **c** ), 0) == **c**.

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

`maskVal` Hodnota masky lze porovnat znakem.

`first` Ukazatel na první znak v rozsahu ke skenování.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu ke skenování.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, který bude odpovídat zadaná maska. Pokud žádná taková hodnota existuje, vrátí funkce `last.`

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [do_scan_is –](#do_scan_is)( `maskVal`, `first`, `last`).

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

`maskVal` Hodnota masky tak, aby odpovídala znak.

`first` Ukazatel na první znak v rozsahu ke skenování.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu ke skenování.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, který neodpovídá zadané masky. Pokud žádná taková hodnota existuje, vrátí funkce `last`.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [do_scan_not –](#do_scan_not)( `maskVal`, `first`, `last`).

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

`ch` Znak, který má být převeden na malá písmena.

`first` Ukazatel na první znak v rozsahu znaků, jejichž případech se převedou.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu znaků, jejichž případech se převedou.

### <a name="return-value"></a>Návratová hodnota

První člen funkce vrátí malá formu parametr `ch`. Pokud neexistuje žádný malá formulář, vrátí `ch`.

Vrátí druhou členská funkce `last`.

### <a name="remarks"></a>Poznámky

Vrátí první členská funkce [do_tolower –](#do_tolower)( `ch`). Vrátí druhou členská funkce [do_tolower –](#do_tolower)( `first`, `last`).

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

`ch` Znak, který má být převeden na velká písmena.

`first` Ukazatel na první znak v rozsahu znaků, jejichž případech se převedou.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu znaků, jejichž případech se převedou.

### <a name="return-value"></a>Návratová hodnota

První člen funkce vrátí velká formu parametr `ch`. Pokud neexistuje žádný velká formulář, vrátí `ch`.

Vrátí druhou členská funkce `last`.

### <a name="remarks"></a>Poznámky

Vrátí první členská funkce [do_toupper –](#do_toupper)( `ch`). Vrátí druhou členská funkce [do_toupper –](#do_toupper)( `first`, `last`).

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

Převádí znak typu `char` v nativní znakovou sadu odpovídající znaku typ `CharType` používané v národním prostředí.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Parametry

`byte` Nastavit znak znakový typ v nativní znak, který má být převeden.

`first` Ukazatel na první znak v rozsahu znaků, který má být převeden.

`last` Ukazatel na znak hned za jeho poslední znak v rozsahu znaků, který má být převeden.

`dest` Ukazatel na první znak typu `CharType` v cílovém rozsahu, který ukládá převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

První člen funkce vrátí znak typu `CharType` odpovídající parametr znaku nativní typ `char`.

Druhý členská funkce vrátí ukazatel na cílový rozsah znaků typu `CharType` používané v národním prostředí převést z nativní znaky typu `char`.

### <a name="remarks"></a>Poznámky

Vrátí první členská funkce [do_widen –](#do_widen)( `byte`). Vrátí druhou členská funkce [do_widen –](#do_widen)( `first`, `last`, `dest`).

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

## <a name="see-also"></a>Viz také

[\<národní prostředí >](../standard-library/locale.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
