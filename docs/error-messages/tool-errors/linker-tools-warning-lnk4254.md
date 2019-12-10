---
title: Upozornění linkerů LNK4254
ms.date: 11/04/2016
f1_keywords:
- LNK4254
helpviewer_keywords:
- LNK4254
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
ms.openlocfilehash: 8431bd2d89fd5df5cf076ad006ab04006f552c4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988064"
---
# <a name="linker-tools-warning-lnk4254"></a>Upozornění linkerů LNK4254

oddíl ' Section1 ' (offset) se sloučil do ' section2 ' (posunu) s různými atributy

Obsah jednoho oddílu byl sloučen do jiného, ale atributy dvou sekcí se liší. Váš program může poskytnout neočekávané výsledky. Například data, která jste chtěli číst jen pro čtení, se teď můžou nacházet v části s možností zápisu.

Chcete-li vyřešit LINKERŮ LNK4254, upravte nebo odeberte požadavek sloučení.

Při cílení na počítače x86 a systém Windows CE cíle (ARM, MIPS, SH4 a palec) pomocí C++vizuálu,. Oddíl CRT je jen pro čtení. Pokud váš kód závisí na předchozím chování (. Oddíly CRT jsou pro čtení a zápis), můžete se podívat na neočekávané chování.

Další informace najdete v tématu.

- [/MERGE (sloučení oddílů)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Příklad

Následující ukázka generuje LINKERŮ LNK4254.

```cpp
// LNK4254.cpp
// compile with: /W1 /link /WX
// LNK4254 expected
#pragma comment(linker, "/merge:.data=.text")
int main() {}
```
