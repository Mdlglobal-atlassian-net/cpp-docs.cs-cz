---
title: Asyncbase::Cancel – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::Cancel
dev_langs:
- C++
helpviewer_keywords:
- Cancel method
ms.assetid: 8bfebc63-3848-4629-bc89-aa538ed7e7ad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0559f32315265a7db5543e8559097177c2a670fa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859849"
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