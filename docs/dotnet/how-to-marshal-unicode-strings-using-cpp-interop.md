---
title: 'Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: f666e52b604e4713f02cb14744ac12a0407366a3
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988170"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++

Toto téma ukazuje jednu omezující vlastnost interoperability vizuálů C++ . Další informace najdete v tématu [použití C++ zprostředkovatele komunikace (implicitní PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy #pragma pro implementaci spravovaných a nespravovaných funkcí ve stejném souboru, ale tyto funkce spolupracují stejným způsobem, pokud jsou definovány v samostatných souborech. Soubory obsahující pouze nespravované funkce není nutné kompilovat s možností [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

Toto téma ukazuje, jak lze řetězce Unicode předat ze spravovaného do nespravované funkce a naopak. Pro spolupráci s jinými typy řetězců si přečtěte následující témata:

- [Postupy: Zařazování řetězců v kódu ANSI pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>Příklad

K předání řetězce Unicode ze spravovaného do nespravované funkce lze použít funkci PtrToStringChars (deklarovaná v Vcclr. h) k přístupu v paměti, kde je uložen spravovaný řetězec. Vzhledem k tomu, že tato adresa bude předána nativní funkci, je důležité, aby se paměť připnula s [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) , aby se zabránilo přemístění dat řetězce, pokud by se při provádění nespravované funkce prováděl cyklus uvolňování paměti.

```cpp
// MarshalUnicode1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const wchar_t* p) {
   printf_s("(native) received '%S'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("test string");
   pin_ptr<const wchar_t> str = PtrToStringChars(s);

   Console::WriteLine("(managed) passing string to native func...");
   NativeTakesAString( str );
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje zařazování dat potřebné pro přístup k řetězci Unicode ve spravované funkci, která je volána nespravovanou funkcí. Spravovaná funkce na základě přijetí nativního řetězce Unicode převede jej na spravovaný řetězec pomocí metody <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>.

```cpp
// MarshalUnicode2.cpp
// compile with: /clr
#include <iostream>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(wchar_t* s) {
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);
   Console::WriteLine("(managed) received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(unmanaged) calling managed func...\n";
   ManagedStringFunc(L"test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>Viz také:

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
