---
title: 'Postupy: Zařazování řetězců v kódu ANSI pomocí zprostředkovatele komunikace C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
ms.openlocfilehash: 272e64a5dd8faf103daf3ab7fa17449bf3dbb7ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570495"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Postupy: Zařazování řetězců v kódu ANSI pomocí zprostředkovatele komunikace C++

Toto téma ukazuje, jak mohou být řetězce ANSI předaným pomocí zprostředkovatele komunikace C++, ale rozhraní .NET Framework <xref:System.String> představuje řetězce ve formátu Unicode, takže je převod na ANSI přidat další krok. Spolupráce s jinými typy řetězce, naleznete v následujících tématech:

- [Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy #pragma implementace spravovaných a nespravovaných funkcí ve stejném souboru, ale tyto funkce spolupracují stejným způsobem, pokud jsou definovány v samostatných souborech. Protože soubory, které obsahují pouze nespravované funkce nemusí být zkompilovány s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), mohou si zachovat jejich výkonnostní charakteristice.

## <a name="example"></a>Příklad

Příklad ukazuje předávání řetězce ANSI ze spravované na nespravované funkce pomocí <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>. Tato metoda přidělí paměť v nespravované haldě a vrátí adresu, po provedení převodu. To znamená, že není nutné zakázat připínání, (protože paměti v haldě GC. není předána nespravovanou funkci) a že IntPtr vrácená <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> musí být explicitně uvolněn nebo únik paměti.

```
// MarshalANSI1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const char* p) {
   printf_s("(native) received '%s'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("sample string");
   IntPtr ip = Marshal::StringToHGlobalAnsi(s);
   const char* str = static_cast<const char*>(ip.ToPointer());

   Console::WriteLine("(managed) passing string...");
   NativeTakesAString( str );

   Marshal::FreeHGlobal( ip );
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje zařazování dat, které se vyžadují pro přístup k řetězci ANSI ve spravované funkci, která je volána metodou nespravované funkci. Spravované funkce při přijetí nativní řetězec, můžete použít přímo nebo ho převést na spravované řetězce pomocí <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> způsob, jak je znázorněno.

```
// MarshalANSI2.cpp
// compile with: /clr
#include <iostream>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(char* s) {
   String^ ms = Marshal::PtrToStringAnsi(static_cast<IntPtr>(s));
   Console::WriteLine("(managed): received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(native) calling managed func...\n";
   ManagedStringFunc("test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>Viz také

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)