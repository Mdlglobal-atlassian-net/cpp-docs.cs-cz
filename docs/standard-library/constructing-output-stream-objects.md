---
title: Vytváření objektů výstupního datového proudu | Microsoft Docs
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
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: debc39987efffe149b8b7834ba5416027acadf4e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="constructing-output-stream-objects"></a>Vytváření objektů výstupního datového proudu

Pokud používáte pouze předdefinovanou `cout`, `cerr`, nebo `clog` objekty, není potřeba vytvořit výstupního proudu. Je nutné použít konstruktory pro:

- [Výstupní soubor datového proudu konstruktory](#vclrfoutputfilestreamconstructorsanchor1)

- [Výstupní řetězec datového proudu konstruktory](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="vclrfoutputfilestreamconstructorsanchor1"></a> Výstupní soubor datového proudu konstruktory

Můžete vytvořit výstupní proud souboru v jednom ze dvou způsobů:

- Použít výchozí konstruktor a pak zavolají `open` – členská funkce.

   ```cpp
   ofstream myFile; // Static or on the stack
   myFile.open("filename");

   ofstream* pmyFile = new ofstream; // On the heap
   pmyFile->open("filename");
   ```

- Zadejte název souboru a režim příznaky ve volání konstruktoru.

   ```cpp
   ofstream myFile("filename", ios_base::out);
   ```

## <a name="vclrfoutputstringstreamconstructorsanchor2"></a> Výstupní řetězec datového proudu konstruktory

Chcete-li vytvořit řetězec výstupního datového proudu, můžete použít `ostringstream` následujícím způsobem:

```cpp
using namespace std;
// ...
ostringstream myString;
myString << "this is a test" << ends;

string sp = myString.str(); // Obtain string
cout << sp << endl;
```

`ends` "Manipulator" přidá nezbytné ukončující znak hodnoty null do řetězce.

## <a name="see-also"></a>Viz také

[Výstupní streamy](../standard-library/output-streams.md)<br/>
