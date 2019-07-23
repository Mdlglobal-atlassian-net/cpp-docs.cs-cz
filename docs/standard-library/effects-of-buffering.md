---
title: Účinky ukládání do vyrovnávací paměti
ms.date: 11/04/2016
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
ms.openlocfilehash: 23e241794455a92f9e3628a786d75a6d4c7b037e
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376320"
---
# <a name="effects-of-buffering"></a>Účinky ukládání do vyrovnávací paměti

Následující příklad ukazuje účinky ukládání do vyrovnávací paměti. Můžete očekávat, že program bude vytištěn `please wait`, počkat 5 sekund a pak pokračovat. To ale nebude nutně fungovat, protože výstup je uložený ve vyrovnávací paměti.

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

Chcete-li, aby program pracoval logicky `cout` , objekt musí být prázdný, když se zobrazí zpráva. Chcete-li `ostream` objekt vyprázdnit, `flush` odešlete manipulátor:

```cpp
cout <<"Please wait..." <<flush;
```

Tento krok vyprázdní vyrovnávací paměť, což zajistí, že zpráva bude vytištěna před čekáním. Můžete také použít `endl` manipulátor, který vyprázdní vyrovnávací paměť a výstupy datového kanálu pro návrat na začátek řádku, nebo můžete `cin` použít objekt. Tento objekt (s `cerr` objekty nebo `clog` ) `cout` je obvykle svázán s objektem. Proto jakékoli použití `cin` (nebo `cerr` objektů nebo `clog` ) vyprázdní `cout` objekt.

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)<br/>
