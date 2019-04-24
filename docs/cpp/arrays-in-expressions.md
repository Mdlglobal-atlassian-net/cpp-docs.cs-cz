---
title: Pole ve výrazech
ms.date: 11/04/2016
helpviewer_keywords:
- expressions [C++], arrays in
- arrays [C++], in expressions
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
ms.openlocfilehash: 0f2ef43c2a5bc4f8a44378c21d6d53b14f07ea07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184373"
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