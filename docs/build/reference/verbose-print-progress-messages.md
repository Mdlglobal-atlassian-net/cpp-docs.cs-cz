---
title: /VERBOSE (tisk zpráv o průběhu)
ms.date: 06/13/2019
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
ms.openlocfilehash: bbf7b5966c741535f26202979cbfd71f839cc537
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141671"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (tisk zpráv o průběhu)

Zprávy o průběhu výstupy během procesu propojení.

## <a name="syntax"></a>Syntaxe

> **/VERBOSE**\[ **:** {**CLR**|**ICF**|**INCR**|**LIB**|**REF**|**SAFESEH**|**UNUSEDDELAYLOAD**|**UNUSEDLIBS**}\]

## <a name="remarks"></a>Poznámky

Linker odesílá informace o průběhu relace propojení do **výstup** okna. Na příkazovém řádku informace odeslány na standardní výstup a je možné přesměrovat do souboru.

| Možnost | Popis |
| ------------ | ----------------- |
| / VERBOSE | Zobrazí podrobnosti o procesu propojení. |
| / VERBOSE: CLR | Zobrazí informace o činnosti linkeru, které jsou specifické pro objekty a metadata zkompilován s použitím [/CLR](clr-common-language-runtime-compilation.md). |
| / VERBOSE: ICF | Zobrazí informace o činnosti linkeru, která je výsledkem použití [/OPT:ICF](opt-optimizations.md). |
| / VERBOSE: INCR | Zobrazí informace o zpracování dílčích propojení. |
| / VERBOSE: LIB | Zobrazuje zprávy o průběhu označující jenom knihovny prohledávat.<br/> Zobrazené informace obsahuje proces hledání knihovny. Zobrazí názvy jednotlivých knihoven a objektů (s úplnou cestou), symbolu překládaného z knihovny a seznam objektů, které odkazují na symbol. |
| / VERBOSE: REF | Zobrazí informace o činnosti linkeru, která je výsledkem použití [OPT](opt-optimizations.md). |
| / VERBOSE: SAFESEH | Zobrazí informace o modulech, které nejsou kompatibilní s bezpečného při zpracování strukturovaných výjimek [/SAFESEH](safeseh-image-has-safe-exception-handlers.md) není zadán. |
| / VERBOSE: UNUSEDDELAYLOAD | Zobrazí informace o případné zpoždění načtené knihovny DLL, které mají žádné symboly použité při vytvoření image. |
| / VERBOSE: UNUSEDLIBS | Zobrazí informace o všech souborech knihoven, které nejsou používány při vytvoření image. |

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Přidat možnost **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
