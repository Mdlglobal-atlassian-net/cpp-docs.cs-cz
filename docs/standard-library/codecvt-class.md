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
ms.openlocfilehash: 631c3b88be5e2a03798ff6d8e3fb200ad257a8d7
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890191"
---
# <a name="codecvt-class"></a>codecvt – třída

Šablona třídy, která popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí. Dokáže řídit převody mezi sekvencí hodnot používanou ke kódování znaků v rámci programu a sekvencí hodnot používanou ke kódování znaků mimo program.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Parametry

*CharType* \
Typ používaný v rámci programu ke kódování znaků.

*Bajtové* \
Typ použitý ke kódování znaků mimo program.

*StateType* \
Typ, který lze použít k reprezentaci průběžných stavů převodu mezi interními a externími typy znázornění znaků.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který může sloužit jako [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class)pro řízení převodů mezi sekvencí hodnot typu *CharType* a sekvencí hodnot typu *Byte*. Třída *StateType* charakterizuje transformaci a objekt třídy *StateType* ukládá všechny potřebné informace o stavu během převodu.

Interní kódování používá reprezentaci s pevným počtem bajtů na znak, obvykle buď typ **char** , nebo typ **wchar_t**.

Stejně jako u všech omezujících vlastností národního prostředí má `id` statických objektů počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě ukládá v `id` jedinečnou kladnou hodnotu.

Verze šablon [do_in](#do_in) a [do_out](#do_out) vždycky vracejí `codecvt_base::noconv`.

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

převádí mezi sekvencemi `char16_t` kódované jako znakové sady UTF-16 a sekvence **znaků** kódované jako UTF-8.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

převádí mezi sekvencemi `char32_t` kódovanými jako UTF-32 (UCS-4) a sekvencemi **znaků** zakódovanými jako UTF-8.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[codecvt](#codecvt)|Konstruktor pro objekty třídy `codecvt`, který slouží jako omezující vlastnost národního prostředí pro zpracování převodů.|

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
|[do_encoding](#do_encoding)|Virtuální funkce, která testuje, zda je kódování `Byte`ho datového proudu závislé na stavu, zda je poměr mezi použitými hodnotami `Byte` a `CharType` vyprodukovaný, a pokud ano, určuje hodnotu tohoto poměru.|
|[do_in](#do_in)|Virtuální funkce volaná k převedení sekvence interních `Byte` hodnot na sekvenci externích hodnot `CharType`.|
|[do_length](#do_length)|Virtuální funkce, která určuje, kolik hodnot `Byte` z dané sekvence externích `Byte` hodnot vyprodukuje nevětší než zadaný počet interních `CharType` hodnot a vrátí tento počet `Byte` hodnot.|
|[do_max_length](#do_max_length)|Virtuální funkce, která vrací maximální počet externích bajtů potřebných k vytvoření jednoho interního `CharType`.|
|[do_out](#do_out)|Virtuální funkce volaná k převedení sekvence interních `CharType` hodnot na sekvenci externích bajtů.|
|[do_unshift](#do_unshift)|Virtuální funkce volaná k poskytnutí hodnot `Byte` potřebných v převodu závislém na stavu k dokončení posledního znaku v sekvenci hodnot `Byte`.|
|[kódování](#encoding)|Testuje, zda je kódování `Byte`ho datového proudu závislé na stavu, zda je poměr mezi použitými hodnotami `Byte` a `CharType`ými hodnotami konstantní, a pokud ano, určuje hodnotu tohoto poměru.|
|[in](#in)|Převede externí reprezentace sekvence `Byte` hodnot na vnitřní reprezentaci sekvence `CharType` hodnot.|
|[časový](#length)|Určuje, kolik hodnot `Byte` z dané sekvence externích `Byte` hodnot nepřekračuje zadaný počet interních `CharType` hodnot a vrátí tento počet `Byte` hodnot.|
|[max_length](#max_length)|Vrátí maximální počet externích hodnot `Byte` potřebných k vystavení jednoho interního `CharType`.|
|[out](#out)|Převede sekvenci interních `CharType` hodnot na sekvenci externích hodnot `Byte`.|
|[unshift](#unshift)|Poskytuje externí `Byte` hodnoty potřebné v převodu závislém na stavu k dokončení posledního znaku v sekvenci hodnot `Byte`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="always_noconv"></a>codecvt:: always_noconv

Testuje, zda není třeba provádět převody.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která má **hodnotu true** , pokud není nutné provádět převody; **false** , pokud je potřeba provést aspoň jeden.

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
explicit codecvt(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

\ *ReFS*
Celočíselná hodnota používaná k určení typu správy paměti pro daný objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty pro parametr *ReFS* a jejich význam jsou:

- 0: životnost objektu je spravována místními objekty, které jej obsahují.

- 1: životnost objektu musí být ručně spravovaná.

- 2: tyto hodnoty nejsou definovány.

Konstruktor inicializuje svůj `locale::facet` základní objekt s parametrem [locale:: face](../standard-library/locale-class.md#facet_class)`(refs)`.

## <a name="do_always_noconv"></a>codecvt::d o_always_noconv

Virtuální funkce volaná k otestování, zda není třeba provádět převody.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí **hodnotu true** pouze v případě, že každé volání [do_in](#do_in) nebo [do_out](#do_out) vrátí `noconv`.

Verze šablony vždy vrátí **hodnotu true**.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [always_noconv](#always_noconv), který volá `do_always_noconv`.

## <a name="do_encoding"></a>codecvt::d o_encoding

Virtuální funkce, která testuje, zda je kódování `Byte`ho datového proudu závislé na stavu, zda je poměr mezi použitými hodnotami `Byte` a `CharType` vyprodukovaný, je konstantní a pokud ano, určuje hodnotu tohoto poměru.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí:

- -1, pokud je kódování sekvencí typu `extern_type` závislé na stavu.

- 0, pokud kódování zahrnuje sekvence různých délek.

- *N*, pokud kódování zahrnuje pouze sekvence délky *N*

### <a name="example"></a>Příklad

Podívejte se na příklad pro [kódování](#encoding), který volá `do_encoding`.

## <a name="do_in"></a>codecvt::d o_in

Virtuální funkce volaná k převedení sekvence externích `Byte` hodnot na sekvenci interních `CharType` hodnot.

```cpp
virtual result do_in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parametry

\ *stavu*
Stav převodu, který je udržován mezi voláními členské funkce.

*first1* \
Ukazatel na začátek sekvence, která má být převedena.

*last1* \
Ukazatel na konec sekvence, která má být převedena.

*next1* \
Ukazatel nad koncem převedené sekvence na první převedený znak.

*first2* \
Ukazatel na začátek převedené sekvence.

*last2* \
Ukazatel na konec převedené sekvence.

*next2* \
Ukazatel na `CharType`, který pochází po posledním převedeném `CharType`, na první nezměněný znak v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která indikuje úspěch, částečnou úspěch nebo neúspěch operace. Funkce vrátí:

- `codecvt_base::error`, pokud je zdrojová sekvence nesprávně vytvořená.

- `codecvt_base::noconv`, pokud funkce neprovede žádný převod.

- `codecvt_base::ok`, pokud je převod úspěšný.

- `codecvt_base::partial`, zda je zdroj nedostatečný, nebo pokud cíl není dostatečně velký, aby byl převod úspěšný.

### <a name="remarks"></a>Poznámky

*stav* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní svou uloženou hodnotu podle potřeby, aby odrážela aktuální stav úspěšného převodu. Jeho uložená hodnota je v opačném případě neurčená.

### <a name="example"></a>Příklad

Podívejte se na příklad [v](#in)tématu, který volá `do_in`.

## <a name="do_length"></a>codecvt::d o_length

Virtuální funkce, která určuje, kolik hodnot `Byte` z dané sekvence externích `Byte` hodnot vyprodukuje nevětší než zadaný počet interních `CharType` hodnot a vrátí tento počet `Byte` hodnot.

```cpp
virtual int do_length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parametry

\ *stavu*
Stav převodu, který je udržován mezi voláními členské funkce.

*first1* \
Ukazatel na začátek externí sekvence.

*last1* \
Ukazatel na konec externí sekvence.

*len2*\
Maximální počet `Byte` hodnot, které mohou být vráceny členskou funkcí.

### <a name="return-value"></a>Návratová hodnota

Celé číslo představující počet maximálních převodů, který není větší než *len2*definovaný externí zdrojovou sekvencí na [`first1`, `last1`).

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce efektivně volá `do_in( state, first1, last1, next1, buf, buf + len2, next2)` pro *stav* (kopii stavu), část vyrovnávací paměti `buf`a ukazatele `next1` a `next2`.

Pak vrátí `next2`  -  `buf`. Proto počítá maximální počet převodů, nikoli větší než *len2*, definované zdrojovou sekvencí v [`first1`, `last1`).

Verze šablony vždy vrátí menší z *last1* - *first1* a *len2*.

### <a name="example"></a>Příklad

Podívejte se na příklad [délky](#length), která volá `do_length`.

## <a name="do_max_length"></a>codecvt::d o_max_length

Virtuální funkce, která vrací maximální počet externích `Byte` hodnot nezbytných k vytvoření jednoho interního `CharType`.

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet `Byte` hodnot, které jsou nutné k vyprodukování jednoho `CharType`.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrací největší přípustnou hodnotu, kterou může [do_length](#do_length)`( first1, last1, 1)` vrátit pro libovolné platné hodnoty *first1* a *last1*.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [max_length](#max_length), který volá `do_max_length`.

## <a name="do_out"></a>codecvt::d o_out

Virtuální funkce volaná k převedení sekvence interních `CharType` hodnot na sekvenci externích hodnot `Byte`.

```cpp
virtual result do_out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

\ *stavu*
Stav převodu, který je udržován mezi voláními členské funkce.

*first1* \
Ukazatel na začátek sekvence, která má být převedena.

*last1* \
Ukazatel na konec sekvence, která má být převedena.

*next1* \
Odkaz na ukazatel na první převedený `CharType` po posledním převodu `CharType`

*first2* \
Ukazatel na začátek převedené sekvence.

*last2* \
Ukazatel na konec převedené sekvence.

*next2* \
Odkaz na ukazatel na první převedený `Byte` po posledním převodu `Byte`

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí:

- `codecvt_base::error`, pokud je zdrojová sekvence nesprávně vytvořená.

- `codecvt_base::noconv`, pokud funkce neprovede žádný převod.

- `codecvt_base::ok`, pokud je převod úspěšný.

- `codecvt_base::partial`, zda je zdroj nedostatečný, nebo pokud není cíl dostatečně velký, aby byl převod úspěšný.

### <a name="remarks"></a>Poznámky

*stav* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní svou uloženou hodnotu podle potřeby, aby odrážela aktuální stav úspěšného převodu. Jeho uložená hodnota je v opačném případě neurčená.

### <a name="example"></a>Příklad

Podívejte [se na příklad, který](#out)volá `do_out`.

## <a name="do_unshift"></a>codecvt::d o_unshift

Virtuální funkce volaná k poskytnutí hodnot `Byte` potřebných v převodu závislém na stavu k dokončení posledního znaku v sekvenci hodnot `Byte`.

```cpp
virtual result do_unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

\ *stavu*
Stav převodu, který je udržován mezi voláními členské funkce.

*first2* \
Ukazatel na první pozici v cílovém rozsahu.

*last2* \
Ukazatel na poslední pozici v cílovém rozsahu.

*next2* \
Ukazatel na první nezměněný prvek v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí:

- `codecvt_base::error`, pokud *stav* představuje neplatný stav

- `codecvt_base::noconv`, pokud funkce neprovede žádný převod

- `codecvt_base::ok`, pokud je převod úspěšný

- `codecvt_base::partial`, pokud cíl není dost velký, aby se převod mohl zdařit.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí převést zdrojový element `CharType`(0) na cílovou sekvenci, kterou ukládá v rámci [`first2`, `last2`) s výjimkou ukončovacího elementu `Byte`(0). Vždy ukládá v *next2* ukazatel na první nezměněný prvek v cílové sekvenci.

_ *Stav* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní svou uloženou hodnotu podle potřeby, aby odrážela aktuální stav úspěšného převodu. Obvykle převod zdrojového elementu `CharType` (0) opustí aktuální stav ve stavu prvotního převodu.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [unshift](#unshift), který volá `do_unshift`.

## <a name="encoding"></a>codecvt:: Encoding

Testuje, zda je kódování `Byte`ho datového proudu závislé na stavu, zda je poměr mezi použitými hodnotami `Byte` a `CharType`ými hodnotami konstantní, a pokud ano, určuje hodnotu tohoto poměru.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota kladná, je tato hodnota konstantním počtem `Byte`ch znaků potřebných k vyprodukování `CharType` znaku.

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

## <a name="extern_type"></a>codecvt:: extern_type

Typ znaku, který se používá pro externí reprezentace.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro parametr šablony `Byte`.

## <a name="in"></a>codecvt:: v

Převede externí reprezentace sekvence `Byte` hodnot na vnitřní reprezentaci sekvence `CharType` hodnot.

```cpp
result in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>Parametry

\ *stavu*
Stav převodu, který je udržován mezi voláními členské funkce.

*first1* \
Ukazatel na začátek sekvence, která má být převedena.

*last1* \
Ukazatel na konec sekvence, která má být převedena.

*next1* \
Ukazatel nad koncem převedené sekvence na první převedený znak.

*first2* \
Ukazatel na začátek převedené sekvence.

*last2* \
Ukazatel na konec převedené sekvence.

*next2* \
Ukazatel na `CharType`, která přichází po posledním převodu `Chartype` na první nezměněný znak v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu, která indikuje úspěch, částečnou úspěch nebo neúspěch operace. Funkce vrátí:

- `codecvt_base::error`, pokud je zdrojová sekvence nesprávně vytvořená.

- `codecvt_base::noconv`, pokud funkce neprovede žádný převod.

- `codecvt_base::ok`, pokud je převod úspěšný.

- `codecvt_base::partial`, zda je zdroj nedostatečný, nebo pokud není cíl dostatečně velký, aby byl převod úspěšný.

### <a name="remarks"></a>Poznámky

*stav* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní svou uloženou hodnotu podle potřeby, aby odrážela aktuální stav úspěšného převodu. Po částečné konverzi musí být *stav* nastaven tak, aby bylo možné pokračovat v převodu, když přicházejí nové znaky.

Členská funkce vrací [do_in](#do_in)`( state, first1,  last1,  next1, first2, last2,  next2)`.

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

Typ je synonymum pro parametr šablony `CharType`.

## <a name="length"></a>codecvt:: Length

Určuje, kolik hodnot `Byte` z dané sekvence externích `Byte` hodnot nepřekračuje zadaný počet interních `CharType` hodnot a vrátí tento počet `Byte` hodnot.

```cpp
int length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parametry

\ *stavu*
Stav převodu, který je udržován mezi voláními členské funkce.

*first1* \
Ukazatel na začátek externí sekvence.

*last1* \
Ukazatel na konec externí sekvence.

*len2*\
Maximální počet bajtů, které mohou být vráceny členskou funkcí.

### <a name="return-value"></a>Návratová hodnota

Celé číslo představující počet maximálních převodů, který není větší než *len2*definovaný externí zdrojovou sekvencí na [`first1`, `last1`).

### <a name="remarks"></a>Poznámky

Členská funkce vrací [do_length](#do_length)`( state, first1, last1, len2)`.

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

Vrátí maximální počet externích hodnot `Byte` potřebných k vystavení jednoho interního `CharType`.

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet `Byte` hodnot, které jsou nutné k vyprodukování jednoho `CharType`.

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

Převede sekvenci interních `CharType` hodnot na sekvenci externích hodnot `Byte`.

```cpp
result out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

\ *stavu*
Stav převodu, který je udržován mezi voláními členské funkce.

*first1* \
Ukazatel na začátek sekvence, která má být převedena.

*last1* \
Ukazatel na konec sekvence, která má být převedena.

*next1* \
Odkaz na ukazatel na první převedený `CharType` po posledním převodu `CharType`

*first2* \
Ukazatel na začátek převedené sekvence.

*last2* \
Ukazatel na konec převedené sekvence.

*next2* \
Odkaz na ukazatel na první převedený `Byte` po posledním převedeném `Byte`

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrací [do_out](#do_out)`( state, first1, last1, next1, first2, last2, next2)`.

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

Typ je synonymum pro parametr šablony `StateType`.

## <a name="unshift"></a>codecvt:: unshift

Poskytuje `Byte` hodnoty potřebné v převodu závislém na stavu k dokončení posledního znaku v sekvenci hodnot `Byte`.

```cpp
result unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

\ *stavu*
Stav převodu, který je udržován mezi voláními členské funkce.

*first2* \
Ukazatel na první pozici v cílovém rozsahu.

*last2* \
Ukazatel na poslední pozici v cílovém rozsahu.

*next2* \
Ukazatel na první nezměněný prvek v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí:

- `codecvt_base::error`, pokud stav představuje neplatný stav.

- `codecvt_base::noconv`, pokud funkce neprovede žádný převod.

- `codecvt_base::ok`, pokud je převod úspěšný.

- `codecvt_base::partial`, pokud cíl není dostatečně velký, aby byl převod úspěšný.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se pokusí převést zdrojový element `CharType`(0) na cílovou sekvenci, kterou ukládá v rámci [`first2`, `last2`) s výjimkou ukončovacího elementu `Byte`(0). Vždy ukládá v *next2* ukazatel na první nezměněný prvek v cílové sekvenci.

*stav* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní svou uloženou hodnotu podle potřeby, aby odrážela aktuální stav úspěšného převodu. Obvykle převod zdrojového elementu `CharType` (0) opustí aktuální stav ve stavu prvotního převodu.

Členská funkce vrací [do_unshift](#do_unshift)`( state, first2, last2, next2 )`.

## <a name="see-also"></a>Viz také:

[\<locale >](../standard-library/locale.md) \
[Znakové stránky](../c-runtime-library/code-pages.md) \
[Názvy národních prostředí, jazyky a řetězce země/oblasti](../c-runtime-library/locale-names-languages-and-country-region-strings.md) \
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
