---
title: Účinky ukládání do vyrovnávací paměti
ms.date: 11/04/2016
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
ms.openlocfilehash: e10b28edffdfe3411f86c031bfd12ea886410e20
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50631436"
---
# <a name="effects-of-buffering"></a>Účinky ukládání do vyrovnávací paměti

Následující příklad ukazuje účinky ukládání do vyrovnávací paměti. Očekáváte-li program k vytištění `please wait`, počkejte 5 sekund a pak pokračujte. Nebude to fungovat nutně tímto způsobem, ale protože výstup do vyrovnávací paměti.

```cpp
// effects_buffering.cpp
// compile with: /EHsc
#include <iostream>
#include <time.h>
using namespace std;

int main( )
{
   time_t tm = time( NULL ) + 5;
   cout << "Please wait...";
   while ( time( NULL ) < tm )
      ;
   cout << "\nAll done" << endl;
}
```

Chcete-li program logicky, pracovat `cout` objektu musí prázdný samotné se zobrazí zpráva. Vyprázdnit `ostream` objektu, odeslat ho `flush` manipulátor:

```cpp
cout <<"Please wait..." <<flush;
```

Tento krok vyprázdní vyrovnávací paměť, pro zajištění, že před čekání se zobrazí zpráva. Můžete také použít `endl` manipulátor, která vyprázdní vyrovnávací paměť a vypíše vrátit návrat na začátek řádku-odřádkování, nebo můžete použít `cin` objektu. Tento objekt (s `cerr` nebo `clog` objekty) je obvykle svázány se `cout` objektu. Díky tomu se jakékoli použití `cin` (nebo `cerr` nebo `clog` objekty) vyprázdní `cout` objektu.

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)<br/>
