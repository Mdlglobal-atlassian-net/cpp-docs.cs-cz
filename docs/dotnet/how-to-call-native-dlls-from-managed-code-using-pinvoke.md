---
title: "Postupy: volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- platform invoke [C++], calling native DLLs
- interop [C++], calling native DLLs
- marshaling [C++], calling native DLLs
- data marshaling [C++], calling native DLLs
ms.assetid: 3273eb4b-38d1-4619-92a6-71bda542be72
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5d22f493a582b6ef09615f94c7b321a7cc535e5b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-call-native-dlls-from-managed-code-using-pinvoke"></a>Postupy: Volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke
Funkce, které jsou implementované v nespravované knihovny DLL lze volat ze spravovaného kódu pomocí funkce pro vyvolání platformy (P/Invoke). Pokud zdrojový kód pro knihovnu DLL není k dispozici, P/Invoke je jedinou možností pro spolupráci. Na rozdíl od jiných jazyků .NET, poskytuje Visual C++ alternativu k P/Invoke. Další informace najdete v tématu [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá Win32 [GetSystemMetrics](http://msdn.microsoft.com/library/windows/desktop/ms724385) funkce načíst aktuální rozlišení obrazovky v pixelech.  
  
 Pro funkce, které používají pouze vnitřní typy jako argumenty a návratové hodnoty nejsou vyžadované žádné další kroky. Jiné datové typy, jako jsou ukazatele na funkce, pole a struktury, vyžadují další atributy, které zajistí řádné zařazování dat.  
  
 I když to není nutné, je vhodné zajistit P/Invoke deklarace statické členy třídy hodnot, takže neexistují v globálním oboru názvů, jak je ukázáno v tomto příkladu.  
  
```  
// pinvoke_basic.cpp  
// compile with: /clr  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
value class Win32 {  
public:  
   [DllImport("User32.dll")]  
   static int GetSystemMetrics(int);  
  
   enum class SystemMetricIndex {  
      // Same values as those defined in winuser.h.  
      SM_CXSCREEN = 0,  
      SM_CYSCREEN = 1  
   };  
};  
  
int main() {  
   int hRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CXSCREEN) );  
   int vRes = Win32::GetSystemMetrics( safe_cast<int>(Win32::SystemMetricIndex::SM_CYSCREEN) );  
   Console::WriteLine("screen resolution: {0},{1}", hRes, vRes);  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)