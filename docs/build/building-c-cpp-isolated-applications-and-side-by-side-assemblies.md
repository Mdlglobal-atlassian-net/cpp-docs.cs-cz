---
title: Sestavení izolovaných aplikací C/C++ a souběžných sestavení
ms.date: 11/04/2016
helpviewer_keywords:
- isolated applications [C++]
- WinSxS [C++]
- native assembly cache [C++]
- builds [C++], isolated applications
- side-by-side applications [C++]
- builds [C++], side-by-side assemblies
ms.assetid: 9465904e-76f7-48bd-bb3f-c55d8f1699b6
ms.openlocfilehash: b962796c3bf32bc312d3047535ae90a40a37094d
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58772459"
---
# <a name="building-cc-isolated-applications-and-side-by-side-assemblies"></a>Sestavení izolovaných aplikací C/C++ a souběžných sestavení

Jazyk Visual C++ podporuje model nasazení pro klientské aplikace Windows podle představu o [izolovaných aplikací](/windows/desktop/SbsCs/isolated-applications) a [sestavení vedle sebe](/windows/desktop/SbsCs/about-side-by-side-assemblies-). Ve výchozím nastavení, Visual C++ sestavení všech nativních aplikací C/C++ jako izolované aplikace, které používají [manifesty](/windows/desktop/sbscs/manifests) k popisu jejich závislosti v knihovnách jazyka Visual C++.

Sestavování programů jazyka C/C++ jako izolované aplikace nabízí řadu výhod. Izolované aplikace je například to neovlivní, když jiné aplikace C/C++ instalace nebo odinstalace knihoven Visual C++. Knihovny Visual C++ používá izolované aplikace možné distribuovat stále v buď místní složce aplikace nebo po instalaci do mezipaměti nativních sestavení (WinSxS); ale obsluhu knihoven Visual C++ pro již nasazené aplikace se dá zjednodušit pomocí [konfigurační soubor vydavatele](/windows/desktop/SbsCs/publisher-configuration). Izolované aplikační model nasazení je snazší zajistit, že aplikace C/C++, které jsou spuštěny v určitém počítači použít nejnovější verzi knihovny Visual C++, přičemž stále otevřete možnost pro správce systému a aplikace autorům určit, vázání verze explicitní aplikací na jejich závislé knihovny DLL.

Tato část popisuje, jak můžete svou aplikaci C/C++ jako izolované aplikace a ujistěte se, že vytvoří vazbu s knihovnami Visual C++ pomocí manifestu. Informace v této části především se vztahuje na nativní, nebo nespravované, aplikace Visual C++. Informace o nasazení nativních aplikací vytvořených v jazyce Visual C++, naleznete v tématu [Redistribuce souborů Visual C++](../windows/redistributing-visual-cpp-files.md).

## <a name="in-this-section"></a>V tomto oddílu

[Koncept izolovaných aplikací a souběžných sestavení](concepts-of-isolated-applications-and-side-by-side-assemblies.md)

[Sestavení izolovaných aplikací C/C++](building-c-cpp-isolated-applications.md)

[Sestavení souběžných sestavení C/C++](building-c-cpp-side-by-side-assemblies.md)

[Postupy: Sestavení součástí modelu COM bez registrace](how-to-build-registration-free-com-components.md)

[Postupy: Sestavení izolovaných aplikací pro zpracování součástí modelu COM](how-to-build-isolated-applications-to-consume-com-components.md)

[Základní informace o generování manifestu pro programy C/C++](understanding-manifest-generation-for-c-cpp-programs.md)

[Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními](troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

## <a name="related-sections"></a>Související oddíly

[Izolované aplikace a sestavení vedle sebe](/windows/desktop/SbsCs/isolated-applications-and-side-by-side-assemblies-portal)

[Nasazení aplikací klasické pracovní plochy](../windows/deploying-native-desktop-applications-visual-cpp.md)