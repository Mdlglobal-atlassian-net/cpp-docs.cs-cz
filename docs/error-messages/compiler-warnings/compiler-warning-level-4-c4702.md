---
title: Kompilátor upozornění (úroveň 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 96ae3a0742db5e3a5006f031ce62beb281c38ccd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395245"
---
# <a name="compiler-warning-level-4-c4702"></a>Kompilátor upozornění (úroveň 4) C4702

Nedosažitelný kód

Toto upozornění je výsledkem kompilátoru prací, které bylo provedeno pro Visual Studio .NET 2003: nedosažitelný kód. Když kompilátor (back-end) zjistí nedosažitelný kód, C4702, vygeneruje upozornění úrovně 4.

Pro kód, který je platný v Visual Studio .NET 2003 i Visual Studio .NET verzí jazyka Visual C++ odebrání nedosažitelného kódu nebo zajistit, že je dostupná pro některé toku provádění s veškerým zdrojovým kódem.

## <a name="example"></a>Příklad

Následující ukázka generuje C4702.

```
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

## <a name="example"></a>Příklad

Při kompilaci s **/GX**, **parametr/EHC**, **/EHsc**, nebo **/EHac** a pomocí funkce extern C, kód se může stát nedostupný protože extern C Funkce předpokládá, že není throw, proto není dosažitelný bloku catch.  Pokud se domníváte, že toto upozornění není platný, protože může vyvolat funkci, proveďte kompilaci s **/EHa** nebo **/EHS**podle toho, že došlo k výjimce.

Další informace najdete v tématu [/EH (Model zpracování výjimek)](../../build/reference/eh-exception-handling-model.md) Další informace.

Následující ukázka generuje C4702.

```
// C4702b.cpp
// compile with: /W4 /EHsc
#include <iostream>

using namespace std;
extern "C" __declspec(dllexport) void Function2(){}

int main() {
   try {
      Function2();
   }
   catch (...) {
      cout << "Exp: Function2!" << endl;   // C4702
   }
}
```