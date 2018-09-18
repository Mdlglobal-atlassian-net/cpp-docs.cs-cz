---
title: Chyba kompilátoru C2447 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2447
dev_langs:
- C++
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9cc18c8e6ffb31de062957e16f6f3a6573379ee
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035133"
---
# <a name="compiler-error-c2447"></a>Chyba kompilátoru C2447

{: chybějící hlavička funkce (formální seznam ve starém stylu)

Kompilátor narazil v globálním oboru na neočekávanou otevřenou složenou závorku. Ve většině případů je příčinou chybný formát hlavičky funkce, nesprávně umístěná deklarace nebo zapomenutý středník. Chcete-li tento problém vyřešit, ověřte, zda za otevřenou složenou závorkou následuje hlavička funkce se správným formátem, a zda před ní není deklarace nebo zapomenutý středník.

Tato chyba může být také způsobena seznamem formálních argumentů jazyka C ve starém stylu. Chcete-li tento problém vyřešit, přepište seznam argumentů tak, aby používal moderní styl, tedy byl uzavřený do závorek.

Následující ukázka generuje C2447:

```
// C2447.cpp
int c;
{}       // C2447
```