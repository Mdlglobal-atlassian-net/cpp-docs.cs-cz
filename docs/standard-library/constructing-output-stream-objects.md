---
title: Vytváření objektů výstupního datového proudu
ms.date: 11/04/2016
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
ms.openlocfilehash: 7da7d9dd0fae3ce3fa21ecd774f88643dca49c26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62211998"
---
# <a name="constructing-output-stream-objects"></a>Vytváření objektů výstupního datového proudu

Pokud používáte pouze předdefinované `cout`, `cerr`, nebo `clog` objekty, není potřeba vytvořit výstupní datový proud. Je nutné použít konstruktory pro:

- [Výstupní soubor Stream konstruktory](#vclrfoutputfilestreamconstructorsanchor1)

- [Výstupní řetězec Stream konstruktory](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="vclrfoutputfilestreamconstructorsanchor1"></a> Výstupní soubor Stream konstruktory

Můžete vytvořit výstupní datový proud souboru v jednom ze dvou způsobů:

- Použít výchozí konstruktor a následně zavolat `open` členskou funkci.

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

## <a name="vclrfoutputstringstreamconstructorsanchor2"></a> Výstupní řetězec Stream konstruktory

Chcete-li vytvořit řetězec výstupní datový proud, můžete použít `ostringstream` následujícím způsobem:

```cpp
using namespace std;
// ...
ostringstream myString;
myString << "this is a test" << ends;

string sp = myString.str(); // Obtain string
cout << sp << endl;
```

`ends` "Manipulátor" přidá potřebné ukončujícího znaku null na řetězec.

## <a name="see-also"></a>Viz také:

[Výstupní streamy](../standard-library/output-streams.md)<br/>
