---
title: codecvt – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocale/std::codecvt
- xlocale/std::codecvt::extern_type
- xlocale/std::codecvt::intern_type
- xlocale/std::codecvt::state_type
- xlocale/std::codecvt::always_noconv
- xlocale/std::codecvt::do_always_noconv
- xlocale/std::codecvt::do_encoding
- xlocale/std::codecvt::do_in
- xlocale/std::codecvt::do_length
- xlocale/std::codecvt::do_max_length
- xlocale/std::codecvt::do_out
- xlocale/std::codecvt::do_unshift
- xlocale/std::codecvt::encoding
- xlocale/std::codecvt::in
- xlocale/std::codecvt::length
- xlocale/std::codecvt::max_length
- xlocale/std::codecvt::out
- xlocale/std::codecvt::unshift
dev_langs:
- C++
helpviewer_keywords:
- std::codecvt [C++]
- std::codecvt [C++], extern_type
- std::codecvt [C++], intern_type
- std::codecvt [C++], state_type
- std::codecvt [C++], always_noconv
- std::codecvt [C++], do_always_noconv
- std::codecvt [C++], do_encoding
- std::codecvt [C++], do_in
- std::codecvt [C++], do_length
- std::codecvt [C++], do_max_length
- std::codecvt [C++], do_out
- std::codecvt [C++], do_unshift
- std::codecvt [C++], encoding
- std::codecvt [C++], in
- std::codecvt [C++], length
- std::codecvt [C++], max_length
- std::codecvt [C++], out
- std::codecvt [C++], unshift
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f02f6a2810f5ac3a51abb80245c22a7f0c2df434
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074146"
---
# <a name="codecvt-class"></a>codecvt – třída

Třída šablony popisující objekt, který může sloužit jako podmínka národního prostředí. Dokáže řídit převody mezi sekvencí hodnot používanou ke kódování znaků v rámci programu a sekvencí hodnot používanou ke kódování znaků mimo program.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Parametry

*CharType*<br/>
Typ používaný v rámci programu ke kódování znaků.

*Bajtů*<br/>
Typ použitý ke kódování znaků mimo program.

*StateType*<br/>
Typ, který lze použít k reprezentaci průběžných stavů převodu mezi interními a externími typy znázornění znaků.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který může sloužit jako [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class)pro řízení převodů mezi sekvencí hodnot typu *CharType* a sekvencí hodnot typu *bajt*. Třída *StateType* charakterizuje transformaci a objekt třídy *StateType* uchovává všechny nezbytné informace o stavu během převodu.

Interní kódování používá znázornění s pevným počtem bajtů na znak, obvykle buď typu **char** nebo typ **wchar_t**.

Stejně jako u omezující vlastnosti národního prostředí má statický objekt `id` počáteční uloženou hodnotu nula. První pokus o přístup k jeho uložené hodnotě uloží jedinečnou kladnou hodnotu v `id`.

Verze šablony [do_in](#do_in) a [do_out](#do_out) vždy vrátí `codecvt_base::noconv`.

Standardní knihovny C++ definuje několik explicitních specializací:

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

převádí mezi **wchar_t** a **char** pořadí.

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

převádí mezi `char16_t` kódováním UTF-16 a **char** kódováním UTF-8.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

převádí mezi `char32_t` kódováním UTF-32 (UCS-4) a **char** kódováním UTF-8.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[codecvt –](#codecvt)|Konstruktor pro objekty třídy `codecvt` , který slouží jako omezující vlastnost národního prostředí pro zpracování převodů.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[extern_type](#extern_type)|Typ znaku, který se používá pro externí reprezentace.|
|[intern_type](#intern_type)|Typ znaku, který se používá pro interní reprezentace.|
|[state_type](#state_type)|Typ znaku, který se používá k reprezentaci průběžných stavů během převodu mezi interními a externími znázorněními.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[always_noconv](#always_noconv)|Ověřuje, zda je nutné provést nějaké převody.|
|[do_always_noconv](#do_always_noconv)|Virtuální funkce volaná k ověření, zda je nutné provést nějaké převody.|
|[do_encoding](#do_encoding)|Virtuální funkce, která testuje, zda kódování `Byte` datový proud je závisí na stavu a zda poměr mezi `Byte`použitou a `CharType`s vytvořený je konstantní a pokud ano, stanoví hodnotu tohoto poměru.|
|[do_in](#do_in)|Virtuální funkce volaná k převedení sekvence interních `Byte`na sekvenci externích `CharType`s.|
|[do_length](#do_length)|Virtuální funkce, která určuje, kolik `Byte`z dané sekvence externích `Byte`vytvoří maximální počet interních `CharType`s a vrátí daný počet `Byte`s.|
|[do_max_length](#do_max_length)|Virtuální funkce, která vrátí maximální počet externích bajtů nezbytných k vytvoření jednoho interního `CharType`.|
|[do_out](#do_out)|Virtuální funkce volaná k převedení sekvence interních `CharType`na sekvenci externích bajtů.|
|[do_unshift](#do_unshift)|Virtuální funkce volaná k poskytování `Byte`potřebných při převodu závislém na stavu k dokončení posledního znaku v sekvenci `Byte`s.|
|[Kódování](#encoding)|Testuje, zda kódování `Byte` datový proud je závisí na stavu a zda je poměr mezi `Byte`použitou a `CharType`s vytvořený je konstantní a pokud ano, stanoví hodnotu tohoto poměru.|
|[in](#in)|Převede externí znázornění sekvence `Byte`s interní znázornění sekvence `CharType`s.|
|[Délka](#length)|Určuje, kolik `Byte`z dané sekvence externích `Byte`vytvoří maximální počet interních `CharType`s a vrátí daný počet `Byte`s.|
|[max_length](#max_length)|Vrátí maximální počet externích `Byte`nezbytných k vytvoření jednoho interního `CharType`.|
|[out](#out)|Převede sekvenci interních `CharType`na sekvenci externích `Byte`s.|
|[unshift –](#unshift)|Poskytne externí `Byte`potřebných při převodu závislém na stavu k dokončení posledního znaku v sekvenci `Byte`s.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="always_noconv"></a>  codecvt::always_noconv

Ověřuje, zda je nutné provést nějaké převody.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která je **true** Pokud je nutné provést nějaké převody; **false** je alespoň jeden je potřeba udělat.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_always_noconv –](#do_always_noconv).

### <a name="example"></a>Příklad

```cpp
// codecvt_always_noconv.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result1 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;

   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result2 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;
}
```

```Output
No conversion is needed.
At least one conversion is required.
```

## <a name="codecvt"></a>  codecvt::codecvt

Konstruktor pro objekty třídy codecvt, která slouží jako omezující vlastnost národního prostředí pro zpracování převodů.

```cpp
explicit codecvt(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*<br/>
Celočíselná hodnota určuje typ Správa paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *_Refs* parametrů a jejich význam:

- 0: Životnost objektu se spravuje přes národní prostředí, které je obsahují.

- 1: doba života objektu je nutné ručně spravovat.

- 2: tyto hodnoty nejsou definovány.

Konstruktor inicializuje jeho `locale::facet` základního objektu s **locale::**[omezující vlastnost](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="do_always_noconv"></a>  codecvt::do_always_noconv

Virtuální funkce volaná k ověření, zda je nutné provést nějaké převody.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí **true** pouze tehdy, pokud všechna volání [do_in](#do_in) nebo [do_out](#do_out) vrátí `noconv`.

Verze šablony vždy vrátí **true**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [always_noconv –](#always_noconv), který volá `do_always_noconv`.

## <a name="do_encoding"></a>  codecvt::do_encoding

Virtuální funkce, která testuje, zda kódování `Byte` datový proud je závisí na stavu a zda poměr mezi `Byte`použitou a `CharType`s vytvořený je konstantní a pokud ano, stanoví hodnotu tohoto poměru.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí:

- -1, pokud kódování sekvencí typu `extern_type` závisí stavu.

- 0, pokud kódování zahrnuje sekvence různých délek.

- *N*, pokud kódování zahrnuje pouze pořadí délky *N*

### <a name="example"></a>Příklad

Podívejte se na příklad pro [kódování](#encoding), který volá `do_encoding`.

## <a name="do_in"></a>  codecvt::do_in

Virtuální funkce volaná k převedení sekvence externích `Byte`na sekvenci interních `CharType`s.

```cpp
virtual result do_in(
    StateType& _State,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parametry

*_Stavu*<br/>
Stav převodu, který se spravuje mezi voláními na členskou funkci.

*first1*<br/>
Ukazatel na začátek sekvence má být převeden.

*Příjmení1*<br/>
Ukazatel na konci sekvence má být převeden.

*next1*<br/>
Ukazatel za koncem převedený pořadí první nepřevedeném znak.

*first2*<br/>
Ukazatel na začátek převedený pořadí.

*Příjmení2*<br/>
Ukazatel na konci převedený sekvence.

*next2*<br/>
Ukazatel `CharType` , která se dodává po převedení poslední `CharType`, první nezměněném znaku v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Vrátí, která udává úspěch, částečný úspěch nebo selhání operace. Tato funkce vrátí hodnotu:

- `codecvt_base::error` Pokud je zdrojové sekvence výplně tvar.

- `codecvt_base::noconv` Pokud funkce provádí převod.

- `codecvt_base::ok` v případě, že převod je úspěšný.

- `codecvt_base::partial` Pokud je nedostatek zdroj nebo cíl není dostatečně velký pro úspěšný převod.

### <a name="remarks"></a>Poznámky

*_Stavu* musí představovat počáteční převodu stavu na začátku nové zdrojové sekvence. Funkce mění jeho uložené hodnotě podle potřeby tak, aby odrážela aktuální stav úspěšný převod. Jinak není zadána jeho uložené hodnotě.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [v](#in), který volá `do_in`.

## <a name="do_length"></a>  codecvt::do_length

Virtuální funkce, která určuje, kolik `Byte`z dané sekvence externích `Byte`vytvoří maximální počet interních `CharType`s a vrátí daný počet `Byte`s.

```cpp
virtual int do_length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Parametry

*_Stavu*<br/>
Stav převodu, který se spravuje mezi voláními na členskou funkci.

*first1*<br/>
Ukazatel na začátek pořadí externí.

*Příjmení1*<br/>
Ukazatel na konci externí sekvence.

*_Len2*<br/>
Maximální počet `Byte`, které může být vrácen členskou funkci.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které představuje maximální počet převody, není větší než počet *_Len2*definovaná pořadím externího zdroje v [ `first1`, `last1`).

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce efektivně volá `do_in`( `_State`, `first1`, `last1`, `next1`, `_Buf`, `_Buf`  +  `_Len2`, `next2`) pro *_Stavu* (kopii stavu), některé vyrovnávací paměti `_Buf`a ukazatele `next1`a `next2`.

Potom vrátí `next2`  -  `buf`. Díky tomu se určí maximální počet převody, není větší než *_Len2*definovaná ve zdrojové sekvence v [ `first1`, `last1`).

Verze šablony vždy vrátí hodnotu menší než délka *Příjmení1* - *first1* a *_Len2*.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [délka](#length), který volá `do_length`.

## <a name="do_max_length"></a>  codecvt::do_max_length

Virtuální funkce, která vrátí maximální počet externích `Byte`nezbytných k vytvoření jednoho interního `CharType`.

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet `Byte`nezbytných k vytvoření jednoho `CharType`.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrátí největší povolenou hodnotu, která může být vrácen [do_length –](#do_length)( `first1`, `last1`, 1) pro libovolné platné hodnoty *first1* a *Příjmení1*.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [max_length](#max_length), který volá `do_max_length`.

## <a name="do_out"></a>  codecvt::do_out

Virtuální funkce volaná k převedení sekvence interních `CharType`na sekvenci externích `Byte`s.

```cpp
virtual result do_out(
    StateType& _State,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_Stavu*<br/>
Stav převodu, který se spravuje mezi voláními na členskou funkci.

*first1*<br/>
Ukazatel na začátek sekvence má být převeden.

*Příjmení1*<br/>
Ukazatel na konci sekvence má být převeden.

*next1*<br/>
Odkaz na ukazatel na první nepřevedený `CharType`, za poslední `CharType` převést.

*first2*<br/>
Ukazatel na začátek převedený pořadí.

*Příjmení2*<br/>
Ukazatel na konci převedený sekvence.

*next2*<br/>
Odkaz na ukazatel na první nepřevedený `Byte`, za poslední `Byte` převést.

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrátí hodnotu:

- `codecvt_base::error` Pokud je zdrojové sekvence výplně tvar.

- `codecvt_base::noconv` Pokud funkce provádí převod.

- `codecvt_base::ok` v případě, že převod je úspěšný.

- `codecvt_base::partial` Pokud je nedostatek zdroj nebo cíl není dostatečně velký pro úspěšný převod.

### <a name="remarks"></a>Poznámky

*_Stavu* musí představovat počáteční převodu stavu na začátku nové zdrojové sekvence. Funkce mění jeho uložené hodnotě podle potřeby tak, aby odrážela aktuální stav úspěšný převod. Jinak není zadána jeho uložené hodnotě.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [si](#out), který volá `do_out`.

## <a name="do_unshift"></a>  codecvt::do_unshift

Virtuální funkce volaná k poskytování `Byte`potřebných při převodu závislém na stavu k dokončení posledního znaku v sekvenci `Byte`s.

```cpp
virtual result do_unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_Stavu*<br/>
Stav převodu, který se spravuje mezi voláními na členskou funkci.

*first2*<br/>
Ukazatel na první pozici v cílovém rozsahu.

*Příjmení2*<br/>
Ukazatel na poslední pozice v cílové oblasti.

*next2*<br/>
Ukazatel na první prvek beze změny v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrátí hodnotu:

- `codecvt_base::error` Pokud _ *stavu* představuje neplatném stavu

- `codecvt_base::noconv` Pokud funkce neprovede žádný převod.

- `codecvt_base::ok` v případě, že převod je úspěšný

- `codecvt_base::partial` Pokud cíl není dostatečně velký pro úspěšný převod

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí převést source element `CharType`(0) na cílové sekvenci, který je uložený v rámci [ `first2`, `last2`), s výjimkou ukončujícího prvku `Byte`(0). Je vždy uložený v *next2* ukazatel na první prvek beze změny v cílové sekvenci.

_ *Stavu* musí představovat počáteční převodu stavu na začátku nové zdrojové sekvence. Funkce mění jeho uložené hodnotě podle potřeby tak, aby odrážela aktuální stav úspěšný převod. Obvykle, převod source element `CharType`(0) zůstanou ve stavu počáteční převod aktuální stav.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [unshift](#unshift), který volá `do_unshift`.

## <a name="encoding"></a>  codecvt::Encoding

Testuje, zda kódování `Byte` datový proud je závisí na stavu a zda je poměr mezi `Byte`použitou a `CharType`s vytvořený je konstantní a pokud ano, stanoví hodnotu tohoto poměru.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud vrácená hodnota je kladné, pak je tato hodnota stálého počtu `Byte` znaků vyžadovaný pro vytvoření `CharType` znak.

Chráněná virtuální členská funkce vrátí:

- -1, pokud kódování sekvencí typu `extern_type` závisí stavu.

- 0, pokud kódování zahrnuje sekvence různých délek.

- *N*, pokud kódování zahrnuje pouze pořadí délky *N.*

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_encoding –](#do_encoding).

### <a name="example"></a>Příklad

```cpp
// codecvt_encoding.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
}
```

```Output
1
1
1
```

## <a name="extern_type"></a>  codecvt::extern_type

Typ znaku, který se používá pro externí reprezentace.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Byte`.

## <a name="in"></a>  codecvt::in

Převede externí znázornění sekvence `Byte`s interní znázornění sekvence `CharType`s.

```cpp
result in(
    StateType& _State,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parametry

*_Stavu*<br/>
Stav převodu, který se spravuje mezi voláními na členskou funkci.

*first1*<br/>
Ukazatel na začátek sekvence má být převeden.

*Příjmení1*<br/>
Ukazatel na konci sekvence má být převeden.

*next1*<br/>
Ukazatel za koncem převedený pořadí první nepřevedeném znak.

*first2*<br/>
Ukazatel na začátek převedený pořadí.

*Příjmení2*<br/>
Ukazatel na konci převedený sekvence.

*next2*<br/>
Ukazatel `CharType` , která se dodává po převedení poslední `Chartype` první nezměněném znaku v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Vrátí, která udává úspěch, částečný úspěch nebo selhání operace. Tato funkce vrátí hodnotu:

- `codecvt_base::error` Pokud je zdrojové sekvence výplně tvar.

- `codecvt_base::noconv` Pokud funkce provádí převod.

- `codecvt_base::ok` v případě, že převod je úspěšný.

- `codecvt_base::partial` Pokud je nedostatek zdroj nebo cíl není dostatečně velký pro úspěšný převod.

### <a name="remarks"></a>Poznámky

*_Stavu* musí představovat počáteční převodu stavu na začátku nové zdrojové sekvence. Funkce mění jeho uložené hodnotě podle potřeby tak, aby odrážela aktuální stav úspěšný převod. Po částečné převodu *_stavu* musí být nastaven tak, aby převod na pokračovat, až dorazí nové znaky.

Členská funkce vrátí [do_in](#do_in)( `_State`, _ *First1 Příjmení1, next1, First2, _Llast2, next2*).

### <a name="example"></a>Příklad

```cpp
// codecvt_in.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));
   const char* pszNext;
   wchar_t* pwszNext;
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).in( state,
          pszExt, &pszExt[strlen(pszExt)], pszNext,
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;
   exit(-1);
}
```

```Output
It worked! The converted string is:
[This is the string to be converted!]
```

## <a name="intern_type"></a>  codecvt::intern_type

Typ znaku, který se používá pro interní reprezentace.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `CharType`.

## <a name="length"></a>  codecvt::length

Určuje, kolik `Byte`z dané sekvence externích `Byte`vytvoří maximální počet interních `CharType`s a vrátí daný počet `Byte`s.

```cpp
int length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Parametry

*_Stavu*<br/>
Stav převodu, který se spravuje mezi voláními na členskou funkci.

*first1*<br/>
Ukazatel na začátek pořadí externí.

*Příjmení1*<br/>
Ukazatel na konci externí sekvence.

*_Len2*<br/>
Maximální počet bajtů, které můžete členské funkce.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které představuje maximální počet převody, není větší než počet *_Len2*definovaná pořadím externího zdroje v [ `first1`, `last1`).

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_length –](#do_length)( *_stavu first1*, `last1`, `_Len2`).

### <a name="example"></a>Příklad

```cpp
// codecvt_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string whose length is to be measured!";
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).length( state,
          pszExt, &pszExt[strlen(pszExt)], LEN );
   cout << "The length of the string is: ";
   wcout << res;
   cout << "." << endl;
   exit(-1);
}
```

```Output
The length of the string is: 50.
```

## <a name="max_length"></a>  codecvt::max_length

Vrátí maximální počet externích `Byte`nezbytných k vytvoření jednoho interního `CharType`.

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet `Byte`nezbytných k vytvoření jednoho `CharType`.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_max_length –](#do_max_length).

### <a name="example"></a>Příklad

```cpp
// codecvt_max_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc( "C");//English_Britain" );//German_Germany
   int res = use_facet<codecvt<char, char, mbstate_t> >
     ( loc ).max_length( );
   wcout << res << endl;
}
```

```Output
1
```

## <a name="out"></a>  codecvt::Out

Převede sekvenci interních `CharType`na sekvenci externích `Byte`s.

```cpp
result out(
    StateType& _State,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_Stavu*<br/>
Stav převodu, který se spravuje mezi voláními na členskou funkci.

*first1*<br/>
Ukazatel na začátek sekvence má být převeden.

*Příjmení1*<br/>
Ukazatel na konci sekvence má být převeden.

*next1*<br/>
Odkaz na ukazatel na první nepřevedený `CharType` za poslední `CharType` převést.

*first2*<br/>
Ukazatel na začátek převedený pořadí.

*Příjmení2*<br/>
Ukazatel na konci převedený sekvence.

*next2*<br/>
Odkaz na ukazatel na první nepřevedený `Byte` po převedení poslední `Byte`.

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí [do_out](#do_out)( `_State`, `first1`, `last1`, `next1`, `first2`, `last2`, `next2`).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [codecvt::do_out](#do_out).

### <a name="example"></a>Příklad

```cpp
// codecvt_out.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
#include <wchar.h>
using namespace std;
#define LEN 90
int main( )
{
   char pszExt[LEN+1];
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );
   char* pszNext;
   const wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).out( state,
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );
   pszExt[wcslen( pwszInt )] = 0;
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )
   << "The converted string is:\n ["
   << &pszExt[0]
   << "]" << endl;
}
```

```Output
It worked: The converted string is:
[This is the wchar_t string to be converted.]
```

## <a name="state_type"></a>  codecvt::state_type

Typ znaku, který se používá k reprezentaci průběžných stavů během převodu mezi interními a externími znázorněními.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `StateType`.

## <a name="unshift"></a>  codecvt::unshift

Poskytuje `Byte`potřebných při převodu závislém na stavu k dokončení posledního znaku v sekvenci `Byte`s.

```cpp
result unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_Stavu*<br/>
Stav převodu, který se spravuje mezi voláními na členskou funkci.

*first2*<br/>
Ukazatel na první pozici v cílovém rozsahu.

*Příjmení2*<br/>
Ukazatel na poslední pozice v cílové oblasti.

*next2*<br/>
Ukazatel na první prvek beze změny v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Tato funkce vrátí hodnotu:

- `codecvt_base::error` Pokud státu představuje neplatném stavu.

- `codecvt_base::noconv` Pokud funkce provádí převod.

- `codecvt_base::ok` v případě, že převod je úspěšný.

- `codecvt_base::partial` Pokud cíl není dostatečně velký pro úspěšný převod.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí převést source element `CharType`(0) na cílové sekvenci, který je uložený v rámci [ `first2`, `last2`), s výjimkou ukončujícího prvku `Byte`(0). Je vždy uložený v *next2* ukazatel na první prvek beze změny v cílové sekvenci.

*_Stavu* musí představovat počáteční převodu stavu na začátku nové zdrojové sekvence. Funkce mění jeho uložené hodnotě podle potřeby tak, aby odrážela aktuální stav úspěšný převod. Obvykle, převod source element `CharType`(0) zůstanou ve stavu počáteční převod aktuální stav.

Členská funkce vrátí [do_unshift –](#do_unshift)( `_State`, `first2`, `last2`, `next2` ).

## <a name="see-also"></a>Viz také:

[\<národní prostředí >](../standard-library/locale.md)<br/>
[Znakové stránky](../c-runtime-library/code-pages.md)<br/>
[Názvy národních prostředí, jazyků a Country/Region Strings](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
