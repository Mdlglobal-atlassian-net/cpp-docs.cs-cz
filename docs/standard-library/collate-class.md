---
title: COLLATE – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ee2b6c5e4847737ce0208b35a2db9fac783c225f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848073"
---
# <a name="collate-class"></a>collate – třída

Třída šablony popisující objekt, který může sloužit jako omezující vlastnost národního prostředí pro ovládání řazení a seskupování znaků v rámci řetězce a k jejich porovnání s hodnotami hash řetězců.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType>
class collate : public locale::facet;
```

### <a name="parameters"></a>Parametry

`CharType` Typ v rámci programu použitá ke kódování znaků.

## <a name="remarks"></a>Poznámky

Stejně jako u omezující vlastnosti národního prostředí má ID statického objektu počáteční uloženou hodnotu nula. Ukládá jedinečné kladnou hodnotu v první pokus o přístup k jeho uložené hodnoty **id.** V některých jazycích jsou znaky seskupeny a považovány za jeden znak a v jiných jsou jednotlivé znaky zpracovány tak, jako by se jednalo o dva znaky. Kolační služby poskytované kolační třídou poskytují způsob řazení těchto případů.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[COLLATE](#collate)|V konstruktoru pro objekty třídy `collate` sloužícím jako národní prostředí omezující vlastnost zpracovat řetězec řazení konvence.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[char_type](#char_type)|Typ, který popisuje znak typu `CharType`.|
|[STRING_TYPE](#string_type)|Typ, který popisuje řetězec typu `basic_string` obsahující znaky typu `CharType`.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[compare](#compare)|Porovná dvě znakové sekvence podle pravidel na základě jejich omezujících vlastností a zjistí rovnost či nerovnost.|
|[do_compare](#do_compare)|Virtuální funkce volaná k porovnání dvou znakových sekvencí podle pravidel na základě jejich omezujících vlastností a zjištění rovnosti či nerovnosti.|
|[do_hash](#do_hash)|Virtuální funkce volaná k určení hodnoty hash sekvencí podle pravidel na základě jejich omezujících vlastností.|
|[do_transform](#do_transform)|Virtuální funkce volaná k převedení znakové sekvence z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.|
|[Hodnota hash](#hash)|Určí hodnotu hash sekvence podle pravidel na základě její omezující vlastnosti.|
|[Transformace](#transform)|Převede znakovou sekvenci z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** – std

## <a name="char_type"></a>  COLLATE::char_type

Typ, který popisuje znak typu **CharType**.

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony **CharType**.

## <a name="collate"></a>  COLLATE::COLLATE

V konstruktoru pro objekty třídy collate, která slouží jako národní prostředí omezující vlastnost zpracovat řetězec řazení konvence.

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

`_Refs` Celočíselná hodnota určuje typ správy paměti pro objekt.

`_Locname` Název národního prostředí.

### <a name="remarks"></a>Poznámky

Možné hodnoty `_Refs` parametrů a jejich významu jsou:

- 0: doba života objektu spravuje národní prostředí, které je obsahují.

- 1: doba života objektu, se musí ručně spravovat.

- \> 1: tyto hodnoty nejsou definovány.

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

`first1` Ukazatel na prvním elementem v první pořadí, který se má porovnat.

`last1` Ukazatel na posledním prvkem v první pořadí, který se má porovnat.

`first2` Ukazatel na prvním elementem v druhé pořadí, který se má porovnat.

`last2` Ukazatel na posledním prvkem v druhé pořadí, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Členské funkce vrátí hodnotu:

- -1, pokud je první pořadí porovná nižší než druhý pořadí.

- + 1, pokud druhý pořadí porovná nižší než první pořadí.

- 0, pokud odpovídají pořadí.

### <a name="remarks"></a>Poznámky

První pořadí porovnává menší, pokud má menší element v nejdřívější nerovné pár v pořadí, nebo, pokud neexistují žádné nerovné páry, ale je první pořadí je kratší.

Členské funkce vrátí hodnotu [do_compare –](#do_compare)( `first1`, `last1`, `first2`, `last2`).

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

`first1` Ukazatel na prvním elementem v první pořadí, který se má porovnat.

`last1` Ukazatel na posledním prvkem v první pořadí, který se má porovnat.

`first2` Ukazatel na prvním elementem v druhé pořadí, který se má porovnat.

`last2` Ukazatel na posledním prvkem v druhé pořadí, který se má porovnat.

### <a name="return-value"></a>Návratová hodnota

Členské funkce vrátí hodnotu:

- -1, pokud je první pořadí porovná nižší než druhý pořadí.

- + 1, pokud druhý pořadí porovná nižší než první pořadí.

- 0, pokud odpovídají pořadí.

### <a name="remarks"></a>Poznámky

Chráněný člen virtuální funkce porovná pořadí v [* first1, Příjmení1) * s pořadím v *[first2, Příjmení2*). Porovná hodnoty použitím **operátor <** mezi páry odpovídající elementy typu **CharType**. První pořadí porovnává menší, pokud má menší element v nejdřívější nerovné pár v daná pořadí nebo pokud neexistuje žádné nerovné páry ale první pořadí je kratší.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [collate::compare](#compare), který volá `do_compare`.

## <a name="do_hash"></a>  COLLATE::do_hash

Virtuální funkce volaná k určení hodnoty hash sekvencí podle pravidel na základě jejich omezujících vlastností.

```cpp
virtual long do_hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

`first` Ukazatel na první znak v pořadí, jehož má hodnotu je možné určit.

`last` Ukazatel na poslední znak v pořadí, jehož má hodnotu je možné určit.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash typu **dlouho** pořadí.

### <a name="remarks"></a>Poznámky

Hodnota hash může být užitečná, například při distribuci pořadí náhodně pseudo na řadu seznamy.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [hash](#hash), který volá `do_hash`.

## <a name="do_transform"></a>  COLLATE::do_transform

Virtuální funkce volaná k převedení znakové sekvence z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.

```cpp
virtual string_type do_transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

`first` Ukazatel na první znak v pořadí, které má být převeden.

`last` Ukazatel na poslední znak v pořadí, které má být převeden.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který je posloupnost transformovaných znaků.

### <a name="remarks"></a>Poznámky

Chráněný člen virtuální funkce vrátí objekt třídy [string_type](#string_type) jejichž řízené sekvenci je kopie sekvenci [ `first`, `last`). Pokud třída odvozená z collate\< **CharType**> přepsání [do_compare –](#do_compare), měla by také přepsat `do_transform` tak, aby odpovídaly. Když předána `collate::compare`, dva řetězce transformovaných by měl yield stejný výsledek, které byste získali z předávání Netransformovaný řetězce k porovnání v odvozené třídě.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [transformace](#transform), který volá `do_transform`.

## <a name="hash"></a>  COLLATE::hash

Určí hodnotu hash sekvence podle pravidel na základě její omezující vlastnosti.

```cpp
long hash(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

`first` Ukazatel na první znak v pořadí, jehož má hodnotu je možné určit.

`last` Ukazatel na poslední znak v pořadí, jehož má hodnotu je možné určit.

### <a name="return-value"></a>Návratová hodnota

Hodnota hash typu **dlouho** pořadí.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [do_hash –](#do_hash)( `first`, `last`).

Hodnota hash může být užitečná, například při distribuci pořadí náhodně pseudo na řadu seznamy.

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

Typ, který popisuje řetězec typu `basic_string` obsahující znaky typu **CharType**.

```cpp
typedef basic_string<CharType> string_type;
```

### <a name="remarks"></a>Poznámky

Popisuje typ specializace šablon třídy [basic_string](../standard-library/basic-string-class.md) jejichž objekty může ukládat kopie zdrojové sekvence.

### <a name="example"></a>Příklad

Příklad toho, jak deklarace a používání `string_type`, najdete v části [transformace](#transform).

## <a name="transform"></a>  COLLATE::Transform

Převede znakovou sekvenci z národního prostředí na řetězec, který lze použít v lexikografických porovnáních s ostatními znakovými sekvencemi podobně převedenými ze stejného národního prostředí.

```cpp
string_type transform(const CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>Parametry

`first` Ukazatel na první znak v pořadí, které má být převeden.

`last` Ukazatel na poslední znak v pořadí, které má být převeden.

### <a name="return-value"></a>Návratová hodnota

Řetězec, který obsahuje posloupnost transformovaných znaků.

### <a name="remarks"></a>Poznámky

Členské funkce vrátí hodnotu [do_transform –](#do_transform)( `first`, `last`).

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

[\<národní prostředí >](../standard-library/locale.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
