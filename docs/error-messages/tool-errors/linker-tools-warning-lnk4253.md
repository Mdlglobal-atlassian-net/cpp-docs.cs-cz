---
title: Upozornění linkerů LNK4253
ms.date: 11/04/2016
f1_keywords:
- LNK4253
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
ms.openlocfilehash: d2fd7238a3f57b11b91813bd40b66cb3e9f47202
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352516"
---
# <a name="linker-tools-warning-lnk4253"></a>Upozornění linkerů LNK4253

část sekci ' 1' nebyly sloučeny sekci '2'; už se sloučil do "section3.

Linker zjištěn více, požádá o konfliktu sloučení. Propojovací program bude ignorovat jedné žádosti.

A **/MERGE** došlo k možnosti nebo direktivě a `from` části již byly sloučeny do jiného oddílu než z důvodu předchozí **/MERGE** možnosti nebo direktivě (nebo kvůli implicitní sloučení z linker).

Vyřešit LNK4253, odeberte jeden z požadavků na sloučení.

Při cílení na x86 počítače a cíle Windows CE (ARM, MIPS, architekturu SH4 a Thumb) v jazyce Visual C++. Část CRT je nyní jen pro čtení. Pokud váš kód závisí na předchozím chování (. Oddíly CRT jsou r/w), může docházet k neočekávanému chování.

Další informace najdete v tématu,

- [/MERGE (sloučení oddílů)](../../build/reference/merge-combine-sections.md)

- [comment (C/C++)](../../preprocessor/comment-c-cpp.md)

## <a name="example"></a>Příklad

V následujícím příkladu je linkeru pokyn ke sloučení `.rdata` části dvakrát, ale do různých oddílů. Následující ukázka generuje LNK4253.

```
// LNK4253.cpp
// compile with: /W1 /link /merge:.rdata=text2
// LNK4253 expected
#pragma comment(linker, "/merge:.rdata=.text")
int main() {}
```