---
title: /NXCOMPAT (kompatibilní s předcházením spuštění dat)
ms.date: 12/29/2017
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: a8550337189f9c92a1c8a8d86f2f9b2b829bbc3e
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813315"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (kompatibilní s předcházením spuštění dat)

Označuje, že spustitelný soubor je kompatibilní s funkcí Zabránění spuštění dat Windows.

## <a name="syntax"></a>Syntaxe

> **/NXCOMPAT**[**:NO**]

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení **/NXCOMPAT** zapnutý.

**: No** umožňuje explicitní zadání spustitelného souboru jako nekompatibilního s prevencí spuštění dat.

Další informace o zabránění spuštění dat najdete v těchto článcích:

- [Podrobný popis funkce Zabránění spuštění dat (DEP)](https://support.microsoft.com/help/875352/a-detailed-description-of-the-data-execution-prevention-dep-feature-in)

- [Zabránění spuštění dat](/windows/desktop/Memory/data-execution-prevention)

- [Zabránění spuštění dat (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio

1. Otevřete projekt **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Zvolte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte parametr do **další možnosti** pole. Zvolte **OK** nebo **použít** na použití změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
