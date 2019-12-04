---
title: Závažná chyba C1103
ms.date: 11/04/2016
f1_keywords:
- C1103
helpviewer_keywords:
- C1103
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
ms.openlocfilehash: f037d1acb281b5997e3486a542784abc4b4b7542
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747381"
---
# <a name="fatal-error-c1103"></a>Závažná chyba C1103

Závažná chyba při importu ProgID: ' Message '

Kompilátor zjistil problém s importem knihovny typů.  Například nelze zadat knihovnu typů s identifikátorem ProgID a zároveň zadat `no_registry`.

Další informace najdete v tématu [direktiva #import](../../preprocessor/hash-import-directive-cpp.md).

V následujícím příkladu se vygeneruje C1103:

```cpp
// C1103.cpp
#import "progid:a.b.id.1.5" no_registry auto_search   // C1103
```
