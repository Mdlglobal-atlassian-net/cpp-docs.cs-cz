---
title: Runtimeclass::getweakreference – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::GetWeakReference
dev_langs:
- C++
helpviewer_keywords:
- GetWeakReference method
ms.assetid: 26656ace-7f20-4364-87c9-4a75dd30912e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5cba36256e6abe176c6f5785b49a105395a30ee7
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014180"
---
# <a name="runtimeclassgetweakreference-method"></a>RuntimeClass::GetWeakReference – metoda
Získá ukazatel na objekt nestálý odkaz pro aktuální **RuntimeClass** objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDMETHOD(  
   GetWeakReference  
)(_Deref_out_ IWeakReference **weakReference);  
```  
  
### <a name="parameters"></a>Parametry  
 *weakreference –*  
 Když tato operace dokončí, ukazatel na objekt nestálý odkaz.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vždy S_OK.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [RuntimeClass – třída](../windows/runtimeclass-class.md)