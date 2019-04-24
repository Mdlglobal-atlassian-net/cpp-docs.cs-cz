---
title: /EH (model zpracování výjimek)
ms.date: 08/14/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 9f5eed60ecb51abc1d8fbd3c38773bbf782b23a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62271798"
---
# <a name="eh-exception-handling-model"></a>/EH (model zpracování výjimek)

Určuje druh zpracování výjimek v kompilátoru, když k optimalizaci tokeny výjimka zkontroluje a, jestli se má zničit objekty C++, které přesahují rozsah z důvodu výjimky. Pokud **/EH** není zadán, kompilátor umožňuje kódu zachytit asynchronní strukturované výjimky a výjimky jazyka C++, ale nezničí objekty C++, které přesahují rozsah z důvodu asynchronní výjimky.

## <a name="syntax"></a>Syntaxe

> **/EH**{**s**|**a**}[**c**][**r**][**-**]

## <a name="arguments"></a>Arguments

**a**<br/>
Model ošetření výjimek, který zachytává asynchronní (strukturované) a synchronní výjimky (C++) pomocí jazyka C++ `catch(...)` syntaxe.

**s**<br/>
Model ošetření výjimek, který zachytává pouze synchronní výjimky (C++) a instruuje kompilátor, aby předpokládal, že funkce deklarované jako **extern "C"** může vyvolat výjimku.

**c**<br/>
Pokud je použita s **s** (**/EHsc**), zachytává pouze výjimky jazyka C++ a instruuje kompilátor, aby předpokládal, že funkce deklarované jako **extern "C"** nikdy nevyvolají výjimku C++. **/ EHca** je ekvivalentní **/EHa**.

**r**<br/>
Instruuje kompilátor, aby vždy generovat kontroly ukončení za běhu pro všechny **noexcept** funkce. Ve výchozím nastavení, modul runtime vyhledává **noexcept** může být optimalizován okamžitě, pokud kompilátor zjistí funkce volá pouze non-throwing. funkce.

## <a name="remarks"></a>Poznámky

**/EHa** – možnost kompilátoru je používá pro podporu zpracování asynchronních strukturovaných výjimek (SEH) s nativním kódu C++ `catch(...)` klauzuli. K implementaci SEH bez zadání **/EHa**, můžete použít **__try**, **__except**, a **__finally** syntaxe. I když Windows a Visual C++ podporují SEH, důrazně doporučujeme použít zpracování výjimek jazyka C++ podle standardu ISO (**/EHS** nebo **/EHsc**) totiž kód větší přenositelnosti a flexibility. Nicméně v existujícím kódu nebo v určitých typech programů – například v kódu kompilovaném pro podporu modul common language runtime ([/CLR (kompilace Common Language Runtime)](clr-common-language-runtime-compilation.md)) – budete stále muset použít SEH. Další informace najdete v tématu [strukturovaného zpracování výjimek (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).

Určení **/EHa** pokus o zpracování všech výjimek pomocí `catch(...)` může být nebezpečné. Ve většině případů jsou asynchronní výjimky nenapravitelné a měly by se považovat za fatální. Jejich zachycení a zpracování může způsobit poškození procesu a vést k chybám, které lze jen těžko najít a opravit.

Pokud používáte **/EHS** nebo **/EHsc**, pak vaše `catch(...)` klauzule nezachytí asynchronní strukturované výjimky. Narušení přístupu a spravované <xref:System.Exception?displayProperty=fullName> výjimky a objekty v oboru při generování asynchronní výjimky nejsou zničeny, i v případě, že asynchronní výjimka ošetřena.

Pokud používáte **/EHa**, bitové kopie mohou být delší a méně také může provést, protože kompilátor neoptimalizuje **zkuste** agresivně blokovat. Rovněž ponechá filtry výjimek, které automaticky volají destruktory všech místních objektů, přestože kompilátor nezjistí žádný kód, který může vyvolat výjimky jazyka C++. To umožňuje bezpečné uvolnění zásobníku pro asynchronní výjimky a výjimky jazyka C++. Při použití **/EHS**, kompilátor předpokládá, že výjimky může probíhat jedině v **throw** prohlášení nebo ve volání funkce. To umožňuje kompilátoru eliminovat kód pro sledování životnosti neuvolnitelných objektů, což může výrazně zmenšit velikost kódu.

Doporučujeme, abyste propojení objekty zkompilovanými s použitím **/EHa** spolu s objekty zkompilovanými s použitím **/EHS** nebo **/EHsc** do stejného spustitelného modulu. Pokud je nutné ošetřit asynchronní výjimky pomocí **/EHa** kdekoli v modulu, použijte **/EHa** k komplikaci veškerého kódu v modulu. Můžete použít ve stejném modulu jako kód, který je zkompilován pomocí syntaxe zpracování strukturovaných výjimek **/EHS**, nemůžete ale kombinovat syntaxi SEH s **zkuste**, **throw**a **catch** ve stejné funkci.

Použití **/EHa** Pokud chcete zachytit výjimku, kterou vyvolá něco jiného než **throw**. Tento příklad vygeneruje a zachytí strukturovanou výjimku:

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

**Parametr/EHC** možnost vyžaduje, aby **/EHS** nebo **/EHa** je zadán. **/CLR** znamená možnost **/EHa** (to znamená, **/CLR** **/EHa** je nadbytečné). Kompilátor vygeneruje chybu, pokud **/EHS** nebo **/EHsc** se používá po **/CLR**. Optimalizace toto chování neovlivňují. Při zachycení výjimky vyvolá kompilátor destruktor třídy nebo destruktory objektů, které jsou ve stejném oboru jako výjimka. Pokud výjimka není zachycena, nejsou tyto destruktory spuštěny.

Informace o omezeních zpracování výjimek **/CLR**, naleznete v tématu [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

Možnost může být zrušena symbolem **-**. Například **/EHsc-** je interpretován jako **/EHS** **/EHc-** a je ekvivalentní **/EHS**.

**/EHr** – možnost kompilátoru vynutí kontroly ukončení za běhu ve všech funkcí, které mají **noexcept** atribut. Ve výchozím nastavení, kontroly za běhu může být vypuštěn Pokud back-endu kompilátoru zjistí, že funkce jen volá *non-throwing.* funkce. Non-throwing. funkce jsou všechny funkce, které mají atribut, který určuje, že můžou být vyvolány žádné výjimky. To zahrnuje funkce označené **noexcept**, `throw()`, `__declspec(nothrow)`a kdy **parametr/EHC** není zadána, **extern "C"** funkce. Non-throwing. funkce také zahrnovat všechny, které kompilátor zjistil jsou non-throwing. pomocí kontroly. Výchozí hodnota je možné nastavit explicitně pomocí **/EHr-**.

Atribut non-throwing. však není zaručeno, že funkce mohou být vyvolány žádné výjimky. Na rozdíl od chování **noexcept** funkce, a kompilátorem MSVC bude považovat za výjimka vyvolaná objektem funkce deklarovaná pomocí `throw()`, `__declspec(nothrow)`, nebo **extern "C"** jako nedefinované chování. Funkce, které používají tyto deklarace tři atributy Nevynucovat kontroly ukončení za běhu pro výjimky. Můžete použít **/EHr** možnost, abyste mohli snadno identifikovat toto nedefinované chování, můžete vynutit bude kompilátor generovat kontroly za běhu pro neošetřené výjimky, které řídicí **noexcept** funkce.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete v projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [vlastnosti kompilátoru a sestavení nastavte C++ v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte **vlastnosti konfigurace** > **C/C++** > **generování kódu**.

1. Upravit **povolit výjimky jazyka C++** vlastnost.

   Nebo nastavte **povolit výjimky jazyka C++** k **ne**a pak na **příkazového řádku** stránce vlastností **další možnosti** přidejte – možnost kompilátoru.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Viz také:

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Ošetření chyb a výjimek](../../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
