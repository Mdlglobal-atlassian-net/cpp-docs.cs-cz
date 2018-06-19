---
title: Účinky ukládání do vyrovnávací paměti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c28deb0f5e30d3ec28fac4805a86645bebf27f22
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842375"
---
# <a name="effects-of-buffering"></a>Účinky ukládání do vyrovnávací paměti

Následující příklad ukazuje účinky ukládání do vyrovnávací paměti. By se dalo očekávat program při `please wait`, počkejte 5 sekund a poté pokračujte. Nebude fungovat nutně tímto způsobem, ale protože výstup do vyrovnávací paměti.

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

Nastavit, aby program logicky, fungovat `cout` objekt musí prázdný samotné při zpráva se má zobrazit. Vyprázdnění `ostream` objektu, odešle `flush` manipulator:

```cpp
cout <<"Please wait..." <<flush;
```

Tento krok vyprázdní vyrovnávací paměť, pro zajištění, že před dobu zobrazí zpráva. Můžete také `endl` manipulator, která vyprázdní vyrovnávací paměť a výstupy vrátit-konce znaků CR řádku, nebo můžete použít `cin` objektu. Tento objekt (s `cerr` nebo `clog` objekty) je obvykle vázaný na `cout` objektu. Proto jakékoli použití `cin` (nebo `cerr` nebo `clog` objekty) vyprázdnění `cout` objektu.

## <a name="see-also"></a>Viz také

[Výstupní streamy](../standard-library/output-streams.md)<br/>
