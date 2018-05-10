---
title: Vytváření objektů vstupního datového proudu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7066ffe50dc76c26528e7bfcd3dc9e9778e1473a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="constructing-input-stream-objects"></a>Vytváření objektů vstupního datového proudu

Pokud používáte pouze `cin` objektu, není potřeba vytvořit vstupního datového proudu. Pokud používáte, je nutné vytvořit vstupní datový proud:

- [Vstupní soubor datového proudu konstruktory](#vclrfinputfilestreamconstructorsanchor8)

- [Vstupní řetězec datového proudu konstruktory](#vclrfinputstringstreamconstructorsanchor9)

## <a name="vclrfinputfilestreamconstructorsanchor8"></a> Vstupní soubor datového proudu konstruktory

Existují dva způsoby vytvoření datového proudu vstupní soubor:

- Použití `void` argument konstruktoru, potom zavolejte `open` – členská funkce:

   ```cpp
   ifstream myFile; // On the stack
   myFile.open("filename");

   ifstream* pmyFile = new ifstream; // On the heap
   pmyFile->open("filename");
   ```

- Zadejte název souboru a režim příznaky ve volání konstruktoru, během procesu vytváření a otevírání souboru:

   ```cpp
   ifstream myFile("filename");
   ```

## <a name="vclrfinputstringstreamconstructorsanchor9"></a> Vstupní řetězec datového proudu konstruktory

Vstupní řetězec datového proudu konstruktory vyžadovat adresu předběžně přidělené, preinitialized úložiště:

```cpp
string s("123.45");

double amt;
istringstream myString(s);

//istringstream myString("123.45") also works
myString>> amt; // amt contains 123.45
```

## <a name="see-also"></a>Viz také

[Vstupní streamy](../standard-library/input-streams.md)<br/>
