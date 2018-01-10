---
title: "-fp (zadání chování s plovoucí desetinnou čárkou) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
dev_langs: C++
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0f4a86c7bbbd38887944080a5a5c8124310fdd4a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (zadání chování hodnot s plovoucí desetinnou čárkou)
Určuje chování plovoucí desetinné čárky v souboru zdrojového kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/fp:[precise | except[-] | fast | strict ]  
```  
  
## <a name="flags"></a>Příznaky  
 **přesné**  
 Výchozí nastavení  
  
 Zlepšuje konzistenci testů čísel s plovoucí desetinnou čárkou na rovnost a nerovnost zakázáním optimalizací, které by mohly změnit přesnost výpočtů s plovoucí desetinnou čárkou. (Zachování určité přesnosti se vyžaduje pro striktní dodržování ANSI.) V kódu pro architekturu x86 kompilátor standardně používá 80bitové registry koprocesoru, v nichž uchovává průběžné výsledky výpočtů s plovoucí desetinnou čárkou. To zvyšuje rychlost programu a snižuje jeho velikost. Protože však výpočty zahrnují datové typy s plovoucí desetinnou čárkou reprezentované v paměti méně než 80 bity, může přenos dodatečných bitů přesnosti (80 bitů minus počet bitů v menším typu s plovoucí desetinnou čárkou) napříč delším výpočtem zapříčinit nekonzistentní výsledky.  
  
 S **/fp: přesné** na x86 procesory, kompilátor provádí zaokrouhlení v proměnné typu `float` do správné přesnost pro přiřazení a přetypování a když jsou parametry předaný funkci. Toto zaokrouhlení zaručuje, že si data nezachovají větší platnost, než je kapacita jejich typu. Program kompilovat s **/fp: přesné** může být pomalejší a větší než jedna kompilovat bez **/fp: přesné**. **/FP: přesné** vnitřní zakáže funkce; standardní běhové knihovny se místo toho používají rutiny. Další informace najdete v tématu [/Oi (Generovat vnitřní funkce)](../../build/reference/oi-generate-intrinsic-functions.md).  
  
 Toto chování s plovoucí desetinnou čárkou je povolená s **/fp: přesné**:  
  
-   Zkrácení – použití složené operace, která provede pouze jedno zaokrouhlení na konci a nahrazuje více operací.  
  
-   Optimalizace výrazů, které jsou neplatné pro zvláštní hodnoty (NaN, +nekonečno, -nekonečno, +0, -0), nejsou povoleny. Optimalizace x-x > 0 = x * 0 = > 0, x-0 = > x, x + 0 = > x a 0 x = > - x jsou neplatné z různých důvodů. (Viz IEEE 754 a standard C99.)  
  
-   Kompilátor správně zpracovává porovnání, která zahrnují hodnotu NaN. Například x! = x se vyhodnocuje **true** Pokud `x` je NaN a seřazené porovnání zahrnující NaN vyvolat výjimku.  
  
-   Vyhodnocení výrazů dodržuje metodu FLT_EVAL_METHOD=2 standardu C99 s touto výjimkou: pokud je program určen pro procesory x86, považuje se to za přesnost long-double, protože jednotka FPU je nastavena na 53bitovou přesnost.  
  
-   Násobení hodnotou přesně 1,0 se transformuje na použití druhého činitele. x * y\*1.0 transformována do x\*y. Podobně x\*1.0\*y transformována do x\*y.  
  
-   Dělení hodnotou přesně 1,0 se transformuje na použití dělence. x * y/1.0 transformována do x\*y. Podobně x / 1.0\*y transformována do x\*y.  
  
 Pomocí **/fp: přesné** při [fenv_access –](../../preprocessor/fenv-access.md) je na zakáže optimalizace například kompilaci vyhodnocení výrazů s plovoucí desetinnou čárkou. Například, pokud používáte [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) změnit režim zaokrouhlení a kompilátor provádí výpočet s plovoucí desetinnou čárkou, zaokrouhlení je zadaný režim není v platnosti Pokud `fenv_access`je ON.  
  
 **/FP: přesné** nahrazuje **/Op** – možnost kompilátoru.  
  
 **Rychlé**  
 Vytvoří ve většině případů nejrychlejší kód zmírněním pravidel pro optimalizaci operací s plovoucí desetinnou čárkou. To umožňuje, aby kompilátor optimalizoval kód výpočtů s plovoucí desetinnou čárkou na rychlost na úkor přesnosti a správnosti. Když **/fp:fast** je zadán, kompilátor nemusí správně zaokrouhlit na příkazy přiřazení, přiřadí typ ukazatel, nebo volání funkce a nemusí provádí zaokrouhlení zprostředkující výrazů. Kompilátor může změnit pořadí operací nebo provádět algebraické transformace – například dodržováním asociativních a distributivních pravidel – bez ohledu na vliv na konečnou přesnost výsledků. Kompilátor může operace a operandy změnit na jednoduchou přesnost a nemusí dodržovat pravidla povyšování typů jazyka C++. Optimalizace floating point konkrétní zmenšení vždy povolena ([fp_contract –](../../preprocessor/fp-contract.md) je ON). Výjimky s plovoucí desetinnou čárkou a FPU prostředí přístup, jsou zakázané (**/fp: kromě-** je implicitní a [fenv_access –](../../preprocessor/fenv-access.md) je OFF).  
  
 **/FP:Fast** nelze použít s **/fp: striktní** nebo **/fp: přesné**. Použije se poslední parametr zadaný na příkazovém řádku. Zadání obou **/fp:fast** a **/fp: kromě** generuje chybu kompilátoru.  
  
 Určení [/Za, /Ze (zakázat jazyková rozšíření)](../../build/reference/za-ze-disable-language-extensions.md) (ANSI režim kompatibility) a **/fp:fast** může způsobit neočekávané chování. Například operace s plovoucí desetinnou čárkou s jednoduchou přesností nemusejí být zaokrouhleny na jednoduchou přesnost.  
  
 **s výjimkou [-]**  
 Spolehlivý model výjimek s plovoucí desetinnou čárkou Výjimky jsou vyvolány okamžitě po aktivaci. Tento parametr je standardně vypnutý. Připojením znaménka minus k tomuto parametru ho explicitně zakážete.  
  
 **striktní**  
 Nejpřísnější model plovoucí desetinné čárky **/FP: striktní** způsobí, že [fp_contract –](../../preprocessor/fp-contract.md) být OFF a [fenv_access –](../../preprocessor/fenv-access.md) být ON. **/FP: kromě** je implicitní a je možné zakázat explicitním zadáním **/fp: kromě-**. Při použití s **/fp: kromě-**, **/fp: striktní** vynucuje přísné s plovoucí desetinnou čárkou sémantiku, ale bez ohledu pro výjimečné události.  
  
## <a name="remarks"></a>Poznámky  
 Více **/fp** možnosti lze zadat ve stejné kompilaci.  
  
 Můžete řídit chování s plovoucí desetinnou čárkou podle funkce, najdete v článku [float_control –](../../preprocessor/float-control.md) – Direktiva pragma. Přepíše **/fp** nastavení kompilátoru. Podle osvědčené technické praxe doporučujeme uložit a obnovit místní chování výpočtů s plovoucí desetinnou čárkou:  
  
```cpp  
#pragma float_control(precise, on, push)  
// Code that uses /fp:precise mode  
#pragma float_control(pop)  
```  
  
 Většina s plovoucí desetinnou čárkou optimalizace související s **/fp: striktní**, **/fp: kromě** (a jeho odpovídající direktivy) a `fp_contract` – Direktiva pragma jsou závislé na počítač. **/FP: striktní** a **/fp: kromě** nejsou kompatibilní s **/CLR**.  
  
 **/FP: přesné** je potřeba vyřešit většinu požadavků aplikace s plovoucí desetinnou čárkou. Můžete použít **/fp: kromě** a **/fp: striktní**, ale mohou být některé snížení výkonu. Pokud je nejdůležitější výkon, zvažte použití **/fp:fast**.  
  
 **/FP: striktní**, **/fp:fast**, a **/fp: přesné** režimy přesnost (správnost). Současně může být aktivní pouze jeden. Pokud oba **/fp: striktní** a **/fp: přesné** jsou nastaveny, kompilátor použije, který zpracovává poslední. Obě **/fp: striktní** a **/fp:fast** nelze zadat.  
  
 Další informace najdete v tématu [Microsoft Visual C++ Floating-Point optimalizace](http://msdn.microsoft.com/library/aa289157.aspx).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte **vlastnosti konfigurace** uzlu.  
  
3.  Rozbalte **C/C++** uzlu.  
  
4.  Vyberte **generování kódu** stránku vlastností.  
  
5.  Změnit **plovoucí modelu bodu** vlastnost.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Microsoft Visual C++ plovoucí bodu optimalizace](http://msdn.microsoft.com/library/aa289157.aspx)