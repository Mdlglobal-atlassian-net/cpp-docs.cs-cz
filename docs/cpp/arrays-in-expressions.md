---
title: Pole ve výrazech | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 34f8a45dfa9de9a5a48e13cb6a38f667e5963f2d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068543"
---
# <a name="arrays-in-expressions"></a>Pole ve výrazech

Když identifikátor typu pole objeví ve výrazu jiné než `sizeof`, adresy (**&**), nebo inicializace odkazu, je převeden na ukazatel na první prvek pole. Příklad:

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

Ukazatel `psz` odkazuje na první prvek pole `szError1`. Všimněte si, že pole, narozdíl od ukazatelů, nejsou upravitelné l-hodnoty. Proto je následující přiřazení neplatné:

```cpp
szError1 = psz;
```

## <a name="see-also"></a>Viz také:

[Pole](../cpp/arrays-cpp.md)