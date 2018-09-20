---
title: 'Postupy: zařazování zpětných volání a delegátů pomocí funkcí interoperability C++ | Dokumentace Microsoftu'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: db3d4cf59aa3ec14e964d53a54afbe5a9fe0aecd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46381891"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>Postupy: Zařazování zpětných volání a delegátů pomocí funkcí interoperability C++

Toto téma ukazuje zařazování zpětných volání a delegátů (spravovaná verze zpětné volání) mezi spravovaným a nespravovaným kódem pomocí jazyka Visual C++.

Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy #pragma implementace spravovaných a nespravovaných funkcí ve stejném souboru, ale funkce mohou být také definovány v samostatných souborech. Soubory, které obsahují pouze nespravované funkce nemusí být kompilována s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat nespravovaného rozhraní API pro spuštění spravovaného delegáta. Vytvořili spravovaných delegáta a jednu z metod interoperability <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>, slouží k načtení základní vstupní bod pro delegáta. Tato adresa je pak předán nespravovanou funkci, která volá bez znalosti skutečnost, že je implementovaný jako spravované funkce.

Všimněte si, že je to možné, ale není nezbytné, PIN kód delegáta pomocí [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) zabránit, aby ji znovu umístěný nebo odstraněny pomocí systému uvolňování paměti. Ochrana před předčasné uvolňování paměti je potřeba, ale připnutí poskytuje větší ochranu než je nezbytné, protože brání kolekce, ale také zabraňuje přemístění.

Pokud delegát je přemístěn podle kolekce uvolnění paměti, nebude to mít vliv podkladové zpětné volání, takže <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> se používá k přidání odkazu na delegáta, což přemístění delegáta, ale brání vyřazení. Popisovač GCHandle místo pin_ptr snižuje potenciální fragmentace spravované haldy.

```
// MarshalDelegate1.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);

int TakesCallback(ANSWERCB fp, int n, int m) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n, m);
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   return n + m;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   GCHandle gch = GCHandle::Alloc(fp);
   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

// force garbage collection cycle to prove
// that the delegate doesn't get disposed
   GC::Collect();

   int answer = TakesCallback(cb, 243, 257);

// release reference to delegate
   gch.Free();
}
```

## <a name="example"></a>Příklad

Následující příklad je podobný jako předchozí příklad, ale v tomto případě je poskytnutý ukazatel funkce se ukládá pomocí nespravovaného rozhraní API, tak může být vyvolán v každém okamžiku vyžadující, že uvolňování paměti potlačit u libovolné délky času. V důsledku toho následující příklad používá globální instanci <xref:System.Runtime.InteropServices.GCHandle> zabránit delegáta přemístění, nezávisle na rozsah funkce. Jak je popsáno v prvním příkladu, pomocí pin_ptr není nutný pro tyto příklady, ale v takovém případě nebude fungovat i přesto, jako rozsah pin_ptr je omezen na jedinou funkci.

```
// MarshalDelegate2.cpp
// compile with: /clr
#include <iostream>

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

// Declare an unmanaged function type that takes two int arguments
// Note the use of __stdcall for compatibility with managed code
typedef int (__stdcall *ANSWERCB)(int, int);
static ANSWERCB cb;

int TakesCallback(ANSWERCB fp, int n, int m) {
   cb = fp;
   if (cb) {
      printf_s("[unmanaged] got callback address (%d), calling it...\n", cb);
      return cb(n, m);
   }
   printf_s("[unmanaged] unregistering callback");
   return 0;
}

#pragma managed

public delegate int GetTheAnswerDelegate(int, int);

int GetNumber(int n, int m) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;

   return n + m + x;
}

static GCHandle gch;

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);

   gch = GCHandle::Alloc(fp);

   IntPtr ip = Marshal::GetFunctionPointerForDelegate(fp);
   ANSWERCB cb = static_cast<ANSWERCB>(ip.ToPointer());
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TakesCallback(cb, 243, 257);

   // possibly much later (in another function)...

   Console::WriteLine("[managed] releasing callback mechanisms...");
   TakesCallback(0, 243, 257);
   gch.Free();
}
```

## <a name="see-also"></a>Viz také

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)