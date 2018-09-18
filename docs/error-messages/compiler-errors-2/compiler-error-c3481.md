---
title: Chyba kompilátoru C3481 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3481
dev_langs:
- C++
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25634bb455a032ceff51d5e35f7a16e00e020326
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46066892"
---
# <a name="compiler-error-c3481"></a>Chyba kompilátoru C3481

'příkaz var': proměnná zachycení lambda nebyl nalezen

Kompilátor nemůže najít definice proměnné, kterou jste předali do seznamu zachycení výrazu lambda.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Proměnnou můžete odeberte ze seznamu zachycení výrazu lambda.

## <a name="example"></a>Příklad

Následující příklad generuje C3481 protože proměnné `n` není definován:

```
// C3481.cpp

int main()
{
   [n] {}(); // C3481
}
```

## <a name="see-also"></a>Viz také

[Výrazy lambda](../../cpp/lambda-expressions-in-cpp.md)