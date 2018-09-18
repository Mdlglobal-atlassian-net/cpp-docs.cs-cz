---
title: Chyba matematické operace M6111 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95a55ec6b7cdf0b6e4c15bd283dde77c610698fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074822"
---
# <a name="math-error-m6111"></a>Chyba matematické operace M6111

podtečení zásobníku

Operaci s plovoucí desetinnou čárkou výsledkem podtečení zásobníku na koprocesoru 287 8087. 387 nebo emulátoru.

Tato chyba je často způsobeno volání `long double` funkce, která nevrací hodnotu. Například následující vygeneruje tuto chybu, pokud kompilované a spusťte:

```
long double ld() {};
main ()
{
  ld();
}
```

Program se ukončí s ukončovacím kódem 139.