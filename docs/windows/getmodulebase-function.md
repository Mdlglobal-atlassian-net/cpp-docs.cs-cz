---
title: "Getmodulebase – funkce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::GetModuleBase
dev_langs: C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
caps.latest.revision: "2"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 19f575705b1f8680a68e9100f20be66ca22ec87a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="getmodulebase-function"></a>GetModuleBase – funkce
Načte [ModuleBase](../windows/modulebase-class.md) ukazatele, který umožňuje zvyšování a dekrementace počet odkazů [RuntimeClass](../windows/runtimeclass-class.md) objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline Details::ModuleBase* GetModuleBase() throw()  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ukazatel na `ModuleBase` objektu.  
  
## <a name="remarks"></a>Poznámky  
 Tato funkce se používá interně ke zvýší a sníží počty odkaz na objekt.  
  
 Tuto funkci můžete použít k řízení počty odkazů voláním [modulebase::incrementobjectcount –](../windows/modulebase-incrementobjectcount-method.md) a [modulebase::decrementobjectcount –](../windows/modulebase-decrementobjectcount-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)