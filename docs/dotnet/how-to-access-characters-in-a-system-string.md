---
title: 'Postupy: Přístup ke znakům v datech třídy System::String'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
ms.openlocfilehash: 3c44c5e7651bb1c5b4c28654b896cbe64bd5bec7
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988643"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>Postupy: Přístup ke znakům v datech třídy System::String

Můžete získat přístup k znakům objektu <xref:System.String> pro vysoce výkonné volání nespravovaných funkcí, které přijímají `wchar_t*` řetězce. Metoda vrací vnitřní ukazatel na první znak objektu <xref:System.String>. Tento ukazatel se může manipulovat přímo nebo připnuté a předávat do funkce, která očekává běžný `wchar_t` řetězec.

## <a name="example"></a>Příklad

`PtrToStringChars` vrátí <xref:System.Char>, což je vnitřní ukazatel (označovaný také jako `byref`). V takovém případě je předmětem uvolňování paměti. Tento ukazatel nemusíte připnout, pokud ho nebudete předávat nativní funkci.

Vezměte v úvahu následující kód.  Připnutí není nutné, protože `ppchar` je vnitřní ukazatel a pokud systém uvolňování paměti přesune řetězec, na který odkazuje, bude také aktualizovat `ppchar`. Bez [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md)bude kód fungovat a nebude mít potenciální výkon způsobený připnutím.

Pokud předáte `ppchar` nativní funkci, musí se jednat o ukazatel připnutí; systém uvolňování paměti nebude moci aktualizovat žádné ukazatele na nespravovaném bloku zásobníku.

```cpp
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

```cpp
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

Vnitřní ukazatel má všechny vlastnosti nativního C++ ukazatele. Můžete ho například použít k Projděte si propojenou datovou strukturu a vkládat a odstraňovat pomocí jenom jednoho ukazatele:

```cpp
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

## <a name="see-also"></a>Viz také:

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
