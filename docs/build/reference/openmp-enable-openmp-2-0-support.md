---
title: / OpenMP (povolit podporu OpenMP)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: caa06d89c590abd2b3a74a5a6b118d6ba4acd910
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/17/2019
ms.locfileid: "59674263"
---
# <a name="openmp-enable-openmp-support"></a>/ OpenMP (povolit podporu OpenMP)

Způsobí, že kompilátor zpracování [ `#pragma omp` ](../../preprocessor/omp.md) direktivy podporu OpenMP.

## <a name="syntax"></a>Syntaxe

::: moniker range=">= vs-2019"

> **/ openmp**\[**:**__experimentální__]

::: moniker-end

::: moniker range="<= vs-2017"

> **/ OpenMP**

::: moniker-end

## <a name="remarks"></a>Poznámky

`#pragma omp` slouží k určení [direktivy](../../parallel/openmp/reference/openmp-directives.md) a [klauzule](../../parallel/openmp/reference/openmp-clauses.md). Pokud **/OpenMP** není zadán v kompilaci Kompilátor ignoruje OpenMP – klauzule a direktivy. [OpenMP – funkce](../../parallel/openmp/reference/openmp-functions.md) i když kompilátor zpracovává volání **/OpenMP** není zadán.

::: moniker range=">= vs-2019"

C++ Kompilátoru v současné době podporuje standard OpenMP 2.0. Visual Studio 2019 však nyní také nabízí funkce SIMD. Pokud chcete použít SIMD, kompilovat s použitím **/OpenMP: experimentální** možnost. Tato možnost povolí obě obvyklé funkce OpenMP a další funkce OpenMP SIMD není k dispozici při použití **/OpenMP** přepnout.

::: moniker-end

Aplikace kompilované pomocí **/OpenMP** a **/CLR** lze spustit pouze v jedné aplikace domény procesu. Více domén aplikace nejsou podporovány. To znamená, když konstruktor modulu (`.cctor`) je spuštění, zjistí, jestli proces je kompilován pomocí **/OpenMP**, a pokud aplikace je načtena do jiné než výchozí modul runtime. Další informace najdete v tématu [appdomain](../../cpp/appdomain.md), [/CLR (kompilace Common Language Runtime)](clr-common-language-runtime-compilation.md), a [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).

Při pokusu o načtení aplikace sestavena pomocí obou **/OpenMP** a **/CLR** do domény aplikace jiné než výchozí, <xref:System.TypeInitializationException> mimo ladicí program, je vyvolána výjimka a `OpenMPWithMultipleAppdomainsException` výjimky v ladicím programu, je vyvolána.

Tyto výjimky se dá vyvolat také v následujících situacích:

- Pokud vaše aplikace je kompilována použitím **/CLR** , ale ne **/OpenMP**a je načteno do domény aplikace jiné než výchozí, kde proces obsahuje aplikaci kompilováno s použitím   **/OpenMP**.

- Pokud předáte vaše **/CLR** aplikaci tak, aby nástroj, jako například [regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), což způsobí načtení jeho cílové sestavení do domény aplikace jiné než výchozí.

Zabezpečení přístupu kódu common language runtime nebude fungovat v oblasti OpenMP. Pokud použijete atributu zabezpečení přístupu kódu CLR mimo paralelní oblasti, nebudou v platnosti v paralelní oblasti.

Microsoft nebude doporučujeme, že napíšete **/OpenMP** aplikací, které umožňují částečně důvěryhodné volající. Nepoužívejte <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, nebo všechny atributy zabezpečení přístupu kódu CLR.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** > **C /C++** > **jazyk** stránku vlastností.

1. Upravit **podpory OpenMP** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Příklad

Následující příklad ukazuje některé důsledků při spuštění vlákna fondu oproti použití fondu vláken po jeho spuštění. Za předpokladu, že x64, jednojádrový, dvoujádrový procesor, fondu vláken trvá asi 16 ms se spustí. Poté je něco malého navíc zdarma fondu vláken.

Pokud kompilujete pomocí **/OpenMP**, druhé volání test2 nikdy nespustí déle, než pokud kompilujete pomocí **/openmp-**, protože není žádná spuštění fondu vláken. Na milion iterací **/OpenMP** verze je rychlejší než **/openmp-** verze pro druhé volání test2. Za 25 iterací obě **/openmp-** a **/OpenMP** verze register méně než hodiny členitosti.

Pokud máte pouze v jednom průchodu ve vaší aplikaci a poběží v méně než 15 ms (přizpůsobené pro přibližné režijní náklady na svém počítači), **/OpenMP** nemusí být vhodné. Pokud je vyšší, můžete chtít zvážit použití **/OpenMP**.

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

## <a name="see-also"></a>Viz také:

[Možnosti kompilátoru MSVC](compiler-options.md) \
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md) \
[OpenMP ve MSVC](../../parallel/openmp/openmp-in-visual-cpp.md)
