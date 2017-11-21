---
title: "Postupy: zařazování zpětných volání a delegátů pomocí funkcí interoperability C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- C++ Interop, callbacks and delegates
- interop [C++], callbacks and delegates
- delegates [C++], marshaling
- marshaling [C++], callbacks and delegates
- callbacks [C++], marshaling
ms.assetid: 2313e9eb-5df9-4367-be0f-14b4712d8d2d
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2a835dbdbce23f7f92f13fabd038d6e294345981
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-marshal-callbacks-and-delegates-by-using-c-interop"></a>Postupy: Zařazování zpětných volání a delegátů pomocí funkcí interoperability C++
Toto téma ukazuje zařazování zpětných volání a delegátů (spravovaná verze zpětné volání) mezi spravovanými a nespravovanými kódu pomocí Visual C++.  
  
 Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy jazyka #pragma k implementaci spravovaných a nespravovaných funkcí ve stejném souboru, ale funkce mohou být také definovány v samostatné soubory. Soubory obsahující pouze nespravovaná funkce nemusí být zkompilovány s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nakonfigurovat nespravovaného rozhraní API pro aktivaci spravovaného delegáta. Je vytvořen spravovaný delegát a jednu z metod interoperability, <xref:System.Runtime.InteropServices.Marshal.GetFunctionPointerForDelegate%2A>, slouží k načtení základní vstupní bod pro delegáta. Tato adresa je pak předána nespravované funkci, která volá bez znalosti fakt, že je implementovaný jako spravované funkce.  
  
 Všimněte si, že je možné, ale není nezbytné, aby se PIN kód delegáta pomocí [pin_ptr (C + +/ CLI)](../windows/pin-ptr-cpp-cli.md) zabránit, aby ji se znovu umístění nebo odstranění z modulem garbage collector. Je potřeba ochrany z předčasné uvolňování paměti, ale připnutí poskytuje větší ochranu, než je nezbytné, protože zabraňuje uvolňování, ale také zabraňuje přemístění.  
  
 Pokud delegát je znovu nalézt uvolnění paměti, nebude to mít vliv podkladové zpětné volání, takže <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> se používá k přidání odkazu na delegáta, což přemístění delegáta, ale zabráněním vyřazení. Použití GCHandle namísto pin_ptr snižuje potenciální fragmentace spravované haldy.  
  
```  
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
 V následujícím příkladu je podobně jako v předchozím příkladu, ale v takovém případě je poskytnutý ukazatel funkce ukládá nespravovaného rozhraní API, takže ji nelze vyvolat v každém okamžiku vyžadující, aby uvolňování potlačit libovolný dobu. V důsledku toho následující příklad používá globální instanci <xref:System.Runtime.InteropServices.GCHandle> aby delegát nebylo přemístěné, nezávisle na rozsahu funkce. Jak je popsáno v prvním příkladu, pomocí pin_ptr není nutný pro tyto příklady, ale v takovém případě by přesto fungovat, protože rozsah pin_ptr je omezený na jedné funkce.  
  
```  
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
  
## <a name="see-also"></a>Viz také  
 [Pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)