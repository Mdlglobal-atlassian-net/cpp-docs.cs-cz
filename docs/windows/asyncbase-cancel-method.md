---
title: "Asyncbase::Cancel – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Cancel
dev_langs:
- C++
helpviewer_keywords:
- Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f23cae24cc3009108dd3bdadd7efc396459f0a60
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="asyncbasecancel-method"></a>AsyncBase::Cancel – metoda
Zruší asynchronní operace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   Cancel  
)(void);  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Ve výchozím nastavení vždy vrátí hodnotu S_OK.  
  
## <a name="remarks"></a>Poznámky  
 Cancel() je výchozí implementaci třídy IAsyncInfo::Cancel a nemá žádné samotnou práci. Pokud chcete skutečně zrušit asynchronní operaci, potlačení OnCancel() čistý virtuální metody.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)