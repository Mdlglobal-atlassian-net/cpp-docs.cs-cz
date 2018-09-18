---
title: Upozornění Linkerů LNK4253 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4253
dev_langs:
- C++
helpviewer_keywords:
- LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d26d688825f504cbce8224adc9a5766a555d2fc8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016816"
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