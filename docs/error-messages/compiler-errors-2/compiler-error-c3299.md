---
title: Chyba kompilátoru C3299 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3299
dev_langs:
- C++
helpviewer_keywords:
- C3299
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ca5a57ca1cdfe442386872d738a01cf4235685c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117826"
---
# <a name="compiler-error-c3299"></a>Chyba kompilátoru C3299

'member_function': nelze zadat omezení, dědí se ze základní metody

Při přepisování obecné členskou funkci, nelze zadat klauzule omezení (s opakováním, omezení znamená, že nejsou děděna omezení).

Klauzule omezení u obecných funkce, které jsou přepsání se budou dědit.

Další informace najdete v tématu [omezení parametrů obecných typů (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md).

## <a name="example"></a>Příklad

Následující ukázka generuje C3299.

```
// C3299.cpp
// compile with: /clr /c
public ref struct R {
   generic<class T>
   where T : R
   virtual void f();
};

public ref struct S : R {
   generic<class T>
   where T : R   // C3299
   virtual void f() override;
};
```