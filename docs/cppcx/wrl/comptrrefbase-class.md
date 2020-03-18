---
title: ComPtrRefBase – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::Details::ComPtrRefBase
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable**
- client/Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown**
- client/Microsoft::WRL::Details::ComPtrRefBase::ptr_
helpviewer_keywords:
- Microsoft::WRL::Details::ComPtrRefBase class
- Microsoft::WRL::Details::ComPtrRefBase::operator IInspectable** operator
- Microsoft::WRL::Details::ComPtrRefBase::operator IUnknown** operator
- Microsoft::WRL::Details::ComPtrRefBase::ptr_ data member
ms.assetid: 6d344c1a-cc13-4a3f-8a0d-f167ccb9348f
ms.openlocfilehash: df4e2aa1ce650fd5b1f04baf2f7c4cd2fb4cff93
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418312"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase – třída

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
[ComPtr\<t >](comptr-class.md) typ nebo typ odvozený z něj, nikoli pouze rozhraní reprezentované `ComPtr`.

## <a name="remarks"></a>Poznámky

Představuje základní třídu pro třídu [ComPtrRef](comptrref-class.md) .

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

Název            | Popis
--------------- | -------------------------------------------------
`InterfaceType` | Synonymum pro typ parametru šablony *T*.

### <a name="public-operators"></a>Veřejné operátory

Název                                                                       | Popis
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase:: operator IInspectable * *](#operator-iinspectable-star-star) | Přetypování aktuálního datového členu [ptr_](#ptr) na ukazatel na `IInspectable` rozhraní.
[ComPtrRefBase:: operator IUnknown * *](#operator-iunknown-star-star)         | Přetypování aktuálního datového členu [ptr_](#ptr) na ukazatel na `IUnknown` rozhraní.

### <a name="protected-data-members"></a>Chránění členové dat

Název                        | Popis
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::p tr_](#ptr) | Ukazatel na typ určený aktuálním parametrem šablony.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ComPtrRefBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Client. h

**Obor názvů:** Microsoft:: WRL::D etails

## <a name="operator-iinspectable-star-star"></a>ComPtrRefBase:: operator IInspectable\*– operátor \*

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Poznámky

Přetypování aktuálního datového členu [ptr_](#ptr) na ukazatel na `IInspectable` rozhraní.

Pokud aktuální `ComPtrRefBase` není odvozena od `IInspectable`, bude vyvolána chyba.

Toto přetypování je k dispozici, pouze pokud je definována `__WRL_CLASSIC_COM__`.

## <a name="operator-iunknown-star-star"></a>ComPtrRefBase:: operator IUnknown * * – operátor

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Poznámky

Přetypování aktuálního datového členu [ptr_](#ptr) na ukazatel na `IUnknown` rozhraní.

Pokud aktuální `ComPtrRefBase` není odvozena od `IUnknown`, bude vyvolána chyba.

## <a name="ptr"></a>ComPtrRefBase::p tr_

Podporuje infrastrukturu WRL a není určena pro použití přímo v kódu.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Poznámky

Ukazatel na typ určený aktuálním parametrem šablony. `ptr_` je chráněným datovým členem.
