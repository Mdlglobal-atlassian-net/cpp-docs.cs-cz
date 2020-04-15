---
title: HStringReference – třída
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HStringReference class
- Microsoft::WRL::Wrappers::HStringReference::CopyTo method
- Microsoft::WRL::Wrappers::HStringReference::Get method
- Microsoft::WRL::Wrappers::HStringReference::HStringReference, constructor
- Microsoft::WRL::Wrappers::HStringReference::operator= operator
- Microsoft::WRL::Wrappers::HStringReference::operator== operator
- Microsoft::WRL::Wrappers::HStringReference::operator!= operator
- Microsoft::WRL::Wrappers::HStringReference::operator< operator
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
ms.openlocfilehash: fd064f97081fad1a9df9de0865bb7c46ad5b4484
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371427"
---
# <a name="hstringreference-class"></a>HStringReference – třída

Představuje HSTRING, který je vytvořen z existujícího řetězce.

## <a name="syntax"></a>Syntaxe

```cpp
class HStringReference;
```

## <a name="remarks"></a>Poznámky

Životnost záložní vyrovnávací paměti v novém hstringu není spravována prostředím Windows Runtime. Volající přiděluje zdrojový řetězec v rámci zásobníku, aby se zabránilo přidělení haldy a eliminovat riziko nevracení paměti. Volající musí také zajistit, že zdrojový řetězec zůstane nezměněn během životnosti připojeného HSTRING. Další informace naleznete v [tématu WindowsCreateStringReference funkce](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                                    | Popis
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference::HStringReference](#hstringreference) | Inicializuje novou instanci třídy. `HStringReference`

### <a name="public-methods"></a>Veřejné metody

Člen                              | Popis
----------------------------------- | ------------------------------------------------------------------
[hStringReference::CopyTo](#copyto) | Zkopíruje `HStringReference` aktuální objekt do objektu HSTRING.
[HStringReference::Získat](#get)       | Načte hodnotu základního popisovače HSTRING.
[HStringReference::GetRawBuffer](#getrawbuffer) | Načte ukazatel na podkladová data řetězce.

### <a name="public-operators"></a>Veřejné operátory

Name (Název)                                                  | Popis
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operátor=](#operator-assign)       | Přesune hodnotu `HStringReference` jiného objektu na aktuální `HStringReference` objekt.
[HStringReference::operátor==](#operator-equality)    | Označuje, zda jsou dva parametry stejné.
[HStringReference::operátor!=](#operator-inequality)  | Označuje, zda dva parametry nejsou stejné.
[HStringReference::operátor&lt;](#operator-less-than) | Označuje, zda je první parametr menší než druhý parametr.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HStringReference`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Obor názvů:** Microsoft::WRL::Obálky

## <a name="hstringreferencecopyto"></a><a name="copyto"></a>hStringReference::CopyTo

Zkopíruje `HStringReference` aktuální objekt do objektu HSTRING.

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

## <a name="hstringreferenceget"></a><a name="get"></a>HStringReference::Získat

Načte hodnotu základního popisovače HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Návratová hodnota

Hodnota podkladového popisovače HSTRING.

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a>HStringReference::GetRawBuffer

Načte ukazatel na podkladová data řetězce.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parametry

*délka* Ukazatel **na int** proměnnou, která přijímá délku dat.

### <a name="return-value"></a>Návratová hodnota

**Const** ukazatel na základní řetězcová data.

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a>HStringReference::HStringReference

Inicializuje novou instanci třídy. `HStringReference`

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>Parametry

*sizeDest*<br/>
Parametr šablony, který určuje velikost `HStringReference` cílové vyrovnávací paměti.

*Str*<br/>
Odkaz na řetězec s širokým znakem.

*Len*<br/>
Maximální délka vyrovnávací paměti parametru *str,* která má být v této operaci. Pokud není zadán parametr *len,* použije se celý parametr *str.* Pokud je *len* větší než *sizeDest*, *je len* nastaven na *sizeDest*-1.

*Další*<br/>
Další `HStringReference` objekt.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje `HStringReference` nový objekt, který má stejnou velikost jako parametr *str*.

Druhý konstruktor inicializuje `HStringReference` nový objekt, který velikost specifeid podle *parametru len*.

Třetí konstruktor inicializuje `HStringReference` nový objekt na hodnotu *jiného* parametru a pak zničí *další* parametr.

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a>HStringReference::operátor=

Přesune hodnotu `HStringReference` jiného objektu na aktuální `HStringReference` objekt.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Existující objekt `HStringReference`.

### <a name="remarks"></a>Poznámky

Hodnota existujícího *jiného* objektu je `HStringReference` zkopírována do aktuálního objektu a *druhý* objekt je zničen.

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a>HStringReference::operátor==

Označuje, zda jsou dva parametry stejné.

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
První parametr porovnat. *lhs* může `HStringReference` být objekt nebo popisovač HSTRING.

*rhs*<br/>
Druhý parametr porovnat.  *rhs* může `HStringReference` být objekt nebo popisovač HSTRING.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *jsou parametry lhs* a *rhs* stejné; jinak **false**.

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a>HStringReference::operátor!=

Označuje, zda dva parametry nejsou stejné.

```cpp
inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
První parametr porovnat. *lhs* může `HStringReference` být objekt nebo popisovač HSTRING.

*rhs*<br/>
Druhý parametr porovnat.  *rhs* může `HStringReference` být objekt nebo popisovač HSTRING.

### <a name="return-value"></a>Návratová hodnota

**true,** pokud *parametry lhs* a *rhs* nejsou stejné; jinak **false**.

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a>HStringReference::operátor&lt;

Označuje, zda je první parametr menší než druhý parametr.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
První parametr porovnat. *lhs* může být odkaz `HStringReference`na .

*rhs*<br/>
Druhý parametr porovnat.  *rhs* může být odkaz `HStringReference`na .

### <a name="return-value"></a>Návratová hodnota

**true,** pokud je parametr *lhs* menší než parametr *rhs;* jinak **false**.
