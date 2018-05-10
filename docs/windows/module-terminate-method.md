---
title: Module::Terminate – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Terminate
dev_langs:
- C++
helpviewer_keywords:
- Terminate method
ms.assetid: cf358117-45dc-43c7-ac1e-1e1eedc59e41
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2c1822f8c1a854274ff30795096bb639520ea8cd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="moduleterminate-method"></a>Module::Terminate – metoda
Způsobí, že všechny objekty Factory mohl vytvořit jeho instanci modulu vypnout.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void Terminate();  
```  
  
## <a name="remarks"></a>Poznámky  
 Uvolní objekty Factory v mezipaměti.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [Module – třída](../windows/module-class.md)