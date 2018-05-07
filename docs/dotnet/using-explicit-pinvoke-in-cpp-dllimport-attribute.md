---
title: Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- marshaling [C++], platform invoke
- C++ Interop, platform invoke
- interop [C++], platform invoke
- platform invoke [C++], marshaling in C++
- data marshaling [C++], platform invoke
ms.assetid: 18e5218c-6916-48a1-a127-f66e22ef15fc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 82215e4815d25dd116cf930be9cc0f40da761bf8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-explicit-pinvoke-in-c-dllimport-attribute"></a>Použití explicitního volání PInvoke v jazyce C++ (atribut DllImport)
Rozhraní .NET Framework poskytuje funkce explicitního nespravovaného kódu (PInvoke) s `Dllimport` atribut povolit spravovaným aplikacím volat nespravované funkce zabalené uvnitř knihovny DLL. Explicitní PInvoke je vyžadováno v situacích, kdy nespravovaná rozhraní API spojených jako knihovny DLL a zdrojový kód není k dispozici. Volání Win32 funkcí, například vyžaduje PInvoke. Jinak použijte implicitní P {Invoke; viz [pomocí zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md) Další informace.  
  
 PInvoke pracuje pomocí <xref:System.Runtime.InteropServices.DllImportAttribute>. Tento atribut, který přebírá název knihovny DLL jako svůj první argument, je umístěna před deklaraci funkce pro každý vstupní bod knihovny DLL, která bude použita. Podpis funkce musí odpovídat názvu funkce exportované knihovnou DLL (ale některé převody typů můžete provedeny implicitně definováním `DllImport` deklarace z hlediska spravovaných typů.)  
  
 Výsledkem je spravovaný vstupní bod pro každou nativní knihovny DLL funkci, která obsahuje nezbytné přechod code (nebo převodu) a jednoduché datové převody. Potom může volat spravované funkce do knihovny DLL prostřednictvím těchto vstupních bodů. Kód vloženy do modulu jako výsledek PInvoke je zcela spravován.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Volání nativních funkcí ze spravovaného kódu](../dotnet/calling-native-functions-from-managed-code.md)  
  
-   [Postupy: Volání nativních knihoven DLL ze spravovaného kódu pomocí služby PInvoke](../dotnet/how-to-call-native-dlls-from-managed-code-using-pinvoke.md)  
  
-   [Postupy: Zařazení řetězců pomocí služby PInvoke](../dotnet/how-to-marshal-strings-using-pinvoke.md)  
  
-   [Postupy: Zařazení struktur pomocí služby PInvoke](../dotnet/how-to-marshal-structures-using-pinvoke.md)  
  
-   [Postupy: Zařazení polí pomocí služby PInvoke](../dotnet/how-to-marshal-arrays-using-pinvoke.md)  
  
-   [Postupy: Zařazení ukazatelů na funkce pomocí služby PInvoke](../dotnet/how-to-marshal-function-pointers-using-pinvoke.md)  
  
-   [Postupy: Zařazení vložených ukazatelů pomocí služby PInvoke](../dotnet/how-to-marshal-embedded-pointers-using-pinvoke.md)  
  
## <a name="see-also"></a>Viz také  
 [Volání nativních funkcí ze spravovaného kódu](../dotnet/calling-native-functions-from-managed-code.md)