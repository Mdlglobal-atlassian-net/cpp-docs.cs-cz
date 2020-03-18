---
title: HString – třída
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
- corewrappers/Microsoft::WRL::Wrappers::HString::Release
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
- corewrappers/Microsoft::WRL::Wrappers::HString::~HString
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HString class
- Microsoft::WRL::Wrappers::HString::Attach method
- Microsoft::WRL::Wrappers::HString::CopyTo method
- Microsoft::WRL::Wrappers::HString::Detach method
- Microsoft::WRL::Wrappers::HString::Get method
- Microsoft::WRL::Wrappers::HString::GetAddressOf method
- Microsoft::WRL::Wrappers::HString::HString, constructor
- Microsoft::WRL::Wrappers::HString::IsValid method
- Microsoft::WRL::Wrappers::HString::MakeReference method
- Microsoft::WRL::Wrappers::HString::operator= operator
- Microsoft::WRL::Wrappers::HString::operator== operator
- Microsoft::WRL::Wrappers::HString::operator!= operator
- Microsoft::WRL::Wrappers::HString::operator< operator
- Microsoft::WRL::Wrappers::HString::Release method
- Microsoft::WRL::Wrappers::HString::Set method
- Microsoft::WRL::Wrappers::HString::~HString, destructor
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
ms.openlocfilehash: a3765da94560eb84a1d441a6b25c42822fc857bb
ms.sourcegitcommit: 44eeb065c3148d0484de791080a3f963109744fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79509468"
---
# <a name="hstring-class"></a>HString – třída

Pomocná třída pro správu životnosti [HSTRING](/windows/win32/WinRT/hstring) pomocí vzoru RAII.

## <a name="syntax"></a>Syntaxe

```cpp
class HString;
```

## <a name="remarks"></a>Poznámky

Prostředí Windows Runtime poskytuje přístup k řetězcům prostřednictvím popisovačů [HSTRING](/windows/win32/WinRT/hstring) . Třída `HString` poskytuje praktické funkce a operátory pro zjednodušení používání HSTRINGch popisovačů. Tato třída může zpracovávat životnost HSTRING, kterou vlastní, prostřednictvím vzoru RAII.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                | Popis
----------------------------------- | -----------------------------------------------------
[HString:: HString](#hstring)        | Inicializuje novou instanci třídy `HString`.
[HString:: ~ HString](#tilde-hstring) | Odstraní aktuální instanci třídy `HString`.

### <a name="public-methods"></a>Veřejné metody

Název                                     | Popis
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString:: Attach](#attach)               | Přidruží zadaný objekt `HString` k aktuálnímu objektu `HString`.
[HString:: CopyTo](#copyto)               | Zkopíruje aktuální objekt `HString` do objektu HSTRING.
[HString::D etach](#detach)               | Zruší přidružení zadaného objektu `HString` od jeho nadřazené hodnoty.
[HString:: Get](#get)                     | Načte hodnotu podkladového popisovače HSTRING.
[HString:: GetAddressOf –](#getaddressof)   | Načte ukazatel na podkladový popisovač HSTRING.
[HString:: GetRawBuffer](#getrawbuffer)   | Načte ukazatel na podkladová řetězcová data.
[HString:: IsValid](#isvalid)             | Určuje, zda je aktuální objekt `HString` platný.
[HString:: Makereference –](#makereference) | Vytvoří objekt `HStringReference` ze zadaného řetězcového parametru.
[HString:: Release](#release)             | Odstraní podkladovou řetězcovou hodnotu a inicializuje aktuální objekt `HString` k prázdné hodnotě.
[HString:: set](#set)                     | Nastaví hodnotu aktuálního objektu `HString` na zadaný řetězec s velkým znakem nebo parametr `HString`.

### <a name="public-operators"></a>Veřejné operátory

Název                                         | Popis
-------------------------------------------- | ----------------------------------------------------------------------------
[HString:: operator =](#operator-assign)       | Přesune hodnotu jiného objektu `HString` na aktuální objekt `HString`.
[HString:: operator = = – operátor](#operator-equality)    | Určuje, zda jsou oba parametry stejné.
[HString:: operator! =](#operator-inequality)  | Určuje, zda se tyto dva parametry neshodují.
[HString:: operator&lt;](#operator-less-than) | Určuje, zda je první parametr menší než druhý parametr.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HString`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers. h

**Obor názvů:** Microsoft:: WRL:: Wrappers

## <a name="tilde-hstring"></a>HString:: ~ HString

Odstraní aktuální instanci třídy `HString`.

```cpp
~HString() throw()
```

## <a name="attach"></a>HString:: Attach

Přidruží zadaný objekt `HString` k aktuálnímu objektu `HString`.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parametry

*hstr*<br/>
Existující objekt `HString`.

## <a name="copyto"></a>HString:: CopyTo

Zkopíruje aktuální objekt `HString` do objektu HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
HSTRING, který kopii obdrží.

### <a name="remarks"></a>Poznámky

Tato metoda volá funkci [WindowsDuplicateString](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring) .

## <a name="detach"></a>HString::D etach

Zruší přidružení zadaného objektu `HString` od jeho nadřazené hodnoty.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Návratová hodnota

Základní hodnota `HString` před zahájením operace odpojení.

## <a name="get"></a>HString:: Get

Načte hodnotu podkladového popisovače HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Návratová hodnota

Hodnota podkladového popisovače HSTRING

## <a name="getaddressof"></a>HString:: GetAddressOf –

Načte ukazatel na podkladový popisovač HSTRING.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na podkladový popisovač HSTRING.

### <a name="remarks"></a>Poznámky

Po této operaci je hodnota řetězce podkladového popisovače HSTRING zničena.

## <a name="getrawbuffer"></a>HString:: GetRawBuffer

Načte ukazatel na podkladová řetězcová data.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parametry

*Délka* Ukazatel na proměnnou typu **int** , která přijímá délku dat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel **const** na podkladová řetězcová data.


## <a name="hstring"></a>HString:: HString

Inicializuje novou instanci třídy `HString`.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parametry

*hstr*<br/>
HSTRING popisovač.

*jiná*<br/>
Existující objekt `HString`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje nový objekt `HString`, který je prázdný.

Druhý konstruktor inicializuje nový objekt `HString` k hodnotě existujícího *jiného* parametru a pak odstraní *druhý* parametr.

## <a name="isvalid"></a>HString:: IsValid

Určuje, zda je aktuální objekt `HString` prázdný.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parametry

**true** , pokud aktuální objekt `HString` není prázdný; v opačném případě **false**.

## <a name="makereference"></a>HString:: Makereference –

Vytvoří objekt `HStringReference` ze zadaného řetězcového parametru.

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>Parametry

*podle velikosti*<br/>
Parametr šablony, který určuje velikost cílového `HStringReference` vyrovnávací paměti.

*str*<br/>
Odkaz na řetězec s velkým znakem.

*funkce*<br/>
Maximální délka vyrovnávací paměti parametru *str* , která se má použít v této operaci. Pokud parametr *len* nezadáte, použije se celý parametr *str* .

### <a name="return-value"></a>Návratová hodnota

Objekt `HStringReference`, jehož hodnota je stejná jako zadaný parametr *str* .

## <a name="operator-assign"></a>HString:: operator = – operátor

Přesune hodnotu jiného objektu `HString` na aktuální objekt `HString`.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parametry

*jiná*<br/>
Existující objekt `HString`.

### <a name="remarks"></a>Poznámky

Hodnota existujícího *jiného* objektu je zkopírována do aktuálního objektu `HString` a *druhý* objekt je zničen.

## <a name="operator-equality"></a>HString:: operator = = – operátor

Určuje, zda jsou oba parametry stejné.

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První parametr, který se má porovnat *LHS* může být objekt `HString` nebo `HStringReference` nebo popisovač HSTRING.

*zarovnání indirekce RHS*<br/>
Druhý parametr, který se má porovnat. *Zarovnání indirekce RHS* může být objekt `HString` nebo `HStringReference` nebo popisovač HSTRING.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou parametry *LHS* a *Zarovnání indirekce RHS* stejné; v opačném případě **false**.

## <a name="operator-inequality"></a>HString:: operator! = – operátor

Určuje, zda se tyto dva parametry neshodují.

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První parametr, který se má porovnat *LHS* může být objekt `HString` nebo `HStringReference` nebo popisovač HSTRING.

*zarovnání indirekce RHS*<br/>
Druhý parametr, který se má porovnat. *Zarovnání indirekce RHS* může být objekt `HString` nebo `HStringReference` nebo popisovač HSTRING.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud nejsou parametry *LHS* a *Zarovnání indirekce RHS* stejné; v opačném případě **false**.

## <a name="operator-less-than"></a>HString:: operator&lt; – operátor

Určuje, zda je první parametr menší než druhý parametr.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První parametr, který se má porovnat *LHS* může být odkazem na `HString`.

*zarovnání indirekce RHS*<br/>
Druhý parametr, který se má porovnat. *Zarovnání indirekce RHS* může být odkaz na `HString`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je parametr *LHS* menší než parametr *Zarovnání indirekce RHS* ; v opačném případě **false**.

## <a name="release"></a>HString:: Release

Odstraní podkladovou řetězcovou hodnotu a inicializuje aktuální objekt `HString` k prázdné hodnotě.

```cpp
void Release() throw()
```

## <a name="set"></a>HString:: set

Nastaví hodnotu aktuálního objektu `HString` na zadaný řetězec s velkým znakem nebo parametr `HString`.

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
Řetězec s velkým znakem.

*funkce*<br/>
Maximální délka parametru *str* , který je přiřazen aktuálnímu objektu `HString`.

*hstr*<br/>
Existující objekt `HString`.
