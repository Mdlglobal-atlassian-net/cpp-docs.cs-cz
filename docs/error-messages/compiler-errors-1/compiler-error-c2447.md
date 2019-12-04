---
title: Chyba kompilátoru C2447
ms.date: 11/04/2016
f1_keywords:
- C2447
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
ms.openlocfilehash: 14fec374927fc798956a249773d9bec814e7a823
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744183"
---
# <a name="compiler-error-c2447"></a>Chyba kompilátoru C2447

{: chybějící hlavička funkce (formální seznam ve starém stylu)

Kompilátor narazil v globálním oboru na neočekávanou otevřenou složenou závorku. Ve většině případů je příčinou chybný formát hlavičky funkce, nesprávně umístěná deklarace nebo zapomenutý středník. Chcete-li tento problém vyřešit, ověřte, zda za otevřenou složenou závorkou následuje hlavička funkce se správným formátem, a zda před ní není deklarace nebo zapomenutý středník.

Tato chyba může být také způsobena seznamem formálních argumentů jazyka C ve starém stylu. Chcete-li tento problém vyřešit, přepište seznam argumentů tak, aby používal moderní styl, tedy byl uzavřený do závorek.

Následující ukázka generuje C2447:

```cpp
// C2447.cpp
int c;
{}       // C2447
```
