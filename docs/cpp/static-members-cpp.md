---
title: Statické členy (C++)
ms.date: 11/04/2016
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
ms.openlocfilehash: c18b29cf69c2f899fbf06c7cb75ebbd2242ab427
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178558"
---
# <a name="static-members-c"></a>Statické členy (C++)

Třídy mohou obsahovat statická členská data a členské funkce. Je-li datový člen deklarován jako **static**, je pro všechny objekty třídy udržována pouze jedna kopie dat.

Statické datové členy nejsou součástí objektů daného typu třídy. V důsledku toho deklarace statického datového členu není považována za definici. Datový člen je deklarován v oboru třídy, ale definice je provedena v oboru souboru. Tito statický členové mají vnější propojení. Ilustruje to následující příklad:

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

V předchozím kódu je členský `bytecount` deklarován ve třídě `BufferedOutput`, ale musí být definován mimo deklaraci třídy.

Na členy statických dat lze odkazovat bez odkazu na objekt typu třídy. Počet bajtů zapsaných pomocí `BufferedOutput` objektů lze získat následujícím způsobem:

```cpp
long nBytes = BufferedOutput::bytecount;
```

Aby existoval statický člen, není nutné, aby existovaly žádné objekty typu třídy. Ke statickým členům lze také přistupovat pomocí výběru členů ( **.** a **->** ) operátory. Příklad:

```cpp
BufferedOutput Console;

long nBytes = Console.bytecount;
```

V předchozím případě není vyhodnocen odkaz na objekt (`Console`); vrácenou hodnotou je `bytecount`statických objektů.

Statickým datovým členům podléhají pravidla přístupu členů třídy, takže privátní přístup ke statickým datovým členům je povolen pouze pro členské funkce a přátele typu třída. Tato pravidla jsou popsána v tématu [Member-Access Control](../cpp/member-access-control-cpp.md). Výjimkou je, že statické datové členy musí být definovány v rozsahu souboru bez ohledu na jejich omezení přístupu. Pokud má být datový člen explicitně inicializován, musí být pro definici k dispozici inicializátor.

Typ statického člena není kvalifikován názvem jeho třídy. Proto je typ `BufferedOutput::bytecount` **dlouhý**.

## <a name="see-also"></a>Viz také

[Třídy a struktury](../cpp/classes-and-structs-cpp.md)
