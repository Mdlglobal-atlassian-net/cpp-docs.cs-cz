---
title: "Asyncbase::continueasyncoperation – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::ContinueAsyncOperation
dev_langs: C++
helpviewer_keywords: ContinueAsyncOperation method
ms.assetid: ce38181d-2fc3-4579-b0ce-237a3c7648bc
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7e86c4857aab7c0e1a23dcd03695d906a3d9e5e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasecontinueasyncoperation-method"></a>AsyncBase::ContinueAsyncOperation – metoda
Určuje, zda by měly pokračovat ve zpracování asynchronní operaci, nebo by měla zastaví.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
inline bool ContinueAsyncOperation();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud je aktuální stav asynchronní operace *spuštění*, což znamená, že operace by měly pokračovat. V opačném `false`, což znamená, že operace by měla zastaví.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)