---
title: Chaininterfaces::Verify – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::ChainInterfaces::Verify
dev_langs:
- C++
helpviewer_keywords:
- Verify method
ms.assetid: c591e130-8686-4130-ba69-1aaedc250038
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 81b3a166215f7731a43333e230621072d760260c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40013529"
---
# <a name="chaininterfacesverify-method"></a>ChainInterfaces::Verify – metoda
Ověřuje, že každé rozhraní určené parametry šablony *I0* prostřednictvím *I9* dědí z `IUnknown` a/nebo `IInspectable`a že *I0* dědí z *I1* prostřednictvím *I9*.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
WRL_NOTHROW __forceinline static void Verify();  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud se ověření nezdaří, **static_assert** vydá chybovou zprávu s popisem chyby.  

 Parametry šablony *I0* a *I1* jsou povinné a parametry *I2* prostřednictvím *I9* jsou volitelné.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ChainInterfaces – struktura](../windows/chaininterfaces-structure.md)