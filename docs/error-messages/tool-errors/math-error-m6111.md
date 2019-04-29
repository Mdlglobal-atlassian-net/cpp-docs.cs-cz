---
title: Chyba matematické operace M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 44f406881d64d13e23ca2c0911ee278c864a2c11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393405"
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