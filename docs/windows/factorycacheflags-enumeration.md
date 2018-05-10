---
title: FactoryCacheFlags – výčet | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::FactoryCacheFlags
dev_langs:
- C++
ms.assetid: 6f54258f-0144-4264-9608-414e5905f6fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5ba3d9b75ff72399e1b9a027c937c24bba4a6c37
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
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
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)