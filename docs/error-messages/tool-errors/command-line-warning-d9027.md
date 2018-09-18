---
title: Upozornění příkazového řádku D9027 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- D9027
dev_langs:
- C++
helpviewer_keywords:
- D9027
ms.assetid: 2a29edc5-5649-48f2-9058-2057c747284c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 105ebbf62027ac3d9377c513c4f7c59e261b983d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112522"
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