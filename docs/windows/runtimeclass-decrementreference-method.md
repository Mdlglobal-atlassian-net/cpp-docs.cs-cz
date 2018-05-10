---
title: Runtimeclass::decrementreference – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass::DecrementReference
dev_langs:
- C++
ms.assetid: f5ecfeaa-2865-455b-9208-94a0685fd2c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 660c78ba8a6b3000facc43541249fb6f9856a813
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="runtimeclassdecrementreference-method"></a>RuntimeClass::DecrementReference – metoda
Snižuje počet odkaz na aktuální objekt RuntimeClass.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ULONG DecrementReference();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** implements.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [RuntimeClass – třída](../windows/runtimeclass-class.md)