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
ms.openlocfilehash: 71ebc02dc56b45e8790bfac7b7d4bac80d5f7729
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500489"
---
# <a name="hstring-class"></a>HString – třída

Pomocná třída pro správu životnosti [HSTRING](/windows/win32/WinRT/hstring) pomocí vzoru RAII.

## <a name="syntax"></a>Syntaxe

```cpp
class HString;
```

## <a name="remarks"></a>Poznámky

Prostředí Windows Runtime poskytuje přístup k řetězcům prostřednictvím popisovačů [HSTRING](/windows/win32/WinRT/hstring) . `HString` Třída poskytuje pohodlí funkcí a operátorů pro zjednodušení používání HSTRINGch popisovačů. Tato třída může zpracovávat životnost HSTRING, kterou vlastní, prostřednictvím vzoru RAII.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name                                | Popis
----------------------------------- | -----------------------------------------------------
[HString:: HString](#hstring)        | Inicializuje novou instanci třídy `HString` třídy.
[HString:: ~ HString](#tilde-hstring) | Odstraní aktuální instanci `HString` třídy.

### <a name="public-methods"></a>Veřejné metody

Name                                     | Popis
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString:: Attach](#attach)               | Přidruží zadaný `HString` objekt k aktuálnímu `HString` objektu.
[HString:: CopyTo](#copyto)               | Zkopíruje aktuální `HString` objekt do objektu HSTRING.
[HString::D etach](#detach)               | Zruší přidružení zadaného `HString` objektu ze své nadřazené hodnoty.
[HString:: Get](#get)                     | Načte hodnotu podkladového popisovače HSTRING.
[HString::GetAddressOf](#getaddressof)   | Načte ukazatel na podkladový popisovač HSTRING.
[HString::GetRawBuffer](#getrawbuffer)   | Načte ukazatel na podkladová řetězcová data.
[HString::IsValid](#isvalid)             | Určuje, zda je `HString` aktuální objekt platný.
[HString:: Makereference –](#makereference) | `HStringReference` Vytvoří objekt ze zadaného řetězcového parametru.
[HString:: Release](#release)             | Odstraní podkladovou řetězcovou hodnotu a inicializuje `HString` aktuální objekt na prázdnou hodnotu.
[HString:: set](#set)                     | Nastaví hodnotu aktuálního `HString` objektu na zadaný řetězec nebo `HString` parametr s velkým znakem.

### <a name="public-operators"></a>Veřejné operátory

Name                                         | Popis
-------------------------------------------- | ----------------------------------------------------------------------------
[HString:: operator =](#operator-assign)       | Přesune hodnotu jiného `HString` objektu na aktuální `HString` objekt.
[HString:: operator = = – operátor](#operator-equality)    | Určuje, zda jsou oba parametry stejné.
[HString:: operator! =](#operator-inequality)  | Určuje, zda se tyto dva parametry neshodují.
[HString:: operator&lt;](#operator-less-than) | Určuje, zda je první parametr menší než druhý parametr.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HString`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers. h

**Hosting** Microsoft::WRL::Wrappers

## <a name="tilde-hstring"></a>HString:: ~ HString

Odstraní aktuální instanci `HString` třídy.

```cpp
~HString() throw()
```

## <a name="attach"></a>HString:: Attach

Přidruží zadaný `HString` objekt k aktuálnímu `HString` objektu.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parametry

*hstr*<br/>
Existující objekt `HString`.

## <a name="copyto"></a>HString:: CopyTo

Zkopíruje aktuální `HString` objekt do objektu HSTRING.

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

Zruší přidružení zadaného `HString` objektu ze své nadřazené hodnoty.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Návratová hodnota

Nadřazená `HString` hodnota před zahájením operace odpojení.

## <a name="get"></a>HString:: Get

Načte hodnotu podkladového popisovače HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Návratová hodnota

Hodnota podkladového popisovače HSTRING

## <a name="getaddressof"></a>HString::GetAddressOf

Načte ukazatel na podkladový popisovač HSTRING.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na podkladový popisovač HSTRING.

### <a name="remarks"></a>Poznámky

Po této operaci je hodnota řetězce podkladového popisovače HSTRING zničena.

## <a name="getrawbuffer"></a>HString::GetRawBuffer

Načte ukazatel na podkladová řetězcová data.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```
### <a name="parameters"></a>Parametry

*Délka* Ukazatel na proměnnou typu **int** , která přijímá délku dat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel **const** na podkladová řetězcová data.


## <a name="hstring"></a>HString:: HString

Inicializuje novou instanci třídy `HString` třídy.

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

První konstruktor inicializuje nový `HString` objekt, který je prázdný.

Druhý konstruktor inicializuje nový `HString` objekt na hodnotu existujícího *jiného* parametru a pak zničí *druhý* parametr.

## <a name="isvalid"></a>HString:: IsValid

Určuje, zda je `HString` aktuální objekt prázdný nebo nikoli.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parametry

**true** , pokud aktuální `HString` objekt není prázdný. v opačném případě **false**.

## <a name="makereference"></a>HString:: Makereference –

`HStringReference` Vytvoří objekt ze zadaného řetězcového parametru.

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
Parametr šablony, který určuje velikost cílové `HStringReference` vyrovnávací paměti.

*str*<br/>
Odkaz na řetězec s velkým znakem.

*funkce*<br/>
Maximální délka vyrovnávací paměti parametru *str* , která se má použít v této operaci. Pokud parametr *len* nezadáte, použije se celý parametr *str* .

### <a name="return-value"></a>Návratová hodnota

Objekt, jehož hodnota je stejná jako zadaný parametr *str.* `HStringReference`

## <a name="operator-assign"></a>HString:: operator = – operátor

Přesune hodnotu jiného `HString` objektu na aktuální `HString` objekt.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parametry

*jiná*<br/>
Existující objekt `HString`.

### <a name="remarks"></a>Poznámky

Hodnota existujícího *jiného* objektu je zkopírována do aktuálního `HString` objektu a *druhý* objekt je zničen.

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
První parametr, který se má porovnat *LHS* může být `HString` objektem `HStringReference` nebo nebo popisovačem HSTRING.

*zarovnání indirekce RHS*<br/>
Druhý parametr, který se má porovnat. *Zarovnání indirekce RHS* může být `HString` objekt nebo `HStringReference` nebo popisovač HSTRING.

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
První parametr, který se má porovnat *LHS* může být `HString` objektem `HStringReference` nebo nebo popisovačem HSTRING.

*zarovnání indirekce RHS*<br/>
Druhý parametr, který se má porovnat. *Zarovnání indirekce RHS* může být `HString` objekt nebo `HStringReference` nebo popisovač HSTRING.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud nejsou parametry *LHS* a *Zarovnání indirekce RHS* stejné; v opačném případě **false**.

## <a name="operator-less-than"></a>HSTRING:: operator&lt; – operátor

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
Druhý parametr, který se má porovnat. *Zarovnání indirekce RHS* může být odkazem na `HString`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je parametr *LHS* menší než parametr *Zarovnání indirekce RHS* ; v opačném případě **false**.

## <a name="release"></a>HString:: Release

Odstraní podkladovou řetězcovou hodnotu a inicializuje `HString` aktuální objekt na prázdnou hodnotu.

```cpp
void Release() throw()
```

## <a name="set"></a>HString:: set

Nastaví hodnotu aktuálního `HString` objektu na zadaný řetězec nebo `HString` parametr s velkým znakem.

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
Maximální délka parametru *str* , který je přiřazen k aktuálnímu `HString` objektu.

*hstr*<br/>
Existující objekt `HString`.
