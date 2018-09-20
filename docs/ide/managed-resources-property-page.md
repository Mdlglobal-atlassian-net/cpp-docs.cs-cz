---
title: Spravovat stránky vlastností prostředků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
dev_langs:
- C++
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 687203787bdab69751aabf0672fe1269974b3014
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399601"
---
# <a name="managed-resources-property-page"></a>Stránka vlastností spravovaných zdrojů

Povolí nastavení pro kompilátor prostředků.

**Spravovaných prostředků** stránka vlastností obsahuje následující vlastnosti:

- **Logický název prostředku**

   Určuje, *logický název* z vygenerované přechodového souboru .resources. Logický název je název používaný k načtení prostředku. Pokud není zadán žádný logický název, název souboru prostředku (RESX) se používá jako logický název.

- **Název výstupního souboru**

   Určuje název konečného výstupního souboru, jež přispívají k souboru prostředku (RESX).

- **Výchozí lokalizované prostředky**

   Určuje, zda soubor daného .resx přispívá do výchozích prostředků nebo satelitní knihovna .dll.

Informace o tom, jak získat přístup **spravovaných prostředků** stránky vlastností naleznete v tématu [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).

## <a name="see-also"></a>Viz také

[Pomocí RC (RC příkazového řádku)](/windows/desktop/menurc/using-rc-the-rc-command-line-)<br>
[Stránky vlastností](../ide/property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE (vložení spravovaného prostředku)](../build/reference/assemblyresource-embed-a-managed-resource.md)