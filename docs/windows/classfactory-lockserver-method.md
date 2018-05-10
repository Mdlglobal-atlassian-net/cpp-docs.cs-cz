---
title: ClassFactory::lockserver – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::LockServer
dev_langs:
- C++
helpviewer_keywords:
- LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9e09a795688c7e2b31771126f9e4036ddfbd8e4f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="classfactorylockserver-method"></a>ClassFactory::LockServer – metoda
Zvýší nebo sníží počet základní objekty, které sleduje aktuální objekt ClassFactory.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   LockServer  
)(BOOL fLock);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fLock`  
 `true` Chcete-li zvýšit počet sledovaných objektů. `false` se sníží počet sledovaných objektů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném E_FAIL.  
  
## <a name="remarks"></a>Poznámky  
 ClassFactory uchovává informace o objekty v instanci základní třídy [modulu](../windows/module-class.md) třídy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ClassFactory – třída](../windows/classfactory-class.md)