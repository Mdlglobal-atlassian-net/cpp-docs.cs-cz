---
title: Chyba kompilátoru C2813 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
dev_langs:
- C++
helpviewer_keywords:
- C2813
ms.assetid: 6cf2135f-7b82-42d1-909a-5e864308a09c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8b7912edeea9edbb32632953166fc2558aeed3e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062654"
---
# <a name="compiler-error-c2813"></a>Chyba kompilátoru C2813

\#Import není podporován s možností/MP

C2813 je vygenerován v příkazu kompilátoru při zadání **/MP** – možnost kompilátoru a dva nebo více souborů do kompilace a jeden nebo více souborů obsahuje[#import](../../preprocessor/hash-import-directive-cpp.md) direktiva preprocesoru. [#Import](../../preprocessor/hash-import-directive-cpp.md) – direktiva generuje třídy C++ typy v zadané knihovny typů a pak zapíše dva soubory hlaviček těchto tříd. [#Import](../../preprocessor/hash-import-directive-cpp.md) – direktiva se nepodporuje, protože pokud několika kompilačních jednotek importovat stejnou knihovnu typů, tyto jednotky dojít ke konfliktu při pokusu o zápis stejné soubory hlaviček ve stejnou dobu.

Tuto chybu kompilátoru a **/MP** – možnost kompilátoru jsou nové v sadě Visual Studio 2008.

## <a name="example"></a>Příklad

Následující ukázka generuje C2813. Na příkazovém řádku ve "kompilovat s:" komentář oznamuje kompilátoru, aby použil **/MP** a **/c** – možnosti kompilátoru pro kompilaci několika souborů. Obsahuje nejméně jeden ze souborů [#import](../../preprocessor/hash-import-directive-cpp.md) směrnice. Stejného souboru dvakrát pro účely testování v tomto příkladu používáme.

```
// C2813.cpp
// compile with: /MP /c C2813.cpp C2813.cpp
#import "C:\windows\system32\stdole2.tlb"   // C2813
int main()
{
}
```