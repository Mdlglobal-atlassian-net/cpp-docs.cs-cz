---
title: Účinky ukládání do vyrovnávací paměti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- buffers, effects of buffering
- buffering, effects of
ms.assetid: 5d544812-e95e-4f28-b15a-edef3f3414fd
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c387ce96d17e1db0dfefac6783dbdc87deeb94fb
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
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
