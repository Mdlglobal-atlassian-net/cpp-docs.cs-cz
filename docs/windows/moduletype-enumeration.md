---
title: ModuleType – výčet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ModuleType
dev_langs:
- C++
helpviewer_keywords:
- ModuleType enumeration
ms.assetid: 61a763af-a5a4-451d-8b40-815af507fcde
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d36355c9f64f9f5c827ef8c4d5b3cb6a77d17b65
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33876833"
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