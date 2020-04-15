---
title: /openmp (Povolit podporu OpenMP)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: d3454650bfaaacd756e5cfc73df056441a39f5ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336195"
---
# <a name="openmp-enable-openmp-support"></a>/openmp (Povolit podporu OpenMP)

Způsobí, že kompilátor zpracovat [`#pragma omp`](../../preprocessor/omp.md) direktivy na podporu OpenMP.

## <a name="syntax"></a>Syntaxe

::: moniker range=">= vs-2019"

> **/openmp**\[**:**__experimentální__]

::: moniker-end

::: moniker range="<= vs-2017"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>Poznámky

`#pragma omp`se používá ke stanovení [směrnic](../../parallel/openmp/reference/openmp-directives.md) a [doložek](../../parallel/openmp/reference/openmp-clauses.md). Pokud **/openmp** není zadán v kompilaci, kompilátor ignoruje OpenMP klauzule a direktivy. [Volání funkce OpenMP](../../parallel/openmp/reference/openmp-functions.md) jsou zpracována kompilátorem i v případě, že **/openmp** není zadán.

::: moniker range=">= vs-2019"

Kompilátor Jazyka C++ aktuálně podporuje standard OpenMP 2.0. Visual Studio 2019 však nyní také nabízí funkce SIMD. Chcete-li použít SIMD, kompilujte pomocí **možnosti /openmp:experimental.** Tato možnost umožňuje jak obvyklé funkce OpenMP, tak další funkce OpenMP SIMD, které nejsou k dispozici při použití přepínače **/openmp.**

::: moniker-end

Aplikace zkompilované pomocí **/openmp** a **/clr** lze spustit pouze v jednom procesu domény aplikace. Více aplikačních domén není podporováno. To znamená, že při`.cctor`spuštění konstruktoru modulu ( ) zjistí, zda je proces kompilován pomocí **/openmp**a pokud je aplikace načtena do jiného než výchozího modulu runtime. Další informace naleznete v [tématu appdomain](../../cpp/appdomain.md), [/clr (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md)a [Inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).

Pokud se pokusíte načíst aplikaci zkompilovanou pomocí **/openmp** a <xref:System.TypeInitializationException> **/clr** do domény aplikace, která `OpenMPWithMultipleAppdomainsException` není výchozí, je mimo ladicí program vyvolána výjimka a v ladicím programu je vyvolána výjimka.

Tyto výjimky mohou být vyvolány také v následujících situacích:

- Pokud je vaše aplikace kompilován pomocí **/clr,** ale ne **/openmp**, a je načten do domény aplikace, která není výchozí, kde proces zahrnuje aplikaci zkompilovanou pomocí **/openmp**.

- Pokud předáte aplikaci **/clr** nástroji, například [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), který načte cílové sestavení do domény aplikace, která není výchozí.

Zabezpečení přístupu kódu běžného jazyka runtime nefunguje v oblastech OpenMP. Pokud použijete atribut zabezpečení přístupu kódu CLR mimo paralelní oblast, nebude v paralelní oblasti platit.

Společnost Microsoft nedoporučuje psát **/openmp** aplikace, které umožňují částečně důvěryhodné volající. Nepoužívejte <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, nebo žádné clr kód přístup k zabezpečení atributy.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte stránku **vlastností Vlastnosti** > **jazyka** **C/C++.** > 

1. Upravte vlastnost **Podpory OpenMP.**

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Příklad

Následující ukázka ukazuje některé účinky spuštění fondu vláken versus pomocí fondu vláken po jeho spuštění. Za předpokladu, že x64, jednojádrový, duální procesor, fond vláken trvá asi 16 ms ke spuštění. Za to, že je tu málo dodatečných nákladů na vlákno fondu.

Při kompilaci pomocí **/openmp**, druhé volání test2 nikdy spustí déle, než pokud kompilovat pomocí **/openmp-**, protože neexistuje žádné spuštění fondu vláken. Na milion iterací **/openmp** verze je rychlejší než **/openmp-** verze pro druhé volání test2. Na 25 iterací **/ openmp-** a **/openmp** verze zaregistrovat méně než hodiny rozlišovací schopnost.

Pokud máte pouze jednu smyčku v aplikaci a běží za méně než 15 ms (upraveno pro přibližnou režii na vašem počítači), **/openmp** nemusí být vhodné. Pokud je vyšší, můžete zvážit použití **/openmp**.

```cpp
// cpp_compiler_options_openmp.cpp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>
#include <windows.h>

volatile DWORD dwStart;
volatile int global = 0;

double test2(int num_steps) {
   int i;
   global++;
   double x, pi, sum = 0.0, step;

   step = 1.0 / (double) num_steps;

   #pragma omp parallel for reduction(+:sum) private(x)
   for (i = 1; i <= num_steps; i++) {
      x = (i - 0.5) * step;
      sum = sum + 4.0 / (1.0 + x*x);
   }

   pi = step * sum;
   return pi;
}

int main(int argc, char* argv[]) {
   double   d;
   int n = 1000000;

   if (argc > 1)
      n = atoi(argv[1]);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);
}
```

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru MSVC](compiler-options.md) \
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md) \
[OpenMP v MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
