---
title: Chyba kompilátoru C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: 2aa922ebeadb374a7eac73a0f452376472b00984
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206025"
---
# <a name="compiler-error-c2383"></a>Chyba kompilátoru C2383

'*symbol*': výchozí argumenty nejsou pro tento symbol povoleny

C++ Kompilátor nepovoluje výchozí argumenty na ukazatelích na funkce.

Tento kód byl přijat kompilátorem společnosti C++ Microsoft ve verzích před aplikací Visual Studio 2005, ale nyní obsahuje chybu. Pro kód, který funguje ve všech verzích jazyka C++Visual, nepřiřazujte výchozí hodnotu argumentu ukazatele na funkci.

## <a name="example"></a>Příklad

Následující příklad generuje C2383 a ukazuje možné řešení:

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```
