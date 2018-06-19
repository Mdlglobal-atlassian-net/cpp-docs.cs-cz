---
title: Inspectableclass – makro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::InspectableClass
dev_langs:
- C++
ms.assetid: ff390b26-58cc-424f-87ac-1fe3cc692b59
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 922f7f74771125aed0122c408ef902da2569e5c7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873768"
---
# <a name="inspectableclass-macro"></a>InspectableClass – makro
Nastaví úroveň runtime třídy název a vztah důvěryhodnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
InspectableClass(  
   runtimeClassName,   
   trustLevel)  
```  
  
#### <a name="parameters"></a>Parametry  
 `runtimeClassName`  
 Úplné textový název třídy modulu runtime.  
  
 `trustLevel`  
 Jeden z [TrustLevel](http://msdn.microsoft.com/library/br224625.aspx) uvedené hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 `InspectableClass` Makro lze použít pouze s typy prostředí Windows Runtime.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [RuntimeClass – třída](../windows/runtimeclass-class.md)