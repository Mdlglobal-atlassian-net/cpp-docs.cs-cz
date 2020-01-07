---
title: /NXCOMPAT (kompatibilní s předcházením spuštění dat)
description: Popisuje možnost linkeru MicrosoftC++ C/(MSVC)/NXCOMPAT, která označuje spustitelný soubor jako kompatibilní s funkcí Zabránění spuštění dat (DEP).
ms.date: 12/17/2019
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: f3a0906a49e3524fff3e1ef1643d1eceee28f169
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298984"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (kompatibilní s předcházením spuštění dat)

Označuje, že spustitelný soubor je kompatibilní s funkcí Zabránění spuštění dat systému Windows.

## <a name="syntax"></a>Syntaxe

> **/NXCOMPAT**[ **:NO**]

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je **/NXCOMPAT** zapnutý.

**/NXCOMPAT: No** se dá použít k explicitnímu zadání spustitelného souboru jako nekompatibilního s zabráněním spuštění dat.

Další informace o zabránění spuštění dat najdete v těchto článcích:

- [Zabránění spuštění dat](/windows/win32/Memory/data-execution-prevention)

- [Zabránění spuštění dat (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace** > stránka vlastností **příkazového řádku** > **linkeru** .

1. Zadejte možnost do pole **Další možnosti** . Kliknutím na **tlačítko OK** nebo **použít** provedete změnu.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Podívejte se na téma <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

\ [Referenční příručka linkeru MSVC](linking.md)
[Možnosti linkeru MSVC](linker-options.md)
