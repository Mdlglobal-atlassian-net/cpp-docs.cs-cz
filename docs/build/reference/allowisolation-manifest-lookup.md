---
title: -ALLOWISOLATION (vyhledání manifestu) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
dev_langs:
- C++
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62f467ff467d785d17601737436e0eb1ff972f37
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205490"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (vyhledání manifestu)
Určuje chování při vyhledávání manifestu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/ALLOWISOLATION[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 **/ALLOWISOLATION:No** označuje knihovny DLL se načítají, jako kdyby byl žádný manifest a způsobí, že nastaví linker `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` bit ve volitelné hlavičce `DllCharacteristics` pole.  
  
 **/ ALLOWISOLATION** způsobí, že operační systém k vyhledání a načtení manifestu.  
  
 **/ ALLOWISOLATION** je výchozí nastavení.  
  
 Izolace zakázán pro spustitelný soubor, zavaděč Windows nebude pokoušet najít manifest aplikace pro nově vytvořený procesu. Nový proces nebude mít výchozí aktivační kontext, i v případě manifestu do spustitelného souboru nebo umístěný ve stejném adresáři jako spustitelný soubor s názvem <em>název spustitelného souboru</em>**. exe.manifest**.  
  
 Další informace najdete v tématu [referenční příručka souborů manifestu](/windows/desktop/SbsCs/manifest-files-reference).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **Linkeru** uzlu.  
  
4.  Vyberte **soubor manifestu** stránku vlastností.  
  
5.  Upravit **Povolit izolaci** vlastnost.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)