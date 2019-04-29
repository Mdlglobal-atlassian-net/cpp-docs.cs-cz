---
title: Kompilátor upozornění (úroveň 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 31711d3709b7c2ae3658d760f538ea9e841d33a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401121"
---
# <a name="compiler-warning-level-4-c4214"></a>Kompilátor upozornění (úroveň 4) C4214

používá se nestandardní rozšíření: jiné typy bitových polí než int.

Pomocí rozšíření výchozí společnosti Microsoft (/Ze) může být členy struktury bitového pole typu integer.

## <a name="example"></a>Příklad

```
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

Tato bitová pole nejsou platné v rámci kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).