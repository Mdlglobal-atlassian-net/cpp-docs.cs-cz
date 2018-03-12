---
title: "/ FUNCTIONPADMIN (vytvořit bitovou kopii opravitelnou za provozu) | Microsoft Docs"
ms.custom: 
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: article
f1_keywords:
- /functionpadmin
dev_langs:
- C++
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c941ec7f0e94ba03979c914ddd26b8bd21237369
ms.sourcegitcommit: eb246547c7c9adc7d7ac4083ef09bf6e54dec914
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2018
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Vytvořit bitovou kopii s možností provádění oprav za běhu)

Připraví bitovou kopii pro opravy za provozu.

## <a name="syntax"></a>Syntaxe

> **/FUNCTIONPADMIN**[**:**_space_]  

### <a name="arguments"></a>Arguments

*space*<br/>
Velikost odsazení přidat na začátek jednotlivé funkce v bajtech. Na x86 tato výchozí hodnota je 5 bajtů odsazení a na x64 jako výchozí použije 6 bajtů. Na jiné cíle je třeba zadat hodnotu.

## <a name="remarks"></a>Poznámky

Aby linkeru k vytvoření bitovou kopii opravitelnou za provozu, soubory .obj musí sestavili jsme s [/hotpatch (vytvořit kopii opravitelnou za provozu)](../../build/reference/hotpatch-create-hotpatchable-image.md).

Při kompilování a propojit bitovou kopii pomocí jednoho volání cl.exe, **/hotpatch** znamená **/functionpadmin**.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **Linkeru** > **příkazového řádku** stránku vlastností.

1. Zadejte **/FUNCTIONPADMIN** možnost **další možnosti**. Zvolte **OK** uložte provedené změny.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)
