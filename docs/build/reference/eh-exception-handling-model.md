---
title: /EH (model ošetření výjimek)
description: Referenční příručka k možnostem kompilátoru Microsoft C++ /EH (model zpracování výjimek) v sadě Visual Studio.
ms.date: 04/14/2020
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
no-loc:
- SEH
- try
- catch
- throw
- extern
- finally
- noexcept
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
ms.openlocfilehash: 68d6af657e7c20c0f5e84674dd91803beb35fba0
ms.sourcegitcommit: 0e4feb35b47c507947262d00349d4a893863a6d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81396287"
---
# <a name="eh-exception-handling-model"></a>/EH (model ošetření výjimek)

Určuje podporu modelu zpracování výjimek generované kompilátorem. Argumenty určují, `catch(...)` zda se má použít syntaxe pro strukturované i standardní výjimky jazyka C++, **noexcept** zda throw ** extern ** se na výjimky předpokládá kód "C" a zda má být některé kontroly optimalizovány.

## <a name="syntax"></a>Syntaxe

> **`/EHa`**[**`-`**]\
> **`/EHs`**[**`-`**]\
> **`/EHc`**[**`-`**]\
> **`/EHr`**[**`-`**]

## <a name="arguments"></a>Argumenty

**`a`**\
Umožňuje standardní odvíjení zásobníku C++. Zachytí strukturované (asynchronní) i standardní c++ (synchronní) `catch(...)` výjimky při použití syntaxe. **`/EHa`** přepíše **`/EHs`** oba **`/EHc`** a argumenty.

**`s`**\
Umožňuje standardní odvíjení zásobníku C++. Zachytí pouze standardní výjimky jazyka `catch(...)` C++ při použití syntaxe. Pokud **`/EHc`** není také zadán, kompilátor předpokládá, že throw funkce deklarované jako ** extern "C"** může výjimku Jazyka C++.

**`c`**\
Při použití **`/EHs`** s , kompilátor předpokládá, že throw funkce deklarované jako ** extern "C"** nikdy výjimku Jazyka C++. Nemá žádný účinek **`/EHa`** při použití **`/EHca`** s (to znamená, že je ekvivalentní **`/EHa`**). **`/EHc`** je ignorována, pokud **`/EHs`** není zadána nebo **`/EHa`** není zadána.

**`r`**\
Říká kompilátoru vždy generovat kontroly **noexcept** ukončení za běhu pro všechny funkce. Ve výchozím nastavení runtime kontroly pro **noexcept** může být optimalizována pryč, pokud kompilátor určuje funkce volá pouze non-throwing funkce. Tato možnost poskytuje přísné shody Jazyka C++ za cenu nějakého kódu navíc. **`/EHr`** je ignorována, pokud **`/EHs`** není zadána nebo **`/EHa`** není zadána.

**`-`**\
Vymaže argument předchozí možnosti. Například **`/EHsc-`** je interpretován **`/EHs /EHc-`** jako , a **`/EHs`** je ekvivalentní .

**`/EH`** argumenty mohou být specifikovány samostatně nebo sdružené v libovolném pořadí. Pokud je zadána více než jedna instance stejného argumentu, poslední přepíše všechny předchozí.  Například **`/EHr- /EHc /EHs`** je stejný **`/EHscr-`** jako **`/EHscr- /EHr`** , a má **`/EHscr`** stejný účinek jako .

## <a name="remarks"></a>Poznámky

### <a name="default-exception-handling-behavior"></a>Výchozí chování zpracování výjimek

Kompilátor vždy generuje kód, který podporuje zpracování asynchronní strukturované výjimky (SEH). Ve výchozím nastavení (to **`/EHsc`** **`/EHs`** znamená, **`/EHa`** pokud není zadánžádný SEH , nebo možnost) kompilátor podporuje obslužné rutiny v nativní klauzuli C++. `catch(...)` Však také generuje kód, který podporuje pouze částečně výjimky jazyka C++. Výchozí výjimka unwinding kód nezničí automatické C++ objekty mimo [try](../../cpp/try-throw-and-catch-statements-cpp.md) bloky, které jdou mimo rozsah z důvodu výjimky. Nevracení prostředků a nedefinované chování může způsobit, když je vyvolána výjimka jazyka C++.

### <a name="standard-c-exception-handling"></a>Standardní zpracování výjimek jazyka C++

Plná podpora kompilátoru pro model zpracování výjimek Standard **`/EHsc`** C++, který bezpečně odpočívá v vyžaduje objekty zásobníku (doporučeno) **`/EHs`** nebo **`/EHa`**.

Pokud **`/EHs`** používáte **`/EHsc`** nebo `catch(...)` , pak vaše catch klauzule nejsou asynchronní strukturované výjimky. Všechna porušení přístupu <xref:System.Exception?displayProperty=fullName> a spravované výjimky neuvíznou. A objekty v oboru při výskytu asynchronní výjimky nejsou zničeny, i v případě, že kód zpracovává asynchronní výjimku. Toto chování je argumentpro opuštění strukturované výjimky neošetřené. Místo toho zvažte tyto výjimky fatální.

Při použití **`/EHs`** **`/EHsc`** nebo kompilátor předpokládá, že výjimky **throw** může dojít pouze na příkaz nebo při volání funkce. Tento předpoklad umožňuje kompilátoru eliminovat kód pro sledování životnosti mnoha unwindable objektů, které mohou výrazně snížit velikost kódu. Pokud používáte **`/EHa`**, spustitelný obraz může být větší a pomalejší, **try** protože kompilátor neoptimalizuje bloky tak agresivně. Také ponechá ve filtrech výjimek, které automaticky vyčistit místní objekty, throw i v případě, že kompilátor nevidí žádný kód, který může výjimku Jazyka C++.

### <a name="structured-and-standard-c-exception-handling"></a>Strukturované a standardní zpracování výjimek jazyka C++

Možnost **`/EHa`** kompilátoru umožňuje bezpečné odvíjení zásobníku pro asynchronní výjimky i výjimky jazyka C++. Podporuje zpracování standardníc++ a strukturované výjimky pomocí nativní `catch(...)` klauzule C++. Chcete-li SEH implementovat bez zadání **`/EHa`**, můžete použít **syntaxi __try**, **__except**a **__finally.** Další informace naleznete [v tématu Strukturované zpracování výjimek](../../cpp/structured-exception-handling-c-cpp.md).

> [!IMPORTANT]
> Určení **`/EHa`** a pokus o zpracování všech `catch(...)` výjimek pomocí může být nebezpečné. Ve většině případů jsou asynchronní výjimky nenapravitelné a měly by se považovat za fatální. Jejich zachycení a zpracování může způsobit poškození procesu a vést k chybám, které lze jen těžko najít a opravit.
>
> I když systém Windows a SEHVisual C++ podporují , důrazně doporučujeme použít**`/EHsc`** zpracování **`/EHs`** výjimek standardu ISO C++ ( nebo ). Díky tomu je váš kód přenosnější a flexibilnější. Stále mohou být časy, SEH které budete muset použít ve starším kódu nebo pro určité druhy programů. Je vyžadována v kódu zkompilovaném pro podporu běžného jazyka runtime ([/clr](clr-common-language-runtime-compilation.md)), například. Další informace naleznete [v tématu Strukturované zpracování výjimek](../../cpp/structured-exception-handling-c-cpp.md).
>
> Doporučujeme, abyste nikdy nepropojili soubory objektů zkompilované pomocí **`/EHa`** souborů zkompilovaných pomocí **`/EHs`** nebo **`/EHsc`** ve stejném spustitelném modulu. Pokud máte zpracovat asynchronní výjimku **`/EHa`** pomocí kdekoli v **`/EHa`** modulu, použijte ke kompilaci všech kód v modulu. Můžete použít strukturované zpracování výjimek syntaxe ve stejném modulu **`/EHs`** jako kód, který je kompilován pomocí . Syntaxi však nelze SEH kombinovat s c++ **try**, **throw** a **catch** ve stejné funkci.

Použijte, **`/EHa`** pokud catch chcete výjimku, která je vyvolána něčím jiným než **throw**. Tento příklad vygeneruje a zachytí strukturovanou výjimku:

```cpp
// compiler_options_EHA.cpp
// compile with: /EHa
#include <iostream>
#include <excpt.h>
using namespace std;

void fail()
{
    // generates SE and attempts to catch it using catch(...)
    try
    {
        int i = 0, j = 1;
        j /= i;   // This will throw a SE (divide by zero).
        printf("%d", j);
    }
    catch(...)
    {
        // catch block will only be executed under /EHa
        cout << "Caught an exception in catch(...)." << endl;
    }
}

int main()
{
    __try
    {
        fail();
    }

    // __except will only catch an exception here
    __except(EXCEPTION_EXECUTE_HANDLER)
    {
        // if the exception was not caught by the catch(...) inside fail()
        cout << "An exception was caught in __except." << endl;
    }
}
```

### <a name="exception-handling-under-clr"></a>Zpracování výjimek pod /clr

Možnost **`/clr`** znamená **`/EHa`** (to **`/clr /EHa`** znamená, že je redundantní). Kompilátor vygeneruje **`/EHs`** chybu, pokud nebo **`/EHsc`** je použit po **`/clr`**. Optimalizace nemají vliv na toto chování. Když je zachycena výjimka, kompilátor vyvolá destruktory třídy pro všechny objekty, které jsou ve stejném oboru jako výjimka. Pokud výjimka není zachycena, tyto destruktory nejsou spuštěny.

Informace o omezeních **`/clr`** zpracování výjimek podle najdete v [tématu _set_se_translator](../../c-runtime-library/reference/set-se-translator.md).

### <a name="runtime-exception-checks"></a>Kontroly výjimek za běhu

Možnost **`/EHr`** vynutí kontroly ukončení za **noexcept** běhu ve všech funkcích, které mají atribut. Ve výchozím nastavení runtime kontroly mohou být optimalizovány pryč, pokud back-end kompilátoru zjistí, že funkce volá pouze *non-throwing* funkce. Non-throwing funkce jsou všechny funkce, které mají atribut, který určuje žádné výjimky mohou být vyvolány. Zahrnují funkce **noexcept** označené `throw()` `__declspec(nothrow)`, , **`/EHc`** , a, pokud je zadán, ** extern "C"** funkce. Non-throwing funkce také všechny, které kompilátor určil, jsou non-throwing kontrolou. Výchozí chování můžete explicitně **`/EHr-`** nastavit pomocí aplikace .

Atribut bez vyvolání není zárukou, že výjimky nelze vyvolat funkcí. Na rozdíl od **noexcept** chování funkce kompilátor MSVC považuje výjimku vyvolanou funkcí deklarovanou pomocí `throw()`, `__declspec(nothrow)`, nebo ** extern "C"** za nedefinované chování. Funkce, které používají tyto tři atributy deklarace nevynucuje kontroly ukončení za běhu pro výjimky. Můžete použít **`/EHr`** možnost, která vám pomůže identifikovat toto nedefinované chování, vynucením kompilátoru **noexcept** generovat kontroly za běhu pro neošetřené výjimky, které uniknou funkci.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Nastavení možnosti v sadě Visual Studio nebo programově

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio

1. Otevřete dialogové okno **Stránky vlastností** projektu. Podrobnosti naleznete v [tématu Nastavení kompilátoru jazyka C++ a vlastnosti sestavení v sadě Visual Studio](../working-with-project-properties.md).

1. Vyberte možnost Generování**kódu** **Vlastnosti** > konfigurace**c/c++** > .

1. Upravte vlastnost **Povolit výjimky jazyka C++.**

   Nebo nastavte **povolit výjimky jazyka C++** na **ne**a potom na stránce vlastností **příkazového řádku** v poli **Další možnosti** přidejte možnost kompilátoru.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

- Viz třída <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>.

## <a name="see-also"></a>Viz také

[Možnosti kompilátoru MSVC](compiler-options.md)\
[Syntaxe příkazového řádku kompilátoru MSVC](compiler-command-line-syntax.md)\
[Chyby a zpracování výjimek](../../cpp/errors-and-exception-handling-modern-cpp.md)\
[Specifikace výjimekthrow( )](../../cpp/exception-specifications-throw-cpp.md)\
[Strukturované zpracování výjimek (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)
