---
title: Asyncbase::putoncomplete – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::PutOnComplete
dev_langs:
- C++
helpviewer_keywords:
- PutOnComplete method
ms.assetid: 1c469ff9-b2df-4637-bf05-01a617043149
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 490484a6988851565b478ef41ad16f0c722eb804
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856069"
---
# <a name="asyncbaseputoncomplete-method"></a>AsyncBase::PutOnComplete – metoda
Nastaví adresu dokončení obslužné rutiny události se zadanou hodnotou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   PutOnComplete  
)(TComplete* completeHandler);  
```  
  
#### <a name="parameters"></a>Parametry  
 `completeHandler`  
 Adresa, na kterou je nastavena obslužné rutiny události dokončení.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)