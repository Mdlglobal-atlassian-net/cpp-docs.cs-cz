---
title: Chyba matematické operace M6201 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6201
dev_langs:
- C++
helpviewer_keywords:
- M6201
ms.assetid: 4041c331-d9aa-4dd4-b565-7dbe0218538c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87d2c09d6448bcf7fb0557fa3a174c60205a34ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099392"
---
# <a name="math-error-m6201"></a>Chyba matematické operace M6201

'function': Chyba _domény

Argument pro danou funkci bylo mimo doménu platné vstupní hodnoty pro tuto funkci.

## <a name="example"></a>Příklad

```
result = sqrt(-1.0)   // C statement
result = SQRT(-1.0)   !  FORTRAN statement
```

Tato chyba volání `_matherr` funkce s názvem funkce, argumentů a typ chyby. Je možné přepsat `_matherr` přizpůsobit zpracování některých chyb za běhu s plovoucí desetinnou čárkou matematické funkce.