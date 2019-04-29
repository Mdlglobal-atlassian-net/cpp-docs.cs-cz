---
title: Kompilátor upozornění (úroveň 2) C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: 7d9a4ed09f026267e2c0f37fbbe4550ecd668dfc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350462"
---
# <a name="compiler-warning-level-2-c4156"></a>Kompilátor upozornění (úroveň 2) C4156

odstranění výrazu pole bez použití pole v podobě 'odstranit'; pole v podobě nahrazena

Bez pole v podobě **odstranit** nelze odstranit pole. Kompilátor přeložil **odstranit** pole formuláře.

Toto upozornění se zobrazí pouze v rámci rozšíření společnosti Microsoft (/Ze).

## <a name="example"></a>Příklad

```
// C4156.cpp
// compile with: /W2
int main()
{
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];
   delete array; // C4156, changed by compiler to "delete [] array;"
}
```