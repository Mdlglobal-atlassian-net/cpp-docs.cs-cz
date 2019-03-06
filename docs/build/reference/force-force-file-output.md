---
title: /FORCE (Vynutit výstup souboru)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: fb5b5b586a9c428d20a7e931a312c8903eb6e8e2
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424467"
---
# <a name="force-force-file-output"></a>/FORCE (Vynutit výstup souboru)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>Poznámky

Parametr/Force přikazuje linkeru, aby vytvořil soubor platný .exe nebo knihovny DLL i v případě, že symbol se odkazuje ale není definované nebo je vynásobit definované.

Parametr/Force může mít nepovinný argument:

- Pomocí /FORCE:MULTIPLE vytvoří výstupní soubor, zda příkaz LINK najde více než jednu definici symbolu nebo nenajde.

- Pomocí parametru/Force: UNRESOLVED se vytvoří výstupní soubor, zda příkaz LINK najde nedefinovaný symbol nebo nenajde. / FORCE: NEROZPOZNANÝ se ignoruje, pokud nevyřešený symbol vstupního bodu.

/ FORCE bez argumentů znamená jak vícenásobné tak nevyřešené.

Soubor vytvořený pomocí této možnosti nebude fungovat podle očekávání. Propojovací program nebude propojují přírůstkově, pokud je zadán parametr/Force.

Pokud modulu je kompilována s **/CLR**, **/FORCE** nevytvoří bitovou kopii.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **příkazového řádku** stránku vlastností.

1. Zadejte možnost do **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
