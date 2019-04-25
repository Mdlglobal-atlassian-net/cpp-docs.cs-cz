---
title: / IGNOREIDL (Don&#39;t procesu atributy do MIDL)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.IgnoreEmbeddedIDL
- /ignoreidl
helpviewer_keywords:
- IGNOREIDL linker option
- -IGNOREIDL linker option
- /IGNOREIDL linker option
ms.assetid: 29514098-6a1c-4317-af2f-1dc268972780
ms.openlocfilehash: 210778adecd87ffdd5f2702c10106f12bd5a1b79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291675"
---
# <a name="ignoreidl-don39t-process-attributes-into-midl"></a>/ IGNOREIDL (Don&#39;t procesu atributy do MIDL)

```
/IGNOREIDL
```

## <a name="remarks"></a>Poznámky

/ Ignoreidl Určuje, že všechny [IDL – atributy](../../windows/idl-attributes.md) ve zdroji kódu nemají být zpracovány do souboru IDL.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **vložené IDL** stránku vlastností.

1. Upravit **ignorovat vložené IDL** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreEmbeddedIDL%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)<br/>
[/IDLOUT (pojmenování výstupních souborů MIDL)](idlout-name-midl-output-files.md)<br/>
[/TLBOUT (pojmenování souboru .TLB)](tlbout-name-dot-tlb-file.md)<br/>
[/MIDL (určení možností příkazového řádku MIDL)](midl-specify-midl-command-line-options.md)<br/>
[Sestavení programu s atributy](../../windows/building-an-attributed-program.md)
