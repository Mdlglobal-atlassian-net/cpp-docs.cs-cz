---
title: Upozornění (úroveň 1) C4662 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4662
dev_langs:
- C++
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b1f1744e0bcefd8b17c39677d7f8266403d8f8ff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109358"
---
# <a name="compiler-warning-level-1-c4662"></a>Kompilátor upozornění (úroveň 1) C4662

explicitní vytváření instancí; Třída šablony 'identifier1' nemá žádnou definici, ze kterého chcete specializovat "identifier2.

Zadanou třídu šablony byla deklarována, ale není definovaný.

## <a name="example"></a>Příklad

```
// C4662.cpp
// compile with: /W1 /LD
template<class T, int i> class MyClass; // no definition
template MyClass< int, 1>;              // C4662
```