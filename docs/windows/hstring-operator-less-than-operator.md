---
title: HString::Operator&lt; operátor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
dev_langs:
- C++
ms.assetid: 48a051cb-4609-42be-b48c-d35fc99d1eab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8fae7195f048cd680be513bd54b635e2e1e9bbf7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="hstringoperatorlt-operator"></a>HString::Operator&lt; – operátor
Určuje, zda je první parametr menší než druhý parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
inline bool operator<(  
    const HString& lhs,   
    const HString& rhs) throw()  
  
```  
  
#### <a name="parameters"></a>Parametry  
 `lhs`  
 První parametr k porovnání. `lhs` může být odkaz na HString.  
  
 `rhs`  
 Druhý parametr k porovnání. `rhs` může být odkaz na HString.  
  
## <a name="return-value"></a>Návratová hodnota  
 `true` Pokud `lhs` parametr je menší než `rhs` parametr, jinak hodnota `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [HString – třída](../windows/hstring-class.md)