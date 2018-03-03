---
title: "Chaininterfaces::Verify – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d34d117091fd8807dfefda074e510910bf059560
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify – metoda
Ověřuje, že každé rozhraní definované parametry šablony `I0` prostřednictvím `I9` dědí z IUnknown nebo IInspectable a že `I0` dědí z `I1` prostřednictvím `I9`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud se ověření nezdaří, `static_assert` vysílá chybová zpráva popisující chybu.  
  
## <a name="remarks"></a>Poznámky  
 Parametry šablony `I0` a `I1` jsou povinné, parametry a `I2` prostřednictvím `I9` jsou volitelné.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ChainInterfaces – struktura](../windows/chaininterfaces-structure.md)