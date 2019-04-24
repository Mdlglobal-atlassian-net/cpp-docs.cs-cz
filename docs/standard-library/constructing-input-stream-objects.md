---
title: Vytváření objektů vstupního datového proudu
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
ms.openlocfilehash: 89d681f1a092957bc966d2ec788a0f9aa2261ada
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62211985"
---
# <a name="constructing-input-stream-objects"></a>Vytváření objektů vstupního datového proudu

Pokud používáte pouze `cin` objektu, není potřeba vytvořit vstupní datový proud. Pokud použijete, je nutné vytvořit vstupní datový proud:

- [Vstupní soubor Stream konstruktory](#vclrfinputfilestreamconstructorsanchor8)

- [Vstupní řetězec Stream konstruktory](#vclrfinputstringstreamconstructorsanchor9)

## <a name="vclrfinputfilestreamconstructorsanchor8"></a> Vstupní soubor Stream konstruktory

Existují dva způsoby, jak vytvořit proud vstupních souborů:

- Použití **void** argument konstruktoru, zavolejte `open` členské funkce:

   ```cpp
   ifstream myFile; // On the stack
   myFile.open("filename");

   ifstream* pmyFile = new ifstream; // On the heap
   pmyFile->open("filename");
   ```

- Zadejte název souboru a režim příznaky ve vyvolání konstruktoru, během procesu vytváření a otevírání souboru:

   ```cpp
   ifstream myFile("filename");
   ```

## <a name="vclrfinputstringstreamconstructorsanchor9"></a> Vstupní řetězec Stream konstruktory

Vstupní řetězec datového proudu konstruktory vyžadovat adresy předem inicializovaná, předběžně přidělené úložiště:

```cpp
string s("123.45");

double amt;
istringstream myString(s);

//istringstream myString("123.45") also works
myString>> amt; // amt contains 123.45
```

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)<br/>
