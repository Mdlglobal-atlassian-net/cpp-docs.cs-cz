---
title: 'Postupy: Změna vlastností projektu jazyka C++ a cíle beze změny souboru projektu'
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: ad527d8ee69a1786be7d325571f9c9ac4f9a8574
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273336"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>Postupy: Změna vlastností projektu jazyka C++ a cíle beze změny souboru projektu

Můžete přepsat vlastnosti projektu a cíle z příkazového řádku MSBuild beze změny souboru projektu. To je užitečné, pokud chcete použít některé vlastnosti dočasně nebo čas od času. Předpokládá základní znalost MSBuild. Další informace najdete v tématu [MSBUild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Můžete použít Editor XML v sadě Visual Studio nebo libovolného textového editoru vytvořte soubor PROPS nebo .targets. Nepoužívejte **Správce vlastností** v tomto scénáři protože přidá vlastnosti do souboru projektu.

*K přepsání vlastností projektu:*

1. Vytvořte soubor PROPS, která určuje vlastnosti, které chcete přepsat.

1. Z příkazového řádku: nastavte ForceImportBeforeCppTargets="C:\sources\my_props.props"

*Chcete-li přepsat cíle projektu:*

1. Vytvoření souboru .targets s jejich provádění nebo konkrétní cílový

2. Z příkazového řádku: nastavte ForceImportAfterCppTargets = "C:\sources\my_target.targets"

Můžete také nastavit jednu z možností příkazového řádku msbuild pomocí možnosti/p::

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

Přepsání vlastností a cílů tímto způsobem je ekvivalentní k přidání následující importy do všech souborů .vcxproj v řešení:

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```
