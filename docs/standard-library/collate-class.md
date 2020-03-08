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
ms.openlocfilehash: 88b04ad4f14faf4d152c0ce2b9c3477928263c52
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866149"
---
# <a name="collate-class"></a>collate – třída

Šablona třídy popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro řízení řazení a seskupování znaků v rámci řetězce, porovnávání mezi nimi a hodnoty hash řetězců.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ používaný v rámci programu ke kódování znaků.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v `id`jedinečnou kladnou hodnotu. V některých jazycích jsou znaky seskupeny a považovány za jeden znak a v jiných jsou jednotlivé znaky zpracovány tak, jako by se jednalo o dva znaky. Kolační služby poskytované kolační třídou poskytují způsob řazení těchto případů.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[COLLATE](#collate)|Konstruktor pro objekty třídy `collate`, který slouží jako omezující vlastnost národního prostředí pro zpracování konvencí řazení řetězců.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který popisuje znak typu `CharType`.|
|[string_type](#string_type)|Typ, který popisuje řetězec typu `basic_string` obsahující znaky typu `CharType`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[porovnán](#compare)|Porovná dvě znakové sekvence podle pravidel na základě jejich omezujících vlastností a zjistí rovnost či nerovnost.|
|[do_compare](#do_compare)|Virtuální funkce volaná k porovnání dvou znakových sekvencí podle pravidel na základě jejich omezujících vlastností a zjištění rovnosti či nerovnosti.|
|[do_hash](#do_hash)|Virtuální funkce volaná k určení hodnoty hash sekvencí podle pravidel na základě jejich omezujících vlastností.|
|[do_transform](#do_transform)|Virtuální funkce volaná k převedení znakové sekvence z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.|
|[kontrole](#hash)|Určí hodnotu hash sekvence podle pravidel na základě její omezující vlastnosti.|
|[převedení](#transform)|Převede znakovou sekvenci z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Obor názvů:** std

## <a name="char_type"></a>COLLATE:: char_type

Typ, který popisuje znak typu `CharType`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `CharType`.

## <a name="collate"></a>COLLATE:: COLLATE

Konstruktor pro objekty třídy COLLATE, který slouží jako omezující vlastnost národního prostředí pro zpracování konvencí řazení řetězců.

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
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

*_Locname*\
Název národního prostředí.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *_Refs* a jejich význam jsou:

- 0: životnost objektu je spravována místními objekty, které jej obsahují.

- 1: životnost objektu musí být ručně spravovaná.

- \> 1: tyto hodnoty nejsou definovány.

Konstruktor inicializuje svůj základní objekt pomocí **locale::** [Face](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="compare"></a>COLLATE:: Compare

Porovná dvě znakové sekvence podle pravidel na základě jejich omezujících vlastností a zjistí rovnost či nerovnost.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*first1*\
Ukazatel na první prvek v první sekvenci, která se má porovnat.

*last1*\
Ukazatel na poslední prvek v první sekvenci, která se má porovnat.

*first2*\
Ukazatel na první prvek v druhé sekvenci, která se má porovnat.

*last2*\
Ukazatel na poslední prvek ve druhé sekvenci, která se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí:

- -1, pokud první sekvence porovná méně než druhou sekvenci.

- \+ 1, pokud druhá sekvence porovnává méně než první sekvence.

- 0, pokud jsou sekvence ekvivalentní.

### <a name="remarks"></a>Poznámky

První sekvence porovná méně, pokud má menší prvek v nejbližším nerovnosti v sekvencích, nebo, pokud žádné nestejné páry neexistují, ale první sekvence je kratší.

Členská funkce vrací [do_compare](#do_compare)(`first1`, `last1`, `first2`, `last2`).

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

## <a name="do_compare"></a>COLLATE::d o_compare

Virtuální funkce volaná k porovnání dvou znakových sekvencí podle pravidel na základě jejich omezujících vlastností a zjištění rovnosti či nerovnosti.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*first1*\
Ukazatel na první prvek v první sekvenci, která se má porovnat.

*last1*\
Ukazatel na poslední prvek v první sekvenci, která se má porovnat.

*first2*\
Ukazatel na první prvek v druhé sekvenci, která se má porovnat.

*last2*\
Ukazatel na poslední prvek ve druhé sekvenci, která se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí:

- -1, pokud první sekvence porovná méně než druhou sekvenci.

- \+ 1, pokud druhá sekvence porovnává méně než první sekvence.

- 0, pokud jsou sekvence ekvivalentní.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce porovnává sekvenci v [* first1, Last1) * se sekvencí v *[First2, last2*). Porovnává hodnoty použitím `operator<` mezi páry odpovídajících prvků typu `CharType`. První sekvence porovná méně, pokud má menší prvek v nejstarším nerovnosti v sekvencích nebo pokud žádné nestejné páry neexistují, ale první sekvence je kratší.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [COLLATE:: Compare](#compare), který volá `do_compare`.

## <a name="do_hash"></a>COLLATE::d o_hash

Virtuální funkce volaná k určení hodnoty hash sekvencí podle pravidel na základě jejich omezujících vlastností.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*první*\
Ukazatel na první znak v sekvenci, jejíž hodnota má být určena.

*poslední*\
Ukazatel na poslední znak v sekvenci, jejíž hodnota má být určena.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash typu **Long** pro sekvenci.

### <a name="remarks"></a>Poznámky

Hodnota hash může být užitečná, například při distribuci sekvencí pseudo-náhodně v poli seznamů.

### <a name="example"></a>Příklad

Podívejte se na příklad [algoritmu hash](#hash), který volá `do_hash`.

## <a name="do_transform"></a>COLLATE::d o_transform

Virtuální funkce volaná k převedení znakové sekvence z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*první*\
Ukazatel na první znak v sekvenci, která má být převedena.

*poslední*\
Ukazatel na poslední znak v sekvenci, která má být převedena.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který je transformační sekvence znaků.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrátí objekt třídy [string_type](#string_type) , jehož řízená sekvence je kopií sekvence [`first`, `last`). Pokud třída odvozená z COLLATE\< **CharType**> Přepisuje [do_compare](#do_compare), měla by také přepsat `do_transform` tak, aby odpovídala. Při předání do `collate::compare`by dva transformované řetězce měly vracet stejný výsledek, který byste získali z předání netransformované řetězce pro porovnání v odvozené třídě.

### <a name="example"></a>Příklad

Podívejte se na příklad [transformace](#transform), která volá `do_transform`.

## <a name="hash"></a>COLLATE:: hash – hodnota

Určí hodnotu hash sekvence podle pravidel na základě její omezující vlastnosti.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*první*\
Ukazatel na první znak v sekvenci, jejíž hodnota má být určena.

*poslední*\
Ukazatel na poslední znak v sekvenci, jejíž hodnota má být určena.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash typu **Long** pro sekvenci.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_hash](#do_hash)(`first`, `last`).

Hodnota hash může být užitečná, například při distribuci sekvencí pseudo-náhodně v poli seznamů.

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

## <a name="string_type"></a>COLLATE:: string_type

Typ, který popisuje řetězec typu `basic_string` obsahující znaky typu `CharType`.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje specializaci šablony třídy [basic_string](../standard-library/basic-string-class.md) jejichž objekty mohou ukládat kopie zdrojové sekvence.

### <a name="example"></a>Příklad

Příklad, jak deklarovat a použít `string_type`, naleznete v tématu [Transforming](#transform).

## <a name="transform"></a>COLLATE:: Transform

Převede znakovou sekvenci z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*první*\
Ukazatel na první znak v sekvenci, která má být převedena.

*poslední*\
Ukazatel na poslední znak v sekvenci, která má být převedena.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který obsahuje transformované sekvence znaků.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_transform](#do_transform)(`first`, `last`).

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

[\<> národního prostředí](../standard-library/locale.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
