---
title: try-finally – příkaz
ms.date: 11/19/2018
f1_keywords:
- __try
- _try
- __leave_cpp
- __leave
- __finally_cpp
- __try_cpp
- __finally
- _finally
helpviewer_keywords:
- __try keyword [C++]
- __finally keyword [C++]
- __leave keyword [C++]
- try-catch keyword [C++], try-finally keyword
- try-finally keyword [C++]
- __finally keyword [C++], try-finally statement syntax
- __leave keyword [C++], try-finally statement
- structured exception handling [C++], try-finally
ms.assetid: 826e0347-ddfe-4f6e-a7bc-0398e0edc7c2
ms.openlocfilehash: d2a1c63f686b46aad4e174c86895f6f9fc00d260
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58778335"
---
# <a name="try-finally-statement"></a>try-finally – příkaz

**Microsoft Specific**

Následující syntaxe popisuje **try-finally** – příkaz:

> **\_\_Zkuste**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;strážené kódu<br/>
> }<br/>
> **\_\_Nakonec**<br/>
> {<br/>
> &nbsp;&nbsp;&nbsp;&nbsp;ukončení programu<br/>
> }<br/>

## <a name="grammar"></a>Gramatika

*try-finally-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\_\_Zkuste** *compound-statement*  **\_ \_nakonec** *compound-statement*

**Try-finally** příkaz je rozšířením společnosti Microsoft pro jazyky C a C++, které umožňuje cílovým aplikacím zaručit spuštění kódu čištění, když dojde k přerušení vykonání bloku kódu. Čištění se skládá z úlohy, jako jsou rušení přidělení paměti, zavírání souborů a uvolněním popisovačů souborů. **Try-finally** příkaz je užitečné hlavně pro rutiny, které mají několika místech, kde se provede kontrola pro chybu, která by mohla způsobit předčasné vrátit z rutiny.

Související informace a ukázky kódu najdete v tématu [zkuste-except – příkaz](../cpp/try-except-statement.md). Další informace o obecně zpracování strukturovaných výjimek naleznete v tématu [strukturovaného zpracování výjimek](../cpp/structured-exception-handling-c-cpp.md). Další informace o zpracování výjimek ve spravovaných aplikacích s C++vyhodnocovací, naleznete v tématu [zpracování výjimek v/CLR](../extensions/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> Strukturované zpracování výjimek funguje na architektuře Win32 pro zdrojové soubory jazyka C i C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Zpracování výjimek jazyka C++ je také více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu. Pro programy C++ je doporučeno použití mechanismu zpracování výjimek jazyka C++ ([try, catch a throw](../cpp/try-throw-and-catch-statements-cpp.md) příkazů).

Složený příkaz za **__try** klauzule je chráněná část. Složený příkaz za **__finally** klauzule je obslužná rutina ukončení. Obslužná rutina udává sadu akcí, které jsou spouštěny, když byl ukončen chráněné části, bez ohledu na to, zda je výjimka (abnormální ukončení) nebo standardní fall prostřednictvím (normální ukončení) byl ukončen chráněné části.

Ovládací prvek dosáhne **__try** prohlášení jednoduchý sekvenční provádění (fall prostřednictvím). Když přejde do ovládacího prvku **__try**, jeho přidružená obslužná rutina stane aktivním. Pokud tok řízení dosáhne konce bloku try, spuštění probíhá následujícím způsobem:

1. Je vyvolána obslužná rutina ukončení.

1. Po dokončení obslužné rutiny ukončení provádění pokračuje **__finally** příkazu. Bez ohledu na to, jak chráněné části končí (třeba přes **goto** mimo tělo strážených nebo **vrátit** příkaz), je provedena obslužná rutina ukončení *před* Tok řízení přesune mimo chráněnou část.

   A **__finally** příkaz neblokuje hledání pro obslužnou rutinu příslušné výjimky.

Pokud dojde k výjimce v **__try** blok, operační systém musí najít obslužné rutiny výjimky nebo program se nezdaří. Pokud obslužná rutina nenajde, všechny **__finally** bloky jsou spouštěny a provádění pokračuje v obslužné rutině.

Předpokládejme například, řadu volání funkcí propojení funkce A funkce D, jak je znázorněno na následujícím obrázku. Každá funkce má jednu obslužnou rutinu ukončení. Pokud je výjimka vyvolána ve funkci D a zpracovávány v A, označují obslužné rutiny ukončení jako systém unwinds zásobníku v tomto pořadí: D, C, B.

![Pořadí ukončení&#45;provádění obslužné rutiny](../cpp/media/vc38cx1.gif "pořadí ukončení&#45;provádění obslužné rutiny") <br/>
Pořadí provádění obslužné rutiny ukončení

> [!NOTE]
> Try-finally chování se liší od jiných jazycích, které podporují použití **nakonec**, jako je C#.  Jediný **__try** může obsahovat buď, ale ne obě sady **__finally** a **__except**.  Pokud jsou obě být použity současně, vnějším zkuste – s výjimkou příkaz musíte uzavřít vnitřní příkaz try-finally.  Pravidla určující při každý blok se spustí se také liší.

Z důvodu kompatibility s předchozími verzemi **_try**, **_finally**, a **_leave** jsou synonyma pro **__try**, **__ Nakonec**, a **__leave** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) určena.

## <a name="the-leave-keyword"></a>Klíčové slovo __leave

**__Leave** – klíčové slovo je platné pouze uvnitř chráněné části **try-finally** příkazu a jeho účinkem je přechod na konec chráněné části. Běh programu pokračuje prvním příkazem v obslužné rutiny ukončení.

A **goto** příkaz lze také přejít mimo chráněnou část, ale sníží výkon, protože vyvolá odvíjení zásobníku. **__Leave** příkazu je mnohem efektivnější, protože nezpůsobí odvíjení zásobníku.

## <a name="abnormal-termination"></a>Abnormální ukončení

Ukončení **try-finally** pomocí příkazu [longjmp](../c-runtime-library/reference/longjmp.md) funkci run-time je považován za abnormální ukončení. Není povoleno přejít do **__try** příkazu, ale právní přejít mimo něj. Všechny **__finally** příkazy, které jsou aktivní mezi bodem odeslání (normální ukončení **__try** bloku) a cíl ( **__except** block, který zpracovává výjimku) musí být spuštěn. Tomu se říká místní uvolnění.

Pokud **zkuste** bloku je předčasně ukončen z jakéhokoli důvodu, včetně skok mimo blok, systém provádí přidružené **nakonec** bloku jako součást procesu odvíjení zásobníku. V takových případech [AbnormalTermination](/windows/desktop/Debug/abnormaltermination) vrací funkce **true** -li volána zevnitř **nakonec** blokovat; v opačném případě vrátí **false**.

Obslužné rutiny ukončení není volána, pokud proces je ukončen průběhu provádění příkazu **try-finally** příkazu.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Syntaxe obslužné rutiny ukončení](/windows/desktop/Debug/termination-handler-syntax)