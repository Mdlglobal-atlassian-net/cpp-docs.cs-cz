---
title: Chyba kompilátoru C2813
ms.date: 11/04/2016
helpviewer_keywords:
- C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
ms.openlocfilehash: b36e966d897b1a3f9a4f601ef281091160da34c3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750933"
---
# <a name="compiler-error-c2813"></a>Chyba kompilátoru C2813

Import \#není v/MP podporován.

C2813 je vygenerována, pokud v příkazu kompilátoru zadáte možnost kompilátoru **/MP** a dva nebo více souborů, které mají být zkompilovány, a jeden nebo více souborů obsahuje direktivu preprocesoru[#import](../../preprocessor/hash-import-directive-cpp.md) . Direktiva [#import](../../preprocessor/hash-import-directive-cpp.md) generuje C++ třídy z typů v zadané knihovně typů a pak je zapisuje do dvou hlavičkových souborů. Direktiva [#import](../../preprocessor/hash-import-directive-cpp.md) není podporována, protože pokud více jednotek kompilace importuje stejnou knihovnu typů, jsou tyto jednotky při pokusu o zápis stejných hlavičkových souborů ve stejnou dobu v konfliktu.

Tato chyba kompilátoru a možnost kompilátoru **/MP** jsou v aplikaci Visual Studio 2008 novinkou.

## <a name="example"></a>Příklad

Následující ukázka generuje C2813. Příkazový řádek v komentáři "kompilovat s:" označuje kompilátor pro použití možností kompilátoru **/MP** a **/c** k zkompilování několika souborů. Nejméně jeden ze souborů obsahuje direktivu [#import](../../preprocessor/hash-import-directive-cpp.md) . Pro účely testování tohoto příkladu používáme stejný soubor dvakrát.

```cpp
// C2813.cpp
// compile with: /MP /c C2813.cpp C2813.cpp
#import "C:\windows\system32\stdole2.tlb"   // C2813
int main()
{
}
```
