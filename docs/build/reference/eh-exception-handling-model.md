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
ms.openlocfilehash: 8546b14995317afb57e4cc23a5d6f81c2172a1a6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328298"
---
# <a name="eh-exception-handling-model"></a>/EH (model zpracování výjimek)

Určuje druh zpracování výjimek, které kompilátor používá, kdy optimalizovat kontroly výjimek a zda zničit objekty Jazyka C++, které z důvodu výjimky nespadají do oboru. Pokud **/EH** není zadán, kompilátor umožňuje kódu zachytit asynchronní strukturované výjimky a výjimky Jazyka C++, ale nezničí objekty Jazyka C++, které jsou mimo rozsah z důvodu asynchronní výjimky.

## <a name="syntax"></a>Syntaxe

> **/EH**{**s**|**a**}[**c**][**r**][**-**]

## <a name="arguments"></a>Argumenty

**A**<br/>
Model zpracování výjimek, který zachycuje asynchronní (strukturované) a synchronní (C++) výjimky pomocí syntaxe jazyka C++. `catch(...)`

**S**<br/>
Model zpracování výjimek, který zachycuje pouze synchronní (C++) výjimky a říká kompilátoru předpokládat, že funkce deklarované jako **extern "C"** může vyvolat výjimku.

**C**<br/>
Při použití s **s** (**/EHsc),** zachytí pouze výjimky Jazyka C++ a řekne kompilátoru, aby předpokládal, že funkce deklarované jako **extern "C"** nikdy nevyvolá výjimku Jazyka C++. **/EHca** je ekvivalentní **/EHa**.

**R**<br/>
Říká kompilátoru vždy generovat kontroly ukončení za běhu pro všechny **noexcept** funkce. Ve výchozím nastavení runtime kontroly **noexcept** může být optimalizovány pryč, pokud kompilátor určuje funkce volá pouze non-throwing funkce.

## <a name="remarks"></a>Poznámky

Možnost kompilátoru **/EHa** se používá k podpoře asynchronnístrukturní ho zpracování `catch(...)` výjimek (SEH) s nativní klauzulí C++. Chcete-li implementovat SEH bez zadání **/EHa**, můžete použít **syntaxi __try**, **__except**a **__finally.** Přestože Windows a Visual C++ podporují SEH, důrazně doporučujeme použít zpracování výjimek iso-standard C++ (**/EHs** nebo **/EHsc),** protože umožňuje přenositelnost kódu a flexibilitu. Nicméně v existujícím kódu nebo pro určité druhy programů – například v kódu kompilovaném pro podporu běžného jazykového runtime ([/clr (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md))– stále může být možné použít SEH. Další informace naleznete [v tématu Strukturované zpracování výjimek (C/C++)](../../cpp/structured-exception-handling-c-cpp.md).

Zadání **/EHa** a pokusu o zpracování `catch(...)` všech výjimek pomocí může být nebezpečné. Ve většině případů jsou asynchronní výjimky nenapravitelné a měly by se považovat za fatální. Jejich zachycení a zpracování může způsobit poškození procesu a vést k chybám, které lze jen těžko najít a opravit.

Pokud používáte **/EHs** nebo **/EHsc**, pak vaše `catch(...)` klauzule nezachytí asynchronní strukturované výjimky. Narušení přístupu <xref:System.Exception?displayProperty=fullName> a spravované výjimky nejsou zachyceny a objekty v oboru při generování asynchronní výjimky nejsou zničeny i v případě, že je zpracována asynchronní výjimka.

Pokud používáte **/EHa**, obraz může být větší a může provádět méně dobře, protože kompilátor neoptimalizuje **try** blok tak agresivně. Také ponechá ve filtrech výjimek, které automaticky volají destruktory všech místních objektů i v případě, že kompilátor nevidí žádný kód, který může vyvolat výjimku jazyka C++. To umožňuje bezpečné odvíjení zásobníku pro asynchronní výjimky, stejně jako pro výjimky jazyka C++. Při použití **/EHs**kompilátor předpokládá, že výjimky může dojít pouze na **throw** příkaz nebo na volání funkce. To umožňuje kompilátoru eliminovat kód pro sledování životnosti neuvolnitelných objektů, což může výrazně zmenšit velikost kódu.

Doporučujeme nepropojovat objekty zkompilované pomocí **/EHa** společně s objekty zkompilovanými pomocí **/EHs** nebo **/EHsc** ve stejném spustitelném modulu. Pokud máte zpracovat asynchronní výjimku pomocí **/EHa** kdekoli ve vašem modulu, použijte **/EHa** zkompilovat veškerý kód v modulu. Můžete použít strukturované výjimky zpracování syntaxe ve stejném modulu jako kód, který je kompilován pomocí **/EHs**, ale nelze kombinovat syntaxi SEH s **try**, **throw**a **catch** ve stejné funkci.

Použijte **/EHa,** pokud chcete zachytit výjimku, která je vyvolána něčím jiným než **throw**. Tento příklad vygeneruje a zachytí strukturovanou výjimku:

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

Možnost **/EHc** vyžaduje, aby byla zadána **/EHs** nebo **/EHa.** Možnost **/clr** implikuje **/EHa** (to **znamená/clr** **/EHa** je redundantní). Kompilátor vygeneruje chybu, pokud **/EHs** nebo **/EHsc** se používá po **/clr**. Optimalizace toto chování neovlivňují. Při zachycení výjimky vyvolá kompilátor destruktor třídy nebo destruktory objektů, které jsou ve stejném oboru jako výjimka. Pokud výjimka není zachycena, nejsou tyto destruktory spuštěny.

Informace o omezeních zpracování výjimek v části **/clr**naleznete [v tématu _set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

Tuto možnost lze vymazat pomocí **-** symbolu . Například **/EHsc-** je interpretován jako **/EHs** **/EHc-** a je ekvivalentní **/EHs**.

Možnost kompilátoru **/EHr** vynutí kontroly ukončení za běhu ve všech funkcích, které mají atribut **noexcept.** Ve výchozím nastavení runtime kontroly mohou být optimalizovány pryč, pokud back-end kompilátoru zjistí, že funkce volá pouze *non-throwing* funkce. Non-throwing funkce jsou všechny funkce, které mají atribut, který určuje žádné výjimky mohou být vyvolány. To zahrnuje funkce označené `throw()` `__declspec(nothrow)` **noexcept**, , a, když **/EHc** je zadán, **extern "C"** funkce. Non-throwing funkce také všechny, které kompilátor určil, jsou non-throwing kontrolou. Výchozí nastavení můžete explicitně nastavit pomocí **parametru /EHr-**.

Atribut bez vyvolání však není zárukou, že funkce nemůže vyvolat žádné výjimky. Na rozdíl od chování **noexcept** funkce Kompilátor MSVC považuje výjimku `throw()`vyvolána funkce deklarované pomocí , `__declspec(nothrow)`, nebo **extern "C"** jako nedefinované chování. Funkce, které používají tyto tři atributy deklarace nevynucují kontroly ukončení za běhu pro výjimky. Můžete použít **/EHr** možnost vám pomůže identifikovat toto nedefinované chování, vynucením kompilátor generovat kontroly za běhu pro neošetřené výjimky, které uniknou **noexcept** funkce.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte možnost Generování**kódu** **Vlastnosti** > konfigurace**c/c++** > .

1. Upravte vlastnost **Povolit výjimky jazyka C++.**

   Nebo nastavte **povolit výjimky jazyka C++** na **ne**a potom na stránce vlastností **příkazového řádku** v poli **Další možnosti** přidejte možnost kompilátoru.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Viz také

[Parametry kompilátoru MSVC](compiler-options.md)<br/>
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)<br/>
[Chyby a zpracování výjimek](../../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[Specifikace výjimek (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
