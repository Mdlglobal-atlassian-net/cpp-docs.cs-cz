---
title: InterfaceList – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: e0dd2a39e4764d6d33c824ca0bd1e0976fbb6ee3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472447"
---
# <a name="interfacelist-structure"></a>InterfaceList – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T, typename U>
struct InterfaceList;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Název rozhraní; první mapované rozhraní seznamu rekurzivní.

*U*<br/>
Název rozhraní; Zbývající rozhraní v seznamu rekurzivní.

## <a name="remarks"></a>Poznámky

Umožňuje vytvořit seznam rekurzivní rozhraní.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|`FirstT`|Synonymum pro parametr šablony *T*.|
|`RestT`|Synonymum pro parametr šablony *U*.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InterfaceList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)