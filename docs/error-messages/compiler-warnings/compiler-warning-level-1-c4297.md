---
title: Kompilátoru (úroveň 1) upozornění C4297 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4297
dev_langs:
- C++
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2c37f82b646902d08c8fc2ce633948969d0755f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33281973"
---
# <a name="compiler-warning-level-1-c4297"></a>C4297 kompilátoru upozornění (úroveň 1)
'function': funkce předpokládá, že není však výjimku  
  
 (Pravděpodobně implicitní) obsahuje deklaraci funkce `noexcept` specifikátor, prázdnou `throw` specifikátor výjimky nebo [__declspec(nothrow)](../../cpp/nothrow-cpp.md) atribut a definice obsahuje jeden nebo více [throw ](../../cpp/try-throw-and-catch-statements-cpp.md) příkazy. Chcete-li vyřešit C4297, nepokoušejte se generování výjimek ve funkcích, které jsou deklarovány `__declspec(nothrow)`, `noexcept(true)` nebo `throw()`. Případně odebrat `noexcept`, `throw()`, nebo `__declspec(nothrow)` specifikace.  
  
 Ve výchozím nastavení, kompilátor vygeneruje implicitní `noexcept(true)` specifikátory pro uživatelem definované destruktory a deallocator funkce generované kompilátorem speciální členské funkce. To je v souladu s bitovou kopií ISO C ++ 11 standardní. Chcete-li zabránit generování specifikátory implicitních noexcept a obnovit kompilátoru nestandardní chování Visual Studio 2013, použijte **/Zc:implicitNoexcept-** – možnost kompilátoru. Další informace najdete v tématu [/Zc: implicitnoexcept (specifikátory implicitních výjimek)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).  
  
 Další informace o specifikace výjimek najdete v tématu [specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md). Další informace naleznete v [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md) informace o tom, jak změnit chování při kompilaci zpracování výjimek.  
  
 Toto upozornění je také vygenerované __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) funkce označeny extern "C", i když jsou funkcí jazyka C++.  
  
 Následující ukázka generuje C4297:  
  
```  
// C4297.cpp  
// compile with: /W1 /LD  
void __declspec(nothrow) f1()   // declared nothrow  
// try the following line instead  
// void f1()  
{  
   throw 1;   // C4297  
}  
```