---
title: Interfacelist – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceList
dev_langs:
- C++
helpviewer_keywords:
- InterfaceList structure
ms.assetid: 6ec3228d-eb3e-4b7e-aef1-7dcf17bdf61a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 61a8e7b36448a485705b914fbb37892271d7d9fc
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597163"
---
# <a name="interfacelist-structure"></a>InterfaceList – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename T,
   typename U
>
struct InterfaceList;
```

### <a name="parameters"></a>Parametry

*T*  
Název rozhraní; první mapované rozhraní seznamu rekurzivní.

*U*  
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