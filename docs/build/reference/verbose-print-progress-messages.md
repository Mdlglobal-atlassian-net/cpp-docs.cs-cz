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
ms.openlocfilehash: 41a8ee835a65a7c9a17df9bb9c155267cae29baf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575614"
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
|/ VERBOSE: ICF|Zobrazení informací o činnosti linkeru, která je výsledkem použití [/OPT:ICF](../../build/reference/opt-optimizations.md).|
|/ VERBOSE: INCR|Zobrazí informace o zpracování dílčích propojení.|
|/ VERBOSE: LIB|Zobrazuje zprávy o průběhu označující jenom knihovny prohledávat.<br /><br /> Zobrazené informace obsahuje proces hledání knihovny a uvádí názvy jednotlivých knihoven a objektů (s úplnou cestou), symbolu překládaného z knihovny a seznam objektů, které odkazují na symbol.|
|/ VERBOSE: REF|Zobrazí informace o činnosti linkeru, která je výsledkem použití [OPT](../../build/reference/opt-optimizations.md).|
|/ VERBOSE: SAFESEH|Zobrazí informace o modulech, které nejsou kompatibilní s bezpečného při zpracování výjimek [/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md) není zadán.|
|/ VERBOSE: UNUSEDLIBS|Zobrazí informace o všech souborech knihoven, které nejsou používány při vytvoření image.|

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Rozbalte **Linkeru** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. Přidat možnost **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)