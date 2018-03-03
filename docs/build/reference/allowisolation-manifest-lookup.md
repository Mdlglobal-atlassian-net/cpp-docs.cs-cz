---
title: "-ALLOWISOLATION (vyhledání manifestu) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d0ca939021a6fc530b11c6ec66fc74cc012da1c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (vyhledání manifestu)
Určuje chování pro vyhledání manifestu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 **/ALLOWISOLATION:No** označuje knihovny DLL se načtou, jako kdyby byl žádný manifest a způsobí, že linkeru nastavit `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bitů v hlavičce volitelné `DllCharacteristics` pole.  
  
 **/ ALLOWISOLATION** způsobí, že operační systém manifest vyhledávání a zatížení.  
  
 **/ ALLOWISOLATION** je výchozí.  
  
 Při izolaci je zakázán pro spustitelný soubor, nebude zavaděč Windows pokus o vyhledání manifest aplikace pro nově vytvořený proces. Nový proces nebude mít výchozí aktivační kontext, i když je v manifestu uvnitř spustitelný soubor nebo umístěný ve stejném adresáři jako spustitelný soubor s názvem *název spustitelného souboru***. exe.manifest**.  
  
 Další informace najdete v tématu [Manifest soubory – referenční dokumentace](http://msdn.microsoft.com/library/aa375632).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **souboru Manifest** stránku vlastností.  
  
5.  Změnit **Povolit izolaci** vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)