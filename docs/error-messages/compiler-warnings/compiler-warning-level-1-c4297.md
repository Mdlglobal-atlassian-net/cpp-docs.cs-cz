---
title: Upozornění (úroveň 1) C4297 kompilátoru | Dokumentace Microsoftu
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
ms.openlocfilehash: f615df5933cfc93918b05758f042c8cf47aa92f1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099431"
---
# <a name="compiler-warning-level-1-c4297"></a>Kompilátor upozornění (úroveň 1) C4297

'function': funkce předpokládá, že nechcete vytvořit výjimku, ale neobsahuje

Obsahuje deklarace funkce (možná implicitně) `noexcept` specifikátor, prázdná `throw` specifikátor výjimky nebo [__declspec(nothrow)](../../cpp/nothrow-cpp.md) atribut a definice obsahuje jeden nebo více [throw ](../../cpp/try-throw-and-catch-statements-cpp.md) příkazy. Chcete-li vyřešit C4297, nepokoušejte se vyvolat výjimky ve funkcích, které jsou deklarovány `__declspec(nothrow)`, `noexcept(true)` nebo `throw()`. Odebrat také, `noexcept`, `throw()`, nebo `__declspec(nothrow)` specifikace.

Ve výchozím nastavení, kompilátor vygeneruje implicitní `noexcept(true)` specifikátory pro destruktory a funkce dealokátor a kompilátorem generované zvláštní členské funkce. To odpovídá ISO standardu C ++ 11. Chcete-li zabránit generace operaci implicit noexcept specifikátorů a obnovit kompilátor nestandardní chování sady Visual Studio 2013, použijte **/Zc:implicitNoexcept-** – možnost kompilátoru. Další informace najdete v tématu [/Zc: implicitnoexcept (specifikátory implicitních výjimek)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Další informace o specifikacích výjimek naleznete v tématu [specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md). Viz také [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md) informace o tom, jak změnit chování v době kompilace zpracování výjimek.

Toto upozornění je také generovány pro __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) funkce označené extern "C", i když jsou funkce jazyka C++.

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