---
title: "Kompilátoru (úroveň 1) upozornění C4291 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4291
dev_langs: C++
helpviewer_keywords: C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 38308fb0932bb3a62c6fe9611e8b973b2819753d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4291"></a>C4291 kompilátoru upozornění (úroveň 1)
"prohlášení": žádný odpovídající delete – operátor nalezen; Pokud se inicializace vyvolá výjimku, nebude uvolnit paměť  
  
 Umístění [nové](../../cpp/new-operator-cpp.md) se používá pro které není žádné umístění [odstranit](../../cpp/delete-operator-cpp.md).  
  
 Když se přidělí paměť pro objekt s operátorem **nové**, volání konstruktoru objektu. Pokud konstruktoru vyvolá výjimku, by měl být navrácena žádné pamětí přidělenou pro objekt. Pokud to nejde trvat místní operátor **odstranit** funkce existuje odpovídající operátor **nové**.  
  
 Pokud používáte operátor **nové** bez jakékoli další argumenty a kompilaci s [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHs](../../build/reference/eh-exception-handling-model.md), nebo/EHa možnosti pro povolení zpracování výjimek, kompilátor vygeneruje kód pro operátor volání **odstranit** Pokud konstruktoru vyvolá výjimku.  
  
 Pokud používáte formu umístění **nové** – operátor (formu s argumenty kromě velikost přidělení) a objektu konstruktor vyvolá výjimku, kompilátor stále vygeneruje kód pro volání operátor **odstranit**; ale pouze, pokud umístění forma operátor akce provede **odstranit** existuje odpovídající umístění formu operátor **nové** , přidělit paměť. Příklad:  
  
```  
// C4291.cpp  
// compile with: /EHsc /W1  
#include <malloc.h>  
  
class CList  
{  
public:  
   CList(int)  
   {  
      throw "Fail!";  
   }  
};  
  
void* operator new(size_t size, char* pszFilename, int nLine)  
{  
   return malloc(size);  
}  
  
int main(void)  
{  
   try  
   {  
      // This will call ::operator new(unsigned int) to allocate heap  
      // memory. Heap memory pointed to by pList1 will automatically be  
      // deallocated by a call to ::operator delete(void*) when  
      // CList::CList(int) throws an exception.  
      CList* pList1 = new CList(10);  
   }  
   catch (...)  
   {  
   }  
  
   try  
   {  
      // This will call the overloaded ::operator new(size_t, char*, int)  
      // to allocate heap memory. When CList::CList(int) throws an  
      // exception, ::operator delete(void*, char*, int) should be called  
      // to deallocate the memory pointed to by pList2. Since  
      // ::operator delete(void*, char*, int) has not been implemented,  
      // memory will be leaked when the deallocation cannot occur.  
      CList* pList2 = new(__FILE__, __LINE__) CList(20);   // C4291  
   }  
   catch (...)  
   {  
   }  
}  
```  
  
 Výše uvedený příklad generuje upozornění C4291, protože žádný formulář umístění operátoru **odstranit** byla definována odpovídající umístění formu operátor **nové**. Chcete-li problém vyřešit, vložte následující kód výše **hlavní**. Všimněte si, že všechny přetížené operátor **odstranit** parametry funkce shodují s těmi, přetížené operátoru **nové**, s výjimkou prvního parametru.  
  
```  
void operator delete(void* pMem, char* pszFilename, int nLine)  
{  
   free(pMem);  
}  
```