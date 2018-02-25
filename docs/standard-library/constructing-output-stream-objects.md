---
title: "Vytváření objektů výstupního datového proudu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cf40e6683462803fcf81a9be915a4672baefd3e9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="constructing-output-stream-objects"></a>Vytváření objektů výstupního datového proudu
Pokud používáte pouze předdefinovanou `cout`, `cerr`, nebo `clog` objekty, není potřeba vytvořit výstupního proudu. Je nutné použít konstruktory pro:  
  
- [Výstupní soubor datového proudu konstruktory](#vclrfoutputfilestreamconstructorsanchor1)  
  
- [Výstupní řetězec datového proudu konstruktory](#vclrfoutputstringstreamconstructorsanchor2)  
  
##  <a name="vclrfoutputfilestreamconstructorsanchor1">Výstupní soubor datového proudu konstruktory</a>  
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
  
##  <a name="vclrfoutputstringstreamconstructorsanchor2">Výstupní řetězec datového proudu konstruktory</a>  
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
 [Výstupní streamy](../standard-library/output-streams.md)

