---
title: "Argtraits::args – konstanta | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Details::ArgTraits::args
dev_langs: C++
helpviewer_keywords: args constant
ms.assetid: a68100ab-254b-4571-a0bc-946f1633a46b
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: baf5f0fa0e95498f677615802b250b56fd94afec
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="argtraitsargs-constant"></a>ArgTraits::args – konstanta
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
static const int args = -1; ;  
```  
  
## <a name="remarks"></a>Poznámky  
 Udržuje počet počet parametrů na metodu Invoke rozhraní delegáta.  
  
## <a name="remarks"></a>Poznámky  
 Když `args` rovná -1 označuje může existovat žádná shoda pro podpis metody Invoke.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Argtraits – struktura](../windows/argtraits-structure.md)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)