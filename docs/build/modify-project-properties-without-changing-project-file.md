---
title: 'Postupy: Úprava vlastností a cílů projektu C++ beze změny souboru projektu'
ms.date: 11/28/2018
helpviewer_keywords:
- project properties [C++], modifying outside project file
ms.openlocfilehash: 72107b572e35f222c0b03959e0edd2d23bd0130a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328465"
---
# <a name="how-to-modify-c-project-properties-and-targets-without-changing-the-project-file"></a>Postupy: Úprava vlastností a cílů projektu C++ beze změny souboru projektu

Vlastnosti projektu a cíle lze přepsat z příkazového řádku MSBuild bez změny souboru projektu. To je užitečné, pokud chcete některé vlastnosti dočasně nebo občas použít. Předpokládá několik znalostí nástroje MSBuild. Další informace najdete v tématu [MSBUild](https://docs.microsoft.com/visualstudio/msbuild/msbuild).

> [!IMPORTANT]
> Můžete použít editor XML v aplikaci Visual Studio nebo libovolný textový editor pro vytvoření souboru. props nebo. targets. Nepoužívejte **Správce vlastností** v tomto scénáři, protože přidává vlastnosti do souboru projektu.

*Přepsání vlastností projektu:*

1. Vytvořte soubor. props, který určuje vlastnosti, které chcete přepsat.

1. Z příkazového řádku: set ForceImportBeforeCppTargets = "C:\sources\ my_props. props"

*Přepsání cílů projektu:*

1. Vytvoření souboru. targets s jejich implementací nebo konkrétním cílem

2. Z příkazového řádku: set ForceImportAfterCppTargets = "C:\sources\ my_target. targets"

Můžete také nastavit buď možnost v příkazovém řádku MSBuild pomocí možnosti/p:

```cmd
> msbuild myproject.sln /p:ForceImportBeforeCppTargets="C:\sources\my_props.props"
> msbuild myproject.sln /p:ForceImportAfterCppTargets="C:\sources\my_target.targets"
```

Přepsání vlastností a cílů tímto způsobem odpovídá přidání následujících importů do všech souborů. vcxproj v řešení:

```cmd
<Import Project=="C:\sources\my_props.props" />
<Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
<Import Project==" C:\sources\my_target.targets"" />
```
