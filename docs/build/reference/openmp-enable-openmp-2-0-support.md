---
title: /openmp (Povolit podporu OpenMP 2.0)
ms.date: 11/04/2016
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: bea51c7af41df666fd441555daa0d8d8387377ac
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414132"
---
# <a name="openmp-enable-openmp-20-support"></a>/openmp (Povolit podporu OpenMP 2.0)

Způsobí, že kompilátor zpracování `#pragma` [omp](../../preprocessor/omp.md).

## <a name="syntax"></a>Syntaxe

```
/openmp
```

## <a name="remarks"></a>Poznámky

`#pragma omp` slouží k určení [direktivy](../../parallel/openmp/reference/openmp-directives.md) a [klauzule](../../parallel/openmp/reference/openmp-clauses.md). Pokud **/OpenMP** není zadán v kompilaci Kompilátor ignoruje OpenMP – klauzule a direktivy. [OpenMP – funkce](../../parallel/openmp/reference/openmp-functions.md) i když kompilátor zpracovává volání **/OpenMP** není zadán.

Zkompilovaná aplikace **/OpenMP** a **/CLR** lze spustit pouze v jedné aplikace domény procesu, se nepodporují více domén aplikace. To znamená, že při spuštění modulu konstruktoru (.cctor) zjistí procesu je zkompilován s **/OpenMP** a pokud načítání aplikace do jiné než výchozí modul runtime. Další informace najdete v tématu [appdomain](../../cpp/appdomain.md), [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md), a [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).

Při pokusu o načtení aplikace kompilována s **/OpenMP** a **/CLR** do domény aplikace jiné než výchozí, <xref:System.TypeInitializationException> mimo ladicí program, bude vyvolána výjimka a Bude vyvolána výjimka OpenMPWithMultipleAppdomainsException v ladicím programu.

Tyto výjimky se dá vyvolat také v následujících situacích:

- Pokud vaše aplikace kompilována s **/CLR**, ale ne s **/OpenMP**, je načteno do domény aplikace jiné než výchozí, ale kde proces obsahuje aplikaci, která byla zkompilována s **/ OpenMP –**.

- Pokud předáte vaše **/CLR** aplikaci nástroje, jako je například regasm.exe ([Regasm.exe (Nástroj registrace sestavení)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)), což způsobí načtení jeho cílové sestavení do domény aplikace jiné než výchozí.

Zabezpečení přístupu kódu common language runtime nebude fungovat v oblasti OpenMP. Pokud použijete atributu zabezpečení přístupu kódu CLR mimo paralelní oblasti, nebudou v platnosti v paralelní oblasti.

Vás Microsoft informuje o tom, že nenapíšete **/OpenMP** aplikace, které umožňuje částečně důvěryhodné volající, pomocí <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, nebo všechny atributy zabezpečení přístupu kódu CLR.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).

1. Rozbalte **vlastnosti konfigurace** uzlu.

1. Rozbalte **C/C++** uzlu.

1. Vyberte **jazyk** stránku vlastností.

1. Upravit **podpory OpenMP** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.

## <a name="example"></a>Příklad

Následující příklad ukazuje některé efekty spuštění fondu vláken oproti použití fondu vláken po jeho spuštění. Za předpokladu, že x x64 jednojádrový, dvoujádrový procesor fondu vláken trvá asi 16ms spuštění. Následně se ale je velmi malé náklady na fondu vláken.

Pokud kompilujete s **/OpenMP**, druhé volání test2 nikdy nespustí déle, než pokud kompilujete s **/openmp-**, protože není žádná spuštění fondu vláken. Na milion iterací **/OpenMP** verze je rychlejší než **/openmp-** verzi u druhého volání test2 a na 25 iterací **/openmp-** a **/OpenMP** verze register méně než hodiny členitosti.

Pokud máte pouze v jednom průchodu ve vaší aplikaci a poběží v méně než 15ms (přizpůsobené pro přibližné režijní náklady na svém počítači), tedy **/OpenMP** nemusí být vhodné, pokud jde o něco větší než největší, možná ale budete chtít zvážit použití **/OpenMP**.

```
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

[Možnosti kompilátoru](../../build/reference/compiler-options.md)<br/>
[Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)
