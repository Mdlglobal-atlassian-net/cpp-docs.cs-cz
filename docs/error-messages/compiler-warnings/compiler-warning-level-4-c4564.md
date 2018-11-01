---
title: Kompilátor upozornění (úroveň 4) C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: 1948bdec5367fa7943f5a0de4338fd4ecd6c6581
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50526227"
---
# <a name="compiler-warning-level-4-c4564"></a>Kompilátor upozornění (úroveň 4) C4564

Metoda "method" třídy 'class' Definuje nepodporovaný výchozí parametr "parametr"

Kompilátor zjistil metodu s jeden nebo více parametrů s výchozími hodnotami. Výchozí hodnoty pro parametry budou ignorovány, když uživatel vyvolá metodu; explicitní zadání hodnot těchto parametrů. Pokud hodnoty těchto parametrů není explicitně zadán, kompilátor vygeneruje chybu.

Daný následující knihovny DLL vytvořené pomocí jazyka Visual Basic, který umožňuje výchozích parametrů na argumenty metody:

```
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

A následující ukázka C++ používající DLL vytvořené pomocí jazyka Visual Basic

```
// C4564.cpp
// compile with: /clr /W4 /WX
#using <C4564.dll>

int main() {
   TestClass ^ myx = gcnew TestClass();   // C4564
   myx->MyMethod(9);
   // try the following line instead, to avoid an error
   // myx->MyMethod(9, 1);
}
```