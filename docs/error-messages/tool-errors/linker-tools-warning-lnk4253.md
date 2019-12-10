---
title: Upozornění linkerů LNK4253
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: c3f45880571e5c06f76d5f063ff993e2f6b2be9b
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988086"
---
# <a name="linker-tools-warning-lnk4253"></a>Upozornění linkerů LNK4253

oddíl ' Section1 ' není sloučen do ' section2 '; již sloučeno do ' section3 '

Linker zjistil více konfliktních žádostí o sloučení. Linker bude ignorovat jednu z požadavků.

Byla zjištěna možnost nebo direktiva **/Merge** a část `from` již byla sloučena do jiného oddílu z důvodu předchozí možnosti nebo direktivy **/Merge** (nebo z důvodu implicitního sloučení z linkeru).

Chcete-li vyřešit LINKERŮ LNK4253, odeberte jednu z požadavků na sloučení.

Při cílení na počítače x86 a systém Windows CE cíle (ARM, MIPS, SH4 a palec) pomocí C++vizuálu,. Oddíl CRT je nyní jen pro čtení. Pokud váš kód závisí na předchozím chování (. Oddíly CRT jsou pro čtení a zápis), můžete se podívat na neočekávané chování.

Další informace najdete v tématu.

- [/MERGE (sloučení oddílů)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Příklad

V následující ukázce má linker pokyn ke sloučení oddílu `.rdata` dvakrát, ale do různých oddílů. Následující ukázka generuje LINKERŮ LNK4253.

```cpp
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```
