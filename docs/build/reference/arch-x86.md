---
title: /Arch (x86)
ms.date: 10/01/2019
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: b1e5501f6edd3eb016395380ff476250c0c388b9
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816320"
---
# <a name="arch-x86"></a>/Arch (x86)

Určuje architekturu pro generování kódu v x86. Viz také [/arch (x64)](arch-x64.md) a [/arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Syntaxe

```
/arch:[IA32|SSE|SSE2|AVX|AVX2|AVX512]
```

## <a name="arguments"></a>Argumenty

**/arch: IA32**<br/>
Neurčuje žádné rozšířené instrukce a také určuje x87 pro výpočty s plovoucí desetinnou čárkou.

**/arch: SSE**<br/>
Povolí použití instrukcí SSE.

**/arch: SSE2**<br/>
Povolí použití instrukcí SSE2. Toto je výchozí instrukce na platformách x86, pokud není zadaná žádná možnost **/arch** .

**/arch: AVX**<br/>
Povoluje použití instrukcí rozšíření Intel Advanced Vector.

**/arch: AVX2**<br/>
Povolí použití instrukcí Intel Advanced Vector Extensions 2.

**/arch: AVX512**<br/>
Povolí použití instrukcí Intel Advanced Vector Extensions 512.

## <a name="remarks"></a>Poznámky

Možnost **/arch** povolí nebo zakáže použití některých rozšíření sady instrukcí, zejména pro výpočet vektoru, který je dostupný v procesorech od platforem Intel a AMD. Obecně platí, že další rozšíření pro procesory můžou podporovat starší procesory, i když byste měli požádat o konkrétní procesor nebo test podpory rozšíření pro instrukční sady pomocí [__. CPUID](../../intrinsics/cpuid-cpuidex.md) před spuštěním kódu pomocí rozšíření sady instrukcí.

**/arch** má vliv jenom na generování kódu pro nativní funkce. Když použijete [/CLR](clr-common-language-runtime-compilation.md) ke kompilaci, nemá **/arch** žádný vliv na generování kódu pro spravované funkce.

Možnosti **/arch** odkazují na rozšíření sady instrukcí s následujícími charakteristikami:

- **IA32** je starší 32 sada instrukcí x86 bez jakýchkoli operací Vector a použití x87 pro výpočty s plovoucí desetinnou čárkou.

- **SSE** umožňuje výpočet s vektory až čtyřmi hodnotami s plovoucí desetinnou čárkou s jednoduchou přesností. Přidaly se také příslušné skalární instrukce s plovoucí desetinnou čárkou.

- **SSE2** umožňuje výpočet s 128 bitovými vektory hodnot typu Single-přesnost, dvojitá přesnost a 1, 2, 4 nebo 8 bajtů. Přidali jsme také skalární instrukce s dvojitou přesností.

- **AVX** představila alternativní kódování instrukcí pro vektorové instrukce a skalární instrukce s plovoucí desetinnou čárkou, která umožňuje vektory buď 128 bitů nebo 256 bitů, a nula – rozšiřuje všechny výsledky vektoru na plnou velikost vektoru. (Kvůli kompatibilitě se staršími verzemi ve stylu SSE zachovávají všechny bity nad bitovou 127.) Většina operací s plovoucí desetinnou čárkou je rozšířena na 256 bitů.

- **AVX2** rozšiřuje většinu celočíselných operací na 256 bitové vektory a povoluje použití pojistných instrukcí pro násobení (FMA).

- **AVX512** zavedl další formulář kódování instrukcí, který umožňuje 512 bitové vektory a některé jiné volitelné funkce. Přidali jsme také pokyny pro další operace.

Optimalizátor vybírá, kdy a jak používat instrukce Vector v závislosti na tom, které **/arch** je zadáno. Skalární výpočty s plovoucí desetinnou čárkou se provádějí pomocí instrukcí SSE nebo AVX, pokud jsou dostupné. Některé konvence volání určují předávání argumentů s plovoucí desetinnou čárkou v zásobníku x87 a výsledkem může být, že váš kód bude používat kombinaci x87 a SSE/AVX instrukcí pro výpočty s plovoucí desetinnou čárkou. Instrukce celočíselného vektoru lze také použít pro některé z 64ch celočíselných operací, pokud jsou k dispozici.

Kromě vektorových instrukcí a skalárních instrukcí s plovoucí desetinnou čárkou může každá možnost **/arch** povolit také použití dalších nevektorových instrukcí, které jsou přidruženy k této možnosti. Příkladem je rodina instrukcí CMOVcc, která se dřív objevila na procesorech Intel Pentium pro. Vzhledem k tomu, že instrukce SSE byly představeny s následným procesorem Intel Pentium III, mohou být vygenerovány pokyny CMOVcc s výjimkou případů, kdy je určena **/arch:**

Operace s plovoucí desetinnou čárkou jsou obvykle zaokrouhleny na dvojitou přesnost (64 bitů) v kódu x87, ale můžete použít `_controlfp` pro úpravu ovládacího prvku FP, včetně nastavení přesnosti ovládacího prvku na rozšířenou přesnost (80 bitů) nebo jednoduchou přesnost (32-bit). Další informace najdete v tématu [_control87, _controlfp @no__t -1 _control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md). SSE a AVX mají pro každou operaci samostatné pokyny pro jednoduchou přesnost a dvojitou přesnost, takže neexistuje žádný ekvivalent pro kód SSE/AVX. To může změnit způsob zaoblení výsledků, pokud je výsledek operace s plovoucí desetinnou čárkou použit přímo v dalším výpočtu namísto přiřazení k uživatelské proměnné. Zvažte použití těchto zdrojů:

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

S explicitním přiřazením:

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

**/arch** a [/QIfist](qifist-suppress-ftol.md) nelze použít na stejném kompilantu. Možnost **/QIfist** mění chování zaokrouhlení s plovoucí desetinnou čárkou na celočíselný převod. Výchozím chováním je zkrátit (zaokrouhlit směrem k nule), zatímco možnost **/QIfist** Určuje použití režimu zaokrouhlení prostředí s plovoucí desetinnou čárkou. Vzhledem k tomu, že se změní chování všech převodů s plovoucí desetinnou čárkou na celočíselné převody, tento příznak je zastaralý. Při kompilaci pro SSE nebo AVX můžete hodnotu s plovoucí desetinnou čárkou zaokrouhlit na celé číslo pomocí režimu zaokrouhlení prostředí s plovoucí desetinnou čárkou pomocí sekvence vnitřních funkcí:

```cpp
int convert_float_to_int(float x) {
    return _mm_cvtss_si32(_mm_set_ss(x));
}

int convert_double_to_int(double x) {
    return _mm_cvtsd_si32(_mm_set_sd(x));
}
```

Makra `_M_IX86_FP`, `__AVX__`, `__AVX2__`, `__AVX512F__`, `__AVX512CD__`, `__AVX512BW__`, `__AVX512DQ__` a `__AVX512VL__` označují, zda byla použita možnost kompilátoru **/arch** . Další informace najdete v tématu [Předdefinovaná makra](../../preprocessor/predefined-macros.md). Byla představena možnost **/arch: AVX2** a makro `__AVX2__` v Visual Studio 2013 Update 2 verze 12.0.34567.1. Omezená podpora pro **/arch: AVX512** se přidala do sady visual Studio 2017 a rozšířila se v aplikaci visual Studio 2019.

### <a name="to-set-this-compiler-option-for-avx-avx2-avx512-ia32-sse-or-sse2-in-visual-studio"></a>Nastavení této možnosti kompilátoru pro AVX, AVX2, AVX512, IA32, SSE nebo SSE2 v sadě Visual Studio

1. Otevřete dialogové okno **stránky vlastností** projektu. Další informace najdete v tématu [nastavení C++ vlastností kompilátoru a sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **Vlastnosti konfigurace**, **C/C++**  složka.

1. Vyberte stránku vlastností **generování kódu** .

1. Upravte vlastnost **Povolit rozšířenou sadu instrukcí** .

### <a name="to-set-this-compiler-option-programmatically"></a>Chcete-li nastavit tuto možnost kompilátoru programově

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Další informace najdete v tématech

[/Arch (minimální architektura procesoru)](arch-minimum-cpu-architecture.md)<br/>
[Možnosti kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)
