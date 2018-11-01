---
title: Binární výstupní soubory
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
ms.openlocfilehash: 99445275a8f92622f451e8a88082dc2b28fb60b6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50615641"
---
# <a name="binary-output-files"></a>Binární výstupní soubory

Datové proudy byly původně navržen pro text, tak režim výstupu výchozí je text. V textovém režimu rozšíří znak nového řádku (hexadecimální 10) návrat na začátek řádku vrátit – znak odřádkování (pouze 16 bitů). Rozšíření může způsobit potíže, jak je znázorněno zde:

```cpp
// binary_output_files.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };
int main( )
{
    ofstream os( "test.dat" );
    os.write( (char *) iarray, sizeof( iarray ) );
}
```

Očekáváte-li tento program do výstupního sekvence bajtů {99, 0, 10, 0}; Místo toho výstupu {99, 0, 13, 10, 0}, což způsobí, že problémy pro program očekává se binární vstup. Pokud potřebujete true binární výstup, ve kterém jsou zapsány znaků zůstanou nepřevedeny, budete moci zadat binární výstup s použitím [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) openmode argument konstruktoru:

```cpp
// binary_output_files2.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };

int main()
{
   ofstream ofs ( "test.dat", ios_base::binary );

   // Exactly 8 bytes written
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );
}
```

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)<br/>
