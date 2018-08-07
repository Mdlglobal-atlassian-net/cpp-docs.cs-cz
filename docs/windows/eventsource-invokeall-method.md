---
title: EventSource::invokeall – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::InvokeAll
dev_langs:
- C++
helpviewer_keywords:
- InvokeAll method
ms.assetid: 1506618f-0421-4428-a4d0-4ea2b10a3bf6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 04a31c7d080ff4fbfae094e07ab02d912966f4b1
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570647"
---
# <a name="eventsourceinvokeall-method"></a>EventSource::InvokeAll – metoda
Volá Každá obslužná rutina události spojené s aktuálním [EventSource](../windows/eventsource-class.md) pomocí zadanými typy argumentu a argumenty.  
  
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
  
### <a name="parameters"></a>Parametry  
 *T0*  
 Typ argumentu ID nultého obslužné rutiny události.  
  
 *T1*  
 Typ prvního argumentu obslužné rutiny události.  
  
 *T2*  
 Typ druhého argumentu obslužné rutiny události.  
  
 *T3*  
 Typ třetí argument obslužné rutiny události.  
  
 *T4*  
 Typ čtvrtého argumentu obslužné rutiny události.  
  
 *T5*  
 Typ pátého argumentu obslužné rutiny události.  
  
 *T6*  
 Typ šestého argumentu obslužné rutiny události.  
  
 *T7*  
 Typ sedmého argumentu obslužné rutiny události.  
  
 *T8*  
 Typ osmého argumentu obslužné rutiny události.  
  
 *T9*  
 Typ devátého argumentu obslužné rutiny události.  
  
 *arg0*  
 Argument obslužné rutiny události ID nultého.  
  
 *arg1*  
 První argument obslužné rutiny události.  
  
 *arg2*  
 Druhý argument obslužné rutiny události.  
  
 *arg3*  
 Třetí argument obslužné rutiny události.  
  
 *arg4*  
 Čtvrtý argument obslužné rutiny události.  
  
 *arg5*  
 Pátý argument obslužné rutiny události.  
  
 *arg6*  
 Šestý argument obslužné rutiny události.  
  
 *arg7*  
 Sedmého argumentu obslužné rutiny události.  
  
 *arg8*  
 Argument obslužné rutiny události osmého.  
  
 *arg9*  
 Devátého argumentu obslužné rutiny události.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** event.h  
  
 **Namespace:** Microsoft::WRL
 
 ## <a name="see-also"></a>Viz také
 [EventSource – třída](../windows/eventsource-class.md)