---
title: DerefHelper – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::Details::DerefHelper
helpviewer_keywords:
- DerefHelper structure
ms.assetid: 86ded58b-c3ee-4a4f-bb86-4f67b895d427
ms.openlocfilehash: 7709ae63e4d49e25aec83a069ad1ac614bfbd953
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334694"
---
# <a name="derefhelper-structure"></a>DerefHelper – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
struct DerefHelper;

template <typename T>
struct DerefHelper<T*>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Parametr šablony.

## <a name="remarks"></a>Poznámky

Představuje ukazatel přes ukazatel `T*` parametr šablony.

**Derefhelper –** , jako je použít ve výrazu: `ComPtr<Details::DerefHelper<ProgressTraits::Arg1Type>::DerefType> operationInterface;`.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`DerefType`|Identifikátor pro parametr šablony přes ukazatel `T*`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`DerefHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** async.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)