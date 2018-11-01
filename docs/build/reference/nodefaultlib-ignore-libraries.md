---
title: /NODEFAULTLIB (Ignorovat knihovny)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLinkerTool.OVERWRITEDefaultLibraryNames
- /nodefaultlib
helpviewer_keywords:
- default libraries, removing
- -NODEFAULTLIB linker option
- libraries, ignore
- NODEFAULTLIB linker option
- /NODEFAULTLIB linker option
- ignore libraries linker option
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
ms.openlocfilehash: 12a6e988828d1e4e2dbdc46d49da5ff2fe9e9d8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50473772"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (Ignorovat knihovny)

```
/NODEFAULTLIB[:library]
```

## <a name="arguments"></a>Arguments

*Knihovna*<br/>
Knihovna, která má linkeru, aby ignorovat při překladu externích odkazů.

## <a name="remarks"></a>Poznámky

Parametr/NODEFAULTLIB přikazuje linkeru, aby odebral jednu nebo více výchozích knihoven ze seznamu knihoven, které prohledává při překladu externích odkazů.

Soubor .obj, který obsahuje odkazy na výchozích knihoven, které vytvoříte pomocí [/Zl (vynechání názvu výchozí knihovny)](../../build/reference/zl-omit-default-library-name.md).

Ve výchozím nastavení odebere se: / NODEFAULTLIB všechny výchozí knihovny ze seznamu knihoven, které prohledává při překladu externích odkazů. Volitelný *knihovny* parametr umožňuje odebrat zadanou knihovnu nebo knihoven ze seznamu knihoven, které prohledává při překladu externích odkazů. Zadejte jednu z možností: / NODEFAULTLIB. pro každou knihovnu, kterou chcete vyloučit.

Linker řeší odkazy na externí definice tak, že nejprve v knihovnách, která explicitně zadáte, pak ve výchozích knihoven zadaný pomocí možnosti /DEFAULTLIB a ve výchozích knihoven, které s názvem v souborech .obj.

/ NODEFAULTLIB:*knihovny* přepíše [/DEFAULTLIB:](../../build/reference/defaultlib-specify-default-library.md)*knihovny* při stejné *knihovny* název je zadán v obou.

Pokud používáte parametr/NODEFAULTLIB, například k vytvoření programu bez knihovny run-time jazyka C, budete muset použít také [/Entry](../../build/reference/entry-entry-point-symbol.md) k určení vstupního bodu (funkce) ve svém programu. Další informace najdete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vstup**stránku vlastností.

1. Vyberte **ignorovat všechny výchozí knihovny** vlastnost, nebo zadejte seznam knihoven chcete ignorovat v **ignorovat konkrétní knihovnu** vlastnost. **Příkazového řádku** stránky vlastností zobrazí změny provedené v těchto vlastností.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)