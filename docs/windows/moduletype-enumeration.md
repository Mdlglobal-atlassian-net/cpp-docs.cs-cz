---
title: "ModuleType – výčet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ModuleType
dev_langs: C++
helpviewer_keywords: ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a516795124ec3de6bb90102b3ea200d3365f33c4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="moduletype-enumeration"></a>ModuleType – výčet
Určuje, zda modul musí podporovat proces serveru nebo serveru mimo proces.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
enum ModuleType;  
```  
  
## <a name="members"></a>Členové  
  
### <a name="values"></a>Hodnoty  
  
|Název|Popis|  
|----------|-----------------|  
|`InProc`|K serveru v procesu.|  
|`OutOfProc`|Serveru mimo proces.|  
|`DisableCaching`|Zakáže ukládání do mezipaměti mechanismus v modulu.|  
|`InProcDisableCaching`|Kombinace `InProc` a `DisableCaching`.|  
|`OutOfProcDisableCaching`|Kombinace `OutOfProc` a `DisableCaching`.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)