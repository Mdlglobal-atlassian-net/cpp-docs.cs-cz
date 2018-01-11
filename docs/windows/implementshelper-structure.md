---
title: "Implementshelper – struktura | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::Details::ImplementsHelper
dev_langs: C++
helpviewer_keywords: ImplementsHelper structure
ms.assetid: b857ba80-81bd-4e53-92b6-210991954243
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1a51de59278e476be1e99b60ef1b0ab8a6e3f3cd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="implementshelper-structure"></a>ImplementsHelper – struktura
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <  
   typename RuntimeClassFlagsT,  
   typename ILst,  
   bool IsDelegateToClass  
>  
friend struct Details::ImplementsHelper;  
```  
  
#### <a name="parameters"></a>Parametry  
 `RuntimeClassFlagsT`  
 Pole příznaky, které určuje jeden nebo více [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) výčty.  
  
 `ILst`  
 Seznam ID rozhraní.  
  
 `IsDelegateToClass`  
 Zadejte `true` Pokud aktuální instancí třídy implementuje je základní třídou první ID rozhraní v `ILst`, jinak hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pomáhá implementovat [implementuje](../windows/implements-structure.md) struktura.  
  
 Tato šablona prochází seznam rozhraní a přidá je jako základní třídy a taky jako informace, které jsou nutné k povolení QueryInterface.  
  
## <a name="members"></a>Členové  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ImplementsHelper`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL:: details –  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace (knihovna prostředí Windows Runtime)](http://msdn.microsoft.com/en-us/00000000-0000-0000-0000-000000000000)   
 [Microsoft::WRL::Details – obor názvů](../windows/microsoft-wrl-details-namespace.md)