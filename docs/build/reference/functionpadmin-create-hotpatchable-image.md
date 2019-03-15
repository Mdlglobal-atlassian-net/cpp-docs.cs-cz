---
title: /FUNCTIONPADMIN (Vytvořit bitovou kopii s možností provádění oprav za běhu)
ms.date: 03/09/2018
f1_keywords:
- /functionpadmin
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
ms.openlocfilehash: 699da3cea9914b5a10bdf769015d41c33936a902
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818619"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Vytvořit bitovou kopii s možností provádění oprav za běhu)

Připraví bitovou kopii k opravě za provozu.

## <a name="syntax"></a>Syntaxe

> **/ FUNCTIONPADMIN**[**:**_místo_]

### <a name="arguments"></a>Arguments

*space*<br/>
Velikost odsazení přidejte na začátek jednotlivých funkcí v bajtech. Na x86 je výchozí hodnota 5 bajtů odsazení a na x64 to výchozí hodnota je 6 bajtů. Na jiných cílů je nutné zadat hodnotu.

## <a name="remarks"></a>Poznámky

Aby linker vytvoří bitovou kopii opravitelnou za provozu, soubory .obj musí být zkompilovány se [/hotpatch (vytvoření Image vyměnitelné za provozu)](hotpatch-create-hotpatchable-image.md).

Když kompilujete a propojujete obrázek s jednoho vyvolání cl.exe, **/hotpatch** znamená **/functionpadmin**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte **/FUNCTIONPADMIN** možnost **další možnosti**. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také:

[Odkaz na MSVC linkeru](linking.md)<br/>
[Možnosti Linkeru MSVC](linker-options.md)
