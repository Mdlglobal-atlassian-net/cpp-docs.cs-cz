---
title: -WINMD (generování metadat Windows) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
dev_langs:
- C++
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d3e628713c8228675db3b34e70d670c88152462
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376176"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (Generování metadat Windows)
Umožňuje generování metadat Windows Runtime (.winmd) souboru.  
  
```  
/WINMD[:{NO|ONLY}]  
```  
  
## <a name="remarks"></a>Poznámky  
 / WINMD  
 Výchozí nastavení pro aplikace pro univerzální platformu Windows. Linkeru generuje binární spustitelný soubor a soubor metadat .winmd.  
  
 /WINMD:NO  
 Linkeru generuje pouze binární spustitelný soubor, ale nejedná se o soubor .winmd.  
  
 / WINMD: JENOM  
 Linkeru generuje pouze soubor .winmd, ale ne binární spustitelný soubor.  
  
 Ve výchozím nastavení, název výstupního souboru má tvar `binaryname`.winmd. Pokud chcete zadat jiný název souboru, použijte [/WINMDFILE](../../build/reference/winmdfile-specify-winmd-file.md) možnost.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **Linkeru** složky.  
  
3.  Vyberte **metadat Windows** stránku vlastností.  
  
4.  V **generování metadat Windows** rozevíracího seznamu vyberte požadovanou možnost.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)