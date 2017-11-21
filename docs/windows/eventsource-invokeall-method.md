---
title: "EventSource::invokeall – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::EventSource::InvokeAll
dev_langs: C++
helpviewer_keywords: InvokeAll method
ms.assetid: 1506618f-0421-4428-a4d0-4ea2b10a3bf6
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 279d40bf8da171547e27313c4f1a9a3578d93be2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="eventsourceinvokeall-method"></a>EventSource::InvokeAll – metoda
Volá každý obslužná rutina události související s aktuálním [EventSource](../windows/eventsource-class.md) pomocí zadané typy argumentů a argumenty.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void InvokeAll();  
template <  
   typename T0  
>  
void InvokeAll(  
   T0arg0  
);  
template <  
   typename T0,  
   typename T1  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7,  
   typename T8  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7,  
   T8arg8  
);  
template <  
   typename T0,  
   typename T1,  
   typename T2,  
   typename T3,  
   typename T4,  
   typename T5,  
   typename T6,  
   typename T7,  
   typename T8,  
   typename T9  
>  
void InvokeAll(  
   T0arg0,  
   T1arg1,  
   T2arg2,  
   T3arg3,  
   T4arg4,  
   T5arg5,  
   T6arg6,  
   T7arg7,  
   T8arg8,  
   T9arg9  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `T0`  
 Typ argumentu zeroth obslužná rutina události.  
  
 `T1`  
 Typ prvního argumentu obslužná rutina události.  
  
 `T2`  
 Typ druhý argument obslužná rutina události.  
  
 `T3`  
 Typ třetí argument obslužná rutina události.  
  
 `T4`  
 Typ čtvrtého argumentu obslužná rutina události.  
  
 `T5`  
 Typ argumentu páté obslužná rutina události.  
  
 `T6`  
 Typ šestého argumentu obslužná rutina události.  
  
 `T7`  
 Typ sedmého argumentu obslužná rutina události.  
  
 `T8`  
 Typ argumentu nakrmeni obslužná rutina události.  
  
 `T9`  
 Typ argumentu deváté obslužná rutina události.  
  
 `arg0`  
 Argument zeroth obslužná rutina události.  
  
 `arg1`  
 První argument obslužná rutina události.  
  
 `arg2`  
 Druhý argument obslužná rutina události.  
  
 `arg3`  
 Třetí argument obslužná rutina události.  
  
 `arg4`  
 Čtvrtý argument obslužná rutina události.  
  
 `arg5`  
 Páté argumentu obslužná rutina události.  
  
 `arg6`  
 Šesté argumentu obslužná rutina události.  
  
 `arg7`  
 Sedmého argumentu obslužná rutina události.  
  
 `arg8`  
 Argument nakrmeni obslužná rutina události.  
  
 `arg9`  
 Deváté argumentu obslužná rutina události.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [EventSource – třída](../windows/eventsource-class.md)