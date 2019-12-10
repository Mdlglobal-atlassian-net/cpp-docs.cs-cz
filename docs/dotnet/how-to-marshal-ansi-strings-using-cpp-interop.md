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
ms.openlocfilehash: 6987b23311354cfe6fd095e0e811d043e9b9692e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988466"
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Postupy: Zařazování řetězců v kódu ANSI pomocí zprostředkovatele komunikace C++

Toto téma ukazuje, jak lze řetězce ANSI předat pomocí C++ technologie interoperability, ale .NET Framework <xref:System.String> představuje řetězce ve formátu Unicode, takže převod na ANSI je další krok. Pro spolupráci s jinými typy řetězců, přečtěte si následující témata:

- [Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy #pragma pro implementaci spravovaných a nespravovaných funkcí ve stejném souboru, ale tyto funkce spolupracují stejným způsobem, pokud jsou definovány v samostatných souborech. Vzhledem k tomu, že soubory obsahující pouze nespravované funkce není nutné kompilovat s možností [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md), mohou zachovat jejich charakteristiky výkonu.

## <a name="example"></a>Příklad

Příklad ukazuje předání řetězce ANSI ze spravovaného do nespravované funkce pomocí <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>. Tato metoda přiděluje paměť na nespravovanou haldě a vrátí adresu po provedení převodu. To znamená, že není nutné žádné připnutí (protože paměť v haldě GC není předávána do nespravované funkci) a že IntPtr, který je vrácený <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>, musí být explicitně vydán nebo jsou vráceny výsledky nevracení paměti.

```cpp
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

Následující příklad ukazuje zařazování dat potřebné pro přístup k řetězci ANSI ve spravované funkci, která je volána nespravovanou funkcí. Spravovaná funkce, při přijetí nativního řetězce, ji může buď použít přímo, nebo ji převést na spravovaný řetězec pomocí metody <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A>, jak je znázorněno na obrázku.

```cpp
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

## <a name="see-also"></a>Viz také:

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
