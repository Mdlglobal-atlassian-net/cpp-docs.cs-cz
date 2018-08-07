---
title: SafeModulus | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeModulus
dev_langs:
- C++
helpviewer_keywords:
- SafeModulus function
ms.assetid: ae5c81eb-5dcf-45a5-aa76-465fdfe68654
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6eaac98e7794ba9a2475cf7b56641d3a779f84d5
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39604882"
---
# <a name="safemodulus"></a>SafeModulus
Provádí operace numerického zbytku dvou čísel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T, typename U>  
inline bool SafeModulus (  
   const T t,  
   const U u,  
   T& result  
) throw ();  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *t*  
 Dělitel. Musí se jednat o typ `T`.  
  
 [in] *u*  
 Dividenda. Musí se jednat o typ `U`.  
  
 [out] *výsledek*  
 Parametr kde **SafeModulus** výsledek je uložen.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určená pro operace numerického zbytku jeden bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).  
  
> [!NOTE]
>  Tato metoda by měla sloužit pouze při jedné matematické operace musí být chráněné. Pokud je více operací, měli byste použít `SafeInt` třídy místo volání jednotlivých samostatné funkce.  
  
 Další informace o typech šablon `T` a `U`, naleznete v tématu [SafeInt – funkce](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## <a name="see-also"></a>Viz také  
 [SafeInt – funkce](../windows/safeint-functions.md)   
 [SafeInt – knihovna](../windows/safeint-library.md)   
 [SafeInt – třída](../windows/safeint-class.md)   
 [SafeDivide](../windows/safedivide.md)