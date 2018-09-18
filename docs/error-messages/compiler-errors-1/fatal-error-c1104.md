---
title: Závažná chyba C1104 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1104
dev_langs:
- C++
helpviewer_keywords:
- C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e624238a1b7616ab84a655839a05cfd6899d38ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048107"
---
# <a name="fatal-error-c1104"></a>Závažná chyba C1104

Závažná chyba při importu libid: "zpráva"

Kompilátor zjistil problém při importu knihovny typů.  Například nelze zadat knihovnu typů s libid a také určit `no_registry`.

Další informace najdete v tématu [#import Directive](../../preprocessor/hash-import-directive-cpp.md).

Následující ukázka vygeneruje C1104:

```
// C1104.cpp
#import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104
```