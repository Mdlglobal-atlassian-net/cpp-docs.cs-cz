---
title: /NATVIS (přidání Natvisu do souboru PDB)
ms.date: 08/10/2017
f1_keywords:
- /natvis
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: a16e320a2f8f946912fef6a354f27f6514a67e29
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439272"
---
# <a name="natvis-add-natvis-to-pdb"></a>/NATVIS (přidání Natvisu do souboru PDB)

> /NATVIS:*název souboru*

## <a name="parameters"></a>Parametry

*Bitmap*<br/>
Soubor Natvis, který se má přidat do souboru PDB. Do souboru PDB vloží vizualizace ladicího programu do souboru Natvis.

## <a name="remarks"></a>Poznámky

Možnost/NATVIS vloží vizualizace ladicího programu definované v souboru Natvis *filename* do souboru PDB GENEROVANÉho odkazem. To umožňuje ladicímu programu zobrazit vizualizace nezávisle na souboru. Natvis. Více možností/NATVIS můžete použít k vložení více než jednoho souboru Natvis do generovaného souboru PDB.

Pokud se soubor PDB nevytvoří pomocí možnosti [/Debug](debug-generate-debug-info.md) , odkaz ignoruje/NATVIS. Informace o vytváření a používání souborů. Natvis najdete v tématu [Vytvoření vlastních zobrazení nativních objektů v ladicím programu sady Visual Studio](/visualstudio/debugger/create-custom-views-of-native-objects).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Ve složce **linkeru** vyberte stránku vlastností **příkazový řádek** .

1. Do textového pole **Další možnosti** přidejte možnost/NATVIS.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Tato možnost nemá programový ekvivalent.

## <a name="see-also"></a>Viz také

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
