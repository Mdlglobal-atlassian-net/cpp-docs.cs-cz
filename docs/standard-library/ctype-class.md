---
title: ctype – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: dae6f62a0eda9263986a77b82754596d17be94e5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373157"
---
# <a name="ctype-class"></a>ctype – třída

Třída poskytující omezující vlastnost, která se používá ke klasifikaci znaků, převodu z velkých a malých písmen a převodu mezi nativní znakovou sadou a sadou používanou národním prostředím.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě `id`ukládá jedinečnou kladnou hodnotu v aplikaci . Klasifikační kritéria mají k dispozici vnořený typ bitové masky v základní třídě ctype_base.

Standardní knihovna jazyka C++ definuje dvě explicitní specializace této šablony třídy:

- `ctype<char>`, explicitní specializace, jejíž rozdíly jsou popsány samostatně. Další informace naleznete [v&lt;&gt; tématu ctype char Class](../standard-library/ctype-char-class.md).

- `ctype<wchar_t>`, který zachází s prvky jako s širokými znaky.

Další specializace třídy `ctype<CharType>`šablony :

- Převeďte hodnotu *ch* typu *CharType* na hodnotu typu **char** s výrazem `(char)ch`.

- Převeďte *bajt* hodnoty **typu char** na hodnotu typu *CharType* s výrazem `CharType(byte)`.

Všechny ostatní operace jsou prováděny na **char** hodnoty stejným `ctype<char>`způsobem jako pro explicitní specializace .

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[Ctype](#ctype)|Konstruktor pro objekty třídy, `ctype` které slouží jako národní omezující znaky.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který popisuje znak používaný národním prostředním.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_is](#do_is)|Virtuální funkce volaná k ověření, zda má jeden znak konkrétní atribut, nebo ke klasifikaci atributů v jednotlivých kontejnerech v rozsahu a jejich uložení v poli.|
|[do_narrow](#do_narrow)|Virtuální funkce volaná k `CharType` převodu znaku typu používaného národním prostředím na odpovídající znak **typu char** v nativní znakové sadě.|
|[do_scan_is](#do_scan_is)|Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který odpovídá zadané masce.|
|[do_scan_not](#do_scan_not)|Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který neodpovídá zadané masce.|
|[do_tolower](#do_tolower)|Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na malá písmena.|
|[do_toupper](#do_toupper)|Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na velká písmena.|
|[do_widen](#do_widen)|Virtuální funkce volaná k převodu znaku **typu char** v nativní znakové sadě na odpovídající znak typu `CharType` používaný národním prostředím.|
|[is](#is)|Ověřuje, zda má jeden znak konkrétní atribut, nebo klasifikuje atributy v jednotlivých kontejnerech v rozsahu a uloží je v poli.|
|[Úzké](#narrow)|Převede znak typu `CharType` používaný národním prostředím na odpovídající znak znaku typu v nativní znakové sadě.|
|[scan_is](#scan_is)|Vyhledá první znak v rozsahu, který odpovídá zadané masce.|
|[scan_not](#scan_not)|Vyhledá první znak v rozsahu, který neodpovídá zadané masce.|
|[Tolower](#tolower)|Převede znak nebo rozsah znaků na malá písmena.|
|[Toupper](#toupper)|Převede znak nebo rozsah znaků na velká písmena.|
|[Rozšířit](#widen)|Převede znak **znaku** typu v nativní znakové `CharType` sadě na odpovídající znak typu používaný národním prostředím.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="ctypechar_type"></a><a name="char_type"></a>ctype::char_type

Typ, který popisuje znak používaný národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro parametr šablony *CharType*.

### <a name="example"></a>Příklad

Viz rozšíření členské [funkce](#widen) pro `char_type` příklad, který používá jako vrácenou hodnotu.

## <a name="ctypectype"></a><a name="ctype"></a>ctype::ctype

Konstruktor pro objekty třídy ctype, které slouží jako národní omezující znaky.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Celá hodnota používaná k určení typu správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* a jejich význam jsou:

- 0: Životnost objektu je spravována národními prostředími, které jej obsahují.

- 1: Životnost objektu musí být spravována ručně.

- \>1: Tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože destruktor je chráněn.

Konstruktor inicializuje `locale::facet` svůj základní objekt pomocí **národního prostředí::**[omezující stolku](../standard-library/locale-class.md#facet_class)( `_Refs`).

## <a name="ctypedo_is"></a><a name="do_is"></a>ctype::do_is

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

*maskaVal*\
Hodnota masky, pro kterou má být znak testován.

*Ch*\
Znak, jehož atributy mají být testovány.

*První*\
Ukazatel na první znak v rozsahu, jehož atributy mají být klasifikovány.

*Poslední*\
Ukazatel na znak bezprostředně následující poslední znak v rozsahu, jehož atributy mají být klasifikovány.

*Dest*\
Ukazatel na začátek pole, kde mají být uloženy hodnoty masky charakterizující atributy každého z těchto znaků.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí logickou hodnotu, která je **pravdivá,** pokud testovaný znak má atribut popsaný hodnotou masky; **false,** pokud se nezdaří mít atribut.

Druhá členská funkce vrátí pole obsahující hodnoty masky charakterizující atributy každého ze znaků v rozsahu.

### <a name="remarks"></a>Poznámky

Hodnoty masky klasifikující atributy znaků jsou poskytovány třídou [ctype_base](../standard-library/ctype-base-class.md), ze které ctype odvozuje. První členská funkce může přijímat výrazy pro svůj první parametr označovaný jako bitové masky a vytvořené z kombinace hodnot masky logickými bitovými operátory (&#124; , & , ^ , ~).

### <a name="example"></a>Příklad

Viz příklad pro [je](#is) `do_is`, který volá .

## <a name="ctypedo_narrow"></a><a name="do_narrow"></a>ctype::do_úzký

Virtuální funkce volaná k `CharType` převodu znaku typu používaného národním prostředím na odpovídající znak **typu char** v nativní znakové sadě.

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

*Ch*\
Znak typu, `Chartype` který má národní prostředí převést.

*Výchozí*\
Výchozí hodnota, kterou má členská funkce `CharType` přiřadit k znakům typu, které nemají znaky protějšku typu **char**.

*První*\
Ukazatel na první znak v rozsahu znaků, které mají být převedeny.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v rozsahu znaků, které mají být převedeny.

*Dest*\
Const ukazatel na první znak typu **char** v cílové oblasti, která ukládá převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

První chráněná členská funkce vrátí nativní znak typu char, `CharType` který odpovídá znaku parametru typu nebo *defaultu,* pokud není definován žádný protějšek.

Druhá chráněná členská funkce vrátí ukazatel do cílového rozsahu `CharType`nativních znaků převedených ze znaků typu .

### <a name="remarks"></a>Poznámky

Druhá chráněná funkce šablony `dest` `I`člena ukládá `do_narrow` `first` do `I` `default`[ `I` ] hodnotu ( `last`  -  `first`[ ], ), pro jivšak v intervalu [0,).

### <a name="example"></a>Příklad

Viz příklad pro [úzký](#narrow) `do_narrow`, který volá .

## <a name="ctypedo_scan_is"></a><a name="do_scan_is"></a>ctype::do_scan_is

Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který odpovídá zadané masce.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskaVal*\
Hodnota masky, která má být spárována znakem.

*První*\
Ukazatel na první znak v oblasti, která má být skenována.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v oblasti, který má být zkontrolován.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v oblasti, která odpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce *hodnotu last*.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce `ptr` vrátí nejmenší `first`ukazatel `last`v rozsahu [ \* `ptr`, ), pro který je [true do_is](#do_is)( `maskVal`, ).

### <a name="example"></a>Příklad

Viz příklad pro [scan_is](#scan_is) `do_scan_is`, který volá .

## <a name="ctypedo_scan_not"></a><a name="do_scan_not"></a>ctype::do_scan_not

Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který neodpovídá zadané masce.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskaVal*\
Hodnota masky, která nemá odpovídat znaku.

*První*\
Ukazatel na první znak v oblasti, která má být skenována.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v oblasti, který má být zkontrolován.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v oblasti, která neodpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce *hodnotu last*.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce `ptr` vrátí nejmenší `first`ukazatel `last`v rozsahu [ \* `ptr`, ), pro který je [do_is](#do_is)( `maskVal`, ) false.

### <a name="example"></a>Příklad

Viz příklad pro [scan_not](#scan_not) `do_scan_not`, který volá .

## <a name="ctypedo_tolower"></a><a name="do_tolower"></a>ctype::do_tolower

Virtuální funkce volaná pro převod znaku nebo rozsahu znaků na malá písmena.

```cpp
virtual CharType do_tolower(CharType ch) const;

virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, který má být převeden na malá písmena.

*První*\
Ukazatel na první znak v rozsahu znaků, jejichž případy mají být převedeny.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v rozsahu znaků, jejichž případy mají být převedeny.

### <a name="return-value"></a>Návratová hodnota

První chráněná členská funkce vrátí tvar malé písmena parametru *ch*. Pokud neexistuje žádný formulář s nižšími písmeny, vrátí *vrátí ch*. Druhá chráněná členská funkce vrátí *poslední*.

### <a name="remarks"></a>Poznámky

Druhá chráněná funkce šablony člena `first` `I`nahradí `I` každý prvek [ `last`  -  `first`], `do_tolower`pro `first` `I`v intervalu [0, ), s ( [ ]).

### <a name="example"></a>Příklad

Viz příklad pro [tolower](#tolower) `do_tolower`, který volá .

## <a name="ctypedo_toupper"></a><a name="do_toupper"></a>ctype::do_toupper

Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na velká písmena.

```cpp
virtual CharType do_toupper(CharType ch) const;

virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, který má být převeden na velká písmena.

*První*\
Ukazatel na první znak v rozsahu znaků, jejichž případy mají být převedeny.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v rozsahu znaků, jejichž případy mají být převedeny.

### <a name="return-value"></a>Návratová hodnota

První chráněná členská funkce vrátí horní tvar parametru *ch*. Pokud neexistuje žádný formulář velkých písmen, vrátí *ch*. Druhá chráněná členská funkce vrátí *poslední*.

### <a name="remarks"></a>Poznámky

Druhá chráněná funkce šablony člena `first` `I`nahradí `I` každý prvek [ `last`  -  `first`], `do_toupper`pro `first` `I`v intervalu [0, ), s ( [ ]).

### <a name="example"></a>Příklad

Viz příklad pro [toupper](#toupper) `do_toupper`, který volá .

## <a name="ctypedo_widen"></a><a name="do_widen"></a>ctype::do_widen

Virtuální funkce volaná k převodu znaku **typu char** v nativní znakové sadě na odpovídající znak typu `CharType` používaný národním prostředím.

```cpp
virtual CharType do_widen(char byte) const;

virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Parametry

*Bajt*\
Znak typu **char** v nativní znakové sadě, která má být převedena.

*První*\
Ukazatel na první znak v rozsahu znaků, které mají být převedeny.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v rozsahu znaků, které mají být převedeny.

*Dest*\
Ukazatel na první znak `CharType` typu v cílové oblasti, který ukládá převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

První chráněná členská funkce `CharType` vrátí znak typu, který odpovídá znaku parametru znaku nativního typu **char**.

Druhá chráněná členská funkce vrátí ukazatel do `CharType` cílového rozsahu znaků používaných národním prostředím převedeným z nativních znaků typu **char**.

### <a name="remarks"></a>Poznámky

Druhá chráněná funkce šablony `dest` `I`člena ukládá `do_widen` `first`do `I`[ `I` ] hodnotu ( `last`  -  `first`[ ]), pro v intervalu [0, ).

### <a name="example"></a>Příklad

Viz příklad pro [rozšíření](#widen) `do_widen`, který volá .

## <a name="ctypeis"></a><a name="is"></a>ctype::je

Testuje, zda jeden znak má určitý atribut nebo klasifikuje atributy každého znaku v oblasti a ukládá je do pole.

```cpp
bool is(mask maskVal, CharType ch) const;

const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parametry

*maskaVal*\
Hodnota masky, pro kterou má být znak testován.

*Ch*\
Znak, jehož atributy mají být testovány.

*První*\
Ukazatel na první znak v rozsahu, jehož atributy mají být klasifikovány.

*Poslední*\
Ukazatel na znak bezprostředně následující poslední znak v rozsahu, jehož atributy mají být klasifikovány.

*Dest*\
Ukazatel na začátek pole, kde mají být uloženy hodnoty masky charakterizující atributy každého z těchto znaků.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí **hodnotu true,** pokud testovaný znak má atribut popsaný hodnotou masky; **false,** pokud se nezdaří mít atribut.

Druhá členská funkce vrátí ukazatel na poslední znak v rozsahu, jehož atributy mají být klasifikovány.

### <a name="remarks"></a>Poznámky

Hodnoty masky klasifikující atributy znaků jsou poskytovány třídou [ctype_base Class](../standard-library/ctype-base-class.md), ze které ctype odvozuje. První členská funkce může přijímat výrazy pro svůj první parametr označovaný jako bitové masky a vytvořené z kombinace hodnot masky logickými bitovými operátory (&#124; , & , ^ , ~).

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

## <a name="ctypenarrow"></a><a name="narrow"></a>ctype::úzký

Převede znaky `CharType` typu používané národním prostředím na odpovídající znaky **znaku** typu v nativní znakové sadě.

```cpp
char narrow(CharType ch, char default = '\0') const;

const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak typu, `Chartype` který má národní prostředí převést.

*Výchozí*\
Výchozí hodnota, kterou má členská funkce `CharType` přiřadit k znakům typu, které nemají znaky protějšku typu **char**.

*První*\
Ukazatel na první znak v rozsahu znaků, které mají být převedeny.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v rozsahu znaků, které mají být převedeny.

*Dest*\
Const ukazatel na první znak typu **char** v cílové oblasti, která ukládá převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí nativní znak typu **char,** který `CharType default` odpovídá znaku parametru typu, pokud není definován protějšek.

Druhá členská funkce vrátí ukazatel do cílového rozsahu nativních znaků převedených ze znaků typu `CharType`.

### <a name="remarks"></a>Poznámky

První členská funkce`ch`vrátí `default` [do_narrow](#do_narrow)( , ). Druhá členská funkce`first`vrátí `last` `default`do_narrow `dest`( , , ). [do_narrow](#do_narrow) Pouze základní zdrojové znaky jsou zaručeny `CharType` mít `narrow`jedinečný inverzní obraz pod . Pro tyto základní zdrojové znaky platí `narrow` následující invariantní znaky: ( [widen](#widen) ( **c** ), 0 ) == **c**.

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

## <a name="ctypescan_is"></a><a name="scan_is"></a>ctype::scan_is

Vyhledá první znak v rozsahu, který odpovídá zadané masce.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskaVal*\
Hodnota masky, která má být spárována znakem.

*První*\
Ukazatel na první znak v oblasti, která má být skenována.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v oblasti, který má být zkontrolován.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v oblasti, která odpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce *hodnotu last*.

### <a name="remarks"></a>Poznámky

Členská funkce [do_scan_is](#do_scan_is)vrátí`maskVal` `first`do_scan_is `last`( , , ).

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

## <a name="ctypescan_not"></a><a name="scan_not"></a>ctype::scan_not

Vyhledá první znak v rozsahu, který neodpovídá zadané masce.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskaVal*\
Hodnota masky, která nemá odpovídat znaku.

*První*\
Ukazatel na první znak v oblasti, která má být skenována.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v oblasti, který má být zkontrolován.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v oblasti, která neodpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce *hodnotu last*.

### <a name="remarks"></a>Poznámky

Členská funkce [do_scan_not](#do_scan_not)vrátí`maskVal` `first`do_scan_not `last`( , , ).

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

## <a name="ctypetolower"></a><a name="tolower"></a>ctype::tolower

Převede znak nebo rozsah znaků na malá písmena.

```cpp
CharType tolower(CharType ch) const;

const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, který má být převeden na malá písmena.

*První*\
Ukazatel na první znak v rozsahu znaků, jejichž případy mají být převedeny.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v rozsahu znaků, jejichž případy mají být převedeny.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí tvar malé písmena parametru *ch*. Pokud neexistuje žádný formulář s nižšími písmeny, vrátí *vrátí ch*.

Druhá členská funkce vrátí *poslední*.

### <a name="remarks"></a>Poznámky

První členská [do_tolower](#do_tolower)funkce`ch`vrátí do_tolower ( ). Druhá členská funkce`first`vrátí `last` [do_tolower](#do_tolower)( , ).

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

## <a name="ctypetoupper"></a><a name="toupper"></a>ctype::toupper

Převede znak nebo rozsah znaků na velká písmena.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*Ch*\
Znak, který má být převeden na velká písmena.

*První*\
Ukazatel na první znak v rozsahu znaků, jejichž případy mají být převedeny.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v rozsahu znaků, jejichž případy mají být převedeny.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí horní tvar parametru *ch*. Pokud neexistuje žádný formulář velkých písmen, vrátí *ch*.

Druhá členská funkce vrátí *poslední*.

### <a name="remarks"></a>Poznámky

První členská [do_toupper](#do_toupper)funkce`ch`vrátí do_toupper ( ). Druhá členská funkce `first`vrátí `last` [do_toupper](#do_toupper)( , ).

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

## <a name="ctypewiden"></a><a name="widen"></a>ctype::rozšířit

Převede znak **znaku** typu v nativní znakové `CharType` sadě na odpovídající znak typu používaný národním prostředím.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Parametry

*Bajt*\
Znak typu char v nativní znakové sadě, která má být převedena.

*První*\
Ukazatel na první znak v rozsahu znaků, které mají být převedeny.

*Poslední*\
Ukazatel na znak bezprostředně následující za posledním znakem v rozsahu znaků, které mají být převedeny.

*Dest*\
Ukazatel na první znak `CharType` typu v cílové oblasti, který ukládá převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí `CharType` znak typu, který odpovídá znaku parametru znaku nativního typu **char**.

Druhá členská funkce vrátí ukazatel do cílového `CharType` rozsahu znaků používaných národním prostředím převedeným z nativních znaků typu **char**.

### <a name="remarks"></a>Poznámky

První členská [do_widen](#do_widen)funkce`byte`vrátí do_widen ( ). Druhá členská funkce`first`vrátí `last` `dest` [do_widen](#do_widen)( , , ).

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

[\<>národního prostředí](../standard-library/locale.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
