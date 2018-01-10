---
title: "Smíšené, čisté a ověřitelné porovnání funkcí (C + +/ CLI) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3ee9fbed3fd82fd450fd179683fd119cb1630034
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mixed-pure-and-verifiable-feature-comparison-ccli"></a>Smíšené, čisté a ověřitelné porovnání funkcí (C++/CLI)
Toto téma porovnává funkce mezi různými **/CLR** režimy kompilace. Další informace najdete v tématu [/CLR (kompilace Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).  
  
 **/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015.  
  
## <a name="feature-comparison"></a>Porovnání funkcí  
  
|Funkce|Smíšená (/ clr)|Čistý (/ clr: pure)|Bezpečné (/ CLR: safe)|Související informace|  
|-------------|---------------------|-------------------------|-------------------------|-------------------------|  
|CRT – knihovna|Podporované|Podporované||[Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)|  
|MFC/ATL|Podporované|||[Běžné aplikace knihovny MFC](../mfc/mfc-desktop-applications.md) &#124; [Přehled tříd](../atl/atl-class-overview.md)|  
|Nespravované funkce|Podporované|||[Smíšená (nativní a spravovaná) sestavení](../dotnet/mixed-native-and-managed-assemblies.md)|  
|Nespravovaná Data|Podporované|Podporované||[Čistý a ověřitelný kód (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)|  
|Volány z nespravovaných funkcí|Podporované|||[Postupy: přechod na/CLR: pure (C + +/ CLI)](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)|  
|Podporuje volání nespravovaných funkcí|Podporované|Pouze funkce jazyka C|Pouze P/Invoke|[Použití zprostředkovatele komunikace C++ (implicitní služba PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)|  
|Podporuje reflexe|Pouze knihovny DLL|Podporované|Podporované|[Reflexe (C++/CLI)](../dotnet/reflection-cpp-cli.md)|  
  
## <a name="see-also"></a>Viz také  
 [Čistý a ověřitelný kód (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)