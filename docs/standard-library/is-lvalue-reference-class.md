---
title: "is_lvalue_reference – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_lvalue_reference
dev_langs:
- C++
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 26cbc7dc51fe6db51f47a8b60c6b209dfbc9a337
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="islvaluereference-class"></a>is_lvalue_reference – třída
Testy, pokud je typ odkazu lvalue.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class Ty>
struct is_lvalue_reference;
```  
  
#### <a name="parameters"></a>Parametry  
 `Ty`  
 Typ, na který chcete odeslat dotaz.  
  
## <a name="remarks"></a>Poznámky  
 Instance této predikátem typu obsahuje hodnotu true, pokud typ `Ty` je odkaz na objekt nebo funkci, jinak má hodnotu false. Všimněte si, že `Ty` nemusí být deklarátor odkazu. Další informace o rvalue najdete v tématu [Rvalue – deklarátor odkazu: & &](../cpp/rvalue-reference-declarator-amp-amp.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<type_traits >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [<type_traits>](../standard-library/type-traits.md)   
 [Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)



