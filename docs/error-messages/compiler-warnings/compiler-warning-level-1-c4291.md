---
title: Upozornění (úroveň 1) C4291 kompilátoru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4291
dev_langs:
- C++
helpviewer_keywords:
- C4291
ms.assetid: c2b95dea-38f2-4609-9104-707c30798da4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8c5f2fe57d26de4b4b2f88a85f20b99344ac201
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46038045"
---
# <a name="compiler-warning-level-1-c4291"></a>Kompilátor upozornění (úroveň 1) C4291

"deklarace": byl nalezen žádný odpovídající operátor delete paměť se neuvolní, pokud při inicializaci dojde k výjimce

Umístění [nové](../../cpp/new-operator-cpp.md) se používá pro něž neexistuje žádné umístění [odstranit](../../cpp/delete-operator-cpp.md).

Když je přidělena paměť pro objekt s operátorem **nové**, je zavolán konstruktor objektu. Pokud konstruktor vyvolá výjimku, by měla uvolnit paměť, která byla objektu přidělena. To nemůže proběhnout Pokud operátor **odstranit** funkce existuje, který odpovídá operátor **nové**.

Pokud použijete operátor **nové** bez jakékoli dalších argumentů a kompilujete s [/GX](../../build/reference/gx-enable-exception-handling.md), [/EHS](../../build/reference/eh-exception-handling-model.md), nebo možnosti/EHa povolit zpracování výjimek, kompilátor vygeneruje kód pro volání operátoru **odstranit** Pokud konstruktor vyvolá výjimku.

Pokud používáte formu umístění **nové** – operátor (formu s argumenty kromě velikosti alokace) a konstruktor objektu vyvolá výjimku, pořád bude kompilátor generovat kód pro volání operátoru **odstranit**; ale pouze provede to pokud formu umístění operátoru **odstranit** existuje odpovídající formu umístění operátoru **nové** , který přidělené paměti. Příklad:

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

Výše uvedený příklad generuje upozornění C4291, protože žádné formu umístění operátoru **odstranit** byla definována, který odpovídá formu umístění operátoru **nové**. K vyřešení problému, vložte následující kód nad **hlavní**. Všimněte si, že všechny přetíženého operátoru **odstranit** parametry funkce shodovat s hodnotami přetíženého operátoru **nové**, s výjimkou první parametr.

```
void operator delete(void* pMem, char* pszFilename, int nLine)
{
   free(pMem);
}
```