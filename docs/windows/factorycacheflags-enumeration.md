---
title: "FactoryCacheFlags – výčet | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::FactoryCacheFlags
dev_langs: C++
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb4efeb716255ae67a01fca7cf04a54816e227d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="factorycacheflags-enumeration"></a>FactoryCacheFlags – výčet
Určuje, zda jsou v mezipaměti objektů factory.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
enum FactoryCacheFlags;  
```  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, je zadán objekt pro vytváření zásad ukládání do mezipaměti, jako [ModuleType](../windows/moduletype-enumeration.md) parametr šablony při vytváření [modulu](../windows/module-class.md) objektu. Chcete-li přepsat tuto zásadu, zadejte `FactoryCacheFlags` hodnota při vytváření objektu factory.  
  
|||  
|-|-|  
|`FactoryCacheDefault`|Pomocí zásad ukládání do mezipaměti `Module` objekt se používá.|  
|`FactoryCacheEnabled`|Nastaví objekt pro vytváření ukládání do mezipaměti bez ohledu na to `ModuleType` parametr šablony, která se používá k vytvoření `Module` objektu.|  
|`FactoryCacheDisabled`|Zakáže ukládání do mezipaměti factory bez ohledu na to `ModuleType` parametr šablony, která se používá k vytvoření `Module` objektu.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)