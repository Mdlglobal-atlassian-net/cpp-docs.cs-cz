---
title: 'Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
ms.openlocfilehash: 8dfdad892261d5ae2d3494734458e1447f8ebd7c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988463"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++

Toto téma ukazuje, jak je BSTR (základní formát řetězce přidaný v programování COM) možné předat ze spravovaného do nespravované funkce a naopak. Pro spolupráci s jinými typy řetězců si přečtěte následující témata:

- [Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Postupy: Zařazování řetězců v kódu ANSI pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy #pragma pro implementaci spravovaných a nespravovaných funkcí ve stejném souboru, ale tyto funkce spolupracují stejným způsobem, pokud jsou definovány v samostatných souborech. Soubory obsahující pouze nespravované funkce není nutné kompilovat s možností [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak lze předat BSTR (formát řetězce použitý v programování modelu COM) ze spravovaného do nespravované funkce. Volající spravovaná funkce používá <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> k získání adresy v řetězci BSTR obsahu rozhraní .NET System. String. Tento ukazatel je připnutý pomocí [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) , aby se zajistilo, že se jeho fyzická adresa během cyklu uvolňování paměti nemění, když se spustí nespravovaná funkce. Systém uvolňování paměti je zakázán z přesunu paměti, dokud [pin_ptrC++(/CLI)](../extensions/pin-ptr-cpp-cli.md) nepřejde do rozsahu.

```cpp
// MarshalBSTR1.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(BSTR bstr) {
   printf_s("%S", bstr);
}

#pragma managed

int main() {
   String^ s = "test string";

   IntPtr ip = Marshal::StringToBSTR(s);
   BSTR bs = static_cast<BSTR>(ip.ToPointer());
   pin_ptr<BSTR> b = &bs;

   NativeTakesAString( bs );
   Marshal::FreeBSTR(ip);
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak lze BSTR předat z nespravovaného do nespravované funkce. Přijímající spravovaná funkce může buď použít řetězec v jako BSTR, nebo použít <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> k jeho převodu na <xref:System.String> pro použití s jinými spravovanými funkcemi. Vzhledem k tomu, že paměť představující BSTR je přidělena nespravované haldě, není nutné žádné připnutí, protože neexistuje uvolňování paměti na nespravované haldě.

```cpp
// MarshalBSTR2.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedTakesAString(BSTR bstr) {
   String^ s = Marshal::PtrToStringBSTR(static_cast<IntPtr>(bstr));
   Console::WriteLine("(managed) convered BSTR to String: '{0}'", s);
}

#pragma unmanaged

void UnManagedFunc() {
   BSTR bs = SysAllocString(L"test string");
   printf_s("(unmanaged) passing BSTR to managed func...\n");
   ManagedTakesAString(bs);
}

#pragma managed

int main() {
   UnManagedFunc();
}
```

## <a name="see-also"></a>Viz také:

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
