---
title: Runtimeclass::addref – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::AddRef
dev_langs:
- C++
helpviewer_keywords:
- AddRef method
ms.assetid: 9c705749-680b-4308-bbec-5b601e8e7dbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3a2f7025d9e367c2a31d14012d9f6b22de3e70f2
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011709"
---
# <a name="runtimeclassaddref-method"></a>RuntimeClass::AddRef – metoda
Zvýší počet odkazů pro aktuální **RuntimeClass** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD_(  
   ULONG,  
   AddRef  
)();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [RuntimeClass – třída](../windows/runtimeclass-class.md)