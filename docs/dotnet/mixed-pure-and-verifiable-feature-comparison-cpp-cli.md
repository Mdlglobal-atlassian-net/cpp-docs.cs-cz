---
title: Smíšené, čisté a ověřitelné porovnání funkcí (C + +/ CLI) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- safe assemblies [C++], vs. pure
- mixed assemblies [C++], vs. pure
- safe assemblies [C++], vs. mixed
- pure MSIL [C++]
- verifiable assemblies [C++]
- pure MSIL [C++], vs. safe
- pure MSIL [C++], vs. mixed
- pure MSIL [C++], compared to mixed and safe
- verifiable assemblies [C++], vs. mixed
- mixed assemblies [C++], vs. safe
- verifiable assemblies [C++], vs. pure
- pure assemblies [C++]
- safe assemblies [C++]
- mixed assemblies [C++]
ms.assetid: 3f7a82ba-0e69-4927-ba0c-fbc3160e4394
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 201f2eb0979857713848a8c381ef0a31ba179c41
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mixed-pure-and-verifiable-feature-comparison-ccli"></a>Smíšené, čisté a ověřitelné porovnání funkcí (C++/CLI)
Toto téma porovnává funkce mezi různými **/CLR** režimy kompilace. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
## <a name="feature-comparison"></a>Porovnání funkcí  
  
|Funkce|Smíšená (/ clr)|Čistý (/ clr: pure)|Bezpečné (/ CLR: safe)|Související informace|  
|-------------|---------------------|-------------------------|-------------------------|-------------------------|  
|CRT – knihovna|Podporované|zastaralé||[Rutiny UCRT (Universal C runtime) podle kategorie](../c-runtime-library/run-time-routines-by-category.md)|  
|MFC/ATL|Podporované|||[Běžné aplikace knihovny MFC](../mfc/mfc-desktop-applications.md) &#124; [přehled tříd](../atl/atl-class-overview.md)|  
|Nespravované funkce|Podporované|||[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)|  
|Nespravovaná Data|Podporované|zastaralé||[Čistý a ověřitelný kód (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)|  
|Volány z nespravovaných funkcí|Podporované||||  
|Podporuje volání nespravovaných funkcí|Podporované|zastaralé|zastaralé|[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)|  
|Podporuje reflexe|Pouze knihovny DLL|zastaralé|zastaralé|[Reflexe (C++/CLI)](../dotnet/reflection-cpp-cli.md)|  
  
## <a name="see-also"></a>Viz také  
 [Čistý a ověřitelný kód (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)