---
title: /NXCOMPAT (kompatibilní s předcházením spuštění dat)
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: 7c788f5ec499f0edf0c44f1ff269af9767af6c08
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492667"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (kompatibilní s předcházením spuštění dat)

Označuje, že spustitelný soubor je kompatibilní s funkcí Zabránění spuštění dat systému Windows.

## <a name="syntax"></a>Syntaxe

> **/NXCOMPAT**[ **:NO**]

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení je **/NXCOMPAT** zapnutý.

**/NXCOMPAT: No** se dá použít k explicitnímu zadání spustitelného souboru jako nekompatibilního s zabráněním spuštění dat.

Další informace o zabránění spuštění dat najdete v těchto článcích:

- [Podrobný popis funkce Zabránění spuštění dat (DEP)](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [Zabránění spuštění dat](/windows/win32/Memory/data-execution-prevention)

- [Zabránění spuštění dat (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Podrobnosti najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte stránku vlastností**příkazový řádek** **linkeru** >  **vlastností** > konfigurace.

1. Zadejte možnost do pole **Další možnosti** . Kliknutím na **tlačítko OK** nebo **použít** provedete změnu.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
