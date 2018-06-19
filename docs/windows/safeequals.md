---
title: SafeEquals | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeEquals
dev_langs:
- C++
helpviewer_keywords:
- SafeEquals function
ms.assetid: 6019627d-f170-413b-9abd-2b5b34396a72
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cfde61e9bcc32e3924e923dd55c8e6ca51cda0eb
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33889319"
---
# <a name="safeequals"></a>SafeEquals
Porovná dvě čísla k určení, zda jsou stejné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
template<typename T, typename U>  
inline bool SafeEquals (  
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
 `true` Pokud `t` a `u` jsou stejné jinak `false`.  
  
## <a name="remarks"></a>Poznámky  
 Metoda rozšiřuje `==` protože `SafeEquals` umožňuje porovnat dva různé typy čísel.  
  
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
 [SafeNotEquals](../windows/safenotequals.md)