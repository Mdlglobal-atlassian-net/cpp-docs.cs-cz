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
ms.openlocfilehash: 4f6dd6449cf8135ad14486d64cea95d8329e0014
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372621"
---
# <a name="comptrrefbase-class"></a>ComPtrRefBase – třída

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtrRefBase;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ>nebo typ odvozený od [společnosti\<ComPtr T,](comptr-class.md) `ComPtr`nikoli pouze rozhraní reprezentované rozhraním .

## <a name="remarks"></a>Poznámky

Představuje základní třídu pro třídu [ComPtrRef.](comptrref-class.md)

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)            | Popis
--------------- | -------------------------------------------------
`InterfaceType` | Synonymum pro typ parametru šablony *T*.

### <a name="public-operators"></a>Veřejné operátory

Name (Název)                                                                       | Popis
-------------------------------------------------------------------------- | -----------------------------------------------------------------------------------------------------
[ComPtrRefBase::operátor IInspectable**](#operator-iinspectable-star-star) | Předává aktuální [ptr_](#ptr) datový člen ukazatel na ukazatel na `IInspectable` rozhraní.
[ComPtrRefBase::operátor INeznámý**](#operator-iunknown-star-star)         | Předává aktuální [ptr_](#ptr) datový člen ukazatel na ukazatel na `IUnknown` rozhraní.

### <a name="protected-data-members"></a>Členové chráněných dat

Name (Název)                        | Popis
--------------------------- | ----------------------------------------------------------------
[ComPtrRefBase::ptr_](#ptr) | Ukazatel na typ určený aktuálním parametrem šablony.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ComPtrRefBase`

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="comptrrefbaseoperator-iinspectable-operator"></a><a name="operator-iinspectable-star-star"></a>ComPtrRefBase::operátor IKontroloce\* \*

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
operator IInspectable**() const;
```

### <a name="remarks"></a>Poznámky

Předává aktuální [ptr_](#ptr) datový člen ukazatel na ukazatel na `IInspectable` rozhraní.

Chyba je vyzařována, pokud proud `ComPtrRefBase` není odvozen z `IInspectable`aplikace .

Toto přetypádka je k dispozici pouze v případě, že `__WRL_CLASSIC_COM__` je definován.

## <a name="comptrrefbaseoperator-iunknown-operator"></a><a name="operator-iunknown-star-star"></a>ComPtrRefBase::operátor INeznámý** Operátor

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
operator IUnknown**() const;
```

### <a name="remarks"></a>Poznámky

Předává aktuální [ptr_](#ptr) datový člen ukazatel na ukazatel na `IUnknown` rozhraní.

Chyba je vyzařována, pokud proud `ComPtrRefBase` není odvozen z `IUnknown`aplikace .

## <a name="comptrrefbaseptr_"></a><a name="ptr"></a>ComPtrRefBase::ptr_

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
T* ptr_;
```

### <a name="remarks"></a>Poznámky

Ukazatel na typ určený aktuálním parametrem šablony. `ptr_`je chráněný datový člen.
