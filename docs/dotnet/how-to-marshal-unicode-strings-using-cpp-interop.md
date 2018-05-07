---
title: 'Postupy: Zařazování řetězců kódování Unicode pomocí zprostředkovatele komunikace C++ | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e5290958a55c61dd55adac0f182af7163896d694
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++
Toto téma popisuje jednu omezující vlastnost vzájemné funkční spolupráce jazyka Visual C++. Další informace najdete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
 Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy jazyka #pragma k implementaci spravovaných a nespravovaných funkcí ve stejném souboru, ale tyto funkce spolupracují stejným způsobem, pokud jsou definovány v samostatné soubory. Soubory obsahující pouze nespravovaná funkce nemusí být zkompilovány s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 Toto téma ukazuje, jak mohou být řetězců v kódu Unicode předány ze spravované na nespravované funkce a naopak. Spolupráce s jinými typy řetězců, najdete v následujících tématech:  
  
-   [Postupy: Zařazování řetězců v kódu ANSI pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
-   [Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)  
  
## <a name="example"></a>Příklad  
 Předat řetězec znaků Unicode ze spravované na nespravované funkce, funkce PtrToStringChars (deklarované v Vcclr.h) slouží k přístupu do paměti, kde je uložen spravovaný řetězec. Protože tato adresa se předají nativní funkci, je důležité, aby byla připojená paměť s [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) Pokud chcete zabránit se přemístění dat řetězců, cyklu uvolňování paměti se uskuteční při nespravované funkce provede.  
  
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
 Následující příklad ukazuje zařazování data požadovaná pro přístup k řetězec znaků Unicode ve spravované funkci nespravovanou funkcí. Převede spravovaný řetězec pomocí spravovaná funkce, obdržení nativní řetězce kódování Unicode <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> metoda.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)