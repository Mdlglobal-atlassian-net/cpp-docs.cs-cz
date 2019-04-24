---
title: /arch (x64)
ms.date: 11/04/2016
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: c515307ee3a49ef746eea939e90d7aecbd661b95
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295279"
---
# <a name="arch-x64"></a>/arch (x64)

Určuje architekturu pro generování kódu na x64. Viz také [/arch (x86)](arch-x86.md) a [/arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[AVX|AVX2]
```

## <a name="arguments"></a>Arguments

**/ arch: AVX**<br/>
Umožňuje použití Intel Advanced Vector Extensions instrukcí.

**/ arch: avx2**<br/>
Umožňuje použití Intel Advanced Vector Extensions 2 instrukcí.

## <a name="remarks"></a>Poznámky

**/ arch** jen ovlivňuje generování kódu pro nativní funkce. Při použití [/CLR](clr-common-language-runtime-compilation.md) ke kompilaci, **/arch** nemá žádný vliv na generování kódu pro spravované funkce.

`__AVX__` Je definován symbol preprocesoru při **/arch: AVX** je zadána možnost kompilátoru. `__AVX2__` Je definován symbol preprocesoru při **/arch: avx2** je zadána možnost kompilátoru. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md). **/Arch: avx2** možnost byla zavedena v aplikaci Visual Studio 2013 Update 2, verze 12.0.34567.1.

### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>Nastavení možnosti kompilátoru/arch: AVX nebo/arch: avx2 v sadě Visual Studio

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace**, **C/C++** složky.

1. Vyberte **generování kódu** stránku vlastností.

1. V **povolení rozšířeného sadu instrukcí** rozevíracího seznamu vyberte **Advanced Vector Extensions (/ arch: AVX)** nebo **Advanced Vector Extensions 2 (/ arch: AVX2)**.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Viz také:

[/arch (minimální architektura procesoru)](arch-minimum-cpu-architecture.md)<br/>
[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
