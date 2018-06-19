---
title: / FUNCTIONPADMIN (vytvořit bitovou kopii opravitelnou za provozu) | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: reference
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
ms.workload:
- cplusplus
ms.openlocfilehash: d0a5ecfcc336e198de0adcc2393f740072d70cae
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376751"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (Vytvořit bitovou kopii s možností provádění oprav za běhu)

Připraví bitovou kopii pro opravy za provozu.

## <a name="syntax"></a>Syntaxe

> **/ FUNCTIONPADMIN**[**:**_místo_]  

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
