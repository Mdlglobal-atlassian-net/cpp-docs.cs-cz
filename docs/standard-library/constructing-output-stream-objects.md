---
title: Vytváření objektů výstupního datového proudu
ms.date: 11/04/2016
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
ms.openlocfilehash: d7bec211f30986deccc869a879dd5155ea70996b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457287"
---
# <a name="constructing-output-stream-objects"></a>Vytváření objektů výstupního datového proudu

Pokud použijete pouze předdefinované `cout` `cerr`objekty, nebo `clog` , nemusíte vytvářet výstupní datový proud. Je nutné použít konstruktory pro:

- [Konstruktory datového proudu výstupního souboru](#vclrfoutputfilestreamconstructorsanchor1)

- [Konstruktory výstupních řetězcových streamů](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="vclrfoutputfilestreamconstructorsanchor1"></a>Konstruktory datového proudu výstupního souboru

Datový proud výstupních souborů můžete vytvořit jedním ze dvou způsobů:

- Použijte výchozí konstruktor a potom zavolejte `open` členskou funkci.

   ```cpp
   ofstream myFile; // Static or on the stack
   myFile.open("filename");

   ofstream* pmyFile = new ofstream; // On the heap
   pmyFile->open("filename");
   ```

- Zadejte název souboru a příznaky režimu ve volání konstruktoru.

   ```cpp
   ofstream myFile("filename", ios_base::out);
   ```

## <a name="vclrfoutputstringstreamconstructorsanchor2"></a>Konstruktory výstupních řetězcových streamů

Chcete-li sestavit výstupní řetězcový proud, můžete použít `ostringstream` následujícím způsobem:

```cpp
using namespace std;
// ...
ostringstream myString;
myString << "this is a test" << ends;

string sp = myString.str(); // Obtain string
cout << sp << endl;
```

`ends` "Manipulátor" přidá do řetězce nezbytný ukončující znak null.

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)
