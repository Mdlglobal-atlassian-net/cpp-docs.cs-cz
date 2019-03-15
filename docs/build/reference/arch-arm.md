---
title: /arch (ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: b732a74d5fe223fdaf3b161d4ae92093ab5df407
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807868"
---
# <a name="arch-arm"></a>/arch (ARM)

Určuje architekturu pro generování kódu na ARM. Viz také [/arch (x86)](arch-x86.md) a [/arch (x64)](arch-x64.md).

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

Při použití [/CLR](clr-common-language-runtime-compilation.md) ke kompilaci, **/arch** nemá žádný vliv na generování kódu pro spravované funkce. **/ arch** jen ovlivňuje generování kódu pro nativní funkce.

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Nastavení parametru kompilátoru /arch:ARMv7VE nebo /arch:VFPv4 v sadě Visual Studio

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **C/C++** složky.

1. Vyberte **příkazového řádku** stránku vlastností.

1. V **další možnosti** přidejte `/arch:ARMv7VE` nebo `/arch:VFPv4`.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Viz také:

[/arch (minimální architektura procesoru)](arch-minimum-cpu-architecture.md)<br/>
[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
