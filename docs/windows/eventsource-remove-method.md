---
title: "EventSource::Remove – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::EventSource::Remove
dev_langs: C++
helpviewer_keywords: Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c1879c939237275c279e1dd4bd1861ab3b02b468
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="eventsourceremove-method"></a>EventSource::Remove – metoda
Odstraní reprezentována registrační token zadané události ze sady obslužné rutiny událostí, které jsou přidružené k aktuálnímu objektu EventSource obslužné rutiny události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `token`  
 Obslužná rutina, která představuje obslužnou rutinu události. Tento token vrácená při obslužné rutiny události byl zaregistrován [Add()](../windows/eventsource-add-method.md) metoda.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota HRESULT určující chyba.  
  
## <a name="remarks"></a>Poznámky  
 Další informace o struktuře EventRegistrationToken najdete v tématu Struktura Windows::Foundation::EventRegistrationToken v prostředí Windows Runtime referenční dokumentaci k nástroji.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [EventSource – třída](../windows/eventsource-class.md)