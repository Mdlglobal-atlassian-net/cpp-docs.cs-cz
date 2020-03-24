---
title: Upozornění kompilátoru (úroveň 4) C4212
ms.date: 11/04/2016
f1_keywords:
- C4212
helpviewer_keywords:
- C4212
ms.assetid: df781ea1-182d-4f9f-9a31-55b6ce80c711
ms.openlocfilehash: d33e5c60bac657060ffef2a43686a5f737eb11cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161305"
---
# <a name="compiler-warning-level-4-c4212"></a>Upozornění kompilátoru (úroveň 4) C4212

používá se nestandardní rozšíření: deklarace funkce použila tři tečky.

Prototyp funkce má proměnný počet argumentů. Definice funkce ne.

Následující ukázka generuje C4212:

```c
// C4212.c
// compile with: /W4 /Ze /c
void f(int , ...);
void f(int i, int j) {}
```
