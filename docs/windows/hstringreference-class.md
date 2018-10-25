---
title: Hstringreference – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/25/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4754a74365b2c596e240bd13eb11fdc852205e2c
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077880"
---
# <a name="hstringreference-class"></a>HStringReference – třída

Představuje HSTRING, který je vytvořený z existujícího řetězce.

## <a name="syntax"></a>Syntaxe

```cpp
class HStringReference;
```

## <a name="remarks"></a>Poznámky

Doba života běhu záložní vyrovnávací paměti v novém HSTRING není spravována modulu Windows Runtime. Volající alokuje zdrojový řetězec v zásobníku přidělení haldy a odstranilo nebezpečí nevracení paměti. Volající také musí zajistit, že zdrojový řetězec se nezmění po celou dobu životnosti připojených HSTRING. Další informace najdete v tématu [WindowsCreateStringReference funkce](/windows/desktop/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                    | Popis
------------------------------------------------------- | -----------------------------------------------------------
[Hstringreference::hstringreference –](#hstringreference) | Inicializuje novou instanci třídy `HStringReference` třídy.

### <a name="public-methods"></a>Veřejné metody

Člen                              | Popis
----------------------------------- | ------------------------------------------------------------------
[Hstringreference::CopyTo –](#copyto) | Zkopíruje aktuální `HStringReference` objektu na objekt HSTRING.
[Hstringreference::Get –](#get)       | Načte hodnotu podkladového popisovače HSTRING.

### <a name="public-operators"></a>Veřejné operátory

Název                                                  | Popis
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operator =](#operator-assign)       | Přesune hodnotu jiného `HStringReference` objektů na aktuální `HStringReference` objektu.
[HStringReference::operator ==](#operator-equality)    | Určuje, zda se tyto dva parametry rovnají.
[HStringReference::operator! =](#operator-inequality)  | Určuje, zda dva parametry nerovnají.
[HStringReference::operator&lt;](#operator-less-than) | Označuje, zda je první parametr je menší než druhý parametr.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HStringReference`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers.h

**Namespace:** Microsoft::WRL:: wrappers –

## <a name="copyto"></a>Hstringreference::CopyTo –

Zkopíruje aktuální `HStringReference` objektu na objekt HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
HSTRING, který přijímá kopii.

### <a name="remarks"></a>Poznámky

Tato metoda volá [WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx) funkce.

## <a name="get"></a>Hstringreference::Get –

Načte hodnotu podkladového popisovače HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Návratová hodnota

Hodnotu podkladového popisovače HSTRING.

## <a name="hstringreference"></a>Hstringreference::hstringreference –

Inicializuje novou instanci třídy `HStringReference` třídy.

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
Parametr šablony, které určuje velikost cílové `HStringReference` vyrovnávací paměti.

*str*<br/>
Odkaz na řetězec širokých znaků.

*Délka*<br/>
Maximální délka *str* parametr vyrovnávací paměti pro použití v této operaci. Pokud *len* parametr není zadán, celý *str* parametr se používá. Pokud *len* je větší než *sizeDest*, *len* je nastavena na *sizeDest*-1.

*Ostatní*<br/>
Jiné `HStringReference` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje novou `HStringReference` objekt, který stejné velikosti jako parametr *str*.

Druhý konstruktor inicializuje novou `HStringReference` objekt, který specifeid velikost parametrem *len*.

Třetí konstruktor inicializuje novou `HStringReference` objektu na hodnotu *jiných* parametr a potom zničí *jiných* parametru.

## <a name="operator-assign"></a>HStringReference::operator =

Přesune hodnotu jiného `HStringReference` objektů na aktuální `HStringReference` objektu.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Existující objekt `HStringReference`.

### <a name="remarks"></a>Poznámky

Hodnota existující *Další* objekt zkopírován do aktuální `HStringReference` objektu a pak *Další* objekt zničen.

## <a name="operator-equality"></a>HStringReference::operator ==

Určuje, zda se tyto dva parametry rovnají.

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

*lhs*<br/>
První parametr k porovnání. *LHS* může být `HStringReference` objektu nebo popisovače HSTRING.

*Zarovnání indirekce RHS*<br/>
Druhý parametr k porovnání.  *Zarovnání indirekce RHS* může být `HStringReference` objektu nebo popisovače HSTRING.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *lhs* a *zarovnání indirekce rhs* parametry jsou stejné, jinak **false**.

## <a name="operator-inequality"></a>HStringReference::operator! =

Určuje, zda dva parametry nerovnají.

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

*lhs*<br/>
První parametr k porovnání. *LHS* může být `HStringReference` objektu nebo popisovače HSTRING.

*Zarovnání indirekce RHS*<br/>
Druhý parametr k porovnání.  *Zarovnání indirekce RHS* může být `HStringReference` objektu nebo popisovače HSTRING.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *lhs* a *zarovnání indirekce rhs* parametry nejsou stejné; jinak **false**.

## <a name="operator-less-than"></a>HStringReference::operator&lt;

Označuje, zda je první parametr je menší než druhý parametr.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První parametr k porovnání. *LHS* může být odkazem na `HStringReference`.

*Zarovnání indirekce RHS*<br/>
Druhý parametr k porovnání.  *Zarovnání indirekce RHS* může být odkazem na `HStringReference`.

### <a name="return-value"></a>Návratová hodnota

**Hodnota TRUE** Pokud *lhs* parametr je menší než *zarovnání indirekce rhs* parametr; v opačném případě **false**.
