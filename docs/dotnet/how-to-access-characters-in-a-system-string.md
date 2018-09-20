---
title: 'Postupy: přístup ke znakům v datech třídy System::String | Dokumentace Microsoftu'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 6c5c4c6032330a58a6f1ea9fb85d3da57c28a177
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416185"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>Postupy: Přístup ke znakům v datech třídy System::String

Dostanete znaků <xref:System.String> objekt pro vysoce výkonné volání nespravovaných funkcí, které přijímají `wchar_t*` řetězce. Metoda poskytuje vnitřní ukazatel na první znak <xref:System.String> objektu. This – ukazatel lze manipulovat přímo nebo připnuté a předaný funkci očekává běžný `wchar_t` řetězec.

## <a name="example"></a>Příklad

`PtrToStringChars` Vrátí <xref:System.Char>, což je vnitřní ukazatel (označované také jako `byref`). V důsledku toho se časovač uvolněn z paměti. Není nutné tento ukazatel Připnutí, pokud se chystáte předat nativní funkce.

Uvažujme následující kód.  Připnutí není nutné, protože `ppchar` je vnitřní ukazatel, a pokud uvolňování paměti přesune odkazuje na řetězec, bude také aktualizovat `ppchar`. Bez [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md), kód bude fungovat a nebude mít potenciální výkon, což je způsobeno připnutím.

Pokud předáte `ppchar` nativní funkcí, pak musí být ukazatel Připnutí; systému uvolňování paměti nebude možné aktualizovat všechny ukazatele na rámce zásobníku nespravované.

```
// PtrToStringChars.cpp
// compile with: /clr
#include<vcclr.h>
using namespace System;

int main() {
   String ^ mystring = "abcdefg";

   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );

   for ( ; *ppchar != L'\0'; ++ppchar )
      Console::Write(*ppchar);
}
```

```Output
abcdefg
```

## <a name="example"></a>Příklad

Tento příklad ukazuje, kde je potřeba připnutí.

```
// PtrToStringChars_2.cpp
// compile with: /clr
#include <string.h>
#include <vcclr.h>
// using namespace System;

size_t getlen(System::String ^ s) {
   // Since this is an outside string, we want to be secure.
   // To be secure, we need a maximum size.
   size_t maxsize = 256;
   // make sure it doesn't move during the unmanaged call
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);
   return wcsnlen(pinchars, maxsize);
};

int main() {
   System::Console::WriteLine(getlen("testing"));
}
```

```Output
7
```

## <a name="example"></a>Příklad

Vnitřní ukazatel má všechny vlastnosti nativní ukazatel jazyka C++. Například můžete použít vás propojená datová struktura a provést vložení a odstranění pomocí pouze jednoho ukazatele:

```
// PtrToStringChars_3.cpp
// compile with: /clr /LD
using namespace System;
ref struct ListNode {
   Int32 elem;
   ListNode ^ Next;
};

void deleteNode( ListNode ^ list, Int32 e ) {
   interior_ptr<ListNode ^> ptrToNext = &list;
   while (*ptrToNext != nullptr) {
      if ( (*ptrToNext) -> elem == e )
         *ptrToNext = (*ptrToNext) -> Next;   // delete node
      else
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node
   }
}
```

## <a name="see-also"></a>Viz také

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)