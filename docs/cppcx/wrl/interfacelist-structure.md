---
title: InterfaceList – struktura
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
ms.openlocfilehash: 70565081338f953abb65d2cdc7c5f1eb869f75e5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786706"
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

|Name|Popis|
|----------|-----------------|
|`FirstT`|Synonymum pro parametr šablony *T*.|
|`RestT`|Synonymum pro parametr šablony *U*.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`InterfaceList`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="see-also"></a>Viz také

[Microsoft::WRL::Details – obor názvů](microsoft-wrl-details-namespace.md)