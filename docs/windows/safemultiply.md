---
title: SafeMultiply | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SafeMultiply
dev_langs:
- C++
helpviewer_keywords:
- SafeMultiply function
ms.assetid: 81d988a5-fac7-4930-8c37-c24fa8e2c853
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 37ea091136521fc83fc63a8fb752e0f4f72cb49f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="safemultiply"></a>SafeMultiply
Vynásobí dvou čísel společně způsobem, který chrání před přetečení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T, typename U>  
inline bool SafeMultiply (  
   T t,  
   U u,  
   T& result  
) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 [v]`t`  
 První číslo, které má násobení. Toto musí být typu T.  
  
 [v]`u`  
 Druhé číslo, které má násobení. Musí se jednat o typ U.  
  
 [out]`result`  
 Parametr kde `SafeMultiply` ukládá výsledek.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true`Pokud nedojde k žádné chybě; `false` Pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určená pro operaci jeden násobení bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).  
  
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
 [SafeDivide](../windows/safedivide.md)