---
title: Vymazání prostředků
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
ms.openlocfilehash: 225c3ccaf3342f11ad4eb6d6575ad3ac542acfd2
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246639"
---
# <a name="cleaning-up-resources"></a>Vymazání prostředků

Při provádění obslužné rutiny ukončení nemusíte před voláním rutiny ukončení vědět, které prostředky jsou ve skutečnosti přiděleny. Je možné, že byl blok příkazu **__try** přerušen před přidělením všech prostředků, takže nebyly otevřeny všechny prostředky.

Proto byste dříve, než přikročíte k zpracování vyčištění při ukončení, měli z důvodu bezpečnosti zkontrolovat, které prostředky jsou skutečně otevřené. Doporučený postup je:

1. Inicializovat popisovače na hodnotu NULL.

1. V bloku příkazu **__try** přidělte prostředky. Pokud je prostředek přidělen, jsou popisovače nastaveny na kladné hodnoty.

1. V bloku příkazu **__finally** uvolněte každý prostředek, jehož odpovídající obslužná rutina nebo proměnná příznaku je nenulová nebo nemá hodnotu null.

## <a name="example"></a>Příklad

Například následující kód používá obslužnou rutinu ukončení pro uzavření tří souborů a blok paměti, který byl přidělen v bloku příkazu **__try** . Před vyčištěním prostředků kód nejprve zkontroluje, zda tyto prostředky byly přiděleny.

```cpp
// exceptions_Cleaning_up_Resources.cpp
#include <stdlib.h>
#include <malloc.h>
#include <stdio.h>
#include <windows.h>

void fileOps() {
   FILE  *fp1 = NULL,
         *fp2 = NULL,
         *fp3 = NULL;
   LPVOID lpvoid = NULL;
   errno_t err;

   __try {
      lpvoid = malloc( BUFSIZ );

      err = fopen_s(&fp1, "ADDRESS.DAT", "w+" );
      err = fopen_s(&fp2, "NAMES.DAT", "w+" );
      err = fopen_s(&fp3, "CARS.DAT", "w+" );
   }
   __finally {
      if ( fp1 )
         fclose( fp1 );
      if ( fp2 )
         fclose( fp2 );
      if ( fp3 )
         fclose( fp3 );
      if ( lpvoid )
         free( lpvoid );
   }
}

int main() {
   fileOps();
}
```

## <a name="see-also"></a>Viz také:

[Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)