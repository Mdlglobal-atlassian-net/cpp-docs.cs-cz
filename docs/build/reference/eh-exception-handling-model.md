---
title: -EH (Model zpracování výjimek) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
dev_langs:
- C++
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96b009a9f209ffcc4bb84550c5f37680ef71c9fe
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="eh-exception-handling-model"></a>/EH (model zpracování výjimek)
Určuje typ zpracování výjimky používané kompilátoru, když k optimalizaci tokeny výjimka kontroluje a jestli zrušení C++ objekty, které z důvodu výjimky se dostala mimo rozsah. Pokud **/EH** není zadán, kompilátor zachytí asynchronní strukturovaných výjimky a výjimky jazyka C++, ale nezničí C++ objekty, které z důvodu asynchronní výjimky se dostala mimo rozsah.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/EH{s|a}[c][r][-]  
```  
  
## <a name="arguments"></a>Arguments  
 **a**  
 Model zpracování výjimek, který zachytává asynchronní (strukturované) i synchronní výjimky (C++)  
  
 **s**  
 Model zpracování výjimek, který zachytí pouze výjimky jazyka C++ a říká kompilátoru předpokládají, že funkce deklarované jako `extern "C"` může vyvolat výjimku.  
  
 **c**  
 Pokud se používá s **s** (**/EHsc**), zachytí pouze výjimky jazyka C++ a říká kompilátoru předpokládají, že funkce deklarované jako `extern "C"` nikdy výjimku C++ vyvolat.  
  
 **/ EHca** je ekvivalentní **/EHa**.  
  
 **r**  
 Určuje, kompilátor vždy generovat kontroly ukončení modulu runtime pro všechny `noexcept` funkce. Ve výchozím modulu runtime vyhledává `noexcept` může optimalizovat rychle, pokud kompilátor určuje funkce volá pouze bez funkce vyvolávání.  
  
## <a name="remarks"></a>Poznámky  
 **/EHa** – možnost kompilátoru se používá pro podporu asynchronní strukturované zpracování výjimek (SEH) s nativním kódu C++ `catch(...)` klauzule. K implementaci SEH bez zadání **/EHa**, můžete použít `__try`, `__except`, a `__finally` syntaxe. Přestože systém Windows a Visual C++ podporují SEH, důrazně doporučujeme použít zpracovávání výjimek v jazyce C++ standardem ISO (**/EHs** nebo **/EHsc**) vzhledem k tomu, že umožňuje kód víc přenosného a flexibilní. Nicméně, v existující kód nebo pro určité typy programů – například v kódu zkompilovat pro podporu modul common language runtime ([/CLR (kompilace Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)) – stále možná budete muset použít SEH. Další informace najdete v tématu [strukturované zpracování výjimek (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).  
  
 Určení **/EHa** a při pokusu o zpracování všech výjimek pomocí `catch(...)` může být nebezpečný. Ve většině případů jsou asynchronní výjimky nenapravitelné a měly by se považovat za fatální. Jejich zachycení a zpracování může způsobit poškození procesu a vést k chybám, které lze jen těžko najít a opravit.  
  
 Pokud používáte **/EHs** nebo **/EHsc**, pak vaše `catch(...)` klauzule nezachytí asynchronní strukturovaných výjimky. Přístup k narušení a spravované <xref:System.Exception?displayProperty=fullName> nejsou zachycení výjimky a objektů v oboru, když se vygeneruje výjimku asynchronní nejsou zničení, i když je asynchronní výjimka ošetřena.  
  
 Pokud používáte **/EHa**, bitové kopie může být vyšší a nižší také může provést, protože není optimální pro kompilátor `try` jako intenzivně blokovat. Rovněž ponechá v filtry výjimek, které automaticky volání destruktory všech objektů místní i v případě, že kompilátor nezná kód, který výjimku C++ můžete vyvolat. To umožňuje bezpečné zásobníku unwinding pro asynchronní výjimky stejně jako u výjimky jazyka C++. Při použití **/EHs**, kompilátor předpokládá, že výjimky může dojít pouze v `throw` prohlášení nebo ve volání funkce. To umožňuje kompilátoru eliminovat kód pro sledování životnosti neuvolnitelných objektů, což může výrazně zmenšit velikost kódu.  
  
 Doporučujeme, abyste není propojit objekty zkompilovat pomocí **/EHa** společně s objekty zkompilovat pomocí **/EHs** ve stejném spustitelného souboru modulu. Pokud máte pro zpracování asynchronní výjimky pomocí **/EHa** kdekoli v modulu, použijte **/EHa** zkompilovat všechny kód v modulu. Můžete použít strukturovaného zpracování v modulu stejný jako kód, který je sestaven pomocí syntaxe výjimek **/EHs**, ale není možné kombinovat syntaxi SEH pomocí `try`, `throw`, a `catch` ve stejné funkci.  
  
 Použití **/EHa** Pokud budete chtít zachytit výjimku, která se vyvolá jiné než cokoli, co `throw`. Tento příklad vygeneruje a zachytí strukturovanou výjimku:  
  
```cpp  
// compiler_options_EHA.cpp  
// compile with: /EHa  
#include <iostream>  
#include <excpt.h>  
using namespace std;  
  
void fail() {   // generates SE and attempts to catch it using catch(...)  
   try {  
      int i = 0, j = 1;  
      j /= i;   // This will throw a SE (divide by zero).  
      printf("%d", j);   
   }  
   catch(...) {   // catch block will only be executed under /EHa  
      cout<<"Caught an exception in catch(...)."<<endl;  
   }  
}  
  
int main() {  
   __try {  
      fail();   
   }  
  
   // __except will only catch an exception here  
   __except(EXCEPTION_EXECUTE_HANDLER) {     
   // if the exception was not caught by the catch(...) inside fail()  
      cout << "An exception was caught in __except." << endl;  
   }  
}  
```  
  
 **/EHc** možnost vyžaduje, aby **/EHs** nebo **/EHa** je zadán. **/CLR** znamená možnost **/EHa** (tedy **/ / CLR EHa** je redundantní). Kompilátor vygeneruje chybu, pokud **/EHs [c]** slouží po **/CLR**. Optimalizace toto chování neovlivňují. Při zachycení výjimky vyvolá kompilátor destruktor třídy nebo destruktory objektů, které jsou ve stejném oboru jako výjimka. Pokud výjimka není zachycena, nejsou tyto destruktory spuštěny.  
  
 Informace o omezení za zpracování výjimek **/CLR**, najdete v části [_set_se_translator –](../../c-runtime-library/reference/set-se-translator.md).  
  
 Možnost lze vymazat pomocí symbol **-**. Například **/EHsc-** interpretována jako **/EHs /EHc-** a je ekvivalentní **/EHs**.  
  
 **/EHr** – možnost kompilátoru vynutí kontroly ukončení modulu runtime v všechny funkce, které mají `noexcept` atribut. Ve výchozím modulu runtime kontroly může optimalizovat rychle Pokud back-endu kompilátoru určuje pouze volá funkci *– vyvolání* funkce. Funkce vyvolávání bez jsou všechny funkce, které mají atribut, který určuje, že může být vyvolány žádné výjimky. To zahrnuje funkce, které jsou označeny `noexcept`, `throw()`, `__declspec(nothrow)`a kdy **/EHc** není zadaný, `extern "C"` funkce. Funkce vyvolávání bez také zahrnovat všechny, které určil kompilátor jsou bez vyvolávání pomocí kontroly. Výchozí hodnota je možné nastavit explicitně pomocí **/EHr-**.  
  
 Atribut – vyvolání však není zaručeno, že funkce můžete vyvolat žádné výjimky. Na rozdíl od chování `noexcept` funkce, Visual C++ compiler zvažuje výjimka vyvolaná objektem deklarováno s použitím funkce `throw()`, `__declspec(nothrow)`, nebo `extern "C"` jako nedefinované chování. Funkce, které používají tyto tři deklarace atributy Nevynucovat kontroly ukončení modulu runtime pro výjimky. Můžete použít **/EHr** možnost, který vám pomůže identifikovat toto chování nedefinované vynucením kompilátoru generovat runtime kontroluje neošetřených výjimek, které vyhnuli `noexcept` funkce.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  V levém podokně rozbalte **vlastnosti konfigurace**, **C/C++**, **generování kódu**.  
  
3.  Změnit **povolit výjimky jazyka C++** vlastnost.  
  
     Nebo nastavte **povolit výjimky jazyka C++** k **ne**a pak na **příkazového řádku** stránka Vlastnosti, **další možnosti** pole, přidejte – možnost kompilátoru.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru](../../build/reference/compiler-options.md)   
 [Nastavení možností kompilátoru](../../build/reference/setting-compiler-options.md)   
 [Ošetření chyb a výjimek](../../cpp/errors-and-exception-handling-modern-cpp.md)   
 [Specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md)   
 [Strukturované zpracování výjimek (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)