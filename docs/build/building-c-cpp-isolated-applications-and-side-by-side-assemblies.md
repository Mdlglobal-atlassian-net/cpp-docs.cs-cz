---
title: Sestavení izolovaných aplikací C/C++ a souběžných sestavení
ms.date: 05/06/2019
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: db2978c054362b6c329fb786d0f7da322d4c9201
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80169874"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Sestavení izolovaných aplikací C/C++ a souběžných sestavení

Visual Studio podporuje model nasazení pro klientské aplikace systému Windows na základě nápadu [izolovaných aplikací](/windows/win32/SbsCs/isolated-applications) a [souběžných sestavení](/windows/win32/SbsCs/about-side-by-side-assemblies-). Ve výchozím nastavení Visual Studio sestaví všechny nativní aplikace C/C++ jako izolované aplikace, které používají [manifesty](/windows/win32/sbscs/manifests) k popisu jejich závislostí na Visual C++ch knihoven.

Sestavování programů C/C++ jako izolovaných aplikací představuje řadu výhod. Například izolovaná aplikace není ovlivněná, pokud jiné aplikace C/C++ instalují nebo odinstalují knihovny Visual C++. Knihovny Visual C++ používané izolovanými aplikacemi mohou být nadále distribuovány buď v místní složce aplikace, nebo instalací do nativní mezipaměti sestavení (WinSxS). Obsluha Visual C++ch knihoven pro již nasazené aplikace se však může zjednodušit pomocí [konfiguračního souboru vydavatele](/windows/win32/SbsCs/publisher-configuration). Model nasazení izolovaných aplikací usnadňuje zajištění, že aplikace C/C++, které jsou spuštěny v určitém počítači, používají nejnovější verzi Visual C++ knihoven, a zároveň opouští možnost pro správce systému a autory aplikací řízení explicitních vazeb verzí aplikací na jejich závislé knihovny DLL.

Tato část popisuje, jak můžete sestavit aplikaci jazyka C/C++ jako izolovanou aplikaci a zajistit, aby se váže k Visual C++ knihoven pomocí manifestu. Informace v této části se týkají především nativních nebo nespravovaných aplikací v jazyce C++. Informace o nasazení nativních aplikací v jazyce C++ vytvořených v aplikaci Visual Studio naleznete v tématu [Redistribuce Visual C++ch souborů](../windows/redistributing-visual-cpp-files.md).

## <a name="in-this-section"></a>V tomto oddílu

[Koncept izolovaných aplikací a souběžných sestavení](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[Sestavení izolovaných aplikací C/C++](building-c-cpp-isolated-applications.md)

[Sestavení souběžných sestavení C/C++](building-c-cpp-side-by-side-assemblies.md)

[Postupy: Sestavení součásti modelu COM bez registrace](how-to-build-registration-free-com-components.md)

[Postupy: Sestavení izolované aplikace pro zpracování součástí modelu COM](how-to-build-isolated-applications-to-consume-com-components.md)

[Základní informace o generování manifestu pro programy C/C++](understanding-manifest-generation-for-c-cpp-programs.md)

[Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>Související oddíly

[Izolované aplikace a souběžná sestavení](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[Nasazení desktopových aplikací](../windows/deploying-native-desktop-applications-visual-cpp.md)
