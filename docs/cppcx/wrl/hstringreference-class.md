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
ms.openlocfilehash: 591af0d66c9c209ba56310a0bd5cf5cd74e34929
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498352"
---
# <a name="hstringreference-class"></a>HStringReference – třída

Představuje HSTRING, který je vytvořen z existujícího řetězce.

## <a name="syntax"></a>Syntaxe

```cpp
class HStringReference;
```

## <a name="remarks"></a>Poznámky

Doba života záložní vyrovnávací paměti v novém HSTRING není spravována prostředí Windows Runtime. Volající přidělí zdrojový řetězec na rámec zásobníku, aby se zabránilo přidělení haldy a vyloučilo riziko nevracení paměti. Volající musí také zajistit, aby zdrojový řetězec zůstal během životnosti připojených HSTRING beze změny. Další informace najdete v tématu [funkce WindowsCreateStringReference](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name                                                    | Popis
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference:: HStringReference](#hstringreference) | Inicializuje novou instanci třídy `HStringReference` třídy.

### <a name="public-methods"></a>Veřejné metody

Člen                              | Popis
----------------------------------- | ------------------------------------------------------------------
[HStringReference:: CopyTo](#copyto) | Zkopíruje aktuální `HStringReference` objekt do objektu HSTRING.
[HStringReference:: Get](#get)       | Načte hodnotu podkladového popisovače HSTRING.
[HStringReference::GetRawBuffer](#getrawbuffer) | Načte ukazatel na podkladová řetězcová data.

### <a name="public-operators"></a>Veřejné operátory

Name                                                  | Popis
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference:: operator =](#operator-assign)       | Přesune hodnotu jiného `HStringReference` objektu na aktuální `HStringReference` objekt.
[HStringReference:: operator = = – operátor](#operator-equality)    | Určuje, zda jsou oba parametry stejné.
[HStringReference:: operator! =](#operator-inequality)  | Určuje, zda se tyto dva parametry neshodují.
[HStringReference:: operator&lt;](#operator-less-than) | Určuje, zda je první parametr menší než druhý parametr.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`HStringReference`

## <a name="requirements"></a>Požadavky

**Záhlaví:** corewrappers. h

**Hosting** Microsoft::WRL::Wrappers

## <a name="copyto"></a>HStringReference:: CopyTo

Zkopíruje aktuální `HStringReference` objekt do objektu HSTRING.

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

## <a name="get"></a>HStringReference:: Get

Načte hodnotu podkladového popisovače HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Návratová hodnota

Hodnota podkladového popisovače HSTRING.

## <a name="getrawbuffer"></a>HStringReference:: GetRawBuffer

Načte ukazatel na podkladová řetězcová data.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```
### <a name="parameters"></a>Parametry

*Délka* Ukazatel na proměnnou typu **int** , která přijímá délku dat.

### <a name="return-value"></a>Návratová hodnota

Ukazatel **const** na podkladová řetězcová data.

## <a name="hstringreference"></a>HStringReference:: HStringReference

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

*podle velikosti*<br/>
Parametr šablony, který určuje velikost cílové `HStringReference` vyrovnávací paměti.

*str*<br/>
Odkaz na řetězec s velkým znakem.

*funkce*<br/>
Maximální délka vyrovnávací paměti parametru *str* , která se má použít v této operaci. Pokud parametr *len* nezadáte, použije se celý parametr *str* . Pokud je funkce *len* větší než *Velikost*, je funkce *len* nastavena na *Velikost*1.

*jiná*<br/>
Jiný `HStringReference` objekt.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje nový `HStringReference` objekt, který má stejnou velikost jako parametr *str*.

Druhý konstruktor inicializuje nový `HStringReference` objekt, jehož velikost specifeid podle parametru *len*.

Třetí konstruktor inicializuje nový `HStringReference` objekt na hodnotu *druhého* parametru a pak odstraní *druhý* parametr.

## <a name="operator-assign"></a>HStringReference:: operator =

Přesune hodnotu jiného `HStringReference` objektu na aktuální `HStringReference` objekt.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parametry

*jiná*<br/>
Existující objekt `HStringReference`.

### <a name="remarks"></a>Poznámky

Hodnota existujícího *jiného* objektu je zkopírována do aktuálního `HStringReference` objektu a *druhý* objekt je zničen.

## <a name="operator-equality"></a>HStringReference:: operator = = – operátor

Určuje, zda jsou oba parametry stejné.

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
První parametr, který se má porovnat *LHS* může být `HStringReference` objekt nebo popisovač HSTRING.

*zarovnání indirekce RHS*<br/>
Druhý parametr, který se má porovnat.  *Zarovnání indirekce RHS* může být `HStringReference` objekt nebo popisovač HSTRING.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud jsou parametry *LHS* a *Zarovnání indirekce RHS* stejné; v opačném případě **false**.

## <a name="operator-inequality"></a>HStringReference:: operator! =

Určuje, zda se tyto dva parametry neshodují.

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
První parametr, který se má porovnat *LHS* může být `HStringReference` objekt nebo popisovač HSTRING.

*zarovnání indirekce RHS*<br/>
Druhý parametr, který se má porovnat.  *Zarovnání indirekce RHS* může být `HStringReference` objekt nebo popisovač HSTRING.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud nejsou parametry *LHS* a *Zarovnání indirekce RHS* stejné; v opačném případě **false**.

## <a name="operator-less-than"></a>HStringReference:: operator&lt;

Určuje, zda je první parametr menší než druhý parametr.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parametry

*lhs*<br/>
První parametr, který se má porovnat *LHS* může být odkazem na `HStringReference`.

*zarovnání indirekce RHS*<br/>
Druhý parametr, který se má porovnat.  *Zarovnání indirekce RHS* může být odkazem na `HStringReference`.

### <a name="return-value"></a>Návratová hodnota

**true** , pokud je parametr *LHS* menší než parametr *Zarovnání indirekce RHS* ; v opačném případě **false**.
