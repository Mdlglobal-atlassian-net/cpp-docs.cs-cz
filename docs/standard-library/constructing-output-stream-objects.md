---
title: "Vytváření objektů výstupního datového proudu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d9bf3e35c311f5e1e270a6fd46d9cfa24b2e4ba4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="constructing-output-stream-objects"></a>Vytváření objektů výstupního datového proudu
Pokud používáte pouze předdefinovanou `cout`, `cerr`, nebo `clog` objekty, není potřeba vytvořit výstupního proudu. Je nutné použít konstruktory pro:  
  
- [Výstupní soubor datového proudu konstruktory](#vclrfoutputfilestreamconstructorsanchor1)  
  
- [Výstupní řetězec datového proudu konstruktory](#vclrfoutputstringstreamconstructorsanchor2)  
  
##  <a name="vclrfoutputfilestreamconstructorsanchor1"></a>Výstupní soubor datového proudu konstruktory  
 Můžete vytvořit výstupní proud souboru v jednom ze dvou způsobů:  
  
-   Použít výchozí konstruktor a pak zavolají `open` – členská funkce.  
  
 ```  
    ofstream myFile; // Static or on the stack  
    myFile.open("filename");

 
    ofstream* pmyFile = new ofstream; // On the heap  
    pmyFile->open("filename");
```  
  
-   Zadejte název souboru a režim příznaky ve volání konstruktoru.  
  
 ```  
    ofstream myFile("filename", ios_base::out);
```  
  
##  <a name="vclrfoutputstringstreamconstructorsanchor2"></a>Výstupní řetězec datového proudu konstruktory  
 Chcete-li vytvořit řetězec výstupního datového proudu, můžete použít `ostringstream` následujícím způsobem:  
  
```  
    using namespace std;  
string sp;  
ostringstream myString;  
myString <<"this is a test" <<ends;  
sp = myString.str();
// Obtain string  
cout <<sp <endl;   
```  
  
 `ends` "Manipulator" přidá nezbytné ukončující znak hodnoty null do řetězce.  
  
## <a name="see-also"></a>Viz také  
 [Výstupní datové proudy](../standard-library/output-streams.md)

