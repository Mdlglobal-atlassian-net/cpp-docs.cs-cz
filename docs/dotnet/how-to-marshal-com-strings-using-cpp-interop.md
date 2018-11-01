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
ms.openlocfilehash: 664c9ed973e2dff4467d13742390da8a944eb87a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559117"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++

Toto téma ukazuje, jak BSTR (formát základní řetězce podporuje programování v modelu COM) mohou být předány ze spravované na nespravované funkce a naopak. Spolupráce s jinými typy řetězce, naleznete v následujících tématech:

- [Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Postupy: Zařazování řetězců v kódu ANSI pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy #pragma implementace spravovaných a nespravovaných funkcí ve stejném souboru, ale tyto funkce spolupracují stejným způsobem, pokud jsou definovány v samostatných souborech. Soubory, které obsahují pouze nespravované funkce nemusí být kompilována s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak mohou být předány BSTR (formátu řetězce programování v modelu COM) ze spravované na nespravované funkci. Volání spravované funkce používá <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> pro získání adresy BSTR reprezentace obsahu .NET System.String. Tento ukazatel je připnutá pomocí [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) zajistit, že jeho fyzické adresy se nemění během cyklu uvolňování paměti kolekce při nespravovanou funkci provede. Uvolňování paměti je zakázáno přesouvat paměť, dokud [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) dostane mimo rozsah.

```
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

Následující příklad ukazuje, jak mohou být předány BSTR z nespravované nespravované funkci. Přijímání spravované funkce můžete použít řetězec BSTR nebo použijte <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> pro převod na <xref:System.String> pro použití s jinými spravované funkce. Protože představující BSTR přidělení paměti na nespravované haldě, připínání je nezbytné, protože není žádná kolekce uvolnění paměti na nespravované haldě.

```
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

## <a name="see-also"></a>Viz také

[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)