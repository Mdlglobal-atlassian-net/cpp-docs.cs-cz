---
title: -MACHINE (zadání cílové platformy) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.TargetMachine
- /machine
dev_langs:
- C++
helpviewer_keywords:
- mapfiles, creating linker
- target platform
- -MACHINE linker option
- /MACHINE linker option
- MACHINE linker option
ms.assetid: 8d41bf4b-7e53-4ab9-9085-d852b08d31c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e159fe15b0aed441b1a96047a3ffb035077d6266
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45708614"
---
# <a name="machine-specify-target-platform"></a>/MACHINE (určení cílové platformy)

```
/MACHINE:{ARM|EBC|X64|X86}
```

## <a name="remarks"></a>Poznámky

Možnost /MACHINE určuje cílovou platformu programu.

Obvykle není nutné možnost /MACHINE zadávat. Volba LINK odvodí typ počítače ze souborů .obj. Nicméně v některých případech nelze určit odkaz typ počítače a problémy [linkerů LNK1113 chyba](../../error-messages/tool-errors/linker-tools-error-lnk1113.md). Pokud k takové chybě dojde, zadejte volbu /MACHINE.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).

1. Klikněte na tlačítko **Linkeru** složky.

1. Klikněte na tlačítko **Upřesnit** stránku vlastností.

1. Upravit **cílový počítač** vlastnost.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)