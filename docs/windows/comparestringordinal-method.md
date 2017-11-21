---
title: "Comparestringordinal – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Details::CompareStringOrdinal
dev_langs: C++
ms.assetid: ffa997fd-8cd7-40a5-b9e7-f55d40b072f4
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 17415efa6519d8e3538f869168db2040ed6e73dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="comparestringordinal-method"></a>CompareStringOrdinal – metoda
Podporuje infrastrukturu rozhraní knihovny WRL a není určena pro použití přímo z vašeho kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline INT32 CompareStringOrdinal(  
   HSTRING lhs,   
   HSTRING rhs)  
```  
  
#### <a name="parameters"></a>Parametry  
 `lhs`  
 První HSTRING k porovnání.  
  
 `rhs`  
 Druhý HSTRING k porovnání.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|Hodnota|Podmínka|  
|-----------|---------------|  
|-1|`lhs`je menší než `rhs`.|  
|0|`lhs`se rovná `rhs`.|  
|1|`lhs`je větší než `rhs`.|  
  
## <a name="remarks"></a>Poznámky  
 Porovná dva objekty zadaného HSTRING a vrátí celé číslo, které označuje jejich relativní pozici v pořadí řazení.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL::Wrappers::Details  
  
## <a name="see-also"></a>Viz také  
 [Namespace Microsoft::WRL::Wrappers::details](../windows/microsoft-wrl-wrappers-details-namespace.md)