---
title: Implementshelper – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs:
- C++
helpviewer_keywords:
- ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5a3a31125d8489551f1eec143013661bf385f29a
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43212442"
---
# <a name="implementshelper-structure"></a>ImplementsHelper – struktura

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template <
   typename RuntimeClassFlagsT,
   typename ILst,
   bool IsDelegateToClass
>
friend struct Details::ImplementsHelper;
```

### <a name="parameters"></a>Parametry

*RuntimeClassFlagsT*  
Pole, která určuje jeden nebo více příznaků [runtimeclasstype –](../windows/runtimeclasstype-enumeration.md) enumerátory.

*ILst*  
Seznam ID rozhraní.

*IsDelegateToClass*  
Zadejte **true** Pokud aktuální instancí třídy `Implements` je základní třídou ID prvního rozhraní v *ILst*; v opačném případě **false**.

## <a name="remarks"></a>Poznámky

Pomáhá implementovat [implementuje](../windows/implements-structure.md) struktury.

Tato šablona prochází seznam rozhraní a přidá je jako základní třídy a jako informace nutné k povolení `QueryInterface`.

## <a name="members"></a>Členové

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ImplementsHelper`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[Referenční dokumentace (knihovna Windows Runtime)](https://msdn.microsoft.com/00000000-0000-0000-0000-000000000000)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)