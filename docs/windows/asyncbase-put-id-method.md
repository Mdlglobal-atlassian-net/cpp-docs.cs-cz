---
title: "Asyncbase::put_id – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: async/Microsoft::WRL::AsyncBase::put_Id
dev_langs: C++
helpviewer_keywords: put_Id method
ms.assetid: aebad85f-4774-42de-b625-a9cf5f65cb4e
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 4b1046b730d2e79971e5478346d011d30e5f6561
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="asyncbaseputid-method"></a>AsyncBase::put_Id – metoda
Nastaví popisovač asynchronní operaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   put_Id  
)(const unsigned int id);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 Nenulové hodnoty obslužná rutina.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota E_INVALIDARG nebo E_ILLEGAL_METHOD_CALL.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** async.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [AsyncBase – třída](../windows/asyncbase-class.md)