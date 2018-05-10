---
title: SafeLessThanEquals | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeLessThanEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeLessThanEquals function
ms.assetid: cbd70526-faf2-4fbc-96a0-b61e8cf5f04a
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dd783f5d611b6055c542f56d04e2249b71b31218
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="safelessthanequals"></a>SafeLessThanEquals
Porovná dvě čísla.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template <typename T, typename U>  
inline bool SafeLessThanEquals (  
   const T t,  
   const U u  
) throw ();  
```  
  
#### <a name="parameters"></a>Parametry  
 [v] `t`  
 První číslo k porovnání. Toto musí být typu T.  
  
 [v] `u`  
 Druhé číslo k porovnání. Musí se jednat o typ U.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `t` je menší než nebo rovno `u`jinak `false`.  
  
## <a name="remarks"></a>Poznámky  
 `SafeLessThanEquals` rozšiřuje regulární relační operátor povolením můžete porovnat dva různé typy čísel.  
  
 Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určená pro operaci jedno porovnání bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).  
  
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
 [SafeGreaterThan](../windows/safegreaterthan.md)   
 [SafeLessThan](../windows/safelessthan.md)   
 [SafeGreaterThanEquals](../windows/safegreaterthanequals.md)