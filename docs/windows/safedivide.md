---
title: SafeDivide | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeDivide
dev_langs:
- C++
helpviewer_keywords:
- SafeDivide function
ms.assetid: b5b27484-ad6e-46b1-ba9f-1c7120dd103b
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7c5698a85e17a8dbcb483dcd5468289df8afadcc
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605042"
---
# <a name="safedivide"></a>SafeDivide
Provede podíl dvou čísel způsobem, který chrání před dělení nulou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T, typename U>  
inline bool SafeDivide (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *t*  
 Dělitel. Toto musí být typu T.  
  
 [in] *u*  
 Dividenda. Musí se jednat o typ U.  
  
 [out] *výsledek*  
 Parametr kde **SafeDivide** výsledek je uložen.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určený pro jednu oblast operaci bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).  
  
> [!NOTE]
>  Tato metoda by měla sloužit pouze při jedné matematické operace musí být chráněné. Pokud je více operací, měli byste použít `SafeInt` třídy místo volání jednotlivých samostatné funkce.  
  
 Další informace o typech šablony T a U najdete v tématu [SafeInt – funkce](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## <a name="see-also"></a>Viz také  
 [SafeInt – funkce](../windows/safeint-functions.md)   
 [SafeInt – knihovna](../windows/safeint-library.md)   
 [SafeInt – třída](../windows/safeint-class.md)   
 [SafeModulus](../windows/safemodulus.md)   
 [SafeMultiply](../windows/safemultiply.md)