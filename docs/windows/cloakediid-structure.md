---
title: CloakedIid – struktura
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::CloakedIid
helpviewer_keywords:
- CloakedIid structure
ms.assetid: 82e0e377-ca3a-46bc-b850-ae2c46c15bb5
ms.openlocfilehash: 7340032e91a9b30b72099477b55b88740b3eb68f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50535301"
---
# <a name="cloakediid-structure"></a>CloakedIid – struktura

Pozná, `RuntimeClass`, `Implements` a `ChainInterfaces` šablony, že zadané rozhraní není v seznamu IID k dispozici.

## <a name="syntax"></a>Syntaxe

```cpp
template<typename T>
struct CloakedIid : T;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Rozhraní, který je skrytý (skryté).

## <a name="remarks"></a>Poznámky

Následuje příklad **cloakediid –** se používá: `struct MyRuntimeClass : RuntimeClass<CloakedIid<IMyCloakedInterface>> {}`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`T`

`CloakedIid`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)