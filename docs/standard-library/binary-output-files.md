---
title: "Binární výstupní soubory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: da2d0ac01919773492f075f2e2dd6a7d210224fb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="binary-output-files"></a>Binární výstupní soubory
Datové proudy byly původně navrženy pro text, tak, aby výchozí režim výstup textu. V režimu textových znak nového řádku (hexadecimální 10) zasahuje do znaků CR vrátit-konce řádku (pouze 16 bitů). Rozšíření může způsobit problémy, jak je vidět tady:  
  
```  
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
  
```  
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
 [Výstupní datové proudy](../standard-library/output-streams.md)
