---
title: / NATVIS (přidání Natvisu do souboru PDB)
ms.date: 08/10/2017
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: 983cbe4c4bd4164d81b83a23fe19569318d5193c
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424974"
---
# <a name="natvis-add-natvis-to-pdb"></a>/ NATVIS (přidání Natvisu do souboru PDB)

> /NATVIS:*filename*

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

## <a name="see-also"></a>Viz také:

[Vytváření vlastních zobrazení nativních objektů v ladicím programu sady Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects)<br/>
[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
