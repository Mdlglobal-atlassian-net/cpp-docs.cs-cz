---
title: Asyncbase::continueasyncoperation – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs:
- C++
helpviewer_keywords:
- ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: caf7cd1cbee97761c6877ec6ab3a51ea956cbfd1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation – metoda
Určuje, zda by měly pokračovat ve zpracování asynchronní operaci, nebo by měla zastaví.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline bool ContinueAsyncOperation();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud je aktuální stav asynchronní operace *spuštění*, což znamená, že operace by měly pokračovat. V opačném `false`, což znamená, že operace by měla zastaví.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)