---
title: Statické členy (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- class members [C++], static
- instance constructors, static members
- class members [C++], shared
- members [C++], static data members
- static members [C++], data members
- static data members [C++]
- data members [C++], static data members
- class instances [C++], shared members
- instance constructors, shared members
- class instances [C++], static members
ms.assetid: 9cc8cf0f-d74c-46f2-8e83-42d4e42c8370
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fba58883db0f5936a8f3dedc1e0c4a19fb0aafa9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086197"
---
# <a name="static-members-c"></a>Statické členy (C++)

Třídy mohou obsahovat statická členská data a členské funkce. Když je datový člen deklarován jako **statické**, pouze jedna kopie dat se zachová pro všechny objekty třídy.

Statické datové členy, které nejsou součástí objekty daného typu třídy. Deklarace statického datového členu v důsledku toho se nepovažuje za definici. Datový člen je deklarovaný v oboru třídy, ale definice se provádí v rozsahu souboru. Tyto statické členy mají vnější propojení. Následující příklad ukazuje toto:

```cpp
// static_data_members.cpp
class BufferedOutput
{
public:
   // Return number of bytes written by any object of this class.
   short BytesWritten()
   {
      return bytecount;
   }

   // Reset the counter.
   static void ResetCount()
   {
      bytecount = 0;
   }

   // Static member declaration.
   static long bytecount;
};

// Define bytecount in file scope.
long BufferedOutput::bytecount;

int main()
{
}
```

V předchozím kódu člena `bytecount` je deklarovaná ve třídě `BufferedOutput`, ale musí být definovány mimo deklaraci třídy.

Členy statických dat lze odkazovat bez odkazující na objekt typu třídy. Počet bajtů zapsaných pomocí `BufferedOutput` objektů můžete získat následujícím způsobem:

```cpp
long nBytes = BufferedOutput::bytecount;
```

Pro statický člen neexistuje není nutné, že neexistují žádné objekty typu třídy. Statickým členům lze rovněž přistupovat pomocí výběru členů (**.** a **->**) operátory. Příklad:

```cpp
BufferedOutput Console;

long nBytes = Console.bytecount;
```

V předchozím případě odkazu na objekt (`Console`), nebude hodnocen; vrácená hodnota je statický objekt `bytecount`.

Statické datové členy jsou v souladu s pravidla pro přístup k členu třídy, takže privátní přístup ke statické datové členy je povoleno pouze pro třídy členskými funkcemi a přáteli. Tato pravidla jsou popsány v [řízení přístupu členů](../cpp/member-access-control-cpp.md). Výjimkou je tato statická data, členy musí být definován v oboru souboru bez ohledu na omezení jejich přístupu. Pokud explicitně inicializovat datový člen, třeba zadat inicializátor s definicí.

Typ statického člena, který není kvalifikován pomocí názvu třídy. Proto typ `BufferedOutput::bytecount` je **dlouhé**.

## <a name="see-also"></a>Viz také:

[Třídy a struktury](../cpp/classes-and-structs-cpp.md)