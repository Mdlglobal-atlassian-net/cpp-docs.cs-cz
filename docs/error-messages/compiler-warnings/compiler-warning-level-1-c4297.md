---
title: Upozornění kompilátoru (úroveň 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: 48ae909b9484fd0581f4691059272c5a488ea5fe
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626623"
---
# <a name="compiler-warning-level-1-c4297"></a>Upozornění kompilátoru (úroveň 1) C4297

' function ': funkce předpokládá, že nevyvolá výjimku, ale má

Deklarace funkce obsahuje specifikátor (případně implicitní) `noexcept`, prázdný Specifikátor výjimky `throw` nebo atribut [__declspec (throw)](../../cpp/nothrow-cpp.md) a definice obsahuje jeden nebo více příkazů [throw](../../cpp/try-throw-and-catch-statements-cpp.md) . Chcete-li vyřešit C4297, nepokoušejte se vyvolávat výjimky ve funkcích, které jsou deklarovány `__declspec(nothrow)`, `noexcept(true)` nebo `throw()`. Případně Odeberte specifikaci `noexcept`, `throw()`nebo `__declspec(nothrow)`.

Ve výchozím nastavení kompilátor generuje implicitní specifikátory `noexcept(true)` pro uživatelsky definované destruktory a funkce dealokace a speciální členské funkce generované kompilátorem. To odpovídá standardu ISO C++ 11. Chcete-li zabránit generování implicitních specifikátorů s výjimkou a vrátit kompilátor zpět na nestandardní chování Visual Studio 2013, použijte možnost **/Zc: implicitNoexcept-** Compiler. Další informace naleznete v tématu [/Zc: implicitNoexcept (implicitní specifikátory výjimek)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Další informace o specifikacích výjimek naleznete v tématu [Specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md). Další informace o tom, jak upravit chování zpracování výjimek v době kompilace, naleznete také v tématu [/EH (model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md) .

Toto upozornění je také generováno pro funkce __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) označené jako extern "C", i když C++ jsou funkce.

Následující ukázka generuje C4297:

```cpp
// C4297.cpp
// compile with: /W1 /LD
void __declspec(nothrow) f1()   // declared nothrow
// try the following line instead
// void f1()
{
   throw 1;   // C4297
}
```