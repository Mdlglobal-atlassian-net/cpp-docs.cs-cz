---
title: Kompilátor upozornění (úroveň 1) C4659
ms.date: 11/04/2016
f1_keywords:
- C4659
helpviewer_keywords:
- C4659
ms.assetid: e29ba8db-7917-43f6-8e34-868b752279ae
ms.openlocfilehash: 2aef25e922d8f38ac7103b1b12ccb31c282f0403
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374648"
---
# <a name="compiler-warning-level-1-c4659"></a>Kompilátor upozornění (úroveň 1) C4659

\#pragma – direktiva "pragma": používání vyhrazeného segmentu 'segmentu' má nedefinované chování, použijte #pragma comment (linker,...)

Možnost .drectve byla použita k předání možností do linkeru. Místo toho použít direktivu pragma [komentář](../../preprocessor/comment-c-cpp.md) pro předávání možností propojovacího programu.

```
// C4659.cpp
// compile with: /W1 /LD
#pragma code_seg(".drectve")   // C4659
```