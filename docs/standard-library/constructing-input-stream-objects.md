---
title: "Vytváření objektů vstupního datového proudu | Microsoft Docs"
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
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a189fa948bc8c6be7acdac0dcc50e9585e82a082
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="constructing-input-stream-objects"></a>Vytváření objektů vstupního datového proudu
Pokud používáte pouze `cin` objektu, není potřeba vytvořit vstupního datového proudu. Pokud používáte, je nutné vytvořit vstupní datový proud:  
  
- [Vstupní soubor datového proudu konstruktory](#vclrfinputfilestreamconstructorsanchor8)  
  
- [Vstupní řetězec datového proudu konstruktory](#vclrfinputstringstreamconstructorsanchor9)  
  
##  <a name="vclrfinputfilestreamconstructorsanchor8">Vstupní soubor datového proudu konstruktory</a>  
 Existují dva způsoby vytvoření datového proudu vstupní soubor:  
  
-   Použití `void` argument konstruktoru, potom zavolejte `open` – členská funkce:  
  
 ```  
    ifstream myFile; // On the stack  
    myFile.open("filename");

 
    ifstream* pmyFile = new ifstream; // On the heap  
    pmyFile->open("filename");
```  
  
-   Zadejte název souboru a režim příznaky ve volání konstruktoru, během procesu vytváření a otevírání souboru:  
  
 ```  
    ifstream myFile("filename");
```  
  
##  <a name="vclrfinputstringstreamconstructorsanchor9">Vstupní řetězec datového proudu konstruktory</a>  
 Vstupní řetězec datového proudu konstruktory vyžadovat adresu předběžně přidělené, preinitialized úložiště:  
  
```  
string s("123.45");

double amt;  
istringstream myString(s);

//istringstream myString("123.45") also works  
myString>> amt; // amt contains 123.45  
```  
  
## <a name="see-also"></a>Viz také  
 [Vstupní streamy](../standard-library/input-streams.md)

