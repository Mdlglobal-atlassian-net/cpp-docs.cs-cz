---
title: Upozornění kompilátoru (úroveň 1) C4662
ms.date: 11/04/2016
f1_keywords:
- C4662
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
ms.openlocfilehash: ff8a2f73523802a7c62e999be00c77400fbc0f23
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051429"
---
# <a name="compiler-warning-level-1-c4662"></a>Upozornění kompilátoru (úroveň 1) C4662

explicitní vytváření instancí; Šablona třídy ' identifier1 ' nemá žádnou definici, ze které by bylo možné specializovat ' identifier2 '

Zadaná třída Template-Class byla deklarována, ale není definována.

## <a name="example"></a>Příklad

```cpp
// C4662.cpp
// compile with: /W1 /LD
template<class T, int i> class MyClass; // no definition
template MyClass< int, 1>;              // C4662
```