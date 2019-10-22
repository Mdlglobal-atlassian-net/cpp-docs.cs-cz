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
ms.openlocfilehash: 640b2cc8506e498006feedbea6825a0e51a88209
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688172"
---
# <a name="ctype-class"></a>ctype – třída

Třída poskytující omezující vlastnost, která se používá ke klasifikaci znaků, převodu z velkých a malých písmen a převodu mezi nativní znakovou sadou a sadou používanou národním prostředím.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>Parametry

*CharType* \
Typ používaný v rámci programu ke kódování znaků.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v `id` jedinečnou kladnou hodnotu. Klasifikační kritéria mají k dispozici vnořený typ bitové masky v základní třídě ctype_base.

C++ Standardní knihovna definuje dvě explicitní specializace této šablony třídy:

- `ctype<char>` explicitní specializace, jejíž rozdíly jsou popsány samostatně. Další informace naleznete v tématu [ctype &lt;char &gt; třídy](../standard-library/ctype-char-class.md).

- `ctype<wchar_t>`, který zpracovává prvky jako velké znaky.

Další specializace šablony třídy `ctype<CharType>`:

- Převeďte hodnotu *ch* typu *CharType* na hodnotu typu **char** s výrazem `(char)ch`.

- Převeďte *bajt* hodnoty typu **char** na hodnotu typu *CharType* s výrazem `CharType(byte)`.

Všechny ostatní operace se provádí na hodnotách typu **char** stejným způsobem jako u explicitní specializace `ctype<char>`.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[CType](#ctype)|Konstruktor pro objekty třídy `ctype`, které slouží jako omezující vlastnosti národního prostředí pro znaky.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který popisuje znak používaný národním prostředním.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[do_is](#do_is)|Virtuální funkce volaná k ověření, zda má jeden znak konkrétní atribut, nebo ke klasifikaci atributů v jednotlivých kontejnerech v rozsahu a jejich uložení v poli.|
|[do_narrow](#do_narrow)|Virtuální funkce volaná k převodu znaku typu `CharType` používaného národním prostředím na odpovídající znak typu **char** v nativní znakové sadě.|
|[do_scan_is](#do_scan_is)|Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který odpovídá zadané masce.|
|[do_scan_not](#do_scan_not)|Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který neodpovídá zadané masce.|
|[do_tolower](#do_tolower)|Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na malá písmena.|
|[do_toupper](#do_toupper)|Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na velká písmena.|
|[do_widen](#do_widen)|Virtuální funkce volaná k převodu znaku typu **char** v nativní znakové sadě na odpovídající znak typu `CharType` používaného národním prostředím.|
|[is](#is)|Ověřuje, zda má jeden znak konkrétní atribut, nebo klasifikuje atributy v jednotlivých kontejnerech v rozsahu a uloží je v poli.|
|[dále](#narrow)|Převede znak typu `CharType` používaného národním prostředím na odpovídající znak typu char v nativní znakové sadě.|
|[scan_is](#scan_is)|Vyhledá první znak v rozsahu, který odpovídá zadané masce.|
|[scan_not](#scan_not)|Vyhledá první znak v rozsahu, který neodpovídá zadané masce.|
|[ToLower](#tolower)|Převede znak nebo rozsah znaků na malá písmena.|
|[ToUpper](#toupper)|Převede znak nebo rozsah znaků na velká písmena.|
|[rozšiřuje](#widen)|Převede znak typu **char** v nativní znakové sadě na odpovídající znak typu `CharType` používaný národním prostředím.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="char_type"></a>CType:: char_type

Typ, který popisuje znak používaný národním prostředním.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony *CharType*.

### <a name="example"></a>Příklad

Podívejte se, jak členské funkce [rozšiřují](#widen) příklad, který používá `char_type` jako návratovou hodnotu.

## <a name="ctype"></a>CType:: CType

Konstruktor pro objekty třídy CType, které slouží jako omezující vlastnosti národního prostředí pro znaky.

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs* \
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *_Refs* a jejich význam jsou:

- 0: životnost objektu je spravována místními objekty, které jej obsahují.

- 1: životnost objektu musí být ručně spravovaná.

- \> 1: tyto hodnoty nejsou definovány.

Nejsou možné žádné přímé příklady, protože je destruktor chráněný.

Konstruktor inicializuje svůj `locale::facet` základní objekt pomocí **locale::** [Face](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="do_is"></a>CType::d o_is

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

*maskVal* \
Hodnota masky, pro kterou má být testován znak.

*ch* \
Znak, jehož atributy mají být testovány.

*první* \
Ukazatel na první znak v rozsahu, jehož atributy mají být klasifikovány.

*poslední* \
Ukazatel na znak hned po posledním znaku v rozsahu, jehož atributy mají být klasifikovány.

*cílový* \
Ukazatel na začátek pole, kde jsou uloženy hodnoty masky characterizing atributů každého znaku.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí logickou hodnotu, která má **hodnotu true** , pokud testovaný znak má atribut popsaný hodnotou masky; **hodnota false** , pokud se nezdařila pro atribut

Druhá členská funkce vrátí pole obsahující hodnoty masky characterizing atributy každého znaku v rozsahu.

### <a name="remarks"></a>Poznámky

Hodnoty masky klasifikace atributů znaků jsou poskytovány třídou [ctype_base](../standard-library/ctype-base-class.md), ze které je odvozen CType. První členská funkce může přijmout výrazy pro svůj první parametr, který je odkazován jako vyčíslení a vytvořen z kombinace hodnot masky pomocí logických operátorů (&#124; , &, ^, ~).

### <a name="example"></a>Příklad

Podívejte [se na příklad pro,](#is)který volá `do_is`.

## <a name="do_narrow"></a>CType::d o_narrow

Virtuální funkce volaná k převodu znaku typu `CharType` používaného národním prostředím na odpovídající znak typu **char** v nativní znakové sadě.

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

*ch* \
Znak typu `Chartype` používané národním prostředím, které má být převedeno.

*výchozí* \
Výchozí hodnota, která má být přiřazena členskou funkcí znakům typu `CharType`, které nemají znaky protějšku typu **char**.

*první* \
Ukazatel na první znak v rozsahu znaků, který má být převeden.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu znaků, který má být převeden.

*cílový* \
Const ukazatel na první znak typu **char** v cílovém rozsahu, ve kterém je uložený převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

První chráněná členská funkce vrátí nativní znak typu char, který odpovídá znaku parametru typu `CharType` nebo *Default* , pokud není definován žádný protějšek.

Druhá chráněná členská funkce vrátí ukazatel na cílový rozsah nativních znaků převedených ze znaků typu `CharType`.

### <a name="remarks"></a>Poznámky

Druhá chráněná šablona člena ukládá do `dest` [`I`] hodnotu `do_narrow` (`first` [`I`], `default`) pro `I` v intervalu [0 `last`  -  `first`).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [zúžení](#narrow), který volá `do_narrow`.

## <a name="do_scan_is"></a>CType::d o_scan_is

Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který odpovídá zadané masce.

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal* \
Hodnota masky odpovídající znaku.

*první* \
Ukazatel na první znak v rozsahu, který chcete prohledat.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu, který chcete prohledat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, který odpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce *Poslední*.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce vrátí nejmenší ukazatel `ptr` v rozsahu [`first`, `last`), pro který má vlastnost [do_is](#do_is)(`maskVal`, \* `ptr`) hodnotu true.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [scan_is](#scan_is), který volá `do_scan_is`.

## <a name="do_scan_not"></a>CType::d o_scan_not

Virtuální funkce volaná k vyhledání prvního znaku v rozsahu, který neodpovídá zadané masce.

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal* \
Hodnota masky nesmí odpovídat znaku.

*první* \
Ukazatel na první znak v rozsahu, který chcete prohledat.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu, který chcete prohledat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, který neodpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce *Poslední*.

### <a name="remarks"></a>Poznámky

Chráněná členská funkce vrátí nejmenší ukazatel `ptr` v rozsahu [`first`, `last`), pro který je [do_is](#do_is)(`maskVal` \* `ptr`) false.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [scan_not](#scan_not), který volá `do_scan_not`.

## <a name="do_tolower"></a>CType::d o_tolower

Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na malá písmena.

```cpp
virtual CharType do_tolower(CharType ch) const;

virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch* \
Znak, který má být převeden na malá písmena.

*první* \
Ukazatel na první znak v rozsahu znaků, jejichž případy mají být převedeny.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu znaků, jejichž případy mají být převedeny.

### <a name="return-value"></a>Návratová hodnota

První chráněná členská funkce vrátí formu malých písmen parametru *ch*. Pokud neexistují žádné formuláře s malým písmenem, vrátí *ch*. Druhá chráněná členská funkce vrátí *Poslední*.

### <a name="remarks"></a>Poznámky

Druhá funkce šablony Protected member nahradí každý prvek `first` [`I`] pro `I` v intervalu [0, `last`  -  `first`) s `do_tolower` (`first` [`I`]).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [ToLower](#tolower), který volá `do_tolower`.

## <a name="do_toupper"></a>CType::d o_toupper

Virtuální funkce volaná k převedení znaku nebo rozsahu znaků na velká písmena.

```cpp
virtual CharType do_toupper(CharType ch) const;

virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch* \
Znak, který má být převeden na velká písmena.

*první* \
Ukazatel na první znak v rozsahu znaků, jejichž případy mají být převedeny.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu znaků, jejichž případy mají být převedeny.

### <a name="return-value"></a>Návratová hodnota

První chráněná členská funkce vrátí formu velkých písmen parametru *ch*. Pokud neexistují žádné formy velkých písmen, vrátí *ch*. Druhá chráněná členská funkce vrátí *Poslední*.

### <a name="remarks"></a>Poznámky

Druhá funkce šablony Protected member nahradí každý prvek `first` [`I`] pro `I` v intervalu [0, `last`  -  `first`) s `do_toupper` (`first` [`I`]).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [ToUpper](#toupper), který volá `do_toupper`.

## <a name="do_widen"></a>CType::d o_widen

Virtuální funkce volaná k převodu znaku typu **char** v nativní znakové sadě na odpovídající znak typu `CharType` používaného národním prostředím.

```cpp
virtual CharType do_widen(char byte) const;

virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>Parametry

*bajtové* \
Znak typu **char** v nativní znakové sadě, která má být převedena.

*první* \
Ukazatel na první znak v rozsahu znaků, který má být převeden.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu znaků, který má být převeden.

*cílový* \
Ukazatel na první znak typu `CharType` v cílovém rozsahu, ve kterém je uložený převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

První chráněná členská funkce vrátí znak typu `CharType`, který odpovídá znaku parametru nativního typu **char**.

Druhá chráněná členská funkce vrací ukazatel na cílový rozsah znaků typu `CharType` používané národním prostředím převedených z nativních znaků typu **char**.

### <a name="remarks"></a>Poznámky

Druhá chráněná šablona člena ukládá do `dest` [`I`] hodnotu `do_widen` (`first` [`I`]) pro `I` v intervalu [0 `last`  -  `first`).

### <a name="example"></a>Příklad

Podívejte se na příklad pro [rozšíření](#widen), který volá `do_widen`.

## <a name="is"></a>CType:: is

Testuje, zda má jeden znak konkrétní atribut, nebo klasifikuje atributy každého znaku v rozsahu a ukládá je do pole.

```cpp
bool is(mask maskVal, CharType ch) const;

const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>Parametry

*maskVal* \
Hodnota masky, pro kterou má být testován znak.

*ch* \
Znak, jehož atributy mají být testovány.

*první* \
Ukazatel na první znak v rozsahu, jehož atributy mají být klasifikovány.

*poslední* \
Ukazatel na znak hned po posledním znaku v rozsahu, jehož atributy mají být klasifikovány.

*cílový* \
Ukazatel na začátek pole, kde jsou uloženy hodnoty masky characterizing atributů každého znaku.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí **hodnotu true** , pokud testovaný znak má atribut popsaný hodnotou masky; **hodnota false** , pokud se nezdařila pro atribut

Druhá členská funkce vrátí ukazatel na poslední znak v rozsahu, jehož atributy mají být klasifikovány.

### <a name="remarks"></a>Poznámky

Hodnoty masky klasifikace atributů znaků jsou poskytovány [třídou ctype_base](../standard-library/ctype-base-class.md)třídy, ze které je odvozen CType. První členská funkce může přijmout výrazy pro svůj první parametr, který je odkazován jako vyčíslení a vytvořen z kombinace hodnot masky pomocí logických operátorů (&#124; , &, ^, ~).

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

## <a name="narrow"></a>CType:: Narrow

Převede znaky typu `CharType` používané národním prostředím na odpovídající znaky typu **char** v nativní znakové sadě.

```cpp
char narrow(CharType ch, char default = '\0') const;

const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>Parametry

*ch* \
Znak typu `Chartype` používané národním prostředím, které má být převedeno.

*výchozí* \
Výchozí hodnota, která má být přiřazena členskou funkcí znakům typu `CharType`, které nemají znaky protějšku typu **char**.

*první* \
Ukazatel na první znak v rozsahu znaků, který má být převeden.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu znaků, který má být převeden.

*cílový* \
Const ukazatel na první znak typu **char** v cílovém rozsahu, ve kterém je uložený převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrací nativní znak typu **char** , který odpovídá znaku parametru typu `CharType default`, pokud není protějšek definován.

Druhá členská funkce vrátí ukazatel na cílový rozsah nativních znaků převedených ze znaků typu `CharType`.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [do_narrow](#do_narrow)(`ch`, `default`). Druhá členská funkce vrátí [do_narrow](#do_narrow) (`first`, `last`, `default`, `dest`). U základních zdrojových znaků je zaručeno, že mají v `narrow` jedinečný `CharType` obrázku. Pro tyto základní zdrojové znaky následující invariantní uchovávají: `narrow` ( [rozšířit](#widen) ( **c** ), 0) = = **c**.

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

## <a name="scan_is"></a>CType:: scan_is

Vyhledá první znak v rozsahu, který odpovídá zadané masce.

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal* \
Hodnota masky odpovídající znaku.

*první* \
Ukazatel na první znak v rozsahu, který chcete prohledat.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu, který chcete prohledat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, který odpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce *Poslední*.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_scan_is](#do_scan_is)(`maskVal`, `first`, `last`).

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

## <a name="scan_not"></a>CType:: scan_not

Vyhledá první znak v rozsahu, který neodpovídá zadané masce.

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*maskVal* \
Hodnota masky nesmí odpovídat znaku.

*první* \
Ukazatel na první znak v rozsahu, který chcete prohledat.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu, který chcete prohledat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na první znak v rozsahu, který neodpovídá zadané masce. Pokud žádná taková hodnota neexistuje, vrátí funkce *Poslední*.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_scan_not](#do_scan_not)(`maskVal`, `first`, `last`).

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

## <a name="tolower"></a>CType:: ToLower

Převede znak nebo rozsah znaků na malá písmena.

```cpp
CharType tolower(CharType ch) const;

const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch* \
Znak, který má být převeden na malá písmena.

*první* \
Ukazatel na první znak v rozsahu znaků, jejichž případy mají být převedeny.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu znaků, jejichž případy mají být převedeny.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí formu malých písmen parametru *ch*. Pokud neexistují žádné formuláře s malým písmenem, vrátí *ch*.

Druhá členská funkce vrátí *Poslední*.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [do_tolower](#do_tolower)(`ch`). Druhá členská funkce vrátí [do_tolower](#do_tolower)(`first`, `last`).

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

## <a name="toupper"></a>CType:: ToUpper

Převede znak nebo rozsah znaků na velká písmena.

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*ch* \
Znak, který má být převeden na velká písmena.

*první* \
Ukazatel na první znak v rozsahu znaků, jejichž případy mají být převedeny.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu znaků, jejichž případy mají být převedeny.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí formu velkých písmen parametru *ch*. Pokud neexistují žádné formy velkých písmen, vrátí *ch*.

Druhá členská funkce vrátí *Poslední*.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [do_toupper](#do_toupper)(`ch`). Druhá členská funkce vrátí [do_toupper](#do_toupper)(`first`, `last`).

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

## <a name="widen"></a>CType:: rozšířit

Převede znak typu **char** v nativní znakové sadě na odpovídající znak typu `CharType` používaný národním prostředím.

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>Parametry

*bajtové* \
Znak typu char v nativní znakové sadě, která má být převedena.

*první* \
Ukazatel na první znak v rozsahu znaků, který má být převeden.

*poslední* \
Ukazatel na znak hned za posledním znakem v rozsahu znaků, který má být převeden.

*cílový* \
Ukazatel na první znak typu `CharType` v cílovém rozsahu, ve kterém je uložený převedený rozsah znaků.

### <a name="return-value"></a>Návratová hodnota

První členská funkce vrátí znak typu `CharType`, který odpovídá znaku parametru nativního typu **char**.

Druhá členská funkce vrátí ukazatel na cílový rozsah znaků typu `CharType` používané národním prostředím převedeným z nativních znaků typu **char**.

### <a name="remarks"></a>Poznámky

První členská funkce vrátí [do_widen](#do_widen)(`byte`). Druhá členská funkce vrátí [do_widen](#do_widen)(`first`, `last`, `dest`).

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

[\<locale >](../standard-library/locale.md) \
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
