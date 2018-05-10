---
title: Asyncbase::putonprogress – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnProgress
dev_langs:
- C++
helpviewer_keywords:
- PutOnProgress method
ms.assetid: 1f5f180e-eb5a-4afe-ac16-69dbf36f0383
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c12709bdcac615937c938468bcf0e2daca437675
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="asyncbaseputonprogress-method"></a>AsyncBase::PutOnProgress – metoda
Nastaví adresu průběh obslužné rutiny události se zadanou hodnotou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   PutOnProgress  
)(TProgress* progressHandler);  
```  
  
#### <a name="parameters"></a>Parametry  
 `progressHandler`  
 Adresa, na kterou je nastavena obslužné rutiny události průběh.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)