---
title: Compiler Error C2447
ms.date: 11/04/2016
f1_keywords:
- C2447
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
ms.openlocfilehash: 64dca8313af8b640b7b03c1ab27a1a31fa90de09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301965"
---
# <a name="compiler-error-c2447"></a>Compiler Error C2447

{: chybějící hlavička funkce (formální seznam ve starém stylu)

Kompilátor narazil v globálním oboru na neočekávanou otevřenou složenou závorku. Ve většině případů je příčinou chybný formát hlavičky funkce, nesprávně umístěná deklarace nebo zapomenutý středník. Chcete-li tento problém vyřešit, ověřte, zda za otevřenou složenou závorkou následuje hlavička funkce se správným formátem, a zda před ní není deklarace nebo zapomenutý středník.

Tato chyba může být také způsobena seznamem formálních argumentů jazyka C ve starém stylu. Chcete-li tento problém vyřešit, přepište seznam argumentů tak, aby používal moderní styl, tedy byl uzavřený do závorek.

Následující ukázka generuje C2447:

```
// C2447.cpp
int c;
{}       // C2447
```