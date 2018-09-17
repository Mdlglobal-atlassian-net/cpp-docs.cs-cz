---
title: -NOLOGO (Potlačit úvodní nápis při spouštění) (Linker) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
dev_langs:
- C++
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 405cfd08b681d8b48343bae5055f5be9cf23dadb
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707574"
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (Potlačit úvodní nápis při spouštění) (linker)

```
/NOLOGO
```

## <a name="remarks"></a>Poznámky

Parametr/nologo zakazuje zobrazení čísla o autorských právech zprávu a verze.

Tato možnost také potlačí zobrazování souborů příkazu. Podrobnosti najdete v tématu [soubory příkazů LINK](../../build/reference/link-command-files.md).

Ve výchozím nastavení tyto informace jsou odeslány pomocí linkeru, aby v okně výstup. Na příkazovém řádku je odeslán na standardní výstup a je možné přesměrovat do souboru.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Tato možnost by měla sloužit pouze z příkazového řádku.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Tohoto parametru linkeru nelze změnit prostřednictvím kódu programu.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)