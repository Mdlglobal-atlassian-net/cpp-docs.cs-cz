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
ms.openlocfilehash: 625d7b7d6fc001a6fb63144807b5f29d3620485b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371433"
---
# <a name="hstring-class"></a>HString – třída

Pomocná třída pro správu životnosti [HSTRING](/windows/win32/WinRT/hstring) pomocí vzoru RAII.

## <a name="syntax"></a>Syntaxe

```cpp
class HString;
```

## <a name="remarks"></a>Poznámky

Prostředí Windows Runtime poskytuje přístup k řetězcům prostřednictvím popisovačů [HSTRING.](/windows/win32/WinRT/hstring) Třída `HString` poskytuje pohodlí funkce a operátory pro zjednodušení pomocí HSTRING úchyty. Tato třída může zpracovat životnost HSTRING, který vlastní prostřednictvím vzoru RAII.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                | Popis
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | Inicializuje novou instanci třídy. `HString`
[HString::~HString](#tilde-hstring) | Zničí aktuální instanci `HString` třídy.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                     | Popis
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Připojit](#attach)               | Přidruží `HString` zadaný `HString` objekt k aktuálnímu objektu.
[hstring::CopyTo](#copyto)               | Zkopíruje `HString` aktuální objekt do objektu HSTRING.
[HString::Detach](#detach)               | Odpojí zadaný `HString` objekt od jeho základní hodnoty.
[HString::Získat](#get)                     | Načte hodnotu základního popisovače HSTRING.
[hstring::GetaddressOf](#getaddressof)   | Načte ukazatel na základní popisovač HSTRING.
[HString::GetRawBuffer](#getrawbuffer)   | Načte ukazatel na podkladová data řetězce.
[HString::IsValid](#isvalid)             | Označuje, zda `HString` je aktuální objekt platný.
[HString::MakeReference](#makereference) | Vytvoří `HStringReference` objekt z zadaného parametru řetězce.
[HString::Uvolnění](#release)             | Odstraní základní hodnotu řetězce a intializes aktuální `HString` objekt na prázdnou hodnotu.
[HString::Nastavit](#set)                     | Nastaví hodnotu `HString` aktuálního objektu na zadaný řetězec nebo `HString` parametr se širokým znakem.

### <a name="public-operators"></a>Veřejné operátory

Name (Název)                                         | Popis
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operátor=](#operator-assign)       | Přesune hodnotu `HString` jiného objektu na aktuální `HString` objekt.
[HString::operátor==](#operator-equality)    | Označuje, zda jsou dva parametry stejné.
[HString::operátor!=](#operator-inequality)  | Označuje, zda dva parametry nejsou stejné.
[HString::operátor&lt;](#operator-less-than) | Označuje, zda je první parametr menší než druhý parametr.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HString`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky

## <a name="hstringhstring"></a><a name="tilde-hstring"></a>HString::~HString

Zničí aktuální instanci `HString` třídy.

```cpp
~HString() throw()
```

## <a name="hstringattach"></a><a name="attach"></a>HString::Připojit

Přidruží `HString` zadaný `HString` objekt k aktuálnímu objektu.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parametry

*hstr*<br/>
Existující objekt `HString`.

## <a name="hstringcopyto"></a><a name="copyto"></a>hstring::CopyTo

Zkopíruje `HString` aktuální objekt do objektu HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametry

*Str*<br/>
HSTRING, který obdrží kopii.

### <a name="remarks"></a>Poznámky

Tato metoda volá funkci [WindowsDuplicateString.](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring)

## <a name="hstringdetach"></a><a name="detach"></a>HString::Detach

Odpojí zadaný `HString` objekt od jeho základní hodnoty.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Návratová hodnota

Základní `HString` hodnota před zahájením operace odpojení.

## <a name="hstringget"></a><a name="get"></a>HString::Získat

Načte hodnotu základního popisovače HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Návratová hodnota

Hodnota podkladového popisovače HSTRING

## <a name="hstringgetaddressof"></a><a name="getaddressof"></a>hstring::GetaddressOf

Načte ukazatel na základní popisovač HSTRING.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na základní popisovač HSTRING.

### <a name="remarks"></a>Poznámky

Po této operaci je zničena hodnota řetězce základního popisovače HSTRING.

## <a name="hstringgetrawbuffer"></a><a name="getrawbuffer"></a>HString::GetRawBuffer

Načte ukazatel na podkladová data řetězce.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parametry

*délka* Ukazatel **na int** proměnnou, která přijímá délku dat.

### <a name="return-value"></a>Návratová hodnota

**Const** ukazatel na základní řetězcová data.

## <a name="hstringhstring"></a><a name="hstring"></a>HString::HString

Inicializuje novou instanci třídy. `HString`

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parametry

*hstr*<br/>
Popisovač HSTRING.

*Další*<br/>
Existující objekt `HString`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje `HString` nový objekt, který je prázdný.

Druhý konstruktor inicializuje `HString` nový objekt na hodnotu existujícího *jiného* parametru a pak zničí *další* parametr.

## <a name="hstringisvalid"></a><a name="isvalid"></a>HString::IsValid

Označuje, zda `HString` je aktuální objekt prázdný nebo ne.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parametry

**true,** pokud `HString` aktuální objekt není prázdný; jinak **false**.

## <a name="hstringmakereference"></a><a name="makereference"></a>HString::MakeReference

Vytvoří `HStringReference` objekt z zadaného parametru řetězce.

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

*sizeDest*<br/>
Parametr šablony, který určuje velikost `HStringReference` cílové vyrovnávací paměti.

*Str*<br/>
Odkaz na řetězec s širokým znakem.

*Len*<br/>
Maximální délka vyrovnávací paměti parametru *str,* která má být v této operaci. Pokud není zadán parametr *len,* použije se celý parametr *str.*

### <a name="return-value"></a>Návratová hodnota

Objekt, `HStringReference` jehož hodnota je stejná jako zadaný parametr *str.*

## <a name="hstringoperator-operator"></a><a name="operator-assign"></a>HString::Operátor= Operátor

Přesune hodnotu `HString` jiného objektu na aktuální `HString` objekt.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Existující objekt `HString`.

### <a name="remarks"></a>Poznámky

Hodnota existujícího *jiného* objektu je `HString` zkopírována do aktuálního objektu a *druhý* objekt je zničen.

## <a name="hstringoperator-operator"></a><a name="operator-equality"></a>HString::operátor== Operátor

Označuje, zda jsou dva parametry stejné.

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

*Lhs*<br/>
První parametr porovnat. *lhs* může `HString` být `HStringReference` nebo objekt nebo popisovač HSTRING.

*rhs*<br/>
Druhý parametr porovnat. *rhs* může `HString` být `HStringReference` nebo objekt, nebo popisovač HSTRING.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *jsou parametry lhs* a *rhs* stejné; jinak **false**.

## <a name="hstringoperator-operator"></a><a name="operator-inequality"></a>HString::Operátor!= Operátor

Označuje, zda dva parametry nejsou stejné.

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

*Lhs*<br/>
První parametr porovnat. *lhs* může `HString` být `HStringReference` nebo objekt nebo popisovač HSTRING.

*rhs*<br/>
Druhý parametr porovnat. *rhs* může `HString` být `HStringReference` nebo objekt, nebo popisovač HSTRING.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *parametry lhs* a *rhs* nejsou stejné; jinak **false**.

## <a name="hstringoperatorlt-operator"></a><a name="operator-less-than"></a>HString::Operátor&lt; operátora

Označuje, zda je první parametr menší než druhý parametr.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
První parametr porovnat. *lhs* může být odkaz `HString`na .

*rhs*<br/>
Druhý parametr porovnat. *rhs* může být odkaz `HString`na .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je parametr *lhs* menší než parametr *rhs;* jinak **false**.

## <a name="hstringrelease"></a><a name="release"></a>HString::Uvolnění

Odstraní základní hodnotu řetězce a intializes aktuální `HString` objekt na prázdnou hodnotu.

```cpp
void Release() throw()
```

## <a name="hstringset"></a><a name="set"></a>HString::Nastavit

Nastaví hodnotu `HString` aktuálního objektu na zadaný řetězec nebo `HString` parametr se širokým znakem.

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

*Str*<br/>
Řetězec s širokým znakem.

*Len*<br/>
Maximální délka *str* parametr, který je `HString` přiřazen k aktuálnímu objektu.

*hstr*<br/>
Existující objekt `HString`.
