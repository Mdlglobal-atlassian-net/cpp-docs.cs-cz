---
title: /arch (ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: 7fd396f4ed9c02daff5363342d7c851d022919ac
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424987"
---
# <a name="arch-arm"></a>/arch (ARM)

Určuje architekturu pro generování kódu na ARM. Viz také [/arch (x86)](../../build/reference/arch-x86.md) a [/arch (x64)](../../build/reference/arch-x64.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>Arguments

**/arch:ARMv7VE**<br/>
Povoluje použití instrukcí ARMv7VE virtualizace rozšíření.

**/arch:VFPv4**<br/>
Povoluje použití instrukcí ARM VFPv4. Pokud není tato možnost zadána, VFPv3 je výchozí nastavení.

## <a name="remarks"></a>Poznámky

`_M_ARM_FP` – Makro (pro pouze ARM) označuje, který, pokud nějaké existují, **/arch** byla použita možnost kompilátoru. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md).

Při použití [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) ke kompilaci, **/arch** nemá žádný vliv na generování kódu pro spravované funkce. **/ arch** jen ovlivňuje generování kódu pro nativní funkce.

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Nastavení parametru kompilátoru /arch:ARMv7VE nebo /arch:VFPv4 v sadě Visual Studio

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **C/C++** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. V **další možnosti** přidejte `/arch:ARMv7VE` nebo `/arch:VFPv4`.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Viz také:

[/arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
