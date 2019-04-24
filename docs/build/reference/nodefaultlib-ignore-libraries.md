---
title: /NODEFAULTLIB (Ignorovat knihovny)
ms.date: 03/26/2019
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
ms.openlocfilehash: 24528eb4c387c4cd0921ab089370d72b076ad640
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320513"
---
# <a name="nodefaultlib-ignore-libraries"></a>/NODEFAULTLIB (Ignorovat knihovny)

> **/ NODEFAULTLIB**[__:__*knihovny*]

## <a name="arguments"></a>Arguments

*Knihovna*<br/>
Knihovna, která má linkeru, aby ignorovat při překladu externích odkazů.

## <a name="remarks"></a>Poznámky

Parametr/NODEFAULTLIB přikazuje linkeru, aby odebral jednu nebo více výchozích knihoven ze seznamu knihoven, které prohledává při překladu externích odkazů.

K vytvoření souboru .obj, který neobsahuje žádné odkazy na výchozí knihovny, použijte [/Zl (vynechání názvu výchozí knihovny)](zl-omit-default-library-name.md).

Ve výchozím nastavení odebere se: / NODEFAULTLIB všechny výchozí knihovny ze seznamu knihoven, které prohledává při překladu externích odkazů. Volitelný *knihovny* parametr umožňuje odebrat zadanou knihovnu ze seznamu knihoven, které prohledává při překladu externích odkazů. Zadejte jednu z možností: / NODEFAULTLIB. pro každou knihovnu, kterou chcete vyloučit.

Linker řeší odkazy na externí definice tak, že nejprve v knihovnách, která explicitně zadáte, pak ve výchozích knihoven zadaným [/DEFAULTLIB:](defaultlib-specify-default-library.md) možnost, a potom ve výchozích knihoven s názvem v souboru .obj soubory.

/ NODEFAULTLIB:*knihovny* přepíše /DEFAULTLIB:*knihovny* při stejné *knihovny* název je zadán v obou.

Pokud používáte parametr/NODEFAULTLIB k vytvoření programu bez knihovny run-time jazyka C, bude pravděpodobně nutné použít také [/Entry](entry-entry-point-symbol.md) k určení funkce vstupního bodu ve svém programu. Další informace najdete v tématu [funkce knihovny CRT](../../c-runtime-library/crt-library-features.md).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **vstup** stránku vlastností.

1. Vyberte **ignorovat všechny výchozí knihovny** vlastnost. Nebo zadejte středníkem oddělený seznam knihoven, které chcete ignorovat v **ignorovat konkrétní výchozí knihovny** vlastnost. **Příkazového řádku** stránka vlastností zobrazuje změny provedené v těchto vlastností.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A> a <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
