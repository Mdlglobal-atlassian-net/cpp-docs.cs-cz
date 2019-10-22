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
ms.openlocfilehash: ce03510bec05f3e5e770e930759648c9add0387f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684057"
---
# <a name="wstring_convert-class"></a>wstring_convert – třída

Šablona třídy `wstring_convert` provádí převody mezi šířkou řetězce a bajtovým řetězcem.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```

### <a name="parameters"></a>Parametry

*Codecvt* \
Omezující vlastnost [národního prostředí](../standard-library/locale-class.md) , která představuje objekt převodu.

*Elem* \
Typ elementu s velkým znakem.

## <a name="remarks"></a>Poznámky

Šablona třídy popisuje objekt, který ovládá převody mezi objekty s řetězci třídy `std::basic_string<Elem>` a objekty bajtů bajtů třídy `std::basic_string<char>` (označované také jako `std::string`). Šablona třídy definuje typy `wide_string` a `byte_string` jako synonyma těchto dvou typů. Převod mezi sekvencí `Elem` hodnoty (uložený v objektu `wide_string`) a vícebajtové sekvence (uložené v objektu `byte_string`) se provádí pomocí objektu třídy `Codecvt<Elem, char, std::mbstate_t>`, který splňuje požadavky standardní omezující vlastnosti převodu kódu `std::codecvt<Elem, char, std::mbstate_t>`.

Objekt této šablony třídy ukládá:

- Bajtový řetězec, který se má zobrazit u chyb

- Velký řetězec, který se má zobrazit na chybách

- Ukazatel na objekt přidělené konverze (který je uvolněn při zničení objektu wbuffer_convert)

- Objekt stavu konverze typu [state_type](#state_type)

- Počet převodů

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[wstring_convert](#wstring_convert)|Vytvoří objekt typu `wstring_convert`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[byte_string](#byte_string)|Typ, který představuje bajtový řetězec.|
|[wide_string](#wide_string)|Typ, který představuje řetězec v šířce.|
|[state_type](#state_type)|Typ, který představuje stav převodu.|
|[int_type](#int_type)|Typ, který představuje celé číslo.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[from_bytes](#from_bytes)|Převede bajtový řetězec na řetězec, který je v šířce.|
|[to_bytes](#to_bytes)|Převede řetězec na bajt, který je velký.|
|[veden](#converted)|Vrátí počet úspěšných převodů.|
|[státech](#state)|Vrátí objekt představující stav převodu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<locale >

**Obor názvů:** std

## <a name="byte_string"></a>wstring_convert::byte_string

Typ, který představuje bajtový řetězec.

```cpp
typedef std::basic_string<char> byte_string;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `std::basic_string<char>`.

## <a name="converted"></a>wstring_convert:: převedeno

Vrátí počet úspěšných převodů.

```cpp
size_t converted() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet úspěšných převodů.

### <a name="remarks"></a>Poznámky

Počet úspěšných převodů je uložený v objektu Count konverze.

## <a name="from_bytes"></a>wstring_convert::from_bytes

Převede bajtový řetězec na řetězec, který je v šířce.

```cpp
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Bytové*|Sekvence bajtů s jedním prvkem, která má být převedena.|
|*ptr*|Styl C, sekvence znaků zakončených hodnotou null, které mají být převedeny.|
|*BSTR*|[Byte_string](#byte_string) , který se má převést.|
|*první*|První znak v rozsahu znaků, který má být převeden.|
|*posledního*|Poslední znak v rozsahu znaků, který má být převeden.|

### <a name="return-value"></a>Návratová hodnota

Objekt s velkým řetězcem, který je výsledkem převodu.

### <a name="remarks"></a>Poznámky

Pokud objekt [stavu konverze](../standard-library/wstring-convert-class.md) *nebyl vytvořen pomocí* explicitní hodnoty, je nastavena na jeho výchozí hodnotu (počáteční stav převodu) před zahájením převodu. V opačném případě zůstane beze změny.

Počet úspěšně převedených vstupních elementů je uložený v objektu Count konverze. Pokud nedochází k žádné chybě převodu, vrátí členská funkce převedený řetězec s velkým množstvím. V opačném případě, pokud byl objekt vytvořen pomocí inicializátoru pro chybovou zprávu s řetězci na šířku, vrátí členská funkce objekt chybové zprávy s velkým řetězcem. V opačném případě členská funkce vyvolá objekt třídy [range_error](../standard-library/range-error-class.md).

## <a name="int_type"></a>wstring_convert::int_type

Typ, který představuje celé číslo.

```cpp
typedef typename wide_string::traits_type::int_type int_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `wide_string::traits_type::int_type`.

## <a name="state"></a>wstring_convert:: State

Vrátí objekt představující stav převodu.

```cpp
state_type state() const;
```

### <a name="return-value"></a>Návratová hodnota

Objekt [stavu konverze](../standard-library/wstring-convert-class.md) , který představuje stav převodu.

### <a name="remarks"></a>Poznámky

## <a name="state_type"></a>wstring_convert::state_type

Typ, který představuje stav převodu.

```cpp
typedef typename Codecvt::state_type state_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může představovat stav konverze. Typ je synonymum pro `Codecvt::state_type`.

## <a name="to_bytes"></a>wstring_convert::to_bytes

Převede řetězec na bajt, který je velký.

```cpp
byte_string to_bytes(Elem Char);
byte_string to_bytes(const Elem* Wptr);
byte_string to_bytes(const wide_string& Wstr);
byte_string to_bytes(const Elem* first, const Elem* last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Char*|Velký znak, který má být převeden.|
|*Wptr*|Znak C-zakončený hodnotou null, počínaje od `wptr`, který má být převeden.|
|*Wstr*|[Wide_string](#wide_string) , který se má převést.|
|*první*|První prvek v rozsahu prvků, který má být převeden.|
|*posledního*|Poslední prvek v rozsahu prvků, který má být převeden.|

### <a name="remarks"></a>Poznámky

Pokud objekt [stavu konverze](../standard-library/wstring-convert-class.md) *nebyl vytvořen pomocí* explicitní hodnoty, je nastavena na jeho výchozí hodnotu (počáteční stav převodu) před zahájením převodu. V opačném případě zůstane beze změny.

Počet úspěšně převedených vstupních elementů je uložený v objektu Count konverze. Pokud nedochází k žádné chybě převodu, vrátí členská funkce převedený bajtový řetězec. V opačném případě, pokud byl objekt vytvořen pomocí inicializátoru pro chybovou zprávu bajtového řetězce, vrátí členská funkce objekt chybové zprávy bajtového řetězce. V opačném případě členská funkce vyvolá objekt třídy [range_error](../standard-library/range-error-class.md).

## <a name="wide_string"></a>wstring_convert::wide_string

Typ, který představuje řetězec v šířce.

```cpp
typedef std::basic_string<Elem> wide_string;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `std::basic_string<Elem>`.

## <a name="wstring_convert"></a>wstring_convert::wstring_convert

Vytvoří objekt typu `wstring_convert`.

```cpp
wstring_convert(Codecvt *Pcvt = new Codecvt);
wstring_convert(Codecvt *Pcvt, state_type _State);
wstring_convert(const byte_string& _Berr, const wide_string& Werr = wide_string());
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*\*Pcvt*|Objekt typu `Codecvt` k provedení převodu.|
|*_State*|Objekt typu [state_type](#state_type) představující stav převodu.|
|*_Berr*|[Byte_string](#byte_string) , který se má zobrazit na chybách|
|*Werr*|[Wide_string](#wide_string) , který se má zobrazit na chybách|

### <a name="remarks"></a>Poznámky

První konstruktor ukládá *Pcvt_arg* do objektu pro [Převod](../standard-library/wstring-convert-class.md) .
