---
title: Vytváření objektů vstupního datového proudu
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
ms.openlocfilehash: c000a9e927169ef710554372217ba15089ee11b8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457299"
---
# <a name="constructing-input-stream-objects"></a>Vytváření objektů vstupního datového proudu

Pokud použijete pouze `cin` objekt, není nutné vytvářet vstupní datový proud. Vstupní datový proud musíte vytvořit, pokud používáte:

- [Konstruktory vstupního datového proudu souborů](#vclrfinputfilestreamconstructorsanchor8)

- [Konstruktory vstupního datového proudu řetězců](#vclrfinputstringstreamconstructorsanchor9)

## <a name="vclrfinputfilestreamconstructorsanchor8"></a>Konstruktory vstupního datového proudu souborů

Existují dva způsoby, jak vytvořit datový proud vstupního souboru:

- Použijte konstruktor argumentů **void** a pak zavolejte `open` členskou funkci:

   ```cpp
   ifstream myFile; // On the stack
   myFile.open("filename");

   ifstream* pmyFile = new ifstream; // On the heap
   pmyFile->open("filename");
   ```

- Zadejte název souboru a příznaky režimu ve volání konstruktoru, čímž otevřete soubor během procesu konstrukce:

   ```cpp
   ifstream myFile("filename");
   ```

## <a name="vclrfinputstringstreamconstructorsanchor9"></a>Konstruktory vstupního datového proudu řetězců

Konstruktory vstupního datového proudu vyžadují adresu předvyhrazeného předinicializovaného úložiště:

```cpp
string s("123.45");

double amt;
istringstream myString(s);

//istringstream myString("123.45") also works
myString>> amt; // amt contains 123.45
```

## <a name="see-also"></a>Viz také:

[Vstupní streamy](../standard-library/input-streams.md)
