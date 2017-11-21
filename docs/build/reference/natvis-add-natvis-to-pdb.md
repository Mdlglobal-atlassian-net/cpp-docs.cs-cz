---
title: "-NATVIS (přidání Natvis do souboru PDB) | Microsoft Docs"
ms.date: 08/10/2017
ms.tgt_pltfrm: 
ms.technology: cpp-tools
ms.topic: article
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs: C++
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 36c1baec22ce0804b4271718dd9495c4213941b3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS (přidání Natvis do souboru PDB)
  
> / NATVIS:*filename*  
  
## <a name="parameters"></a>Parametry  
  
*Název souboru*  
Soubor Natvis přidání do souboru PDB. Vizualizace ladicí program v souboru Natvis se vloží do PDB.  
  
## <a name="remarks"></a>Poznámky  
  
Možnost /NATVIS vloží ladicí program vizualizacemi definované v souboru Natvis *filename* do souboru PDB generované odkaz. To umožňuje zobrazit vizualizacemi nezávisle na soubor .natvis ladicího programu. Více možností /NATVIS můžete vložit více než jeden soubor Natvis vygenerovaný soubor PDB.  
  
ODKAZ /NATVIS ignoruje, pokud soubor PDB nebyl vytvořen pomocí [/DEBUG](../../build/reference/debug-generate-debug-info.md) možnost. Informace o vytváření a používání souborů .natvis najdete v tématu [vytváření vlastních pohledů nativních objektů v ladicím programu sady Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Vyberte **příkazového řádku** stránka vlastností v **Linkeru** složky.  
  
3.  Přidat možnost /NATVIS **další možnosti** textové pole.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   Tato možnost není k dispozici programový ekvivalent.  
  
## <a name="see-also"></a>Viz také  
  
[Vytváření vlastních pohledů nativních objektů v ladicím programu sady Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects)  
[Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)  
[Možnosti linkeru](../../build/reference/linker-options.md)