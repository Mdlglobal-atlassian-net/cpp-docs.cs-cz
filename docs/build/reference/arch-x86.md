---
title: /arch (x86)
ms.date: 11/04/2016
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: fb115d564ca24ff29e120e0d8c25e0dbe28024cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549705"
---
# <a name="arch-x86"></a>/arch (x86)

Určuje architekturu pro generování kódu na x86. Viz také [/arch (x64)](../../build/reference/arch-x64.md) a [/arch (ARM)](../../build/reference/arch-arm.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[IA32|SSE|SSE2|AVX|AVX2]
```

## <a name="arguments"></a>Arguments

**/arch:IA32**<br/>
Určuje žádné rozšířené instrukce a také určuje x87 pro výpočtů s plovoucí desetinnou čárkou.

**/arch:SSE**<br/>
Povoluje použití instrukcí SSE.

**SSE2**<br/>
Umožňuje použití pokynů SSE2. Toto je výchozí instrukce na x86 platformy, pokud žádné **/arch** je zadána možnost.

**/ arch: AVX**<br/>
Umožňuje použití Intel Advanced Vector Extensions instrukcí.

**/ arch: avx2**<br/>
Umožňuje použití Intel Advanced Vector Extensions 2 instrukcí.

## <a name="remarks"></a>Poznámky

Instrukce SSE a SSE2 existovat na různých procesorech Intel a AMD. Pokyny AVX existovat na procesorech Intel Sandy most a procesorů AMD Bulldozer. AVX2 pokyny jsou podporovány Broadwell procesorů Intel Haswell a procesory AMD rýpadla.

`_M_IX86_FP`, `__AVX__` a `__AVX2__` označení makra, která, pokud nějaké existují, **/arch** byla použita možnost kompilátoru. Další informace najdete v tématu [předdefinovaná makra](../../preprocessor/predefined-macros.md). **/Arch: avx2** možnost a `__AVX2__` – makro byly zavedeny v aplikaci Visual Studio 2013 Update 2, verze 12.0.34567.1.

Optimalizátor zvolí, kdy a jak můžete využít pokynů SSE a SSE2 při **/arch** je zadán. Používá SSE a SSE2 pokyny, jak některé skalární výpočtů s plovoucí desetinnou čárkou když zjistí, že je rychlejší použití instrukce SSE nebo SSE2 a registrů místo s plovoucí desetinnou čárkou x87 registrace zásobníku. V důsledku toho váš kód skutečně použít kombinaci x87 a SSE a SSE2 pro výpočtů s plovoucí desetinnou čárkou. Navíc se **SSE2**, SSE2 pokyny slouží pro některé operace 64bitové celé číslo.

Kromě použití instrukce SSE a SSE2, kompilátor používá také další pokyny, které jsou k dispozici na na procesoru revize, které podporují SSE a SSE2. Příkladem je CMOV pokyn, nejprve zobrazilo na procesory Intel Pentium Pro revizi.

Protože x86 kompilátor generuje kód, který používá SSE2 pokyny ve výchozím nastavení, je nutné zadat **/arch:IA32** zakázat generování instrukcí SSE a SSE2 x86 procesory.

**/ arch** jen ovlivňuje generování kódu pro nativní funkce. Při použití [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) ke kompilaci, **/arch** nemá žádný vliv na generování kódu pro spravované funkce.

**/ arch** a [/QIfist](../../build/reference/qifist-suppress-ftol.md) nelze použít na stejném kompilace. Konkrétně, pokud nepoužijete `_controlfp` upravit řídicí slovo FP pak za běhu při spuštění kódu nastaví x87 FPU ovládací prvek slovo přesnost – ovládací prvek pole na 53 bitů. Proto všechny plovoucí desetinnou čárkou a double operace ve výrazu používá 53bitovou mantisy a exponentu 15-bit. Však všechny operace s jednoduchou přesností SSE používá 24-bit mantisy a exponentu 8 bitů a operace s dvojitou přesností SSE2 používají 53bitovou mantisy a 11bitový exponent. Další informace najdete v tématu [_control87 _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md). Tyto rozdíly jsou možné u strom výrazů, ale nejsou v případech, kde je zahrnuta přiřazení uživatelů po každé dílčí výraz. Vezměte v úvahu následující:

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

Porovnání:

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

### <a name="to-set-this-compiler-option-for-avx-avx2-ia32-sse-or-sse2-in-visual-studio"></a>Nastavení této možnosti kompilátoru pro AVX, AVX2, IA32, SSE nebo SSE2 v sadě Visual Studio

1. Otevřít **stránky vlastností** dialogové okno pro projekt. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace**, **C/C++** složky.

1. Vyberte **generování kódu** stránku vlastností.

1. Upravit **povolení rozšířeného sadu instrukcí** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Viz také

[/arch (minimální architektura procesoru)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)