---
title: -openmp (povolit podporu OpenMP 2.0) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
dev_langs:
- C++
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fe64011f48255a18aa8f8ccab7571533540a598a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378727"
---
# <a name="openmp-enable-openmp-20-support"></a>/openmp (Povolit podporu OpenMP 2.0)
Způsobí, že kompilátor zpracovat `#pragma` [omp –](../../preprocessor/omp.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/openmp  
```  
  
## <a name="remarks"></a>Poznámky  
 `#pragma omp` slouží k určení [direktivy](../../parallel/openmp/reference/openmp-directives.md) a [klauzule](../../parallel/openmp/reference/openmp-clauses.md). Pokud **/OpenMP** není zadán v kompilaci, kompilátor ignoruje OpenMP – klauzule a direktivy. [Funkce OpenMP](../../parallel/openmp/reference/openmp-functions.md) zpracovává volání kompilátoru i když **/OpenMP** není zadán.  
  
 Aplikace, kompilovat s **/OpenMP** a **/CLR** lze spustit pouze v jedné aplikace domény procesu; více domén aplikací nejsou podporovány. To znamená, když se spustí modul konstruktoru (.cctor), poté zjistit, proces je kompilovat s **/OpenMP** a pokud aplikace do jiné než výchozí runtime načítá. Další informace najdete v tématu [appdomain](../../cpp/appdomain.md), [/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md), a [inicializace smíšených sestavení](../../dotnet/initialization-of-mixed-assemblies.md).  
  
 Pokud pokus o načtení aplikace, kompilovat s **/OpenMP** a **/CLR** do domény aplikace jiné než výchozí, <xref:System.TypeInitializationException> výjimce mimo ladicí program a OpenMPWithMultipleAppdomainsException dojde k výjimce v ladicím programu.  
  
 Tyto výjimky mohou být vyvolány také v těchto situacích:  
  
-   Pokud vaše aplikace, kompilovat s **/CLR**, ale ne při **/OpenMP**, je načteno do domény aplikace jiné než výchozí, ale kde proces zahrnuje aplikace, která bylo kompilováno s **/ OpenMP**.  
  
-   Pokud předáte vaše **/CLR** aplikace na nástroj, jako je například regasm.exe ([Regasm.exe (Nástroj registrace sestavení)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)), který načte jeho cíl sestavení do domény aplikace jiné než výchozí.  
  
 Zabezpečení přístupu kódu modul common language runtime nefunguje v oblastech OpenMP. Pokud použijete CLR atribut zabezpečení přístupu kódu mimo paralelní oblast, nebude platit v paralelní oblasti.  
  
 Microsoft informuje o tom, že jste Nezapisovat **/OpenMP** aplikace, které umožňuje částečně důvěryhodné volající, pomocí <xref:System.Security.AllowPartiallyTrustedCallersAttribute>, nebo všechny atributy zabezpečení přístupu kódu CLR.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **C/C++** uzlu.  
  
4.  Vyberte **jazyk** stránku vlastností.  
  
5.  Změnit **podporu OpenMP** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje některé důsledky spuštění fondu a kdy zachovalo po jeho spuštění. Za předpokladu, že x64, jednojádrový, dvoujádrový procesor zachovalo trvá asi 16ms spuštění. Po, ale je velmi malé náklady fondu.  
  
 Když kompilujete s **/OpenMP**, druhé volání test2 nikdy běží déle, než když kompilujete s **/openmp-**, protože neexistuje žádná spuštění fondu. Na milion iterací **/OpenMP** verze je rychlejší než **/openmp-** verze druhé volání test2 a na 25 iterací **/openmp-** a **/OpenMP** verze registrace menší než členitost hodiny.  
  
 Pokud máte pouze jeden smyčky v aplikaci a spustí se v menší než 15ms (přizpůsobené pro přibližnou režijní náklady na váš počítač), **/OpenMP** nemusí být vhodné, ale pokud je více než nic, můžete chtít zvažte použití **/OpenMP**.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)