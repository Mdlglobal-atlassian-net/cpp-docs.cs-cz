---
title: Vytváření objektů výstupního datového proudu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ff3c924327c11d00dd9137a91ebd19ef7bdc9eaa
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
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
