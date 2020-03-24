---
title: Upozornění kompilátoru (úroveň 4) C4202
ms.date: 11/04/2016
f1_keywords:
- C4202
helpviewer_keywords:
- C4202
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
ms.openlocfilehash: 8a449ee7650196d34d30df646ebdc333c1333af2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161423"
---
# <a name="compiler-warning-level-4-c4202"></a>Upozornění kompilátoru (úroveň 4) C4202

používá se nestandardní rozšíření: '... ': parametr Prototype v seznamu názvů je neplatný.

Definice funkce starého stylu obsahuje argumenty proměnných. Tyto definice vygenerují chybu v rámci kompatibility ANSI ([/za](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="example"></a>Příklad

```c
// C4202.c
// compile with: /W4
void func( a, b, ...)   // C4202
int a, b;
{}

int main()
{
}
```
