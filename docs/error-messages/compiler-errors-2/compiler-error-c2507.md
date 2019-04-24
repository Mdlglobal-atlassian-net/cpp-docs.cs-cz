---
title: Chyba kompilátoru C2507
ms.date: 11/04/2016
f1_keywords:
- C2507
helpviewer_keywords:
- C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
ms.openlocfilehash: 63f9594eb9ee8a251faafe7323418b343c03063c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165226"
---
# <a name="compiler-error-c2507"></a>Chyba kompilátoru C2507

'identifier': moc virtuálních modifikátorů základní třídy

Třídy nebo struktury je deklarován jako `virtual` více než jednou. Pouze jeden `virtual` modifikátor se může objevit pro každou třídu v seznamu základních tříd.

Následující ukázka generuje C2507:

```
// C2507.cpp
// compile with: /c
class A {};
class B : virtual virtual public A {};   // C2507
class C : virtual public A {};   // OK
```