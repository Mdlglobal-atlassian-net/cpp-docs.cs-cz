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
ms.openlocfilehash: 5bb328b93231646cd3b0ceeea42382d8f8857e21
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Microsoft::WRL:: details – Namespace](../windows/microsoft-wrl-details-namespace.md)