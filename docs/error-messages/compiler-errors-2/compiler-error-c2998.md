---
title: Chyba kompilátoru C2998 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2998
dev_langs:
- C++
helpviewer_keywords:
- C2998
ms.assetid: 8193d491-b5d9-4477-acb1-cf166889c070
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 181db50f9b2598379d1b9d56720551f1b18cbf18
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118424"
---
# <a name="compiler-error-c2998"></a>Chyba kompilátoru C2998

'identifier': nemůže být definice šablony

Kompilátor nemůže zpracovat syntaxe používané v definici šablony.

Následující ukázka generuje C2998:

```
// C2998.cpp
// compile with: /c
template <class T> int x = 1018; // C2998
```