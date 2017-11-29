---
title: "ClassFactory::lockserver – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::ClassFactory::LockServer
dev_langs: C++
helpviewer_keywords: LockServer method
ms.assetid: 8d859815-956d-4f81-a5af-7cdee7e945de
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 477df9807c3eda089289930cafbe6dce1c0f6da6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 `true`Chcete-li zvýšit počet sledovaných objektů. `false`se sníží počet sledovaných objektů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném E_FAIL.  
  
## <a name="remarks"></a>Poznámky  
 ClassFactory uchovává informace o objekty v instanci základní třídy [modulu](../windows/module-class.md) třídy.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ClassFactory – třída](../windows/classfactory-class.md)