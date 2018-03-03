---
title: "Postupy: Zařazování řetězců ANSI pomocí zprostředkovatele komunikace C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- ANSI [C++], marshaling strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
ms.assetid: 5eda2eb6-5140-40f0-82cf-7ce171fffb45
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 7e70d62fa7a94a7278080c31f6650b31b71ff35b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-marshal-ansi-strings-using-c-interop"></a>Postupy: Zařazování řetězců v kódu ANSI pomocí zprostředkovatele komunikace C++
Toto téma ukazuje, jak mohou být řetězců v kódu ANSI předaným pomocí zprostředkovatele komunikace C++, ale rozhraní .NET Framework <xref:System.String> představuje řetězce ve formátu Unicode, takže převod na ANSI čeká na další krok. Spolupráce s jinými typy řetězců, najdete v následujících tématech:  
  
-   [Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
 Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy jazyka #pragma k implementaci spravovaných a nespravovaných funkcí ve stejném souboru, ale tyto funkce spolupracují stejným způsobem, pokud jsou definovány v samostatné soubory. Protože soubory obsahující pouze nespravovaná funkce nemusí být zkompilovány s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md), mohou si zachovat jejich výkonnostní charakteristice.  
  
## <a name="example"></a>Příklad  
 Příklad ukazuje předávání řetězce ANSI ze spravované na nespravované funkce pomocí <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A>. Tato metoda se přidělí paměť na nespravované haldě a vrátí adresu po provedení převodu. To znamená, že není nutné žádné Připnutí, (protože paměť na haldě GC není předána nespravované funkci) a že IntPtr vrácená z <xref:System.Runtime.InteropServices.Marshal.StringToHGlobalAnsi%2A> musí být explicitně uvolněn nebo únik paměti.  
  
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
 Následující příklad ukazuje zařazování data požadovaná pro přístup k řetězec ANSI ve spravované funkci, která je volána metodou nespravované funkce. Spravovaná funkce obdržení nativní řetězce, můžete buď používat přímo nebo ji převést na řetězec spravované pomocí <xref:System.Runtime.InteropServices.Marshal.PtrToStringAnsi%2A> metoda, jak je vidět.  
  
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