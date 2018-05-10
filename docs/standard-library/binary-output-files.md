---
title: Binární výstupní soubory | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdb101620b1a61f3a29057ee408cf9e89d38f9e8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="binary-output-files"></a>Binární výstupní soubory

Datové proudy byly původně navrženy pro text, tak, aby výchozí režim výstup textu. V režimu textových znak nového řádku (hexadecimální 10) zasahuje do znaků CR vrátit-konce řádku (pouze 16 bitů). Rozšíření může způsobit problémy, jak je vidět tady:

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

Očekáváte může tento program k vypsání pořadí bajtů {99, 0, 10, 0}; Místo toho vyprodukuje {99, 0, 13, 10, 0}, což způsobuje problémy programu očekáván binární vstup. Pokud třeba PRAVDA binární výstup, ve kterém jsou zapsány znaky nepřeložený, budete moci zadat binární výstup pomocí [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) openmode – argument konstruktoru:

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

## <a name="see-also"></a>Viz také

[Výstupní streamy](../standard-library/output-streams.md)<br/>
