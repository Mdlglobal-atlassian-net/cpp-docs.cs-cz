---
title: Chyba kompilátoru C2383 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2383
dev_langs:
- C++
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9c529c22636f112291fa53b852899cad78dac589
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46113224"
---
# <a name="compiler-error-c2383"></a>Chyba kompilátoru C2383

"*symbol*': výchozí argumenty nejsou povolené pro tento symbol

Kompilátor C++ nepovoluje výchozí argumenty na ukazatele na funkce.

Tento kód byl přijat kompilátorem jazyka Visual C++ ve verzích před Visual Studio 2005, ale nyní vrátí chybu. Pro kód, který funguje ve všech verzích aplikace Visual C++ nepřiřazujte výchozí hodnota pro argument typu ukazatel na funkci.

## <a name="example"></a>Příklad

Následující příklad generuje C2383 a zobrazuje možná řešení:

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```