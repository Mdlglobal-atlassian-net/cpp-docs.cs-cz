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
ms.openlocfilehash: c26b72f7c675a4130f38c515cf71ecc290328ccc
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "69498609"
---
# <a name="try-finally-statement"></a>try-finally – příkaz

**Specifické pro společnost Microsoft**

Následující syntaxe popisuje příkaz **try-finally** :

> **\_ \_try**<br/>
> {<br/>
> &nbsp; &nbsp; &nbsp; &nbsp;//chráněný kód<br/>
> }<br/>
> **\_ \_finally**<br/>
> {<br/>
> &nbsp; &nbsp; &nbsp; &nbsp;//ukončovací kód<br/>
> }

## <a name="grammar"></a>Gramatika

*try-finally-příkaz*:<br/>
&nbsp; &nbsp; &nbsp; &nbsp; **\_ \_try** *složený* příkaz \_ **0finally** *složený* příkaz

Příkaz **try-finally** je rozšířením společnosti Microsoft pro jazyky C a C++ , které umožňuje cílovým aplikacím zaručit spuštění kódu pro vyčištění v případě přerušení provádění bloku kódu. Vyčištění se skládá z těchto úloh jako rušení přidělení paměti, zavírání souborů a uvolňování obslužných rutin souborů. Příkaz **try-finally** je zvláště užitečný pro rutiny, které mají několik míst, kde je provedena kontrola chyby, která by mohla způsobit předčasné vrácení z rutiny.

Související informace a ukázku kódu naleznete v [příkazu try-except](../cpp/try-except-statement.md). Další informace o strukturovaném zpracování výjimek obecně naleznete v tématu [strukturované zpracování výjimek](../cpp/structured-exception-handling-c-cpp.md). Další informace o zpracování výjimek ve spravovaných aplikacích pomocí C++/CLI naleznete v tématu [zpracování výjimek v rámci/CLR](../extensions/exception-handling-cpp-component-extensions.md).

> [!NOTE]
> Strukturované zpracování výjimek funguje na architektuře Win32 pro zdrojové soubory jazyka C i C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Zpracování výjimek jazyka C++ je také více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu. Pro C++ programy se doporučuje použít mechanismus zpracování C++ výjimek (příkazy[Try, Catch a throw](../cpp/try-throw-and-catch-statements-cpp.md) ).

Složený příkaz za klauzulí **__try** je chráněný oddíl. Složený příkaz za klauzulí **__finally** je obslužná rutina ukončení. Obslužná rutina určuje sadu akcí, které se spustí, když se chráněný oddíl ukončí bez ohledu na to, jestli je chráněný oddíl ukončený výjimkou (abnormální ukončení) nebo podle standardu (normální ukončení).

Ovládací prvek dosáhne příkazu **__try** pomocí jednoduchého sekvenčního spuštění (Přejít do). Když řízení vstoupí do **__try**, jeho přidružená obslužná rutina se stane aktivní. Pokud tok řízení dosáhne konce bloku try, provádění pokračuje následujícím způsobem:

1. Je vyvolána obslužná rutina ukončení.

1. Po dokončení obslužné rutiny ukončení pokračuje provádění i po příkazu **__finally** . Bez ohledu na to, jak chráněná část končí (například prostřednictvím příkazu **goto** z chráněného těla nebo příkazu **return** ), je obslužná rutina ukončení provedena před tím, *než* se ovládací prvek přemístí do chráněné části.

   Příkaz **__finally** neblokuje hledání vhodné obslužné rutiny výjimky.

Pokud dojde k výjimce v bloku **__try** , operační systém musí najít obslužnou rutinu pro výjimku nebo se program nezdaří. Pokud je nalezena obslužná rutina, všechny a všechny bloky **__finally** jsou spuštěny a provádění pokračuje v obslužné rutině.

Předpokládejme například, že řada volání funkce odkazuje funkce A na funkci D, jak je znázorněno na následujícím obrázku. Každá funkce má jednu obslužnou rutinu ukončení. Je-li ve funkci D vyvolána výjimka a je zpracována v, jsou v tomto pořadí volány obslužné rutiny ukončení, protože systém odvíjí zásobník: D, C, B.

![Pořadí provádění obslužné&#45;rutiny ukončení](../cpp/media/vc38cx1.gif "Pořadí provádění obslužné&#45;rutiny ukončení") <br/>
Pořadí provádění obslužné rutiny ukončení

> [!NOTE]
> Chování příkazu try-finally se liší od jiných jazyků, které podporují použití příkazu **finally**, například C#.  Jeden **__try** může mít buď, ale ne obojí, z **__finally** i **__except**.  Pokud se obě mají použít společně, příkaz vnějšího příkazu try-except musí být uzavřený do vnitřního příkazu try-finally.  Pravidla, která určují, kdy se každý blok spustí, jsou také odlišná.

Z důvodu kompatibility s předchozími verzemi jsou **_try**, **_finally**a **_leave** synonyma pro **__try**, **__finally**a **__leave** , pokud možnost kompilátoru [/za \(Disable jazykové rozšíření](../build/reference/za-ze-disable-language-extensions.md) není. dané.

## <a name="the-__leave-keyword"></a>Klíčové slovo __leave

Klíčové slovo **__leave** je platné pouze v rámci chráněné části příkazu **try-finally** a jeho efekt je přejít na konec chráněné části. Provádění pokračuje u prvního příkazu v obslužné rutině ukončení.

Příkaz **goto** se také může přesunout mimo chráněný oddíl, ale snižuje výkon, protože vyvolá odvíjení zásobníku. Příkaz **__leave** je efektivnější, protože nezpůsobí vrácení zásobníku zpět.

## <a name="abnormal-termination"></a>Abnormální ukončení

Ukončení příkazu **try-finally** pomocí běhové funkce [longjmp](../c-runtime-library/reference/longjmp.md) se považuje za abnormální ukončení. Je neplatné přeskočit do příkazu **__try** , ale právnímu přechodu z jednoho z nich. Musí být spuštěny všechny **__finally** příkazy, které jsou aktivní mezi bodem odeslání (normální ukončení bloku **__try** ) a cíl (blok **__except** , který zpracovává výjimku). Označuje se jako místní unwind.

Pokud je blok **Try** předčasně ukončen z jakéhokoli důvodu, včetně skoku mimo blok, systém spustí přidružený blok **finally** jako součást procesu odvíjení zásobníku. V takových případech funkce [AbnormalTermination](/windows/win32/Debug/abnormaltermination) vrací **hodnotu true** , pokud je volána v rámci bloku **finally** ; v opačném případě vrátí **hodnotu false**.

Obslužná rutina ukončení není volána, pokud je proces ukončen uprostřed provádění příkazu **try-finally** .

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Zápis obslužné rutiny ukončení](../cpp/writing-a-termination-handler.md)<br/>
[Strukturované zpracování výjimek (C/C++)](../cpp/structured-exception-handling-c-cpp.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)<br/>
[Ukončení – syntaxe obslužné rutiny](/windows/win32/Debug/termination-handler-syntax)