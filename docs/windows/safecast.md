---
title: SafeCast | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeCast
dev_langs:
- C++
helpviewer_keywords:
- SafeCast function
ms.assetid: 55316729-8456-403a-9f96-59d4038f67af
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07311e916fa78f1ba946ad4631905968912f8195
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40019063"
---
# <a name="safecast"></a>SafeCast
Přetypování jednom typu čísla do jiného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
template<typename T, typename U>  
inline bool SafeCast (  
   const T From,  
   U& To  
);  
```  
  
### <a name="parameters"></a>Parametry  
 [in] *z*  
 Zdroj číslo k převedení. Musí se jednat o typ `T`.  
  
 [out] *Do*  
 Odkaz na nový typ number. Musí se jednat o typ `U`.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** Pokud nenastane žádná chyba; **false** Pokud dojde k chybě.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda je součástí [SafeInt – knihovna](../windows/safeint-library.md) a je určená pro přetypování jedné operace bez vytvoření instance [SafeInt – třída](../windows/safeint-class.md).  
  
> [!NOTE]
>  Tato metoda by měla sloužit pouze pokud jedné operace musí být chráněné. Pokud je více operací, měli byste použít `SafeInt` třídy místo volání jednotlivých samostatné funkce.  
  
 Další informace o typech šablony T a U najdete v tématu [SafeInt – funkce](../windows/safeint-functions.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** safeint.h  
  
 **Namespace:** Microsoft::Utilities  
  
## <a name="see-also"></a>Viz také  
 [SafeInt – funkce](../windows/safeint-functions.md)   
 [SafeInt – knihovna](../windows/safeint-library.md)   
 [SafeInt – třída](../windows/safeint-class.md)