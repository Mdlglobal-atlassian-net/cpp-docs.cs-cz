---
title: Kompilátor upozornění (úroveň 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: 07dd6c65498ddd0d377ec3e0fbc7b44e52bec96b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408625"
---
# <a name="compiler-warning-level-1-c4297"></a>Kompilátor upozornění (úroveň 1) C4297

'function': funkce předpokládá, že nechcete vytvořit výjimku, ale neobsahuje

Obsahuje deklarace funkce (možná implicitně) `noexcept` specifikátor, prázdná `throw` specifikátor výjimky nebo [__declspec(nothrow)](../../cpp/nothrow-cpp.md) atribut a definice obsahuje jeden nebo více [throw ](../../cpp/try-throw-and-catch-statements-cpp.md) příkazy. Chcete-li vyřešit C4297, nepokoušejte se vyvolat výjimky ve funkcích, které jsou deklarovány `__declspec(nothrow)`, `noexcept(true)` nebo `throw()`. Odebrat také, `noexcept`, `throw()`, nebo `__declspec(nothrow)` specifikace.

Ve výchozím nastavení, kompilátor vygeneruje implicitní `noexcept(true)` specifikátory pro destruktory a funkce dealokátor a kompilátorem generované zvláštní členské funkce. To odpovídá ISO standardu C ++ 11. Chcete-li zabránit generace operaci implicit noexcept specifikátorů a obnovit kompilátor nestandardní chování sady Visual Studio 2013, použijte **/Zc:implicitNoexcept-** – možnost kompilátoru. Další informace najdete v tématu [/Zc: implicitnoexcept (specifikátory implicitních výjimek)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Další informace o specifikacích výjimek naleznete v tématu [specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md). Viz také [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md) informace o tom, jak změnit chování v době kompilace zpracování výjimek.

Toto upozornění je také generovány pro __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) funkce označené extern "C", i když jsou C++ funkce.

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