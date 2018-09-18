---
title: Chyba kompilátoru C2466 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2466
dev_langs:
- C++
helpviewer_keywords:
- C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d43ee9d09fba77db022177a06c6ebe95c65ff79
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037837"
---
# <a name="compiler-error-c2466"></a>Chyba kompilátoru C2466

nejde přidělit pole s konstantní velikostí 0

Pole je přidělena nebo deklarované s nulovou velikostí. Konstantní výraz pro velikost pole musí být celé číslo větší než nula. Deklarace pole s nulovou dolní index je platný pouze pro třídy, struktury nebo člen sjednocení a pouze s rozšířeními společnosti Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

Následující ukázka generuje C2466:

```
// C2466.cpp
// compile with: /c
int i[0];   // C2466
int j[1];   // OK
char *p;
```