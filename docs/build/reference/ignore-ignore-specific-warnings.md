---
title: "-Ignorovat (ignorovat konkrétní varování) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /OVERWRITE
dev_langs: C++
helpviewer_keywords: /IGNORE linker option
ms.assetid: 37e77387-8838-4697-898f-d376ac641124
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0d8815438ce56629bd120c30b0d0db9fef96916d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ignore-ignore-specific-warnings"></a>/IGNORE (Ignorovat konkrétní varování)
```  
/IGNORE:warning[,warning]  
```  
  
## <a name="parameters"></a>Parametry  
 `warning`  
 Počet upozornění pro potlačení v rozsahu 4000 do 4999 linkeru.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení sestavy odkaz všech upozornění. Zadejte **/ignorovat:** `warning` říct linkeru pro potlačení specifické číslo upozornění. Několik upozornění ignorovat, čísla upozornění oddělujte čárkami.  
  
 Linkeru neumožňuje některé upozornění ignorovat. Tato tabulka uvádí upozornění, která nejsou potlačit pomocí **/Ignorovat**:  
  
|Upozornění linkerů||  
|--------------------|-|  
|LNK4017|`keyword`příkaz není podporován pro cílovou platformu; Ignorovat|  
|[LNK4044](../../error-messages/tool-errors/linker-tools-warning-lnk4044.md)|Nerozpoznaný možnost '`option`'; ignorováno|  
|LNK4062|'`option`'není kompatibilní s'`architecture`se cílový počítač; možnost Ignorovat|  
|[LNK4075](../../error-messages/tool-errors/linker-tools-warning-lnk4075.md)|ignoruje "`option1`"kvůli na"`option2`" specifikace|  
|[LNK4086](../../error-messages/tool-errors/linker-tools-warning-lnk4086.md)|EntryPoint '`function`'není __stdcall s'`number`' bajtů argumenty; bitová kopie nemusí fungovat.|  
|LNK4088|Obrázek generován z důvodu/Force – možnost; bitová kopie nemusí fungovat.|  
|[LNK4105](../../error-messages/tool-errors/linker-tools-warning-lnk4105.md)|žádný argument zadaný s možností "`option`'; bude ignorována přepínače|  
|LNK4203|Chyba při čtení databáze programu '`filename`'; propojování objektů, jako kdyby žádné informace o ladění|  
|[LNK4204](../../error-messages/tool-errors/linker-tools-warning-lnk4204.md)|'`filename`' chybí ladicí informace pro odkazování na modulu; propojování objektů, jako kdyby žádné informace o ladění|  
|[LNK4205](../../error-messages/tool-errors/linker-tools-warning-lnk4205.md)|'`filename`' chybí aktuální informace o ladění pro odkazování na modulu; propojování objektů, jako kdyby žádné informace o ladění|  
|[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)|informace o předkompilovaných typu nebyl nalezen. '`filename`' není propojené nebo přepsána; propojování objektů, jako kdyby žádné informace o ladění|  
|LNK4207|'`filename`' zkompilovat /Yc /Yu /Z7; nelze vytvořit PDB; spojující objekt a pak ji znovu zkompilovat s /Zi, jako kdyby žádné informace o ladění|  
|LNK4208|kompatibilní formát PDB v '`filename`'; odstranit a znovu sestavte; propojování objektů, jako kdyby žádné informace o ladění|  
|LNK4209|informace o ladění poškozený; znovu zkompiluje modulu; propojování objektů, jako kdyby žádné informace o ladění|  
|[LNK4224](../../error-messages/tool-errors/linker-tools-warning-lnk4224.md)|`option`již není podporována; Ignorovat|  
|LNK4228|'`option`se ignoruje; neplatná pro knihovny DLL|  
|[LNK4229](../../error-messages/tool-errors/linker-tools-warning-lnk4229.md)|Neplatná direktiva /`directive` ignorován; najít|  
  
 Obecně platí upozornění linkeru, které nelze ignorovat představují selhání sestavení, chyby příkazového řádku či chyby konfigurace, které problém byste měli odstranit.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  V **Linkeru** složky, vyberte **příkazového řádku** stránku vlastností.  
  
3.  Změnit **další možnosti** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.