---
title: "EventSource::add – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::EventSource::Add
dev_langs: C++
helpviewer_keywords: Add method
ms.assetid: 8bded85b-929e-4425-a464-e5de67bb774c
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: dca2e67baccfedea10f7faae9ac49ebb0e5bdb14
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="eventsourceadd-method"></a>EventSource::Add – metoda
Připojí reprezentována rozhraní zadaného delegáta sadu obslužných rutin událostí pro aktuální objekt EventSource obslužné rutiny události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `delegateInterface`  
 Rozhraní objektu delegáta, který reprezentuje obslužnou rutinu události.  
  
 `token`  
 Po dokončení této operace, popisovač, který představuje událost. Použít tento token jako parametr [Remove()](../windows/eventsource-remove-method.md) metoda vyřadí obslužné rutiny události.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [EventSource – třída](../windows/eventsource-class.md)