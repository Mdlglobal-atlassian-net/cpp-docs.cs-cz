---
title: "is_bind_expression – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: functional/std::is_bind_expression
dev_langs: C++
helpviewer_keywords: is_bind_expression class
ms.assetid: 0715f9e9-2239-4778-a1cf-2c21f49dfd47
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4968a82385cf822a20ff761dd8f4e87998784084
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="isbindexpression-class"></a>is_bind_expression – třída
Testuje, pokud typ generovaná volání `bind`.  
  
## <a name="syntax"></a>Syntaxe  
  
šablony<class Ty>  
{is_bind_expression – struktura  
   statická hodnota const bool;  
   };  
  
## <a name="remarks"></a>Poznámky  
Konstantní členské `value` je hodnota true, pokud typ `Ty` je typ vrácený volání `bind`, jinak hodnota false.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// std__functional__is_bind_expression.cpp   
// compile with: /EHsc   
#include <functional>   
#include <iostream>   
  
void square(double x)
{
    std::cout << x << "^2 == " << x * x << std::endl;
}

template<class Expr>
void test_for_bind(const Expr&)
{
    std::cout << std::is_bind_expression<Expr>::value << std::endl;
}

int main()
{
    test_for_bind(3.0 * 3.0);
    test_for_bind(std::bind(square, 3));

    return (0);
}  
```  
  
```Output  
0  
1  
```  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<funkční >  
  
 **Namespace:** – std  
  
## <a name="see-also"></a>Viz také  
 [vazby](../standard-library/functional-functions.md#bind)

