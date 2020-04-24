---
title: Upozornění kompilátoru (úroveň 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: c1972236e30be4e6ca738b606b00398f5c7860e0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754865"
---
# <a name="compiler-warning-level-1-c4291"></a>Upozornění kompilátoru (úroveň 1) C4291

"prohlášení" : nebyl nalezen žádný odpovídající výmaz operátoru; paměť nebude uvolněna, pokud inicializace vyvolá výjimku

Umístění [nové](../../cpp/new-operator-cpp.md) se používá pro které neexistuje žádné umístění [odstranit](../../cpp/delete-operator-cpp.md).

Při přidělení paměti pro objekt s operátorem **new**, objekt ustaví konstruktor. Pokud konstruktor vyvolá výjimku, všechny paměti, která byla přidělena pro objekt by měl být přidělen. K tomu nemůže dojít, pokud neexistuje funkce **odstranění** operátoru, která odpovídá **operátoru new**.

Pokud použijete operátor **new** bez jakýchkoli dalších argumentů a zkompilujete s [možnostmi /GX](../../build/reference/gx-enable-exception-handling.md), [/EHs](../../build/reference/eh-exception-handling-model.md)nebo /EHa, který povolí zpracování výjimek, kompilátor vygeneruje kód pro volání **operátoru delete,** pokud konstruktor vyvolá výjimku.

Pokud použijete formulář umístění **nového** operátoru (formulář s argumenty kromě velikosti přidělení) a konstruktor objektu vyvolá výjimku, kompilátor bude stále generovat kód pro volání **operátoru delete**; ale bude tak učinit pouze v případě, že existuje forma umístění **operátoru delete** odpovídající formě umístění operátoru **new,** který přidělil paměť. Příklad:

```cpp
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

Výše uvedený příklad generuje upozornění C4291, protože nebyla definována žádná forma umístění **operátoru delete,** která odpovídá formě umístění operátoru **new**. Chcete-li problém vyřešit, vložte následující kód nad **hlavní**. Všimněte si, že všechny přetížené operátor **odstranit** parametry funkce odpovídají těm přetížené operátor **new**, s výjimkou první parametr.

```cpp
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```
