---
title: HStringReference::Operator&lt; operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
dev_langs:
- C++
ms.assetid: 55aa48e8-7c96-4123-9ebe-42b4cd8b9377
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b486157fb42883af724f2356e7f85701e405035
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33877290"
---
# <a name="hstringreferenceoperatorlt-operator"></a>HStringReference::Operator&lt; – operátor
Určuje, zda je první parametr menší než druhý parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline bool operator<(  
    const HStringReference& lhs,   
    const HStringReference& rhs) throw()  
```  
  
#### <a name="parameters"></a>Parametry  
 `lhs`  
 První parametr k porovnání. `lhs` může být odkaz na HStringReference.  
  
 `rhs`  
 Druhý parametr k porovnání.  `rhs` může být odkaz na HStringReference.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `lhs` parametr je menší než `rhs` parametr, jinak hodnota `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HStringReference – třída](../windows/hstringreference-class.md)