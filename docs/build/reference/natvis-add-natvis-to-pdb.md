---
title: -NATVIS (přidání Natvisu do souboru PDB) | Dokumentace Microsoftu
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
ms.openlocfilehash: 2c1a20fef785c0267eb630bf044c8cb9609605e2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708120"
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS (přidání Natvisu do souboru PDB)

> / NATVIS:*název souboru*

## <a name="parameters"></a>Parametry

*Název souboru*<br/>
Soubor Natvis pro přidání do souboru PDB. Vizualizace ladicího programu v souboru Natvis se vloží do PDB.

## <a name="remarks"></a>Poznámky

Možnost /NATVIS vloží vizualizace ladicího programu, které jsou definovány v souboru Natvis *filename* do souboru PDB generovaných odkaz. To umožňuje ladicí program zobrazí se vizualizace bez ohledu na jejich souboru .natvis. Více možností /NATVIS můžete vložit více než jeden soubor Natvis generovaného souboru PDB.

ODKAZ ignoruje /NATVIS při soubor PDB nebyl vytvořen pomocí [/DEBUG](../../build/reference/debug-generate-debug-info.md) možnost. Informace o vytváření a používání soubory .natvis, naleznete v tématu [vytváření vlastních zobrazení nativních objektů v ladicím programu sady Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **příkazového řádku** stránku vlastností v **Linkeru** složky.

1. Přidat možnost /NATVIS **další možnosti** textového pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Tato možnost nemá programový ekvivalent.

## <a name="see-also"></a>Viz také

[Vytváření vlastních zobrazení nativních objektů v ladicím programu sady Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects)<br/>
[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)