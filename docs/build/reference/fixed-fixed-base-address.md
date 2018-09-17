---
title: -FIXED (pevná základní adresa) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
dev_langs:
- C++
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 697f6ccfd98059175311cd04e4e82038877b2110
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45723395"
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

- Zobrazit <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Viz také

[Nastavení možností linkeru](../../build/reference/setting-linker-options.md)<br/>
[Možnosti linkeru](../../build/reference/linker-options.md)