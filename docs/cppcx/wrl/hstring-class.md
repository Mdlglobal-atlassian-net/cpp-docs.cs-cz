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
ms.openlocfilehash: 884efb2a69b05589ad9458148409533880073878
ms.sourcegitcommit: fd466f2e14ad001f52f3dbe54f46d77be10f2d7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894407"
---
# <a name="hstring-class"></a>HString – třída

Pomocná třída pro Správa životního cyklu [HSTRING](/windows/desktop/WinRT/hstring) pomocí vzoru RAII.

## <a name="syntax"></a>Syntaxe

```cpp
class HString;
```

## <a name="remarks"></a>Poznámky

Modul Runtime Windows poskytuje přístup k řetězcům prostřednictvím [HSTRING](/windows/desktop/WinRT/hstring) obslužné rutiny. `HString` Třída poskytuje praktické funkce a operátory pro zjednodušení práce s popisovači HSTRING. Tato třída dokáže zpracovat životnost HSTRING vlastní prostřednictvím vzoru RAII.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name                                | Popis
----------------------------------- | -----------------------------------------------------
[Hstring::hstring –](#hstring)        | Inicializuje novou instanci třídy `HString` třídy.
[HString:: ~ HString](#tilde-hstring) | Odstraní aktuální instanci aplikace `HString` třídy.

### <a name="public-methods"></a>Veřejné metody

Name                                     | Popis
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[Hstring::Attach –](#attach)               | Přidruží zadaný `HString` objektu s aktuálním `HString` objektu.
[Hstring::CopyTo –](#copyto)               | Zkopíruje aktuální `HString` objektu na objekt HSTRING.
[Hstring::detach –](#detach)               | Zruší přidružení zadaného `HString` objekt ze základní hodnoty.
[Hstring::Get –](#get)                     | Načte hodnotu podkladového popisovače HSTRING.
[HString::GetAddressOf](#getaddressof)   | Načte ukazatel na podkladové popisovač HSTRING.
[HString::GetRawBuffer](#getrawbuffer)   | Načte ukazatel na podkladová data řetězce.
[HString::IsValid](#isvalid)             | Určuje, zda aktuální `HString` objektu je neplatný.
[Hstring::makereference –](#makereference) | Vytvoří `HStringReference` objekt ze zadaného parametru řetězce.
[Hstring::Release –](#release)             | Odstraní hodnotu řetězce a inicializuje aktuální `HString` objektu na prázdnou hodnotu.
[Hstring::set –](#set)                     | Nastaví hodnotu aktuální `HString` objektu zadaného řetězce širokého znaku nebo `HString` parametru.

### <a name="public-operators"></a>Veřejné operátory

Name                                         | Popis
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operator =](#operator-assign)       | Přesune hodnotu jiného `HString` objektů na aktuální `HString` objektu.
[HString::operator ==](#operator-equality)    | Určuje, zda se tyto dva parametry rovnají.
[HString::operator! =](#operator-inequality)  | Určuje, zda dva parametry nerovnají.
[HString::operator&lt;](#operator-less-than) | Označuje, zda je první parametr je menší než druhý parametr.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HString`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL::Wrappers

## <a name="tilde-hstring"></a>HString:: ~ HString

Odstraní aktuální instanci aplikace `HString` třídy.

```cpp
~HString() throw()
```

## <a name="attach"></a>Hstring::Attach –

Přidruží zadaný `HString` objektu s aktuálním `HString` objektu.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parametry

*hstr*<br/>
Existující objekt `HString`.

## <a name="copyto"></a>Hstring::CopyTo –

Zkopíruje aktuální `HString` objektu na objekt HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
HSTRING, který přijímá kopii.

### <a name="remarks"></a>Poznámky

Tato metoda volá [WindowsDuplicateString](/windows/desktop/api/winstring/nf-winstring-windowsduplicatestring) funkce.

## <a name="detach"></a>Hstring::detach –

Zruší přidružení zadaného `HString` objekt ze základní hodnoty.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Návratová hodnota

Základní `HString` hodnotu před byla zahájena operace odpojení.

## <a name="get"></a>Hstring::Get –

Načte hodnotu podkladového popisovače HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Návratová hodnota

Hodnotu podkladového popisovače HSTRING

## <a name="getaddressof"></a>HString::GetAddressOf

Načte ukazatel na podkladové popisovač HSTRING.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na podkladové popisovač HSTRING.

### <a name="remarks"></a>Poznámky

Po provedení této operace je zničen řetězcovou hodnotu podkladového popisovače HSTRING.

## <a name="getrawbuffer"></a>HString::GetRawBuffer

Načte ukazatel na podkladová data řetězce.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```
### <a name="parameters"></a>Parametry

*Délka* ukazatel **int** proměnné, která obdrží délka dat.

### <a name="return-value"></a>Návratová hodnota

A **const** ukazatel na podkladová data řetězce.


## <a name="hstring"></a>Hstring::hstring –

Inicializuje novou instanci třídy `HString` třídy.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parametry

*hstr*<br/>
Popisovač HSTRING.

*Ostatní*<br/>
Existující objekt `HString`.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje novou `HString` objekt, který je prázdný.

Druhý konstruktor inicializuje novou `HString` objektu na hodnotu stávající *jiných* parametr a potom zničí *jiných* parametru.

## <a name="isvalid"></a>HString::IsValid

Určuje, zda aktuální `HString` objekt je prázdný, nebo ne.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parametry

**Hodnota TRUE** Pokud aktuální `HString` objekt není prázdný; v opačném případě **false**.

## <a name="makereference"></a>Hstring::makereference –

Vytvoří `HStringReference` objekt ze zadaného parametru řetězce.

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
Parametr šablony, které určuje velikost cílové `HStringReference` vyrovnávací paměti.

*str*<br/>
Odkaz na řetězec širokých znaků.

*Délka*<br/>
Maximální délka *str* parametr vyrovnávací paměti pro použití v této operaci. Pokud *len* parametr není zadán, celý *str* parametr se používá.

### <a name="return-value"></a>Návratová hodnota

`HStringReference` Objekt, jehož hodnota je stejný jako zadaný *str* parametru.

## <a name="operator-assign"></a>HString::operator = – operátor

Přesune hodnotu jiného `HString` objektů na aktuální `HString` objektu.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Existující objekt `HString`.

### <a name="remarks"></a>Poznámky

Hodnota existující *Další* objekt zkopírován do aktuální `HString` objektu a pak *Další* objekt zničen.

## <a name="operator-equality"></a>HString::operator == – operátor

Určuje, zda se tyto dva parametry rovnají.

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
První parametr k porovnání. *LHS* může být `HString` nebo `HStringReference` objektu nebo popisovače HSTRING.

*Zarovnání indirekce RHS*<br/>
Druhý parametr k porovnání. *zarovnání indirekce rhs* může být `HString` nebo `HStringReference` objektu nebo popisovače HSTRING.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *lhs* a *zarovnání indirekce rhs* parametry jsou stejné, jinak **false**.

## <a name="operator-inequality"></a>HString::operator! = – operátor

Určuje, zda dva parametry nerovnají.

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
První parametr k porovnání. *LHS* může být `HString` nebo `HStringReference` objektu nebo popisovače HSTRING.

*Zarovnání indirekce RHS*<br/>
Druhý parametr k porovnání. *zarovnání indirekce rhs* může být `HString` nebo `HStringReference` objektu nebo popisovače HSTRING.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *lhs* a *zarovnání indirekce rhs* parametry nejsou stejné; jinak **false**.

## <a name="operator-less-than"></a>HString::operator&lt; – operátor

Označuje, zda je první parametr je menší než druhý parametr.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První parametr k porovnání. *LHS* může být odkazem na `HString`.

*Zarovnání indirekce RHS*<br/>
Druhý parametr k porovnání. *Zarovnání indirekce RHS* může být odkazem na `HString`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *lhs* parametr je menší než *zarovnání indirekce rhs* parametr; v opačném případě **false**.

## <a name="release"></a>Hstring::Release –

Odstraní hodnotu řetězce a inicializuje aktuální `HString` objektu na prázdnou hodnotu.

```cpp
void Release() throw()
```

## <a name="set"></a>Hstring::set –

Nastaví hodnotu aktuální `HString` objektu zadaného řetězce širokého znaku nebo `HString` parametru.

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
Širokoznaký řetězec.

*Délka*<br/>
Maximální délka *str* parametr, který je přiřazen k aktuální `HString` objektu.

*hstr*<br/>
Existující objekt `HString`.
