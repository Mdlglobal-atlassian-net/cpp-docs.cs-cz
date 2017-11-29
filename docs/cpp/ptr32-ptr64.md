---
title: __ptr32 __ptr64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
dev_langs: C++
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f70de0e9e7bc9c698010e7378c705789d380ed6f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ptr32-ptr64"></a>__ptr32, __ptr64
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Klíčové slovo `__ptr32` představuje nativní ukazatel v 32bitovém systému, zatímco klíčové slovo `__ptr64` představuje nativní ukazatel v 64bitovém systému.  
  
 Následující příklad ukazuje, jak deklarovat jednotlivé typy ukazatelů:  
  
```  
int * __ptr32 p32;  
int * __ptr64 p64;  
```  
  
 V 32bitovém systému je ukazatel deklarovaný pomocí klíčového slova `__ptr64` zkrácen na 32bitový ukazatel. V 64bitovém systému je ukazatel deklarovaný pomocí klíčového slova `__ptr32` převeden na 64bitový ukazatel.  
  
> [!NOTE]
>  Nemůžete použít `__ptr32` nebo `__ptr64` při kompilaci s **/CLR: pure**. Jinak bude vygenerována chyba `Compiler Error C2472`. **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat a přidělit ukazatele pomocí klíčových slov `__ptr32` a `__ptr64`.  
  
```  
#include <cstdlib>  
#include <iostream>  
  
int main()  
{  
    using namespace std;  
  
    int * __ptr32 p32;  
    int * __ptr64 p64;  
  
    p32 = (int * __ptr32)malloc(4);  
    *p32 = 32;  
    cout << *p32 << endl;  
  
    p64 = (int * __ptr64)malloc(4);  
    *p64 = 64;  
    cout << *p64 << endl;  
}  
```  
  
```Output  
32  
64  
```  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Základní typy](../cpp/fundamental-types-cpp.md)