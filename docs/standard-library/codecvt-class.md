---
title: codecvt – třída
ms.date: 11/04/2016
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
ms.openlocfilehash: 936b3ab63b454e8f7e0490c2d155356a7c3b240f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459824"
---
# <a name="codecvt-class"></a>codecvt – třída

Třída šablony popisující objekt, který může sloužit jako podmínka národního prostředí. Dokáže řídit převody mezi sekvencí hodnot používanou ke kódování znaků v rámci programu a sekvencí hodnot používanou ke kódování znaků mimo program.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Parametry

*CharType*\
Typ používaný v rámci programu ke kódování znaků.

*Bytové*\
Typ použitý ke kódování znaků mimo program.

*StateType*\
Typ, který lze použít k reprezentaci průběžných stavů převodu mezi interními a externími typy znázornění znaků.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který může sloužit jako [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class)pro řízení převodů mezi sekvencí hodnot typu *CharType* a sekvencí hodnot typu *Byte*. Třída *StateType* charakterizuje transformaci a objekt třídy *StateType* ukládá všechny potřebné informace o stavu během převodu.

Interní kódování používá reprezentaci s pevným počtem bajtů na znak, obvykle buď typ **char** , nebo typ **wchar_t**.

Stejně jako u všech omezujících vlastností národního prostředí `id` má statický objekt počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá do pole `id`jedinečnou kladnou hodnotu.

Verze šablon [do_in](#do_in) a [do_out](#do_out) vždy vrátí `codecvt_base::noconv`.

C++ Standardní knihovna definuje několik explicitních specializací:

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

převádí mezi sekvencemi **wchar_t** a **char** .

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

převádí mezi `char16_t` sekvencemi kódovanými jako UTF-16 a sekvencemi **znaků** kódovanými jako UTF-8.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

převádí mezi `char32_t` sekvencemi kódovanými jako UTF-32 (UCS-4) a sekvencemi **znaků** zakódovanými jako UTF-8.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[codecvt](#codecvt)|Konstruktor pro objekty třídy `codecvt` , které slouží jako omezující vlastnost národního prostředí pro zpracování převodů.|

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
|[do_encoding](#do_encoding)|Virtuální funkce, která testuje, zda je kódování `Byte` datového proudu závislé na stavu, zda je poměr `Byte`mezi použitou a `CharType`vytvořenou konstantou, a pokud ano, určuje hodnotu tohoto poměru.|
|[do_in](#do_in)|Virtuální funkce volaná k převodu sekvence vnitřních `Byte`s na sekvenci externích `CharType`s.|
|[do_length](#do_length)|Virtuální funkce, která určuje, kolik `Byte`z dané sekvence externích `Byte`s produkuje nepřekračuje zadaný počet interních `CharType`s a vrátí tento počet `Byte`s.|
|[do_max_length](#do_max_length)|Virtuální funkce, která vrací maximální počet externích bajtů potřebných k vytvoření jednoho interního `CharType`.|
|[do_out](#do_out)|Virtuální funkce volaná k převedení sekvence interních `CharType`s na sekvenci externích bajtů.|
|[do_unshift](#do_unshift)|Virtuální funkce volaná k poskytnutí `Byte`potřebných v převodu závislém na stavu k dokončení posledního znaku v `Byte`sekvenci s.|
|[kódování](#encoding)|Testuje, zda je kódování `Byte` datového proudu závislé na stavu, zda je poměr `Byte`mezi použitou a `CharType`vytvořenou konstantou, a pokud ano, určuje hodnotu tohoto poměru.|
|[in](#in)|Převede externí reprezentace sekvence `Byte`s na vnitřní reprezentace `CharType`sekvence s.|
|[length](#length)|Určuje, kolik z dané sekvence externích `Byte`s produkuje nepřekračuje zadaný počet interních `CharType`s a vrátí tento počet `Byte`s. `Byte`|
|[max_length](#max_length)|Vrátí maximální počet externích `Byte`typů, které jsou nezbytné k výrobě jednoho interního. `CharType`|
|[out](#out)|Převede sekvenci interních `CharType`s na sekvenci externích `Byte`s.|
|[unshift](#unshift)|Poskytuje externí `Byte`s potřebné v převodu závislém na stavu k dokončení posledního znaku v `Byte`sekvenci s.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> národního prostředí

**Obor názvů:** std

## <a name="always_noconv"></a>codecvt:: always_noconv

Ověřuje, zda je nutné provést nějaké převody.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která má **hodnotu true** , pokud není nutné provádět převody; **hodnota false** musí být dokončena nejméně jedna.

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_always_noconv](#do_always_noconv).

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

## <a name="codecvt"></a>codecvt:: codecvt

Konstruktor pro objekty třídy codecvt, které slouží jako omezující vlastnost národního prostředí pro zpracování převodů.

```cpp
explicit codecvt(size_t _Refs = 0);
```

### <a name="parameters"></a>Parametry

*_Refs*\
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *_Refs* a jejich význam jsou:

- 0: Životnost objektu je spravována národními prostředími, která jej obsahují.

- 1: Životnost objektu musí být ručně spravovaná.

- 2: Tyto hodnoty nejsou definovány.

Konstruktor inicializuje svůj `locale::facet` základní objekt pomocí **locale::** [Face](../standard-library/locale-class.md#facet_class)(`_Refs`).

## <a name="do_always_noconv"></a>codecvt::d o_always_noconv

Virtuální funkce volaná k ověření, zda je nutné provést nějaké převody.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí **hodnotu true** pouze v případě, že každé volání `noconv` [do_in](#do_in) nebo [do_out](#do_out) vrátí.

Verze šablony vždy vrátí **hodnotu true**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [always_noconv](#always_noconv), která `do_always_noconv`volá.

## <a name="do_encoding"></a>codecvt::d o_encoding

Virtuální funkce, která testuje, zda je kódování `Byte` datového proudu závislé na stavu, zda je poměr `Byte`mezi použitou a `CharType`vytvořenou konstantou, a pokud ano, určuje hodnotu tohoto poměru.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí:

- -1, pokud je kódování sekvencí typu `extern_type` závislé na stavu.

- 0, pokud kódování zahrnuje sekvence různých délek.

- *N*, pokud kódování zahrnuje pouze sekvence délky *N*

### <a name="example"></a>Příklad

Podívejte se na příklad [kódování](#encoding), která volá `do_encoding`.

## <a name="do_in"></a>codecvt::d o_in

Virtuální funkce volaná k převodu sekvence externích `Byte`s na sekvenci interních `CharType`s.

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

*_State*\
Stav převodu, který je udržován mezi voláními členské funkce.

*first1*\
Ukazatel na začátek sekvence, která má být převedena.

*last1*\
Ukazatel na konec sekvence, která má být převedena.

*next1*\
Ukazatel nad koncem převedené sekvence na první převedený znak.

*first2*\
Ukazatel na začátek převedené sekvence.

*last2*\
Ukazatel na konec převedené sekvence.

*next2*\
Ukazatel na `CharType` , který přichází po posledním převodu `CharType`, na první nezměněný znak v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která indikuje úspěch, částečnou úspěch nebo neúspěch operace. Funkce vrátí:

- `codecvt_base::error`v případě, že je zdrojová sekvence nesprávně vytvořená.

- `codecvt_base::noconv`Pokud funkce neprovede žádný převod.

- `codecvt_base::ok`v případě, že převod proběhne úspěšně.

- `codecvt_base::partial`Pokud je zdroj nedostatečný nebo pokud cíl není dostatečně velký, pro převod na úspěch.

### <a name="remarks"></a>Poznámky

*_State* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní svou uloženou hodnotu podle potřeby, aby odrážela aktuální stav úspěšného převodu. Jeho uložená hodnota je v opačném případě neurčená.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [v](#in), který `do_in`volá.

## <a name="do_length"></a>codecvt::d o_length

Virtuální funkce, která určuje, kolik `Byte`z dané sekvence externích `Byte`s produkuje nepřekračuje zadaný počet interních `CharType`s a vrátí tento počet `Byte`s.

```cpp
virtual int do_length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stav převodu, který je udržován mezi voláními členské funkce.

*first1*\
Ukazatel na začátek externí sekvence.

*last1*\
Ukazatel na konec externí sekvence.

*_Len2*\
Maximální počet `Byte`s, který může být vrácen členskou funkcí.

### <a name="return-value"></a>Návratová hodnota

Celé číslo představující počet maximálních převodů, který není větší než *_Len2*definovaný externí zdrojovou sekvencí v [ `first1`, `last1`).

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce efektivně `do_in`volá `_State`( `first1`, `last1`, `next1`, `_Buf`, `_Buf`,  +  ,`next2`)pro _. `_Len2`  *Stav* (kopie stavu), část vyrovnávací paměti `_Buf` `next1`a ukazatele a `next2`.

Pak se vrátí `next2`.  -  `buf` Proto počítá maximální počet převodů, nikoli větší než *_Len2*, definované zdrojovou sekvencí v [ `first1`, `last1`).

Verze šablony vždy vrátí menší z *last1* - *first1* a *_Len2*.

### <a name="example"></a>Příklad

Podívejte se na příklad [délky](#length), která volá `do_length`.

## <a name="do_max_length"></a>codecvt::d o_max_length

Virtuální funkce, která vrací maximální počet externích `Byte`s nezbytnou k vytvoření jednoho interního. `CharType`

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet nezbytných pro `Byte`jednu z nich. `CharType`

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrací největší přípustnou hodnotu, kterou může vrátit [do_length](#do_length) `first1`( `last1`,, 1) pro libovolné platné hodnoty *first1* a *last1*.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [max_length](#max_length), která `do_max_length`volá.

## <a name="do_out"></a>codecvt::d o_out

Virtuální funkce volaná k převodu sekvence vnitřních `CharType`s na sekvenci externích `Byte`s.

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

*_State*\
Stav převodu, který je udržován mezi voláními členské funkce.

*first1*\
Ukazatel na začátek sekvence, která má být převedena.

*last1*\
Ukazatel na konec sekvence, která má být převedena.

*next1*\
Odkaz na ukazatel na první `CharType`převedený, po posledním `CharType` převodu.

*first2*\
Ukazatel na začátek převedené sekvence.

*last2*\
Ukazatel na konec převedené sekvence.

*next2*\
Odkaz na ukazatel na první `Byte`převedený, po posledním `Byte` převodu.

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí:

- `codecvt_base::error`v případě, že je zdrojová sekvence nesprávně vytvořená.

- `codecvt_base::noconv`Pokud funkce neprovede žádný převod.

- `codecvt_base::ok`v případě, že převod proběhne úspěšně.

- `codecvt_base::partial`Pokud je zdroj nedostatečný, nebo pokud cíl není dostatečně velký, aby převod mohl být úspěšný.

### <a name="remarks"></a>Poznámky

*_State* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní svou uloženou hodnotu podle potřeby, aby odrážela aktuální stav úspěšného převodu. Jeho uložená hodnota je v opačném případě neurčená.

### <a name="example"></a>Příklad

Podívejte se na příklad [, který](#out)volá `do_out`.

## <a name="do_unshift"></a>codecvt::d o_unshift

Virtuální funkce volaná k poskytnutí `Byte`potřebných v převodu závislém na stavu k dokončení posledního znaku v `Byte`sekvenci s.

```cpp
virtual result do_unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stav převodu, který je udržován mezi voláními členské funkce.

*first2*\
Ukazatel na první pozici v cílovém rozsahu.

*last2*\
Ukazatel na poslední pozici v cílovém rozsahu.

*next2*\
Ukazatel na první nezměněný prvek v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí:

- `codecvt_base::error`Pokud *stav* _ představuje neplatný stav

- `codecvt_base::noconv`Pokud funkce neprovede žádný převod

- `codecvt_base::ok`Pokud je převod úspěšný

- `codecvt_base::partial`Pokud cíl není dostatečně velký pro převod na úspěch

### <a name="remarks"></a>Poznámky

`CharType`Chráněná virtuální členská funkce se pokusí převést zdrojový element (0) na cílovou sekvenci, kterou ukládá v rámci [ `first2`, `last2`), s výjimkou ukončujícího elementu `Byte`(0). Vždy ukládá v *next2* ukazatel na první nezměněný prvek v cílové sekvenci.

_ *Stav* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní svou uloženou hodnotu podle potřeby, aby odrážela aktuální stav úspěšného převodu. Obvykle převod zdrojového elementu `CharType`(0) opustí aktuální stav ve stavu prvotního převodu.

### <a name="example"></a>Příklad

Podívejte se na příklad [](#unshift)pro unshift, který `do_unshift`volá.

## <a name="encoding"></a>codecvt:: Encoding

Testuje, zda je kódování `Byte` datového proudu závislé na stavu, zda je poměr `Byte`mezi použitou a `CharType`vytvořenou konstantou, a pokud ano, určuje hodnotu tohoto poměru.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota kladná, je tato hodnota konstantním počtem `Byte` znaků vyžadovaných k `CharType` vyprodukování znaku.

Chráněná virtuální členská funkce vrátí:

- -1, pokud je kódování sekvencí typu `extern_type` závislé na stavu.

- 0, pokud kódování zahrnuje sekvence různých délek.

- *N*, pokud kódování zahrnuje pouze sekvence délky *N.*

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_encoding](#do_encoding).

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

Typ je synonymum pro parametr `Byte`šablony.

## <a name="in"></a>codecvt:: v

Převede externí reprezentace sekvence `Byte`s na vnitřní reprezentace `CharType`sekvence s.

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

*_State*\
Stav převodu, který je udržován mezi voláními členské funkce.

*first1*\
Ukazatel na začátek sekvence, která má být převedena.

*last1*\
Ukazatel na konec sekvence, která má být převedena.

*next1*\
Ukazatel nad koncem převedené sekvence na první převedený znak.

*first2*\
Ukazatel na začátek převedené sekvence.

*last2*\
Ukazatel na konec převedené sekvence.

*next2*\
Ukazatel na `CharType` , který přichází po posledním převodu `Chartype` do prvního nezměněného znaku v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která označuje úspěch, částečný úspěch nebo neúspěch operace. Funkce vrátí:

- `codecvt_base::error`v případě, že je zdrojová sekvence nesprávně vytvořená.

- `codecvt_base::noconv`Pokud funkce neprovede žádný převod.

- `codecvt_base::ok`v případě, že převod proběhne úspěšně.

- `codecvt_base::partial`Pokud je zdroj nedostatečný, nebo pokud cíl není dostatečně velký, aby převod mohl být úspěšný.

### <a name="remarks"></a>Poznámky

*_State* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní svou uloženou hodnotu podle potřeby, aby odrážela aktuální stav úspěšného převodu. Po částečné konverzi musí být *_State* nastavené tak, aby bylo možné pokračovat v převodu, když přicházejí nové znaky.

Členská funkce vrací [do_in](#do_in)( `_State`, _ *First1, last1, next1, First2, _Llast2, next2*).

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

## <a name="intern_type"></a>codecvt:: intern_type

Typ znaku, který se používá pro interní reprezentace.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `CharType`šablony.

## <a name="length"></a>codecvt:: Length

Určuje, kolik z dané sekvence externích `Byte`s produkuje nepřekračuje zadaný počet interních `CharType`s a vrátí tento počet `Byte`s. `Byte`

```cpp
int length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stav převodu, který je udržován mezi voláními členské funkce.

*first1*\
Ukazatel na začátek externí sekvence.

*last1*\
Ukazatel na konec externí sekvence.

*_Len2*\
Maximální počet bajtů, které mohou být vráceny členskou funkcí.

### <a name="return-value"></a>Návratová hodnota

Celé číslo představující počet maximálních převodů, který není větší než *_Len2*definovaný externí zdrojovou sekvencí v [ `first1`, `last1`).

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_length](#do_length)( *_State, first1*, `last1`, `_Len2`).

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

## <a name="max_length"></a>codecvt:: max_length

Vrátí maximální počet externích `Byte`typů, které jsou nezbytné k výrobě jednoho interního. `CharType`

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet nezbytných pro `Byte`jednu z nich. `CharType`

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_max_length](#do_max_length).

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

## <a name="out"></a>codecvt:: out

Převede sekvenci interních `CharType`s na sekvenci externích `Byte`s.

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

*_State*\
Stav převodu, který je udržován mezi voláními členské funkce.

*first1*\
Ukazatel na začátek sekvence, která má být převedena.

*last1*\
Ukazatel na konec sekvence, která má být převedena.

*next1*\
Odkaz na ukazatel na první `CharType` převedený po posledním `CharType` převodu.

*first2*\
Ukazatel na začátek převedené sekvence.

*last2*\
Ukazatel na konec převedené sekvence.

*next2*\
Odkaz na ukazatel na první `Byte` převedený po posledním převodu. `Byte`

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí [do_out](#do_out)( `_State`, `first1`, `last1`, `next1`, `first2`, `last2` ,`next2`).

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [codecvt::d o_out](#do_out).

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

## <a name="state_type"></a>codecvt:: state_type

Typ znaku, který se používá k reprezentaci průběžných stavů během převodu mezi interními a externími znázorněními.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr `StateType`šablony.

## <a name="unshift"></a>codecvt:: unshift

Poskytuje potřebný v převodu závislém na stavu k dokončení posledního znaku v `Byte`sekvenci s. `Byte`

```cpp
result unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*_State*\
Stav převodu, který je udržován mezi voláními členské funkce.

*first2*\
Ukazatel na první pozici v cílovém rozsahu.

*last2*\
Ukazatel na poslední pozici v cílovém rozsahu.

*next2*\
Ukazatel na první nezměněný prvek v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí:

- `codecvt_base::error`Pokud stav představuje neplatný stav.

- `codecvt_base::noconv`Pokud funkce neprovede žádný převod.

- `codecvt_base::ok`v případě, že převod proběhne úspěšně.

- `codecvt_base::partial`Pokud cíl není dostatečně velký, aby převod mohl být úspěšný.

### <a name="remarks"></a>Poznámky

`CharType`Chráněná virtuální členská funkce se pokusí převést zdrojový element (0) na cílovou sekvenci, kterou ukládá v rámci [ `first2`, `last2`), s výjimkou ukončujícího elementu `Byte`(0). Vždy ukládá v *next2* ukazatel na první nezměněný prvek v cílové sekvenci.

*_State* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní svou uloženou hodnotu podle potřeby, aby odrážela aktuální stav úspěšného převodu. Obvykle převod zdrojového elementu `CharType`(0) opustí aktuální stav ve stavu prvotního převodu.

Členská funkce vrátí [do_unshift](#do_unshift)( `_State`, `first2`, `last2`, `next2` ).

## <a name="see-also"></a>Viz také:

[\<> národního prostředí](../standard-library/locale.md)\
[Znakové stránky](../c-runtime-library/code-pages.md)\
[Názvy národních prostředí, jazyky a řetězce země/oblasti](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
