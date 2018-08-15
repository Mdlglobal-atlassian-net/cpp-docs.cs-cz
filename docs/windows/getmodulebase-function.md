---
title: Getmodulebase – funkce | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 25e4bb6db6114f7d64522dfe145d51ffaabd476a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874204"
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