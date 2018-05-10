---
title: Variadická makra | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- variadic macros [C++]
- __VA_ARGS__ variadic macro specifier
ms.assetid: 51e757dc-0134-4bb2-bb74-64ea5ad75134
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5918c7d91a3568799f361fcb42edb2e9c7b1445e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="variadic-macros"></a>Variadická makra
Makra variadic jsou makra podobná funkcím, které obsahují proměnný počet argumentů.  
  
## <a name="remarks"></a>Poznámky  
 Variadická makra použít, je možné zadat se třemi tečkami jako konečný argument formální v definici makra a identifikátor nahrazení `__VA_ARGS__` lze v definici vložit další argumenty.  `__VA_ARGS__` je nahrazena všechny argumenty, které odpovídají se třemi tečkami, včetně čárkami mezi nimi.  
  
 Standard C určuje, že třem tečkám musí být předán alespoň jeden argument, aby se makro nepřekládalo na výraz s koncovou čárkou.  Implementace jazyka Visual C++ potlačí koncovou čárku, pokud nejsou třem tečkám předány žádné argumenty.  
  
## <a name="example"></a>Příklad  
  
```cpp  
// variadic_macros.cpp  
#include <stdio.h>  
#define EMPTY  
  
#define CHECK1(x, ...) if (!(x)) { printf(__VA_ARGS__); }  
#define CHECK2(x, ...) if ((x)) { printf(__VA_ARGS__); }  
#define CHECK3(...) { printf(__VA_ARGS__); }  
#define MACRO(s, ...) printf(s, __VA_ARGS__)  
  
int main() {  
    CHECK1(0, "here %s %s %s", "are", "some", "varargs1(1)\n");  
    CHECK1(1, "here %s %s %s", "are", "some", "varargs1(2)\n");   // won't print  
  
    CHECK2(0, "here %s %s %s", "are", "some", "varargs2(3)\n");   // won't print  
    CHECK2(1, "here %s %s %s", "are", "some", "varargs2(4)\n");  
  
    // always invokes printf in the macro  
    CHECK3("here %s %s %s", "are", "some", "varargs3(5)\n");  
  
    MACRO("hello, world\n");  
  
    MACRO("error\n", EMPTY); // would cause error C2059, except VC++   
                             // suppresses the trailing comma  
}  
```  
  
## <a name="output"></a>Výstup  
  
```  
here are some varargs1(1)  
here are some varargs2(4)  
here are some varargs3(5)  
hello, world  
error  
```  
  
## <a name="see-also"></a>Viz také  
 [Makra (C/C++)](../preprocessor/macros-c-cpp.md)