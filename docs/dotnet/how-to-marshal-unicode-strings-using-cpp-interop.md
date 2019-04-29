---
title: 'Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: 37b56834e000cff686557730252f3d425f642772
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400549"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++

Toto téma popisuje jeden aspekt vzájemná funkční spolupráce jazyka Visual C++. Další informace najdete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy #pragma implementace spravovaných a nespravovaných funkcí ve stejném souboru, ale tyto funkce spolupracují stejným způsobem, pokud jsou definovány v samostatných souborech. Soubory, které obsahují pouze nespravované funkce nemusí být kompilována s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

Toto téma ukazuje, jak můžete řetězců v kódu Unicode být předán ze spravované na nespravované funkce a naopak. Spolupráce s jinými typy řetězce, naleznete v následujících tématech:

- [Postupy: Zařazování řetězců v kódu ANSI pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>Příklad

Předat řetězec s kódováním Unicode ze spravované na nespravované funkci, PtrToStringChars – funkce (deklarované v Vcclr.h) slouží k přístupu do paměti, kde spravované řetězec uložen. Tato adresa se předají do nativní funkce, proto je důležité, že je paměť připnout s [pin_ptr (C++vyhodnocovací)](../extensions/pin-ptr-cpp-cli.md) Pokud chcete zakázat data řetězce se přemístění, by měla cyklu uvolňování paměti kolekce probíhat během nespravovanou funkci provede.

```
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

Následující příklad ukazuje zařazování dat, které se vyžadují pro přístup k řetězec znaků Unicode ve spravované funkci volanou třídou nespravované funkci. Převede spravovaný řetězec pomocí spravované funkce při přijetí nativní řetězec znaků Unicode <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> metody.

```
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
