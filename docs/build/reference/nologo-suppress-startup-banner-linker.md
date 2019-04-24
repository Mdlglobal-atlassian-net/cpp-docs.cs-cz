---
title: /NOLOGO (Potlačit úvodní nápis při spouštění) (linker)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.SuppressStartupBanner
- /nologo
helpviewer_keywords:
- suppress startup banner linker option
- -NOLOGO linker option
- /NOLOGO linker option
- copyright message
- version numbers, preventing linker display
- banners, suppressing startup
- NOLOGO linker option
ms.assetid: 3b20dddd-eca6-4545-a331-9f70bf720197
ms.openlocfilehash: 0ef0c6f8e0073e7450daa8d0433ce4d6e82ceab8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320516"
---
# <a name="nologo-suppress-startup-banner-linker"></a>/NOLOGO (Potlačit úvodní nápis při spouštění) (linker)

```
/NOLOGO
```

## <a name="remarks"></a>Poznámky

Parametr/nologo zakazuje zobrazení čísla o autorských právech zprávu a verze.

Tato možnost také potlačí zobrazování souborů příkazu. Podrobnosti najdete v tématu [soubory příkazů LINK](linking.md).

Ve výchozím nastavení tyto informace jsou odeslány pomocí linkeru, aby v okně výstup. Na příkazovém řádku je odeslán na standardní výstup a je možné přesměrovat do souboru.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Tato možnost by měla sloužit pouze z příkazového řádku.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

1. Tohoto parametru linkeru nelze změnit prostřednictvím kódu programu.

## <a name="see-also"></a>Viz také:

[Referenční zdroje k linkeru MSVC](linking.md)<br/>
[Možnosti linkeru MSVC](linker-options.md)
