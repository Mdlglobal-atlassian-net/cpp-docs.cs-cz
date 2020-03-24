---
title: Chyba matematické operace M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: e8abedf6a326a826d0c8ac513b15037c8bf89bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173688"
---
# <a name="math-error-m6111"></a>Chyba matematické operace M6111

podtečení zásobníku

Výsledkem operace s plovoucí desetinnou čárkou je podtečení zásobníku pro procesor 8087/287/387 nebo emulátor.

Tato chyba je často způsobena voláním funkce `long double`, která nevrací hodnotu. Následující příklad vygeneruje tuto chybu při kompilaci a spuštění:

```
long double ld() {};
main ()
{
  ld();
}
```

Program se ukončí s ukončovacím kódem 139.
