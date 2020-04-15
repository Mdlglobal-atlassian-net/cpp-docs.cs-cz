---
title: collate – třída
ms.date: 11/04/2016
f1_keywords:
- locale/std::collate
- locale/std::collate::char_type
- locale/std::collate::string_type
- locale/std::collate::compare
- locale/std::collate::do_compare
- locale/std::collate::do_hash
- locale/std::collate::do_transform
- locale/std::collate::hash
- locale/std::collate::transform
helpviewer_keywords:
- std::collate [C++]
- std::collate [C++], char_type
- std::collate [C++], string_type
- std::collate [C++], compare
- std::collate [C++], do_compare
- std::collate [C++], do_hash
- std::collate [C++], do_transform
- std::collate [C++], hash
- std::collate [C++], transform
ms.assetid: 92168798-9628-4a2e-be6e-fa62dcd4d6a6
ms.openlocfilehash: f05c2e9482f8a0bada3868fdc946d4d26a0e0e1d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371923"
---
# <a name="collate-class"></a>collate – třída

Šablona třídy, která popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení řazení a seskupení znaků v řetězci, porovnání mezi nimi a zapisování řetězců.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě `id`ukládá jedinečnou kladnou hodnotu v aplikaci . V některých jazycích jsou znaky seskupeny a považovány za jeden znak a v jiných jsou jednotlivé znaky zpracovány tak, jako by se jednalo o dva znaky. Kolační služby poskytované kolační třídou poskytují způsob řazení těchto případů.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[Collate](#collate)|Konstruktor pro objekty `collate` třídy, která slouží jako omezující tvář národního prostředí pro zpracování konvence řazení řetězců.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který popisuje znak `CharType`typu .|
|[string_type](#string_type)|Typ, který popisuje řetězec `basic_string` typu obsahující znaky `CharType`typu .|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Porovnat](#compare)|Porovná dvě znakové sekvence podle pravidel na základě jejich omezujících vlastností a zjistí rovnost či nerovnost.|
|[do_compare](#do_compare)|Virtuální funkce volaná k porovnání dvou znakových sekvencí podle pravidel na základě jejich omezujících vlastností a zjištění rovnosti či nerovnosti.|
|[do_hash](#do_hash)|Virtuální funkce volaná k určení hodnoty hash sekvencí podle pravidel na základě jejich omezujících vlastností.|
|[do_transform](#do_transform)|Virtuální funkce volaná k převedení znakové sekvence z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.|
|[Hash](#hash)|Určí hodnotu hash sekvence podle pravidel na základě její omezující vlastnosti.|
|[Transformace](#transform)|Převede znakovou sekvenci z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="collatechar_type"></a><a name="char_type"></a>koláž::char_type

Typ, který popisuje znak `CharType`typu .

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `CharType`parametr šablony .

## <a name="collatecollate"></a><a name="collate"></a>kompletovat::kompletovat

Konstruktor pro objekty třídy komplet, který slouží jako omezující tvář národního prostředí pro zpracování konvence řazení řetězců.

```cpp
public:
    explicit collate(
    size_t _Refs = 0);

protected:
    collate(
const char* _Locname,
    size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Celá hodnota používaná k určení typu správy paměti pro objekt.

*_Locname*\
Název národního prostředí.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* a jejich význam jsou:

- 0: Životnost objektu je spravována národními prostředími, které jej obsahují.

- 1: Životnost objektu musí být spravována ručně.

- \>1: Tyto hodnoty nejsou definovány.

Konstruktor inicializuje svůj základní objekt pomocí **národního prostředí::**[omezující stolku](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="collatecompare"></a><a name="compare"></a>kompletovat::porovnat

Porovná dvě znakové sekvence podle pravidel na základě jejich omezujících vlastností a zjistí rovnost či nerovnost.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*první1*\
Ukazatel na první prvek v prvním pořadí, který má být porovnán.

*last1*\
Ukazatel na poslední prvek v prvním pořadí, který má být porovnán.

*první2*\
Ukazatel na první prvek v druhé sekvenci, která má být porovnána.

*last2*\
Ukazatel na poslední prvek v druhé sekvenci, která má být porovnána.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí:

- -1, pokud první sekvence porovnává méně než druhá sekvence.

- +1, pokud druhá sekvence porovnává méně než první sekvenci.

- 0, pokud jsou sekvence rovnocenné.

### <a name="remarks"></a>Poznámky

První sekvence porovná méně, pokud má menší prvek v nejbližší nerovné dvojice v sekvencích, nebo pokud neexistují žádné nerovné páry, ale první sekvence je kratší.

Členská funkce [do_compare](#do_compare)vrátí `first1` `last1`do_compare `first2` `last2`( , , ).

### <a name="example"></a>Příklad

```cpp
// collate_compare.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare ( s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << result2 << endl;
}
```

## <a name="collatedo_compare"></a><a name="do_compare"></a>kompletovat::do_compare

Virtuální funkce volaná k porovnání dvou znakových sekvencí podle pravidel na základě jejich omezujících vlastností a zjištění rovnosti či nerovnosti.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*první1*\
Ukazatel na první prvek v prvním pořadí, který má být porovnán.

*last1*\
Ukazatel na poslední prvek v prvním pořadí, který má být porovnán.

*první2*\
Ukazatel na první prvek v druhé sekvenci, která má být porovnána.

*last2*\
Ukazatel na poslední prvek v druhé sekvenci, která má být porovnána.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí:

- -1, pokud první sekvence porovnává méně než druhá sekvence.

- +1, pokud druhá sekvence porovnává méně než první sekvenci.

- 0, pokud jsou sekvence rovnocenné.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce porovnává sekvenci v [ * first1, Last1)* s sekvencí *na [ first2, last2*). Porovnává hodnoty použitím `operator<` mezi dvojicemi odpovídajících `CharType`prvků typu . První sekvence porovná méně, pokud má menší prvek v nejbližší nerovné dvojice v sekvencích nebo pokud neexistují žádné nerovné páry, ale první sekvence je kratší.

### <a name="example"></a>Příklad

Viz příklad pro [kompletování::porovnat](#compare), který volá `do_compare`.

## <a name="collatedo_hash"></a><a name="do_hash"></a>koláž::do_hash

Virtuální funkce volaná k určení hodnoty hash sekvencí podle pravidel na základě jejich omezujících vlastností.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*První*\
Ukazatel na první znak v sekvenci, jehož má hodnota má být určena.

*Poslední*\
Ukazatel na poslední znak v sekvenci, jehož má hodnota má být určena.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash typu **long** pro sekvenci.

### <a name="remarks"></a>Poznámky

Hodnota hash může být užitečná, například při distribuci sekvencí pseudo-náhodně v rámci pole seznamů.

### <a name="example"></a>Příklad

Viz příklad pro [hash](#hash) `do_hash`, který volá .

## <a name="collatedo_transform"></a><a name="do_transform"></a>kompletovat::do_transformace

Virtuální funkce volaná k převedení znakové sekvence z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*První*\
Ukazatel na první znak v pořadí, které mají být převedeny.

*Poslední*\
Ukazatel na poslední znak v pořadí, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který je transformované sekvence znaků.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrátí objekt [třídy string_type,](#string_type) jehož řízená sekvence je kopií sekvence [ `first`, `last`). Pokud třída odvozená z\< kompletovat **CharType**> přepíše `do_transform` [do_compare](#do_compare), měla by také přepsat tak, aby odpovídala. Při předání `collate::compare`do , dva transformované řetězce by měly přinést stejný výsledek, který byste získali z předávání netransformovaných řetězců k porovnání v odvozené třídě.

### <a name="example"></a>Příklad

Viz příklad [transformace](#transform), `do_transform`který volá .

## <a name="collatehash"></a><a name="hash"></a>kompletovat::hash

Určí hodnotu hash sekvence podle pravidel na základě její omezující vlastnosti.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*První*\
Ukazatel na první znak v sekvenci, jehož má hodnota má být určena.

*Poslední*\
Ukazatel na poslední znak v sekvenci, jehož má hodnota má být určena.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash typu **long** pro sekvenci.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí `first` `last` [do_hash](#do_hash)( , ).

Hodnota hash může být užitečná, například při distribuci sekvencí pseudo-náhodně v rámci pole seznamů.

### <a name="example"></a>Příklad

```cpp
// collate_hash.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("\x00dfzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet
   _TCHAR * s2 = _T("zzz abc."); // \x00df is the German sharp-s (looks like beta), it comes before z in the alphabet

   long r1 = use_facet< collate<_TCHAR> > ( loc ).
      hash (s1, &s1[_tcslen( s1 )-1 ]);
   long r2 =  use_facet< collate<_TCHAR> > ( loc ).
      hash (s2, &s2[_tcslen( s2 )-1 ] );
   cout << r1 << " " << r2 << endl;
}
```

```Output
541187293 551279837
```

## <a name="collatestring_type"></a><a name="string_type"></a>koláž::string_type

Typ, který popisuje řetězec `basic_string` typu obsahující znaky `CharType`typu .

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_string,](../standard-library/basic-string-class.md) jehož objekty mohou ukládat kopie zdrojové sekvence.

### <a name="example"></a>Příklad

Příklad deklarace a použití `string_type`naleznete v [tématu transformace](#transform).

## <a name="collatetransform"></a><a name="transform"></a>kompletovat::transformovat

Převede znakovou sekvenci z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*První*\
Ukazatel na první znak v pořadí, které mají být převedeny.

*Poslední*\
Ukazatel na poslední znak v pořadí, který má být převeden.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který obsahuje transformované sekvence znaků.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí`first` `last` [do_transform](#do_transform)( , ).

### <a name="example"></a>Příklad

```cpp
// collate_transform.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   _TCHAR* s1 = _T("\x00dfzz abc.");
   // \x00df is the German sharp-s (looks like beta),
   // it comes before z in the alphabet
   _TCHAR* s2 = _T("zzz abc.");

   collate<_TCHAR>::string_type r1;   // OK for typedef
   r1 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s1, &s1[_tcslen( s1 )-1 ]);

   cout << r1 << endl;

   basic_string<_TCHAR> r2 = use_facet< collate<_TCHAR> > ( loc ).
      transform (s2, &s2[_tcslen( s2 )-1 ]);

   cout << r2 << endl;

   int result1 = use_facet<collate<_TCHAR> > ( loc ).compare
      (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );

   cout << _tcscmp(r1.c_str( ),r2.c_str( )) << result1
      << _tcscmp(s1,s2) <<endl;
}
```

```Output

-1-11
```

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
