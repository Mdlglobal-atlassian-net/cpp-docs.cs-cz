---
title: Statické členy (C++) | Microsoft Docs
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
ms.openlocfilehash: ca75d2e54c951e20de842b984f8619dc6639dc00
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="static-members-c"></a>Statické členy (C++)
Třídy může obsahovat statický člen dat a členské funkce. Když je datový člen deklarován jako **statické**, pouze jedna kopie dat bude zachována pro všechny objekty třídy.
  
 Členy statických dat nejsou součástí objekty typu dané třídy. Deklarace člena statických dat v důsledku toho není považováno za definici. Datový člen je deklarován v rozsahu třídy, ale definice se provádí v rozsahu souboru. Tyto statické členy mít externí propojení. Následující příklad ilustruje toto:  
  
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
  
 V předchozí kód člena `bytecount` je deklarovaná ve třídě `BufferedOutput`, ale musí být definován mimo deklaraci třídy.  
  
 Členy statických dat lze odkazovat bez odkazující na objekt typu třídy. Počet bajtů zapsaných pomocí `BufferedOutput` objektů můžete získat následujícím způsobem:  
  
```cpp  
long nBytes = BufferedOutput::bytecount;  
```  
  
 Pro statický člen existovat není nutné, aby všechny objekty typu třídy existovat. Statické členy můžete také získat přístup pomocí výběr členů (**.** a **->**) operátory. Příklad:  
  
```cpp  
BufferedOutput Console;  
  
long nBytes = Console.bytecount;  
```  
  
 V předchozím případě odkaz na objekt (`Console`) není vyhodnocen; hodnota vrácená je, že statické objektu `bytecount`.  
  
 Členy statických dat platí pravidla přístupu k člena třídy, takže privátní přístup k členy statických dat je povolené jenom pro funkce člena třídy a přátel. Tato pravidla jsou popsané v [řízení přístup ke členu](../cpp/member-access-control-cpp.md). Výjimkou je statických dat členů musí být definován v oboru souboru bez ohledu na jejich omezení přístupu. Pokud datový člen je explicitně inicializovat, je třeba zadat inicializátoru s definicí.  
  
 Typ je statický člen není kvalifikován názvem třídy. Proto typ `BufferedOutput::bytecount` je `long`.  
  
## <a name="see-also"></a>Viz také  
 [Třídy a struktury](../cpp/classes-and-structs-cpp.md)