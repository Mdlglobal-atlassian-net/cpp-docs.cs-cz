---
title: -NATVIS (přidání Natvis do souboru PDB) | Microsoft Docs
ms.date: 08/10/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
dev_langs:
- C++
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a3bce34095aec1558d2466447770a8ac4c46528f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377099"
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
[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)  
[Možnosti linkeru](../../build/reference/linker-options.md)