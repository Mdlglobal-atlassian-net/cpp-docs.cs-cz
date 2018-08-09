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
ms.openlocfilehash: 03db2fd8853321e4a9320f2c17b05800b87e466c
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652959"
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
 [Argtraits – struktura](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)