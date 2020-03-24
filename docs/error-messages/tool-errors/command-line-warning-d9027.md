---
title: Upozornění příkazového řádku D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: 46ed5750bd1f315f20658ace9b83fac532fbbabb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196674"
---
# <a name="command-line-warning-d9027"></a>Upozornění příkazového řádku D9027

zdrojový soubor\<filename > se ignoroval.

CL. exe ignoroval vstupní zdrojový soubor.

Toto upozornění může být způsobeno mezerou mezi parametrem/FO a názvem výstupního souboru na příkazovém řádku s možností/c. Příklad:

```
cl /c /Fo output.obj input.c
```

Vzhledem k tomu, že existuje mezera mezi/FO a `output.obj`, soubor CL. exe jako název vstupního souboru používá `output.obj`. Chcete-li tento problém vyřešit, odeberte místo:

```
cl /c /Fooutput.obj input.c
```
