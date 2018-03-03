---
title: "-MANIFESTUAC (vložené informace UAC v manifestu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
dev_langs:
- C++
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 564c17336936866750d05137a7bcd101b3a6534d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (vložené informace UAC v manifestu)
Určuje, zda je v manifestu program vložených informace řízení uživatelských účtů (UAC).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/MANIFESTUAC  
/MANIFESTUAC:NO  
/MANIFESTUAC:fragment  
/MANIFESTUAC:level=_level  
/MANIFESTUAC:uiAccess=_uiAccess  
```  
  
#### <a name="parameters"></a>Parametry  
 `fragment`  
 Řetězec, který obsahuje `level` a `uiAccess` hodnoty. Další informace najdete v části poznámky později v tomto tématu.  
  
 `_level`  
 Jeden z *asInvoker*, *highestAvailable*, nebo *requireAdministrator*. Výchozí hodnota je asInvoker. Další informace najdete v části poznámky později v tomto tématu.  
  
 `_uiAccess`  
 `true`Pokud chcete, aby obešla úrovních ochrany uživatelské rozhraní a jednotky vstup do windows vyšší oprávnění na ploše; v opačném `false`. Použije se výchozí hodnota `false`. Nastavte na `true` pouze pro uživatelské rozhraní usnadnění aplikace.  
  
## <a name="remarks"></a>Poznámky  
 Pokud zadáte více možností /MANIFESTUAC na příkazovém řádku, byl naposledy zadali přednost.  
  
 Volby /MANIFESTUAC:level jsou následující:  
  
-   `asInvoker`: Aplikace spustí se stejnými oprávněními jako proces, který spustil. Aplikace může být se zvýšenými oprávněními na vyšší úroveň oprávnění výběrem **spustit jako správce**.  
  
-   highestAvailable: bude aplikace spuštěna s nejvyšší úrovní oprávnění, která ji můžete. Pokud uživatel, který spustí aplikaci, která je členem skupiny Administrators, tato možnost je stejný jako requireAdministrator. Pokud na nejvyšší úrovni oprávnění k dispozici je vyšší než úroveň proces otevírání, systém zobrazí výzvu pro přihlašovací údaje.  
  
-   requireAdministrator: aplikace spustí s oprávněními správce. Uživatel, který spustí aplikaci, musí být členem skupiny Administrators. Pokud proces otevírání není spuštěn s oprávněními pro správu, systém zobrazí výzvu pro přihlašovací údaje.  
  
 Můžete zadat hodnoty úroveň a uiAccess v jednom kroku pomocí možnosti /MANIFESTUAC:fragment. Fragment musí mít následující tvar:  
  
```  
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"  
```  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **souboru Manifest** stránku vlastností.  
  
5.  Změnit **povolit řízení uživatelských účtů (UAC)**, **úroveň spuštění nástroje Řízení uživatelských účtů**, a **ochrany uživatelského rozhraní nástroje Řízení uživatelských účtů nepoužívat** vlastnosti.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
1.  V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A>, a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)