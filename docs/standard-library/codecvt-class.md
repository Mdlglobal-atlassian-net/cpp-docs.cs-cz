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
ms.openlocfilehash: 3dba971b112c23325e0529e53746cbee827df5e9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371955"
---
# <a name="codecvt-class"></a>codecvt – třída

Šablona třídy, která popisuje objekt, který může sloužit jako omezující vlastnost národního prostředí. Dokáže řídit převody mezi sekvencí hodnot používanou ke kódování znaků v rámci programu a sekvencí hodnot používanou ke kódování znaků mimo program.

## <a name="syntax"></a>Syntaxe

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>Parametry

*Typ znaku*\
Typ používaný v rámci programu ke kódování znaků.

*Bajt*\
Typ použitý ke kódování znaků mimo program.

*Typ stavu*\
Typ, který lze použít k reprezentaci průběžných stavů převodu mezi interními a externími typy znázornění znaků.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který může sloužit jako [omezující vlastnost národního prostředí](../standard-library/locale-class.md#facet_class), pro řízení převodů mezi posloupností hodnot typu *CharType* a posloupností hodnot typu *Byte*. Třída *StateType* charakterizuje transformace – a objekt třídy *StateType* ukládá všechny potřebné informace o stavu během převodu.

Interní kódování používá reprezentaci s pevným počtem bajtů na znak, obvykle typu **char** nebo **typu wchar_t**.

Stejně jako u všech omezujících `id` ploch národního prostředí má statický objekt počáteční uloženou hodnotu nula. První pokus o přístup k uložené hodnotě `id`ukládá jedinečnou kladnou hodnotu v aplikaci .

Verze šablon [do_in](#do_in) a [do_out](#do_out) `codecvt_base::noconv`vždy vrátí .

Standardní knihovna Jazyka C++definuje několik explicitních specializací:

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

převádí mezi **wchar_t** a **char** sekvence.

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

převádí mezi `char16_t` sekvencemi kódované jako UTF-16 a **char** sekvence kódované jako UTF-8.

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

převádí mezi `char32_t` sekvencemi kódované jako UTF-32 (UCS-4) a **char** sekvence kódované jako UTF-8.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[kodek](#codecvt)|Konstruktor pro objekty `codecvt` třídy, která slouží jako omezující znak národního prostředí pro zpracování převodů.|

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
|[do_encoding](#do_encoding)|Virtuální funkce, která testuje, zda `Byte` je kódování datového proudu `Byte` závislé na `CharType` stavu, zda je poměr mezi použitými hodnotami a vytvořenými hodnotami konstantní, a pokud ano, určuje hodnotu tohoto poměru.|
|[do_in](#do_in)|Virtuální funkce volaná pro `Byte` převod posloupnosti `CharType` interních hodnot na posloupnost externích hodnot.|
|[do_length](#do_length)|Virtuální funkce, která určuje, `Byte` kolik hodnot z `Byte` dané posloupnosti externích `CharType` hodnot nevytváří více `Byte` než daný počet interních hodnot a vrací tento počet hodnot.|
|[do_max_length](#do_max_length)|Virtuální funkce, která vrací maximální počet externích bajtů potřebných k vytvoření jednoho interního `CharType`.|
|[do_out](#do_out)|Virtuální funkce volaná pro `CharType` převod posloupnosti interních hodnot na posloupnost externích bajtů.|
|[do_unshift](#do_unshift)|Virtuální funkce volána `Byte` poskytnout hodnoty potřebné v převodu závislé na stavu `Byte` k dokončení poslední znak v posloupnosti hodnot.|
|[Kódování](#encoding)|Testuje, zda je `Byte` kódování datového proudu závislé na `Byte` stavu, `CharType` zda je poměr mezi použitými hodnotami a vytvořenými hodnotami konstantní, a pokud ano, určuje hodnotu tohoto poměru.|
|[in](#in)|Převede vnější reprezentaci `Byte` posloupnosti hodnot na vnitřní `CharType` reprezentaci posloupnosti hodnot.|
|[Délka](#length)|Určuje, kolik `Byte` hodnot z dané `Byte` posloupnosti externích hodnot nevytvoří více než daný počet vnitřních `CharType` hodnot, a vrátí tento počet `Byte` hodnot.|
|[max_length](#max_length)|Vrátí maximální počet `Byte` externích hodnot potřebných k vytvoření jednoho interního `CharType`.|
|[ven](#out)|Převede posloupnost `CharType` interních hodnot `Byte` na posloupnost externích hodnot.|
|[zrušit řazení](#unshift)|Poskytuje externí `Byte` hodnoty potřebné v převodu závislém na stavu `Byte` k dokončení posledního znaku v posloupnosti hodnot.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="codecvtalways_noconv"></a><a name="always_noconv"></a>kodek::always_noconv

Testuje, zda není nutné provádět žádné převody.

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Logická hodnota, která je **true,** pokud není nutné provést žádné převody; **false,** pokud alespoň jeden je třeba udělat.

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

## <a name="codecvtcodecvt"></a><a name="codecvt"></a>kodek::kodek

Konstruktor pro objekty kodeku třídy, který slouží jako omezující znak národního prostředí pro zpracování převodů.

```cpp
explicit codecvt(size_t refs = 0);
```

### <a name="parameters"></a>Parametry

*Refs*\
Celá hodnota používaná k určení typu správy paměti pro objekt.

### <a name="remarks"></a>Poznámky

Možné hodnoty parametru *refs* a jejich význam jsou:

- 0: Životnost objektu je spravována národními prostředími, které jej obsahují.

- 1: Životnost objektu musí být spravována ručně.

- 2: Tyto hodnoty nejsou definovány.

Konstruktor inicializuje `locale::facet` svůj základní objekt pomocí [národního prostředí::facet](../standard-library/locale-class.md#facet_class)`(refs)`.

## <a name="codecvtdo_always_noconv"></a><a name="do_always_noconv"></a>kodek::do_always_noconv

Virtuální funkce volána k testování, zda není nutné provést žádné převody.

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí **hodnotu** true `noconv`pouze v případě, že každé volání [do_in](#do_in) nebo [do_out](#do_out) vrátí .

Verze šablony vždy vrátí **hodnotu true**.

### <a name="example"></a>Příklad

Viz příklad pro [always_noconv](#always_noconv) `do_always_noconv`, který volá .

## <a name="codecvtdo_encoding"></a><a name="do_encoding"></a>codecvt::do_encoding

Virtuální funkce, která testuje, zda `Byte` je kódování datového proudu `Byte` závislé na `CharType` stavu, zda je poměr mezi použitými hodnotami a vytvořenými hodnotami konstantní, a pokud ano, určuje hodnotu tohoto poměru.

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Chráněná virtuální členská funkce vrátí:

- -1, pokud je kódování sekvencí typu `extern_type` závislé na stavu.

- 0, pokud kódování zahrnuje sekvence různých délek.

- *N*, pokud kódování zahrnuje pouze sekvence délky *N*

### <a name="example"></a>Příklad

Viz příklad [kódování](#encoding), který `do_encoding`volá .

## <a name="codecvtdo_in"></a><a name="do_in"></a>kodek::do_in

Virtuální funkce volaná pro `Byte` převod posloupnosti `CharType` externích hodnot na posloupnost interních hodnot.

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

*Státu*\
Stav převodu, který je udržován mezi volání členské funkce.

*první1*\
Ukazatel na začátek sekvence, která má být převedena.

*last1*\
Ukazatel na konec sekvence, která má být převedena.

*další1*\
Ukazatel za koncem převedené sekvence na první nepřevedený znak.

*první2*\
Ukazatel na začátek převedené sekvence.

*last2*\
Ukazatel na konec převedené sekvence.

*next2*\
Ukazatel na `CharType` který přichází po `CharType`poslední převedeny , na první nezměněný znak v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Návrat, který označuje úspěch, částečný úspěch nebo selhání operace. Funkce vrátí:

- `codecvt_base::error`pokud je zdrojová sekvence špatně vytvořena.

- `codecvt_base::noconv`pokud funkce neprovede žádný převod.

- `codecvt_base::ok`pokud je převod úspěšný.

- `codecvt_base::partial`Pokud zdroj je nedostatečná nebo pokud cíl není dostatečně velký, pro převod úspěšné.

### <a name="remarks"></a>Poznámky

*stav* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní jeho uloženou hodnotu podle potřeby tak, aby odrážela aktuální stav úspěšného převodu. Jeho uložená hodnota je jinak nespecifikovaná.

### <a name="example"></a>Příklad

Viz příklad pro [v](#in) `do_in`, který volá .

## <a name="codecvtdo_length"></a><a name="do_length"></a>kodek::do_délka

Virtuální funkce, která určuje, `Byte` kolik hodnot z `Byte` dané posloupnosti externích `CharType` hodnot nevytváří více `Byte` než daný počet interních hodnot a vrací tento počet hodnot.

```cpp
virtual int do_length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parametry

*Státu*\
Stav převodu, který je udržován mezi volání členské funkce.

*první1*\
Ukazatel na začátek externí sekvence.

*last1*\
Ukazatel na konec externí sekvence.

*len2*\
Maximální počet `Byte` hodnot, které mohou být vráceny členská funkce.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které představuje počet maximálního počtu převodů, které nejsou větší než *len2*, definované externí zdrojovou sekvencí na [ `first1`, `last1`).

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská `do_in( state, first1, last1, next1, buf, buf + len2, next2)` funkce efektivně volá *stav* (kopie `buf`stavu), `next1` některé `next2`vyrovnávací paměti a ukazatele a .

Potom vrátí `next2`  -  `buf`. Počítá tedy maximální počet převodů, které nejsou větší než *len2*, `first1` `last1`definované zdrojovou sekvencí na [ , ).

Verze šablony vždy vrátí menší *last1* - *first1* a *len2*.

### <a name="example"></a>Příklad

Viz příklad [délky](#length), `do_length`který volá .

## <a name="codecvtdo_max_length"></a><a name="do_max_length"></a>kodek::do_max_length

Virtuální funkce, která vrací maximální `Byte` počet externích `CharType`hodnot potřebných k vytvoření jednoho interního .

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet `Byte` hodnot potřebných `CharType`k vytvoření jedné .

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce vrátí největší přípustnou hodnotu, kterou lze vrátit [do_length](#do_length) `( first1, last1, 1)` pro libovolné platné hodnoty *first1* a *last1*.

### <a name="example"></a>Příklad

Podívejte se [max_length](#max_length)na příklad `do_max_length`pro max_length , který volá .

## <a name="codecvtdo_out"></a><a name="do_out"></a>kodek::do_out

Virtuální funkce volaná pro `CharType` převod posloupnosti `Byte` interních hodnot na posloupnost externích hodnot.

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

*Státu*\
Stav převodu, který je udržován mezi volání členské funkce.

*první1*\
Ukazatel na začátek sekvence, která má být převedena.

*last1*\
Ukazatel na konec sekvence, která má být převedena.

*další1*\
Odkaz na ukazatel na první `CharType`nepřevedený `CharType` , po posledním převedeném.

*první2*\
Ukazatel na začátek převedené sekvence.

*last2*\
Ukazatel na konec převedené sekvence.

*next2*\
Odkaz na ukazatel na první `Byte`nepřevedený `Byte` , po posledním převedeném.

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí:

- `codecvt_base::error`pokud je zdrojová sekvence špatně vytvořena.

- `codecvt_base::noconv`pokud funkce neprovede žádný převod.

- `codecvt_base::ok`pokud je převod úspěšný.

- `codecvt_base::partial`pokud zdroj je nedostatečná nebo pokud cíl není dostatečně velký pro převod úspěšné.

### <a name="remarks"></a>Poznámky

*stav* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní jeho uloženou hodnotu podle potřeby tak, aby odrážela aktuální stav úspěšného převodu. Jeho uložená hodnota je jinak nespecifikovaná.

### <a name="example"></a>Příklad

Viz příklad pro [out](#out) `do_out`, který volá .

## <a name="codecvtdo_unshift"></a><a name="do_unshift"></a>kodek::do_unshift

Virtuální funkce volána `Byte` poskytnout hodnoty potřebné v převodu závislé na stavu `Byte` k dokončení poslední znak v posloupnosti hodnot.

```cpp
virtual result do_unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*Státu*\
Stav převodu, který je udržován mezi volání členské funkce.

*první2*\
Ukazatel na první pozici v cílové oblasti.

*last2*\
Ukazatel na poslední pozici v cílové oblasti.

*next2*\
Ukazatel na první nezměněný prvek v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí:

- `codecvt_base::error`pokud *stav* představuje neplatný stav

- `codecvt_base::noconv`pokud funkce neprovádí žádný převod

- `codecvt_base::ok`pokud je převod úspěšný

- `codecvt_base::partial`Pokud cíl není dostatečně velký, aby byl převod úspěšný

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se `CharType`pokusí převést zdrojový prvek (0) na cílovou sekvenci, kterou ukládá do [ `first2`, `last2`), s výjimkou ukončujícího prvku `Byte`(0). Vždy ukládá v *next2* ukazatel na první nezměněný prvek v cílové sekvenci.

_ *Stát* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce změní jeho uloženou hodnotu podle potřeby tak, aby odrážela aktuální stav úspěšného převodu. Převod zdrojového prvku `CharType`(0) obvykle ponechá aktuální stav ve stavu počátečního převodu.

### <a name="example"></a>Příklad

Viz příklad pro [unshift](#unshift) `do_unshift`, který volá .

## <a name="codecvtencoding"></a><a name="encoding"></a>kodek::kódování

Testuje, zda je `Byte` kódování datového proudu závislé na `Byte` stavu, `CharType` zda je poměr mezi použitými hodnotami a vytvořenými hodnotami konstantní, a pokud ano, určuje hodnotu tohoto poměru.

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je vrácená hodnota kladná, je `Byte` tato hodnota `CharType` konstantní počet znaků potřebných k vytvoření znaku.

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

## <a name="codecvtextern_type"></a><a name="extern_type"></a>kodek::extern_type

Typ znaku, který se používá pro externí reprezentace.

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `Byte`parametr šablony .

## <a name="codecvtin"></a><a name="in"></a>kodek::v

Převede vnější reprezentaci `Byte` posloupnosti hodnot na vnitřní `CharType` reprezentaci posloupnosti hodnot.

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

*Státu*\
Stav převodu, který je udržován mezi volání členské funkce.

*první1*\
Ukazatel na začátek sekvence, která má být převedena.

*last1*\
Ukazatel na konec sekvence, která má být převedena.

*další1*\
Ukazatel za koncem převedené sekvence na první nepřevedený znak.

*první2*\
Ukazatel na začátek převedené sekvence.

*last2*\
Ukazatel na konec převedené sekvence.

*next2*\
Ukazatel na `CharType` který přichází po `Chartype` poslední převedeny na první nezměněný znak v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Návrat, který označuje úspěch, částečný úspěch nebo selhání operace. Funkce vrátí:

- `codecvt_base::error`pokud je zdrojová sekvence špatně vytvořena.

- `codecvt_base::noconv`pokud funkce neprovede žádný převod.

- `codecvt_base::ok`pokud je převod úspěšný.

- `codecvt_base::partial`pokud zdroj je nedostatečná nebo pokud cíl není dostatečně velký pro převod úspěšné.

### <a name="remarks"></a>Poznámky

*stav* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce podle potřeby změní uloženou hodnotu tak, aby odrážela aktuální stav úspěšného převodu. Po částečném převodu musí být *nastaven stav* tak, aby převod mohl pokračovat při doručení nových znaků.

Členská funkce vrátí [do_in](#do_in)`( state, first1,  last1,  next1, first2, last2,  next2)`.

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

## <a name="codecvtintern_type"></a><a name="intern_type"></a>kodek::intern_type

Typ znaku, který se používá pro interní reprezentace.

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `CharType`parametr šablony .

## <a name="codecvtlength"></a><a name="length"></a>kodek::délka

Určuje, kolik `Byte` hodnot z dané `Byte` posloupnosti externích hodnot nevytvoří více než daný počet vnitřních `CharType` hodnot, a vrátí tento počet `Byte` hodnot.

```cpp
int length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>Parametry

*Státu*\
Stav převodu, který je udržován mezi volání členské funkce.

*první1*\
Ukazatel na začátek externí sekvence.

*last1*\
Ukazatel na konec externí sekvence.

*len2*\
Maximální počet bajtů, které mohou být vráceny členská funkce.

### <a name="return-value"></a>Návratová hodnota

Celé číslo, které představuje počet maximálního počtu převodů, které nejsou větší než *len2*, definované externí zdrojovou sekvencí na [ `first1`, `last1`).

### <a name="remarks"></a>Poznámky

Členská funkce vrátí [do_length](#do_length)`( state, first1, last1, len2)`.

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

## <a name="codecvtmax_length"></a><a name="max_length"></a>kodek::max_length

Vrátí maximální počet `Byte` externích hodnot potřebných k vytvoření jednoho interního `CharType`.

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Maximální počet `Byte` hodnot potřebných `CharType`k vytvoření jedné .

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

## <a name="codecvtout"></a><a name="out"></a>kodek:out

Převede posloupnost `CharType` interních hodnot `Byte` na posloupnost externích hodnot.

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

*Státu*\
Stav převodu, který je udržován mezi volání členské funkce.

*první1*\
Ukazatel na začátek sekvence, která má být převedena.

*last1*\
Ukazatel na konec sekvence, která má být převedena.

*další1*\
Odkaz na ukazatel na první `CharType` nepřevedený `CharType` po posledním převedeném.

*první2*\
Ukazatel na začátek převedené sekvence.

*last2*\
Ukazatel na konec převedené sekvence.

*next2*\
Odkaz na ukazatel na první `Byte` nepřevedený po `Byte`posledním převedeném .

### <a name="return-value"></a>Návratová hodnota

Členská funkce vrátí [do_out](#do_out)`( state, first1, last1, next1, first2, last2, next2)`.

### <a name="remarks"></a>Poznámky

Další informace naleznete [v tématu codecvt::do_out](#do_out).

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

## <a name="codecvtstate_type"></a><a name="state_type"></a>kodek::state_type

Typ znaku, který se používá k reprezentaci průběžných stavů během převodu mezi interními a externími znázorněními.

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem pro `StateType`parametr šablony .

## <a name="codecvtunshift"></a><a name="unshift"></a>kodek::neřazení

Poskytuje `Byte` hodnoty potřebné v převodu závislém na stavu k `Byte` dokončení posledního znaku v posloupnosti hodnot.

```cpp
result unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>Parametry

*Státu*\
Stav převodu, který je udržován mezi volání členské funkce.

*první2*\
Ukazatel na první pozici v cílové oblasti.

*last2*\
Ukazatel na poslední pozici v cílové oblasti.

*next2*\
Ukazatel na první nezměněný prvek v cílové sekvenci.

### <a name="return-value"></a>Návratová hodnota

Funkce vrátí:

- `codecvt_base::error`pokud stav představuje neplatný stav.

- `codecvt_base::noconv`pokud funkce neprovede žádný převod.

- `codecvt_base::ok`pokud je převod úspěšný.

- `codecvt_base::partial`pokud cíl není dostatečně velký, aby byl převod úspěšný.

### <a name="remarks"></a>Poznámky

Chráněná virtuální členská funkce se `CharType`pokusí převést zdrojový prvek (0) na cílovou sekvenci, kterou ukládá do [ `first2`, `last2`), s výjimkou ukončujícího prvku `Byte`(0). Vždy ukládá v *next2* ukazatel na první nezměněný prvek v cílové sekvenci.

*stav* musí představovat počáteční stav převodu na začátku nové zdrojové sekvence. Funkce podle potřeby změní uloženou hodnotu tak, aby odrážela aktuální stav úspěšného převodu. Převod zdrojového prvku `CharType`(0) obvykle ponechá aktuální stav ve stavu počátečního převodu.

Členská funkce vrátí [do_unshift](#do_unshift)`( state, first2, last2, next2 )`.

## <a name="see-also"></a>Viz také

[\<>národního prostředí](../standard-library/locale.md)\
[Znakové stránky](../c-runtime-library/code-pages.md)\
[Názvy národních prostředí, jazyky a řetězce zemí nebo oblastí](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
