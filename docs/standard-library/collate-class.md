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
ms.openlocfilehash: 21d5825f8d9ea00359f2aa1c87291b831d1f330f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405167"
---
# <a name="collate-class"></a>collate – třída

Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro ovládání řazení a seskupování znaků v rámci řetězce a k jejich porovnání s hodnotami hash řetězců.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ používaný v rámci programu ke kódování znaků.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložené hodnotě uloží jedinečnou kladnou hodnotu v `id`. V některých jazycích jsou znaky seskupeny a považovány za jeden znak a v jiných jsou jednotlivé znaky zpracovány tak, jako by se jednalo o dva znaky. Kolační služby poskytované kolační třídou poskytují způsob řazení těchto případů.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[COLLATE –](#collate)|Konstruktor pro objekty třídy `collate` , který slouží jako omezující vlastnost národního prostředí pro zpracování konvencí řazení řetězců.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který odpovídá znaku typu `CharType`.|
|[string_type](#string_type)|Typ, který popisuje řetězec typu `basic_string` obsahující znaky typu `CharType`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[compare](#compare)|Porovná dvě znakové sekvence podle pravidel na základě jejich omezujících vlastností a zjistí rovnost či nerovnost.|
|[do_compare](#do_compare)|Virtuální funkce volaná k porovnání dvou znakových sekvencí podle pravidel na základě jejich omezujících vlastností a zjištění rovnosti či nerovnosti.|
|[do_hash](#do_hash)|Virtuální funkce volaná k určení hodnoty hash sekvencí podle pravidel na základě jejich omezujících vlastností.|
|[do_transform](#do_transform)|Virtuální funkce volaná k převedení znakové sekvence z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.|
|[Hodnota hash](#hash)|Určí hodnotu hash sekvence podle pravidel na základě její omezující vlastnosti.|
|[transform](#transform)|Převede znakovou sekvenci z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="char_type"></a>  COLLATE::char_type

Typ, který odpovídá znaku typu `CharType`.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `CharType`.

## <a name="collate"></a>  COLLATE::COLLATE

Konstruktor pro objekty třídy kolaci, která slouží jako omezující vlastnost národního prostředí pro zpracování konvencí řazení řetězců.

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

*_Refs*<br/>
Celočíselná hodnota určuje typ Správa paměti pro objekt.

*_Locname*<br/>
Název národního prostředí.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* parametrů a jejich význam:

- 0: Životnost objektu se spravuje přes národní prostředí, které je obsahují.

- 1: Doba života objektu se musí spravovat ručně.

- \> 1: Tyto hodnoty nejsou definovány.

Konstruktor inicializuje jeho základní objekt s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="compare"></a>  COLLATE::Compare

Porovná dvě znakové sekvence podle pravidel na základě jejich omezujících vlastností a zjistí rovnost či nerovnost.

```cpp
int compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Ukazatel na první prvek v první sekvenci, který se má porovnat.

*last1*<br/>
Ukazatel na poslední prvek v první sekvenci, který se má porovnat.

*first2*<br/>
Ukazatel na první prvek v druhé pořadí, který se má porovnat.

*last2*<br/>
Ukazatel na po posledním prvku v druhé pořadí, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí:

- -1, pokud první pořadí porovnává menší než druhý pořadí.

- + 1, pokud druhá sekvence porovnává méně než první pořadí.

- 0, pokud jsou ekvivalentní sekvencí.

### <a name="remarks"></a>Poznámky

První pořadí porovnává menší, pokud má menší element v nejbližší nerovnost pár v sekvencí nebo, pokud neexistuje žádný nerovnost dvojice, ale první pořadí je kratší.

Členská funkce vrátí [do_compare –](#do_compare)( `first1`, `last1`, `first2`, `last2`).

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

## <a name="do_compare"></a>  COLLATE::do_compare

Virtuální funkce volaná k porovnání dvou znakových sekvencí podle pravidel na základě jejich omezujících vlastností a zjištění rovnosti či nerovnosti.

```cpp
virtual int do_compare(const CharType* first1,
    const CharType* last1,
    const CharType* first2,
    const CharType* last2) const;
```

### <a name="parameters"></a>Parametry

*first1*<br/>
Ukazatel na první prvek v první sekvenci, který se má porovnat.

*last1*<br/>
Ukazatel na poslední prvek v první sekvenci, který se má porovnat.

*first2*<br/>
Ukazatel na první prvek v druhé pořadí, který se má porovnat.

*last2*<br/>
Ukazatel na po posledním prvku v druhé pořadí, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí:

- -1, pokud první pořadí porovnává menší než druhý pořadí.

- + 1, pokud druhá sekvence porovnává méně než první pořadí.

- 0, pokud jsou ekvivalentní sekvencí.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce porovná pořadí v [* first1 Příjmení1) * s pořadím v *[first2 Příjmení2*). Porovná s použitím hodnoty `operator<` mezi dvojice prvků odpovídající typu `CharType`. První pořadí porovnává menší, pokud má menší element v nejbližší nerovnost pár v sekvencí nebo pokud neexistuje žádný nerovnost páry ale první pořadí je kratší.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [collate::compare](#compare), který volá `do_compare`.

## <a name="do_hash"></a>  COLLATE::do_hash

Virtuální funkce volaná k určení hodnoty hash sekvencí podle pravidel na základě jejich omezujících vlastností.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*první*<br/>
Ukazatel na první znak v sekvenci, jehož má hodnota má být stanovena.

*last*<br/>
Ukazatel na poslední znak v sekvenci, jehož má hodnota má být stanovena.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash typu **dlouhé** sekvence.

### <a name="remarks"></a>Poznámky

Hodnota hash může být užitečné, například při distribuci pořadí náhodně napříč celou řadu seznamy.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [hash](#hash), který volá `do_hash`.

## <a name="do_transform"></a>  COLLATE::do_transform

Virtuální funkce volaná k převedení znakové sekvence z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*první*<br/>
Ukazatel na první znak v sekvenci, která má být převeden.

*last*<br/>
Ukazatel na poslední znak v sekvenci, která má být převeden.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který je transformovaný znak sekvence.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrátí objekt třídy [string_type](#string_type) jehož řízené sekvence je kopii sekvence [ `first`, `last`). Pokud třída odvozená z collate\< **CharType**> přepíše [do_compare –](#do_compare), by měly také přepsat `do_transform` tak, aby odpovídaly. Když předána `collate::compare`, dva transformovaný řetězce by měla yield stejný výsledek, které byste získali z předávání Netransformovaný řetězce k porovnání v odvozené třídě.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [transformace](#transform), který volá `do_transform`.

## <a name="hash"></a>  COLLATE::hash

Určí hodnotu hash sekvence podle pravidel na základě její omezující vlastnosti.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*první*<br/>
Ukazatel na první znak v sekvenci, jehož má hodnota má být stanovena.

*last*<br/>
Ukazatel na poslední znak v sekvenci, jehož má hodnota má být stanovena.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash typu **dlouhé** sekvence.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_hash –](#do_hash)( `first`, `last`).

Hodnota hash může být užitečné, například při distribuci pořadí náhodně napříč celou řadu seznamy.

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

## <a name="string_type"></a>  COLLATE::STRING_TYPE

Typ, který popisuje řetězec typu `basic_string` obsahující znaky typu `CharType`.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Poznámky

Typ, který popisuje specializace třídy šablony [basic_string](../standard-library/basic-string-class.md) jejíž objekty mohou ukládat kopie zdrojové sekvence.

### <a name="example"></a>Příklad

Příklad toho, jak deklarace a používání `string_type`, naleznete v tématu [transformace](#transform).

## <a name="transform"></a>  COLLATE::Transform

Převede znakovou sekvenci z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

*první*<br/>
Ukazatel na první znak v sekvenci, která má být převeden.

*last*<br/>
Ukazatel na poslední znak v sekvenci, která má být převeden.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který obsahuje sekvence transformovaný znaků.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_transform –](#do_transform)(`first`, `last`).

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

## <a name="see-also"></a>Viz také:

[\<národní prostředí >](../standard-library/locale.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
