---
title: Binární výstupní soubory
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
ms.openlocfilehash: 4562f5c1167aeadc6689313e73545ed1ad9bbcf8
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376329"
---
# <a name="binary-output-files"></a>Binární výstupní soubory

Datové proudy byly původně určeny pro text, takže výchozí režim výstupu je text. V textovém režimu se znak posunu řádku (nový řádek) rozšíří na dvojici kanálů návratového řádku. Rozšíření může způsobit problémy, jak je znázorněno zde:

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

Můžete očekávat, že tento program vypíše bajtovou sekvenci {99, 0, 10, 0}; místo toho produkuje výstup {99, 0, 13, 10, 0}, což způsobuje problémy programu, který očekává binární vstup. Pokud potřebujete skutečný binární výstup, ve kterém jsou znaky zapsány nepřeloženy, můžete zadat binární výstup pomocí argumentu konstruktoru `openmode` [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) :

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

[Výstupní streamy](../standard-library/output-streams.md)
