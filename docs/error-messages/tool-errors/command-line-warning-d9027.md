---
title: Upozornění příkazového řádku D9027
ms.date: 11/04/2016
f1_keywords:
- D9027
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
ms.openlocfilehash: f89e7416efe7a0069ee2dae8df921933bbe76bcf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214113"
---
# <a name="command-line-warning-d9027"></a>Upozornění příkazového řádku D9027

zdrojový soubor '\<název souboru > se ignoruje

CL.exe ignoruje vstupní zdrojový soubor.

Toto upozornění může být způsobeno mezeru mezi možností /Fo a název výstupního souboru na příkazovém řádku s parametrem /c. Příklad:

```
cl /c /Fo output.obj input.c
```

Protože je mezera mezi /Fo a `output.obj`, trvá CL.exe `output.obj` jako název výstupního souboru. Chcete-li problém vyřešit, odeberte místo:

```
cl /c /Fooutput.obj input.c
```