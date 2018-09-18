---
title: Chyba kompilátoru C2500 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2500
dev_langs:
- C++
helpviewer_keywords:
- C2500
ms.assetid: 6bff8161-dc9a-48ca-91f1-fd2eefdbbc93
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b7e24ca520796b63171fe63c2bf841fe8776845
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026670"
---
# <a name="compiler-error-c2500"></a>Chyba kompilátoru C2500

"identifier1": 'identifier2' je již přímé základní třídy.

Třída nebo struktura, zobrazí se více než jednou v seznamu základních tříd.

Přímou základní je uvedených v seznamu základních. Nepřímý základ je základní třídou jednoho v seznamu základních tříd.

Třídu nelze zadat více než jednou jako přímou základní třídu. Třída může sloužit jako nepřímou základní třídou více než jednou.

Následující ukázka generuje C2500:

```
// C2500.cpp
// compile with: /c
class A {};
class B : public A, public A {};    // C2500

// OK
class C : public A {};
class D : public A {};
class E : public C, public D {};
```