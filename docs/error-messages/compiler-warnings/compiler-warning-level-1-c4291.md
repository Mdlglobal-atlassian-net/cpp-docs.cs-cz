---
title: Upozornění kompilátoru (úroveň 1) C4291
ms.date: 11/04/2016
f1_keywords:
- C4291
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
ms.openlocfilehash: c8dc35a58d40d2619f6e035e07b4ad0b3351c45d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626644"
---
# <a name="compiler-warning-level-1-c4291"></a>Upozornění kompilátoru (úroveň 1) C4291

deklarace: nenašel se žádný vyhovující operátor delete; paměť nebude uvolněna, pokud inicializace vyvolá výjimku.

[Nové](../../cpp/new-operator-cpp.md) umístění se používá, pro které neexistuje žádné [odstranění](../../cpp/delete-operator-cpp.md)umístění.

Pokud je paměť přidělena objektu s operátorem **New**, je volána konstruktor objektu. Pokud konstruktor vyvolá výjimku, měla by být uvolněna jakákoli paměť, která byla přidělena objektu. Tato situace nemůže proběhnout, pokud neexistuje funkce **Delete** operátoru, která odpovídá operátoru **New**.

Použijete-li operátor **New** bez dalších argumentů a zkompilujete s možnostmi [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHS](../../build/reference/eh-exception-handling-model.md)nebo/EHa pro povolení zpracování výjimek, kompilátor vygeneruje kód pro volání operátoru **Delete** , pokud konstruktor vyvolá výjimku.

Použijete-li formulář umístění operátoru **New** (formulář s argumenty kromě velikosti přidělení) a konstruktor objektu vyvolá výjimku, kompilátor stále vygeneruje kód pro volání operátoru **Delete**; to ale uděláte jenom v případě, že je tvar operátoru **Odstranit** shodný s tvarem umístění operátoru **New** , který paměť přidělil. Příklad:

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

Výše uvedený příklad generuje upozornění C4291, protože nebyla definována žádná forma operátoru **Delete** , která by odpovídala tvaru umístění operátoru **New**. Chcete-li vyřešit tento problém, vložte následující kód nad **Hlavní**. Všimněte si, že všechny parametry přetíženého operátoru **Delete** se shodují s funkcemi přetíženého operátoru **New**, s výjimkou prvního parametru.

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```