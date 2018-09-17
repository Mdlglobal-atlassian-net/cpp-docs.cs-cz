---
title: wstring_convert – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c56f9ea0770618e65f454acd23ea22f19d3cfa92
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45711097"
---
# <a name="wstringconvert-class"></a>wstring_convert – třída

Třída šablony `wstring_convert` provádí převody mezi širokého řetězce a řetězec bajtů.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Codecvt, class Elem = wchar_t>
class wstring_convert
```

### <a name="parameters"></a>Parametry

*codecvt –*<br/>
[Národní prostředí](../standard-library/locale-class.md) omezující vlastnost, která představuje objekt převodu.

*Elem*<br/>
Typ elementu širokého znaku.

## <a name="remarks"></a>Poznámky

Třída šablony popisuje objekt, který řídí převody mezi objekty širokého řetězce třídy `std::basic_string<Elem>` a bajt řetězcových objektů třídy `std::basic_string<char>` (označované také jako `std::string`). Třída šablony definuje typy `wide_string` a `byte_string` jako synonyma pro tyto dva typy. Převod mezi sekvencí `Elem` hodnoty (uložené v `wide_string` objekt) a vícebajtové sekvence (uložené v `byte_string` objektu) se provádí pomocí objektu třídy `Codecvt<Elem, char, std::mbstate_t>`, který splňuje požadavky standardu omezující vlastnost převodu kódu `std::codecvt<Elem, char, std::mbstate_t>`.

Ukládá se objekt této třídy šablony:

- Řetězec bajtů se zobrazí na chyby

- Široký řetězec k zobrazení chyby

- Ukazatel na objekt přidělený převod, (což je uvolněn po zničení objektu wbuffer_convert –)

- Objekt stavu převodu typu [state_type](#state_type)

- Počet převodu

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[wstring_convert](#wstring_convert)|Vytvoří objekt typu `wstring_convert`.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[byte_string](#byte_string)|Typ, který představuje řetězec bajtů.|
|[wide_string](#wide_string)|Typ, který představuje širokého řetězce.|
|[state_type](#state_type)|Typ, který představuje stav převodu.|
|[int_type](#int_type)|Typ, který představuje celé číslo.|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[from_bytes –](#from_bytes)|Převede řetězec bajtů na široký řetězec.|
|[to_bytes –](#to_bytes)|Převede širokého řetězce na řetězec bajtů.|
|[převést](#converted)|Vrátí počet úspěšných převody.|
|[Stav](#state)|Vrátí objekt představující stav převodu.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<národní prostředí >

**Namespace:** std

## <a name="byte_string"></a>  wstring_convert::byte_string

Typ, který představuje řetězec bajtů.

```cpp
typedef std::basic_string<char> byte_string;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `std::basic_string<char>`.

## <a name="converted"></a>  wstring_convert::converted

Vrátí počet úspěšných převody.

```cpp
size_t converted() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet úspěšných převody.

### <a name="remarks"></a>Poznámky

Počet úspěšných převody jsou uloženy v objektu počet převodu.

## <a name="from_bytes"></a>  wstring_convert::from_bytes

Převede řetězec bajtů na široký řetězec.

```cpp
wide_string from_bytes(char Byte);
wide_string from_bytes(const char* ptr);
wide_string from_bytes(const byte_string& Bstr);
wide_string from_bytes(const char* first, const char* last);
```

### <a name="parameters"></a>Parametry

|Parametr|Popis|
|---------------|-----------------|
|*Bajtů*|Sekvence bajtů jedním prvkem, který má být převeden.|
|*ptr*|Stylu C zakončený hodnotou null posloupnost znaků, které mají být převedeny.|
|*BSTR*|[Byte_string](#byte_string) má být převeden.|
|*první*|První znak v rozsahu znaků, které mají být převedeny.|
|*poslední*|Poslední znak v rozsahu znaků, které mají být převedeny.|

### <a name="return-value"></a>Návratová hodnota

Objekt širokého řetězce vyplývající z převodu.

### <a name="remarks"></a>Poznámky

Pokud [převodu stavu](../standard-library/wstring-convert-class.md) byl objekt *není* vytvořen s explicitní hodnotou, je nastavena na výchozí hodnotu (počáteční převodu stavu) před zahájením převodu. V opačném případě je ponechán beze změny.

Počet úspěšně převeden vstupních prvků, které jsou uloženy v objektu počet převod. Pokud nenastane žádná chyba převodu, členská funkce vrátí převedený širokého řetězce. Jinak pokud objekt byl vytvořen s inicializátorem širokých řetězců chybové zprávy, členská funkce vrátí objekt širokých řetězců chybové zprávy. V opačném případě má členská funkce vyvolá objekt třídy [range_error –](../standard-library/range-error-class.md).

## <a name="int_type"></a>  wstring_convert::int_type

Typ, který představuje celé číslo.

```cpp
typedef typename wide_string::traits_type::int_type int_type;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `wide_string::traits_type::int_type`.

## <a name="state"></a>  wstring_convert::State

Vrátí objekt představující stav převodu.

```cpp
state_type state() const;
```

### <a name="return-value"></a>Návratová hodnota

[Převodu stavu](../standard-library/wstring-convert-class.md) objekt, který představuje stav převodu.

### <a name="remarks"></a>Poznámky

## <a name="state_type"></a>  wstring_convert::state_type

Typ, který představuje stav převodu.

```cpp
typedef typename Codecvt::state_type state_type;
```

### <a name="remarks"></a>Poznámky

Typ popisuje objekt, který může představovat převod stavu. Typ je synonymum pro `Codecvt::state_type`.

## <a name="to_bytes"></a>  wstring_convert::to_bytes

Převede širokého řetězce na řetězec bajtů.

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
|*Wptr*|Stylu C zakončený hodnotou null pořadí, počínaje `wptr`, má být převeden.|
|*WSTR.*|[Wide_string](#wide_string) má být převeden.|
|*první*|První prvek v rozsahu prvků, které mají být převedeny.|
|*poslední*|Po posledním prvku v rozsahu prvků, které má být převeden.|

### <a name="remarks"></a>Poznámky

Pokud [převodu stavu](../standard-library/wstring-convert-class.md) byl objekt *není* vytvořen s explicitní hodnotou, je nastavena na výchozí hodnotu (počáteční převodu stavu) před zahájením převodu. V opačném případě je ponechán beze změny.

Počet úspěšně převeden vstupních prvků, které jsou uloženy v objektu počet převod. Pokud nenastane žádná chyba převodu, členská funkce vrátí řetězec převedený bajt. Jinak pokud objekt byl vytvořen s inicializátorem bajtů na řetězec chybové zprávy, členská funkce vrátí objekt – řetězec chybové zprávy. V opačném případě má členská funkce vyvolá objekt třídy [range_error –](../standard-library/range-error-class.md).

## <a name="wide_string"></a>  wstring_convert::wide_string

Typ, který představuje širokého řetězce.

```cpp
typedef std::basic_string<Elem> wide_string;
```

### <a name="remarks"></a>Poznámky

Typ je synonymum pro `std::basic_string<Elem>`.

## <a name="wstring_convert"></a>  wstring_convert::wstring_convert

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
|*_Stavu*|Objekt typu [state_type](#state_type) představující stav převodu.|
|*_Berr*|[Byte_string](#byte_string) se zobrazí na chyby.|
|*Werr*|[Wide_string](#wide_string) se zobrazí na chyby.|

### <a name="remarks"></a>Poznámky

První konstruktor ukládá *Pcvt_arg* v [převodu objektu](../standard-library/wstring-convert-class.md)
