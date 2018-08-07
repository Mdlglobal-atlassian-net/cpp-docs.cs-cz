---
title: HStringReference::Operator == – operátor | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
dev_langs:
- C++
ms.assetid: cad3d52d-cd67-4194-a270-5239b1121a09
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7620cee350ab69f55737e6336b275218a70b6891
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39607710"
---
# <a name="hstringreferenceoperator-operator"></a>HStringReference::Operator== – operátor
Určuje, zda se tyto dva parametry rovnají.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline bool operator==(  
               const HStringReference& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HSTRING& lhs,   
               const HStringReference& rhs) throw()  
  
inline bool operator==(  
               const HStringReference& lhs,   
               const HSTRING& rhs) throw()  
```  
  
### <a name="parameters"></a>Parametry  
 *lhs*  
 První parametr k porovnání. *LHS* může být **HStringReference** objektu nebo popisovače HSTRING.  
  
 *Zarovnání indirekce RHS*  
 Druhý parametr k porovnání.  *Zarovnání indirekce RHS* může být **HStringReference** objektu nebo popisovače HSTRING.  
  
## <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE** Pokud *lhs* a *zarovnání indirekce rhs* parametry jsou stejné, jinak **false**.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HStringReference – třída](../windows/hstringreference-class.md)