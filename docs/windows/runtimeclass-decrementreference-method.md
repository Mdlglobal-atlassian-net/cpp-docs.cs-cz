---
title: "Runtimeclass::decrementreference – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: implements/Microsoft::WRL::RuntimeClass::DecrementReference
dev_langs: C++
ms.assetid: f5ecfeaa-2865-455b-9208-94a0685fd2c6
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fc2ccc45cad9d42ed47f88f66fa491f76dad8bc4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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