---
title: Stránka vlastností spravovaných zdrojů
ms.date: 08/28/2019
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
ms.openlocfilehash: 14802996e63392bfb5fcc22096ef5f3d9db197c2
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177522"
---
# <a name="managed-resources-property-page"></a>Stránka vlastností spravovaných zdrojů

Stránka vlastností **spravované prostředky** zpřístupňuje při používání prostředků .NET v C++aplikacích/CLI následující vlastnosti spravovaného prostředku, který používá nástroj [Resgen. exe](/dotnet/framework/tools/resgen-exe-resource-file-generator) :

- **Logický název prostředku**

   Určuje *logický název* vygenerovaného zprostředkujícího souboru. Resources. Logický název je název, který se používá k načtení prostředku. Pokud není zadán žádný logický název, použije se jako logický název název souboru prostředků (. resx).

- **Název výstupního souboru**

   Určuje název konečného výstupního souboru, do kterého se má soubor prostředků (. resx) přispěje.

- **Výchozí lokalizované prostředky**

   Určuje, zda daný soubor. resx přispívá do výchozích prostředků nebo satelitní knihovny. dll.

Informace o tom, jak získat přístup ke stránce vlastností **spravovaných prostředků** , najdete v tématu [Nastavení vlastností kompilátoru a sestavení v C++ sadě Visual Studio](../working-with-project-properties.md).

## <a name="see-also"></a>Viz také:

[Použití RC (příkazový řádek RC)](/windows/win32/menurc/using-rc-the-rc-command-line-)<br>
[C++odkaz na stránku vlastností projektu](property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE (vložení spravovaného prostředku)](assemblyresource-embed-a-managed-resource.md)
