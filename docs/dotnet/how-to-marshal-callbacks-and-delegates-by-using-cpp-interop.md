---
title: 'Postupy: Zařazování zpětných volání a delegátů pomocí funkcí interoperability C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
ms.openlocfilehash: 592eae0ff59baddb79b810d46669b78ecc801155
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988187"
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>Postupy: Zařazování zpětných volání a delegátů pomocí funkcí interoperability C++

Toto téma ukazuje Zařazování zpětných volání a delegátů (spravované verze zpětného volání) mezi spravovaným a nespravovaným kódem C++pomocí vizuálu.

Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy #pragma pro implementaci spravovaných a nespravovaných funkcí ve stejném souboru, ale funkce lze také definovat v samostatných souborech. Soubory obsahující pouze nespravované funkce není nutné kompilovat s možností [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak nakonfigurovat nespravované rozhraní API pro aktivaci spravovaného delegáta. Je vytvořen spravovaný delegát a jedna z metod spolupráce, <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>, slouží k načtení základního vstupního bodu pro delegáta. Tato adresa je pak předána nespravované funkci, která ji volá bez vědomí faktu, že je implementována jako spravovaná funkce.

Všimněte si, že je to možné, ale není nutné připnout delegáta pomocí [pin_ptrC++(/CLI)](../extensions/pin-ptr-cpp-cli.md) a zabránit tak jeho opětovnému umístění nebo likvidaci systémem uvolňování paměti. Ochrana proti předčasnému uvolňování paměti je nutná, ale připnutí poskytuje větší ochranu, než je nutné, protože brání v kolekci, ale také zabraňuje přemístění.

Pokud je delegát znovu umístěn v uvolňování paměti, nebude mít vliv na spravované zpětné volání, takže <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> slouží k přidání odkazu na delegáta, který umožňuje přemístění delegáta, ale brání vyřazení. Použití GCHandle místo pin_ptr redukuje potenciál fragmentace spravované haldy.

```cpp
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

Následující příklad je podobný předchozímu příkladu, ale v tomto případě je poskytnutý ukazatel na funkci uložen pomocí nespravovaného rozhraní API, takže jej lze vyvolat kdykoli, což vyžaduje, aby se uvolňování paměti potlačilo na libovolnou dobu. V důsledku toho následující příklad používá globální instanci <xref:System.Runtime.InteropServices.GCHandle> k tomu, aby se zabránilo přemístění delegáta, nezávisle na rozsahu funkce. Jak je popsáno v prvním příkladu, použití pin_ptr je pro tyto příklady zbytečné, ale v tomto případě by nefungovalo, protože rozsah pin_ptr je omezený na jedinou funkci.

```cpp
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

## <a name="see-also"></a>Viz také:

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
