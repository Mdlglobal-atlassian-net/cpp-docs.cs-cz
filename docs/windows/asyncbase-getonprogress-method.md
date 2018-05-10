---
title: Asyncbase::getonprogress – metoda | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- async/Microsoft::WRL::AsyncBase::GetOnProgress
dev_langs:
- C++
helpviewer_keywords:
- GetOnProgress method
ms.assetid: 286ddc9c-3e30-41a2-8e8b-e53d3fb0649d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 83af39180da819349e95051c57dc137835db87bb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="asyncbasegetonprogress-method"></a>AsyncBase::GetOnProgress – metoda
Zkopíruje adresu aktuální obslužné rutiny události průběhu na zadanou proměnnou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   GetOnProgress  
)(TProgress** progressHandler);  
```  
  
#### <a name="parameters"></a>Parametry  
 `progressHandler`  
 Umístění, kde jsou uložené na adresu aktuální obslužné rutiny události průběh.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; v opačném E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)