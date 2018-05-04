---
title: hodnotu true (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- true_cpp
dev_langs:
- C++
helpviewer_keywords:
- true keyword [C++]
ms.assetid: 96be2a70-51c3-4250-9752-874d25a5a11e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 44df8d3e9429c272d83025b600fc8d43cc8f8b73
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="true-c"></a>true (C++)
## <a name="syntax"></a>Syntaxe  
  
```  
  
      bool-identifier = true ;  
bool-expression logical-operator true ;  
```  
  
## <a name="remarks"></a>Poznámky  
 Toto klíčové slovo je jedním ze dvou hodnot pro proměnnou typu [bool](../cpp/bool-cpp.md) nebo podmíněného výrazu (podmíněného výrazu je nyní true logický výraz). Pokud `i` je typu `bool`, pak příkaz `i = true;` přiřadí **true** k `i`.  
  
## <a name="example"></a>Příklad  
  
```  
// bool_true.cpp  
#include <stdio.h>  
int main()  
{  
    bool bb = true;  
    printf_s("%d\n", bb);  
    bb = false;  
    printf_s("%d\n", bb);  
}  
```  
  
```Output  
1  
0  
```  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../cpp/keywords-cpp.md)