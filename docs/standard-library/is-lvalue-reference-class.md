---
title: "is_lvalue_reference – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_lvalue_reference
dev_langs: C++
helpviewer_keywords:
- is_lvalue_reference class
- is_lvalue_reference
ms.assetid: 7f11896b-935c-4de1-9c87-9d0127f904e2
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e095638f11ebf34181928d3708de62f8d0cf0289
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
 [< type_traits >](../standard-library/type-traits.md)   
 [Hodnoty lvalue a rvalue](../cpp/lvalues-and-rvalues-visual-cpp.md)



