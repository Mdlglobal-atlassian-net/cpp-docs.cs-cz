---
title: Upozornění kompilátoru (úroveň 4) C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: e46642494e55769a0676f0e33af0ca40c31939ad
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541804"
---
# <a name="compiler-warning-level-4-c4205"></a>Upozornění kompilátoru (úroveň 4) C4205

používá se nestandardní rozšíření: deklarace statické funkce v oboru funkce.

S rozšířeními Microsoft (/ze) mohou být **statické** funkce deklarovány uvnitř jiné funkce. Funkce je předána globálnímu oboru.

## <a name="example"></a>Příklad

```c
// C4205.c
// compile with: /W4
void func1()
{
   static int func2();  // C4205
};

int main()
{
}
```

Taková inicializace nejsou v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)) platná.