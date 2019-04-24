---
title: Chyba kompilátoru C2286
ms.date: 11/04/2016
f1_keywords:
- C2286
helpviewer_keywords:
- C2286
ms.assetid: 078e0201-35cc-42e2-8dbc-6f8cf557b098
ms.openlocfilehash: 7d3b8297c5f5da29b99abe78999396e8c44df0fd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182766"
---
# <a name="compiler-error-c2286"></a>Chyba kompilátoru C2286

ukazatelé na členy reprezentace 'identifier' je již nastaven na dědičnost – deklarace se ignoruje.

Existují dva odlišné reprezentace ukazatele na členy pro třídu.

Další informace najdete v tématu [klíčová slova dědičnosti](../../cpp/inheritance-keywords.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C2286:

```
// C2286.cpp
// compile with: /c
class __single_inheritance X;
class __multiple_inheritance X;   // C2286
class  __multiple_inheritance Y;   // OK
```