---
title: ArgTraits::args – konstanta | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits::args
dev_langs:
- C++
helpviewer_keywords:
- args constant
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0600f3a6f220d54085ff7c2ff8d60c2148ced625
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593307"
---
# <a name="argtraitsargs-constant"></a>ArgTraits::args – konstanta

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
static const int args = -1; ;
```

## <a name="remarks"></a>Poznámky

Sleduje počet parametrů `Invoke` metoda rozhraní delegáta.

## <a name="remarks"></a>Poznámky

Když **args** rovná -1 znamená, může být nalezena žádná shoda pro `Invoke` podpis metody.

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL:: details –

## <a name="see-also"></a>Viz také

[ArgTraits – struktura](../windows/argtraits-structure.md)  
[Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)