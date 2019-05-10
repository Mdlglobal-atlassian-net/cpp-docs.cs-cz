---
title: Chyba kompilátoru C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: e9c1774fe7cd4a6883aa79f384cc64521a57ed17
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448003"
---
# <a name="compiler-error-c2383"></a>Chyba kompilátoru C2383

"*symbol*': výchozí argumenty nejsou povolené pro tento symbol

Kompilátor C++ nepovoluje výchozí argumenty na ukazatele na funkce.

Tento kód byl přijat Microsoftu C++ kompilátoru ve verzích před Visual Studio 2005, ale nyní vrátí chybu. Pro kód, který funguje ve všech verzích aplikace Visual C++ nepřiřazujte výchozí hodnota pro argument typu ukazatel na funkci.

## <a name="example"></a>Příklad

Následující příklad generuje C2383 a zobrazuje možná řešení:

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```