---
title: /Arch (x64)
ms.date: 10/01/2019
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: 0ade6d9f744339ebaf38981d81334340b56080cb
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816226"
---
# <a name="arch-x64"></a>/Arch (x64)

Určuje architekturu pro generování kódu na platformě x64. Viz také [/arch (x86)](arch-x86.md) a [/arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[AVX|AVX2|AVX512]
```

## <a name="arguments"></a>Argumenty

**/arch: AVX**<br/>
Povoluje použití instrukcí rozšíření Intel Advanced Vector.

**/arch: AVX2**<br/>
Povolí použití instrukcí Intel Advanced Vector Extensions 2.

**/arch: AVX512**<br/>
Povolí použití instrukcí Intel Advanced Vector Extensions 512.

## <a name="remarks"></a>Poznámky

Možnost **/arch** umožňuje použití určitých rozšíření sady instrukcí, zejména pro výpočet vektoru, k dispozici v procesorech od Intel a AMD. Obecně platí, že další rozšíření pro procesory můžou podporovat starší procesory, i když byste měli požádat o konkrétní procesor nebo test podpory rozšíření pro instrukční sady pomocí [__. CPUID](../../intrinsics/cpuid-cpuidex.md) před spuštěním kódu pomocí rozšíření sady instrukcí.

**/arch** má vliv jenom na generování kódu pro nativní funkce. Když použijete [/CLR](clr-common-language-runtime-compilation.md) ke kompilaci, nemá **/arch** žádný vliv na generování kódu pro spravované funkce.

Rozšíření procesoru mají následující vlastnosti:

- Výchozí režim používá pokyny SSE2 pro výpočty skalárních plovoucí desetinné čárky a vektorů. Tyto pokyny umožňují vypočítat 128 bitové vektory s jednou přesností, dvojitou přesností a 1, 2, 4 nebo 8 bajtů celočíselných hodnot a hodnot skalárních plovoucí desetinné čárky s jednoduchou přesností a dvojitou přesností.

- **AVX** představila alternativní kódování instrukcí pro vektorové instrukce a skalární instrukce s plovoucí desetinnou čárkou, která umožňuje vektory buď 128 bitů nebo 256 bitů, a nula – rozšiřuje všechny výsledky vektoru na plnou velikost vektoru. (Kvůli kompatibilitě se staršími verzemi ve stylu SSE zachovávají všechny bity nad bitovou 127.) Většina operací s plovoucí desetinnou čárkou je rozšířena na 256 bitů.

- **AVX2** rozšiřuje většinu celočíselných operací na 256 bitové vektory a povoluje použití pořízeného postupu násobení (FMA).

- **AVX-512** zavedl další formulář kódování instrukcí, který umožňuje 512 vektory a některé jiné volitelné funkce. Přidali jsme také pokyny pro další operace.

Každá možnost **/arch** může také povolit používání dalších nevektorových instrukcí, které jsou přidruženy k této možnosti. Příkladem je použití určitých instrukcí BMI, pokud je určena **/arch: AVX2** .

Symbol preprocesoru `__AVX__` je definován, pokud je zadána možnost kompilátoru **/arch: AVX**, **/arch: AVX2** nebo **/arch: AVX512** . Symbol preprocesoru `__AVX2__` je definován, pokud je zadána možnost kompilátoru **/arch: AVX2** nebo **/arch: AVX512** . Pokud je zadána možnost kompilátoru **/arch: AVX512** , jsou definovány symboly preprocesoru `__AVX512F__`, `__AVX512CD__`, `__AVX512BW__`, `__AVX512DQ__` a `__AVX512VL__`. Další informace najdete v tématu [Předdefinovaná makra](../../preprocessor/predefined-macros.md). Možnost **/arch: AVX2** byla představena ve verzi Visual Studio 2013 Update 2, verze 12.0.34567.1. Omezená podpora pro **/arch: AVX512** se přidala do sady visual Studio 2017 a rozšířila se v aplikaci visual Studio 2019.

### <a name="to-set-the-archavx-archavx2-or-archavx512-compiler-option-in-visual-studio"></a>Nastavení možnosti kompilátoru/arch: AVX,/arch: AVX2 nebo/arch: AVX512 v sadě Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace**, **C/C++**  složka.

1. Vyberte stránku vlastností **generování kódu** .

1. V rozevíracím seznamu **Povolit vylepšenou sadu instrukcí** vyberte **Rozšířená rozšíření vektorů (/arch: AVX)** , **Rozšířená rozšíření vektorů 2 (/arch: AVX2)** nebo **Rozšířená rozšíření Vector 512 (/arch: AVX512)** .

### <a name="to-set-this-compiler-option-programmatically"></a>Chcete-li nastavit tuto možnost kompilátoru programově

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Další informace najdete v tématech

[/Arch (minimální architektura procesoru)](arch-minimum-cpu-architecture.md)<br/>
[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
