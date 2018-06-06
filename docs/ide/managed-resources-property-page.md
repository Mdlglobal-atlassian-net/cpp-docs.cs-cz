---
title: Spravované stránku vlastností zdroje | Microsoft Docs
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
ms.openlocfilehash: 2922a0a92a121d6838478daaf2c32f1c7a630d21
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33340356"
---
# <a name="managed-resources-property-page"></a>Stránka vlastností spravovaných zdrojů
Umožňuje nastavení pro kompilátor prostředků.  
  
 **Spravované prostředky** vlastnost stránka obsahuje následující vlastnosti:  
  
 **Logický název prostředku**  
 Určuje, *logický název* generovaného pomocného zdrojového souboru. Logický název je název sloužící k načtení zdroje. Pokud není zadán žádný logický název, název souboru prostředků (RESX) se používá jako logický název.  
  
 **Název výstupního souboru**  
 Určuje název souboru závěrečný výstup, který souboru prostředků (RESX) přispívá k.  
  
 **Výchozí místní prostředky**  
 Určuje, zda soubor dané .resx přispívá výchozí prostředky nebo satelitní .dll.  
  
 Informace o tom, jak získat přístup **spravované prostředky** stránce vlastností, najdete v části [práce s vlastnostmi projektu](../ide/working-with-project-properties.md).  
  
## <a name="see-also"></a>Viz také  
 [Pomocí RC (RC příkazového řádku)](http://msdn.microsoft.com/library/windows/desktop/aa381055)   
 [Stránky vlastností](../ide/property-pages-visual-cpp.md)   
 [/ASSEMBLYRESOURCE (vložení spravovaného prostředku)](../build/reference/assemblyresource-embed-a-managed-resource.md)