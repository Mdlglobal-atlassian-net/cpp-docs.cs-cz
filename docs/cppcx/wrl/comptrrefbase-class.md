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
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786966"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>Parametry

*T*<br/>
A [ComPtr\<T >](comptr-class.md) typ nebo z ní odvozené, nikoli pouze rozhraní, které jsou reprezentována `ComPtr`.

## <a name="remarks"></a>Poznámky

Představuje základní třídu pro [comptrref –](comptrref-class.md) třídy.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název            | Popis
--------------- | -------------------------------------------------
`InterfaceType` | Synonymum pro typ parametru šablony *T*.

### <a name="public-operators"></a>Veřejné operátory

Název                                                                       | Popis
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase::operator IInspectable **](#operator-iinspectable-star-star) | Přetypování aktuální [ptr_ –](#ptr) na ukazatel na ukazatel – datový člen `IInspectable` rozhraní.
[ComPtrRefBase::operator IUnknown **](#operator-iunknown-star-star)         | Přetypování aktuální [ptr_ –](#ptr) na ukazatel na ukazatel – datový člen `IUnknown` rozhraní.

### <a name="protected-data-members"></a>Chránění členové dat

Název                        | Popis
--------------------------- | ----------------------------------------------------------------
[Comptrrefbase::ptr_ –](#ptr) | Ukazatel na typ zadaný v parametru aktuální šablony.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ComPtrRefBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL::Details

## <a name="operator-iinspectable-star-star"></a>ComPtrRefBase::operator IInspectable\* \* – operátor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Poznámky

Přetypování aktuální [ptr_ –](#ptr) na ukazatel na ukazatel – datový člen `IInspectable` rozhraní.

Je vygenerován chybu, pokud aktuální `ComPtrRefBase` není odvozen od `IInspectable`.

Toto přetypování je k dispozici pouze tehdy, pokud `__WRL_CLASSIC_COM__` je definována.

## <a name="operator-iunknown-star-star"></a>ComPtrRefBase::operator IUnknown ** – operátor

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Poznámky

Přetypování aktuální [ptr_ –](#ptr) na ukazatel na ukazatel – datový člen `IUnknown` rozhraní.

Je vygenerován chybu, pokud aktuální `ComPtrRefBase` není odvozen od `IUnknown`.

## <a name="ptr"></a>Comptrrefbase::ptr_ –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Poznámky

Ukazatel na typ zadaný v parametru aktuální šablony. `ptr_` je chráněný datový člen.
