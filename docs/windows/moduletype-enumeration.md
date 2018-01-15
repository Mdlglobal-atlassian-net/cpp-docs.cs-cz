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
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd68d911a3734510bfb35db4b3ee0c4b8e46a4a0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)