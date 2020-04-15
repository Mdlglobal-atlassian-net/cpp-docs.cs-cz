---
title: wstring_convert – třída
ms.date: 11/04/2016
f1_keywords:
- wstring/stdext::cvt::wstring_convert
- locale/std::wstring_convert::byte_string
- locale/std::wstring_convert::wide_string
- locale/std::wstring_convert::state_type
- locale/std::wstring_convert::int_type
- locale/std::wstring_convert::from_bytes
- locale/std::wstring_convert::to_bytes
- locale/std::wstring_convert::converted
- locale/std::wstring_convert::state
helpviewer_keywords:
- stdext::cvt [C++], wstring_convert
- std::wstring_convert [C++], byte_string
- std::wstring_convert [C++], wide_string
- std::wstring_convert [C++], state_type
- std::wstring_convert [C++], int_type
- std::wstring_convert [C++], from_bytes
- std::wstring_convert [C++], to_bytes
- std::wstring_convert [C++], converted
- std::wstring_convert [C++], state
ms.assetid: e34f5b65-d572-4bdc-ac69-20778712e376
ms.openlocfilehash: f09f12d9100e9faad849de608a9124f457da23df
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366370"
---
# <a name="wstring_convert-class"></a>wstring_convert – třída

Šablona `wstring_convert` třídy provádí převody mezi širokým řetězcem a bajtovým řetězcem.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```

### <a name="parameters"></a>Parametry

*Kodek*\
Omezující [znak národního prostředí,](../standard-library/locale-class.md) který představuje objekt převodu.

*Elem*\
Široký znak ový typ prvku.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který řídí převody `std::basic_string<Elem>` mezi širokoúhlými `std::basic_string<char>` objekty třídy a objekty řetězce bajtů třídy (označované také jako `std::string`). Šablona třídy definuje `wide_string` `byte_string` typy a jako synonyma pro tyto dva typy. Převod mezi posloupností `Elem` hodnot `wide_string` (uložených v objektu) a `byte_string` vícebajtovými sekvencemi `Codecvt<Elem, char, std::mbstate_t>`(uloženými v objektu) se provádí `std::codecvt<Elem, char, std::mbstate_t>`objektem třídy , který splňuje požadavky standardní hostisa převodu kódu .

Objekt této šablony třídy ukládá:

- Bajtový řetězec, který se zobrazí u chyb

- Široký řetězec, který se zobrazí při chybách

- Ukazatel na přidělený objekt převodu (který je uvolněn při zničení wbuffer_convert objektu)

- Objekt stavu převodu typu [state_type](#state_type)

- Počet konverzí

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[wstring_convert](#wstring_convert)|Vytvoří objekt typu `wstring_convert`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[byte_string](#byte_string)|Typ, který představuje řetězec bajtů.|
|[wide_string](#wide_string)|Typ, který představuje široký řetězec.|
|[state_type](#state_type)|Typ, který představuje stav převodu.|
|[int_type](#int_type)|Typ, který představuje celé číslo.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[from_bytes](#from_bytes)|Převede bajtový řetězec na široký řetězec.|
|[to_bytes](#to_bytes)|Převede široký řetězec na bajtový řetězec.|
|[Převedeny](#converted)|Vrátí počet úspěšných převodů.|
|[Státu](#state)|Vrátí objekt představující stav převodu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<> národního prostředí

**Obor názvů:** std

## <a name="wstring_convertbyte_string"></a><a name="byte_string"></a>wstring_convert::byte_string

Typ, který představuje řetězec bajtů.

```cpp
typedef std::basic_string<char> byte_string;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `std::basic_string<char>`pro .

## <a name="wstring_convertconverted"></a><a name="converted"></a>wstring_convert::převedeno

Vrátí počet úspěšných převodů.

```cpp
size_t converted() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet úspěšných převodů.

### <a name="remarks"></a>Poznámky

Počet úspěšných převodů je uložen v objektu počtu převodů.

## <a name="wstring_convertfrom_bytes"></a><a name="from_bytes"></a>wstring_convert::from_bytes

Převede bajtový řetězec na široký řetězec.

```cpp
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Byte*|Jednoelementová bajtová sekvence, která má být převedena.|
|*Ptr*|C-styl, null ukončena sekvence znaků, které mají být převedeny.|
|*Bstr*|[byte_string,](#byte_string) které mají být převedeny.|
|*První*|První znak v rozsahu znaků, které mají být převedeny.|
|*Poslední*|Poslední znak v rozsahu znaků, které mají být převedeny.|

### <a name="return-value"></a>Návratová hodnota

Široký řetězec objekt vyplývající z převodu.

### <a name="remarks"></a>Poznámky

Pokud objekt [stavu převodu](../standard-library/wstring-convert-class.md) *nebyl* vytvořen s explicitní hodnotou, je před zahájením převodu nastaven na výchozí hodnotu (počáteční stav převodu). V opačném případě zůstane beze změny.

Počet úspěšně převedených vstupních prvků je uložen v objektu počtu převodů. Pokud nedojde k žádné chybě převodu, členská funkce vrátí převedený široký řetězec. V opačném případě pokud byl objekt vytvořen s inicializátorem pro širokoúhlou chybovou zprávu, vrátí členská funkce objekt chybové zprávy s širokým řetězcem. V opačném případě členská funkce vyvolá objekt třídy [range_error](../standard-library/range-error-class.md).

## <a name="wstring_convertint_type"></a><a name="int_type"></a>wstring_convert::int_type

Typ, který představuje celé číslo.

```cpp
typedef typename wide_string::traits_type::int_type int_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `wide_string::traits_type::int_type`pro .

## <a name="wstring_convertstate"></a><a name="state"></a>wstring_convert::stav

Vrátí objekt představující stav převodu.

```cpp
state_type state() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt [stavu převodu,](../standard-library/wstring-convert-class.md) který představuje stav převodu.

### <a name="remarks"></a>Poznámky

## <a name="wstring_convertstate_type"></a><a name="state_type"></a>wstring_convert::state_type

Typ, který představuje stav převodu.

```cpp
typedef typename Codecvt::state_type state_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může představovat stav převodu. Typ je synonymem `Codecvt::state_type`pro .

## <a name="wstring_convertto_bytes"></a><a name="to_bytes"></a>wstring_convert::to_bytes

Převede široký řetězec na bajtový řetězec.

```cpp
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Char*|Široký znak, který má být převeden.|
|*Wptr řekl:*|Sekvence ve stylu C a ukončená `wptr`null, začínající na , chcete-li být převedena.|
|*Wstr*|[Wide_string,](#wide_string) které mají být převedeny.|
|*První*|První prvek v rozsahu prvků, které mají být převedeny.|
|*Poslední*|Poslední prvek v rozsahu prvků, které mají být převedeny.|

### <a name="remarks"></a>Poznámky

Pokud objekt [stavu převodu](../standard-library/wstring-convert-class.md) *nebyl* vytvořen s explicitní hodnotou, je před zahájením převodu nastaven na výchozí hodnotu (počáteční stav převodu). V opačném případě zůstane beze změny.

Počet úspěšně převedených vstupních prvků je uložen v objektu počtu převodů. Pokud nedojde k žádné chybě převodu, vrátí členská funkce převedený bajtový řetězec. V opačném případě pokud byl objekt vytvořen s inicializátorem chybové zprávy bajtového řetězce, vrátí členská funkce objekt chybové zprávy bajtového řetězce. V opačném případě členská funkce vyvolá objekt třídy [range_error](../standard-library/range-error-class.md).

## <a name="wstring_convertwide_string"></a><a name="wide_string"></a>wstring_convert::wide_string

Typ, který představuje široký řetězec.

```cpp
typedef std::basic_string<Elem> wide_string;
```

### <a name="remarks"></a>Poznámky

Typ je synonymem `std::basic_string<Elem>`pro .

## <a name="wstring_convertwstring_convert"></a><a name="wstring_convert"></a>wstring_convert::wstring_convert

Vytvoří objekt typu `wstring_convert`.

```cpp
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*\*Pcvt (Pcvt)*|Objekt typu `Codecvt` provést převod.|
|*_State*|Objekt typu [state_type](#state_type) představující stav převodu.|
|*_Berr*|Byte_string [byte_string](#byte_string) zobrazit chyby.|
|*Werr (Rak.)*|Wide_string [wide_string](#wide_string) zobrazit chyby.|

### <a name="remarks"></a>Poznámky

První konstruktor ukládá *Pcvt_arg* v [objektu převodu](../standard-library/wstring-convert-class.md)
