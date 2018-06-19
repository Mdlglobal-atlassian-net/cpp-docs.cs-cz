---
title: Sestavení C/C++ izolovaných aplikací a souběžně sdílená sestavení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ca99de7403ad56ae82fdd25af8ff22167084b91
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361281"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Sestavení izolovaných aplikací C/C++ a souběžných sestavení
Visual C++ podporuje model nasazení pro klientské aplikace Windows podle představu o tom [izolovaných aplikací](http://msdn.microsoft.com/library/aa375190) a [souběžně sdílená sestavení](http://msdn.microsoft.com/library/ff951640). Ve výchozím nastavení, Visual C++ sestavení všechny nativní aplikace C/C++ jako izolované aplikace, které používají [manifesty](http://msdn.microsoft.com/library/aa375365) k popisu závislé na knihovny jazyka Visual C++.  
  
 Vytváření programy C/C++ jako izolované aplikace uvede řadu výhod. Izolované aplikace je například neovlivní při dalších aplikací C/C++ instalace nebo odinstalace knihovny jazyka Visual C++. Knihoven Visual C++ používané izolované aplikace stále dále distribuovat v místní složce buď aplikace nebo při instalaci do mezipaměti nativní sestavení (WinSxS); ale obsluhu knihovny jazyka Visual C++ pro již nasazené aplikace můžete zjednodušit pomocí [vydavatele konfigurační soubor](http://msdn.microsoft.com/library/aa375680). Model nasazení izolované aplikace usnadňuje zkontrolujte, jestli aplikace C/C++, které jsou spuštěny v určitém počítači používají nejnovější verzi knihovny jazyka Visual C++, a přesto nechat otevřete možnost pro správce systému a aplikace autorům určit, vazba explicitní verze aplikací a jejich závislé knihovny DLL.  
  
 Tato část popisuje, jak sestavit aplikaci jako izolovaných aplikací C/C++ a ujistěte se, že se váže k knihoven Visual C++ pomocí manifestu. Informace v této části platí především pro nativní nebo nespravované, aplikací Visual C++. Další informace o nasazení nativních aplikací, které jsou vytvořené s nástroji Visual C++, najdete v části [Redistribuce souborů Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Koncept izolovaných aplikací a souběžných sestavení](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)  
  
 [Sestavení izolovaných aplikací C/C++](../build/building-c-cpp-isolated-applications.md)  
  
 [Sestavení souběžných sestavení C/C++](../build/building-c-cpp-side-by-side-assemblies.md)  
  
 [Postupy: Sestavení součástí modelu COM bez registrace](../build/how-to-build-registration-free-com-components.md)  
  
 [Postupy: Sestavení izolovaných aplikací pro zpracování součástí modelu COM](../build/how-to-build-isolated-applications-to-consume-com-components.md)  
  
 [Základní informace o generování manifestu pro programy C/C++](../build/understanding-manifest-generation-for-c-cpp-programs.md)  
  
 [Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)  
  
## <a name="related-sections"></a>Související oddíly  
 [Izolované aplikace a souběžně sdílená sestavení](http://msdn.microsoft.com/library/dd408052)  
  
 [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)