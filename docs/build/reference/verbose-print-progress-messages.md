---
title: /VERBOSE (tisk zpráv průběhu)
ms.date: 11/04/2016
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
ms.openlocfilehash: 7aed1e17034b40ffdad4da4136fc5a64361b3d77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317299"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (tisk zpráv průběhu)

```
/VERBOSE[:{ICF|INCR|LIB|REF|SAFESEH|UNUSEDLIBS}]
```

## <a name="remarks"></a>Poznámky

Linker odesílá informace o průběhu relace propojení do **výstup** okna. Na příkazovém řádku informace odeslány na standardní výstup a je možné přesměrovat do souboru.

|Možnost|Popis|
|------------|-----------------|
|/ VERBOSE|Zobrazí podrobnosti o procesu propojení.|
|/ VERBOSE: ICF|Zobrazení informací o činnosti linkeru, která je výsledkem použití [/OPT:ICF](opt-optimizations.md).|
|/ VERBOSE: INCR|Zobrazí informace o zpracování dílčích propojení.|
|/ VERBOSE: LIB|Zobrazuje zprávy o průběhu označující jenom knihovny prohledávat.<br /><br /> Zobrazené informace obsahuje proces hledání knihovny a uvádí názvy jednotlivých knihoven a objektů (s úplnou cestou), symbolu překládaného z knihovny a seznam objektů, které odkazují na symbol.|
|/ VERBOSE: REF|Zobrazí informace o činnosti linkeru, která je výsledkem použití [OPT](opt-optimizations.md).|
|/ VERBOSE: SAFESEH|Zobrazí informace o modulech, které nejsou kompatibilní s bezpečného při zpracování výjimek [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) není zadán.|
|/ VERBOSE: UNUSEDLIBS|Zobrazí informace o všech souborech knihoven, které nejsou používány při vytvoření image.|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **Linkeru** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. Přidat možnost **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
