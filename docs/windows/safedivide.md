---
title: SafeDivide | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeDivide
dev_langs:
- C++
helpviewer_keywords:
- SafeDivide function
ms.assetid: b5b27484-ad6e-46b1-ba9f-1c7120dd103b
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0d6d3b774cb014b8257cf412bf2dec2827abeda2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
  
#### <a name="parameters"></a>Parametry  
 [v]`t`  
 Dělitel. Toto musí být typu T.  
  
 [v]`u`  
 Dividenda. Musí se jednat o typ U.  
  
 [out]`result`  
 Parametr kde `SafeDivide` ukládá výsledek.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud nedojde k žádné chybě; `false` Pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určená pro operaci na jednu oblast bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).  
  
> [!NOTE]
>  Tato metoda by měl použít, pouze když jedné matematické operace musí být chráněny. Pokud existují více operací, měli byste použít `SafeInt` třída namísto volání jednotlivých samostatnou funkcí.  
  
 Další informace o typech šablon T a U najdete v tématu [funkce jazyka SafeInt](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## <a name="see-also"></a>Viz také  
 [SafeInt – funkce](../windows/safeint-functions.md)   
 [SafeInt – knihovna](../windows/safeint-library.md)   
 [SafeInt – třída](../windows/safeint-class.md)   
 [SafeModulus](../windows/safemodulus.md)   
 [SafeMultiply](../windows/safemultiply.md)