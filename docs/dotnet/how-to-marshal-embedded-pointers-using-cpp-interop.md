---
title: "Postupy: zařazení vložených ukazatelů pomocí zprostředkovatele komunikace C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- structures [C++], marshaling embedded pointers
- interop [C++], embedded pointers
- C++ Interop, embedded pointers
- marshaling [C++], embedded pointers
- pointers [C++], marshaling
- data marshaling [C++], embedded pointers
ms.assetid: 05fb8858-97f2-47aa-86b2-2c0ad713bdb2
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3916d80089d78925b6b5746146490f901c093c09
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-marshal-embedded-pointers-using-c-interop"></a>Postupy: Zařazení vložených ukazatelů pomocí zprostředkovatele komunikace C++
Následující příklady kódu používají [spravované, nespravované](../preprocessor/managed-unmanaged.md) direktivy jazyka #pragma k implementaci spravovaných a nespravovaných funkcí ve stejném souboru, ale tyto funkce spolupracují stejným způsobem, pokud jsou definovány v samostatné soubory. Soubory obsahující pouze nespravovaná funkce nemusí být zkompilovány s [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak lze volat nespravované funkci, která přebírá strukturu obsahující ukazatele ze spravované funkce. Spravovaná funkce vytvoří instanci struktury a inicializuje vložený ukazatel s new – klíčové slovo (místo [nové, gcnew ref](../windows/ref-new-gcnew-cpp-component-extensions.md) – klíčové slovo). Protože to přidělí paměť na nativní haldě, není nutné připnout pole pro potlačení uvolňování paměti. Paměť však musí být explicitně odstranit, aby se zabránilo úniku paměti.  
  
```  
// marshal_embedded_pointer.cpp  
// compile with: /clr  
#include <iostream>  
  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
// unmanaged struct  
struct ListStruct {  
   int count;  
   double* item;  
};  
  
#pragma unmanaged  
  
void UnmanagedTakesListStruct(ListStruct list) {  
   printf_s("[unmanaged] count = %d\n", list.count);  
   for (int i=0; i<list.count; i++)  
      printf_s("array[%d] = %f\n", i, list.item[i]);  
}  
  
#pragma managed  
  
int main() {  
   ListStruct list;  
   list.count = 10;  
   list.item = new double[list.count];  
  
   Console::WriteLine("[managed] count = {0}", list.count);  
   Random^ r = gcnew Random(0);  
   for (int i=0; i<list.count; i++) {  
      list.item[i] = r->NextDouble() * 100.0;  
      Console::WriteLine("array[{0}] = {1}", i, list.item[i]);  
   }  
  
   UnmanagedTakesListStruct( list );  
   delete list.item;  
}  
```  
  
```Output  
[managed] count = 10  
array[0] = 72.624326996796  
array[1] = 81.7325359590969  
array[2] = 76.8022689394663  
array[3] = 55.8161191436537  
array[4] = 20.6033154021033  
array[5] = 55.8884794618415  
array[6] = 90.6027066011926  
array[7] = 44.2177873310716  
array[8] = 97.754975314138  
array[9] = 27.370445768987  
[unmanaged] count = 10  
array[0] = 72.624327  
array[1] = 81.732536  
array[2] = 76.802269  
array[3] = 55.816119  
array[4] = 20.603315  
array[5] = 55.888479  
array[6] = 90.602707  
array[7] = 44.217787  
array[8] = 97.754975  
array[9] = 27.370446  
```  
  
## <a name="see-also"></a>Viz také  
 [Pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)