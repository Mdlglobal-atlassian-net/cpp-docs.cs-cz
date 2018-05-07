---
title: 'Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++ | Microsoft Docs'
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
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 918825dd6563f59167baa844b94edfc1033498a6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Postupy: Zařazování řetězců modelu COM pomocí zprostředkovatele komunikace C++
Toto téma ukazuje, jak může být BSTR (formát základní řetězce podporuje programování v modelu COM) předán ze spravované na nespravované funkce a naopak. Spolupráce s jinými typy řetězců, najdete v následujících tématech:  
  
-   [Postupy: Zařazování řetězců v kódu Unicode pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)  
  
-   [Postupy: Zařazování řetězců v kódu ANSI pomocí zprostředkovatele komunikace C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)  
  
 Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy jazyka #pragma k implementaci spravovaných a nespravovaných funkcí ve stejném souboru, ale tyto funkce spolupracují stejným způsobem, pokud jsou definovány v samostatné soubory. Soubory obsahující pouze nespravovaná funkce nemusí být zkompilovány s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak lze předat BSTR (formátu řetězce programování v modelu COM) ze spravované na nespravované funkce. Volající spravovaná funkce používá <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> adresu BSTR reprezentace obsahu .NET System.String získat. Tento ukazatel je připnutá pomocí [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) aby její fyzickou adresu není změněn během cyklu kolekce paměti při provede nespravované funkce. Uvolňování paměti je zakázáno přesouvat paměť, dokud [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) ocitne mimo rozsah.  
  
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
 Následující příklad ukazuje, jak lze předat BSTR z nespravované do nespravované funkce. Přijetí spravované funkce můžete buď použít řetězec v BSTR nebo použít <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> převést jej do <xref:System.String> pro použití s jinými spravované funkce. Protože paměť představující BSTR je přidělena na nespravované haldě, žádné Připnutí je nezbytné, protože není žádná kolekce paměti na nespravované haldě.  
  
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