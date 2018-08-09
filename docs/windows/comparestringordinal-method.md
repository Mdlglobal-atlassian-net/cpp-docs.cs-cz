---
title: Comparestringordinal – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
dev_langs:
- C++
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7084b16536533c9605b741adb596a2a7d383c153
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649995"
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal – metoda
Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline INT32 CompareStringOrdinal(  
   HSTRING lhs,   
   HSTRING rhs)  
```  
  
### <a name="parameters"></a>Parametry  
 *lhs*  
 První HSTRING k porovnání.  
  
 *Zarovnání indirekce RHS*  
 Druhý HSTRING k porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|Hodnota|Podmínka|  
|-----------|---------------|  
|-1|*LHS* je menší než *zarovnání indirekce rhs*.|  
|0|*LHS* rovná *zarovnání indirekce rhs*.|  
|1|*LHS* je větší než *zarovnání indirekce rhs*.|  
  
## <a name="remarks"></a>Poznámky  
 Porovná dva objekty zadané HSTRING a vrátí celé číslo určující jejich relativní umístění v pořadí řazení.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers::Details – obor názvů](../windows/microsoft-wrl-wrappers-details-namespace.md)