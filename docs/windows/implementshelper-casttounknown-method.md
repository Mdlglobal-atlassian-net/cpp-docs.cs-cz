---
title: Implementshelper::casttounknown – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::ImplementsHelper::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: 5bcfcbaf-c75f-4d43-87b3-0d6838c838d9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b786bb41e9f0667ebbb81329b2f0977525d4ba96
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598059"
---
# <a name="implementshelpercasttounknown-method"></a>ImplementsHelper::CastToUnknown – metoda

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
IUnknown* CastToUnknown();
```

## <a name="return-value"></a>Návratová hodnota

Ukazatel na základní `IUnknown` rozhraní.

## <a name="remarks"></a>Poznámky

Získá ukazatel na základní `IUnknown` rozhraní pro aktuální `Implements` struktury.

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[ImplementsHelper – struktura](../windows/implementshelper-structure.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)