---
title: /FIXED (Pevná základní adresa)
ms.date: 11/04/2016
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
ms.openlocfilehash: 12ba2d977ecca4805aa01ade1a6ea8239e07716e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523029"
---
# <a name="fixed-fixed-base-address"></a>/FIXED (Pevná základní adresa)

```
/FIXED[:NO]
```

## <a name="remarks"></a>Poznámky

Říká operačním systém načíst program pouze na jeho upřednostňované základní adrese. Pokud není k dispozici upřednostňovaná základní adresa, nenačte operační systém soubor. Další informace najdete v tématu [propojovacího (základní adresa)](../../build/reference/base-base-address.md).

/ Fixed: No je výchozí nastavení pro knihovnu DLL a/fixed je výchozí nastavení pro jakýkoli jiný typ projektu.

Pokud je zadáno/fixed, LINK nevygeneruje část přemístění v programu. V době běhu Pokud je operační systém nejde načíst program na zadané adrese ho vydává chybovou zprávu a nenačte program.

Zadejte/fixed: NO pro vygenerování části přemístění v programu.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **Linkeru** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. Zadejte název možnosti a nastavení **další možnosti** pole.

### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)