---
title: try-except – příkaz (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
ms.openlocfilehash: b186a1923eadedd201119ff8fbbd0a730c33cff8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50611897"
---
# <a name="try-except-statement-c"></a>try-except – příkaz (C)

**Specifické pro Microsoft**

**Zkuste – s výjimkou** příkaz je rozšířením společnosti Microsoft pro jazyk C, která umožňuje aplikacím získat kontrolu programu, pokud dojde k událostem, které za normálních okolností ukončí provádění. Tyto události jsou nazývány výjimkami a mechanismus, který se výjimkami zabývá, se nazývá strukturované zpracování výjimek.

Výjimky mohou být buď hardwaru nebo softwaru založené. I v případech, kdy aplikace nemohou být zotaveny z hardwarových nebo softwarových výjimek, umožňuje strukturované zpracování výjimek zobrazit informace o chybě a zachytit vnitřní stav aplikace pro diagnostiku problému. To je užitečné zejména pro občasné problémy, které nelze snadno reprodukovat.

## <a name="syntax"></a>Syntaxe

*s výjimkou příkazu Try*: **__try**  *compound-statement* 

**__except (**  *výraz*  **)**  *compound-statement*

Složený příkaz za `__try` klauzule je chráněná část. Složený příkaz po klauzuli `__except` je obslužnou rutinou výjimky. Obslužná rutina udává sadu akcí provedených v případě je vyvolána výjimka při provádění chráněné části. Spuštění probíhá následujícím způsobem:

1. Chráněná část je spuštěna.

1. Nedojde-li za běhu chráněné části k žádné výjimce, pokračuje běh programu příkazem za klauzulí `__except`.

1. Pokud dojde k výjimce za běhu chráněné části nebo v jakékoli rutině chráněná část volá, `__except` výraz je vyhodnocen a vrácená hodnota určuje, jak je výjimka ošetřena. Existují tři hodnoty:

   `EXCEPTION_CONTINUE_SEARCH` Výjimka není rozpoznána. Pokračujte ve vyhledávání zásobníkem pro obslužnou rutinu, nejprve obsahující **zkuste – s výjimkou** příkazy, pak u obslužných rutin s druhou nejvyšší prioritou.

   `EXCEPTION_CONTINUE_EXECUTION` Výjimka je rozpoznána, ale vynechat. Program bude pokračovat tam, kde k výjimce došlo.

   `EXCEPTION_EXECUTE_HANDLER` Výjimka je rozpoznána. Řízení je převedeno na obslužnou rutinu výjimek pomocí provádí `__except` složený příkaz a potom pokračovat v provádění v místě, se vyskytla výjimka.

Vzhledem k tomu, `__except` výraz je vyhodnocen jako výraz jazyka C, je omezený na jednu hodnotu, operátor podmíněného výrazu nebo operátor čárky. Je-li požadováno rozsáhlejší zpracování, může výraz zavolat rutinu, která vrátí jednu z výše uvedených tří hodnot.

> [!NOTE]
>  Strukturované zpracování výjimek funguje se zdrojovými soubory C a C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Mechanismus zpracování výjimek jazyka C++ je také mnohem více flexibilní, jelikož dokáže zpracovat výjimky libovolného typu.

> [!NOTE]
>  Pro programy v jazyce C++ je třeba použít zpracování výjimek jazyka C++ místo strukturované zpracování výjimek. Další informace najdete v tématu [zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md) v *referenční dokumentace jazyka C++*.

Každá rutina v aplikaci může mít svůj vlastní obslužné rutiny výjimky. `__except` Výraz spouští v rámci `__try` textu. To znamená, že bude mít přístup k libovolné místní proměnné deklarované existuje.

`__leave` – Klíčové slovo je platný v rámci **zkuste – s výjimkou** blok příkazů. Účinek `__leave` je přechod na konci **zkuste – s výjimkou** bloku. Provádění pokračuje na konci obslužná rutina výjimky. I když `goto` příkaz můžete použít k dosažení stejného výsledku `goto` příkaz způsobí, že odvíjení zásobníku. `__leave` Příkaz je mnohem efektivnější, protože nezahrnuje odvíjení zásobníku.

Ukončení **zkuste – s výjimkou** pomocí příkazu `longjmp` funkci run-time je považován za abnormální ukončení. Není povoleno přejít do `__try` příkazu, ale právní přejít mimo něj. Obslužná rutina výjimky není volána, pokud proces je ukončen průběhu provádění příkazu **zkuste – s výjimkou** příkazu.

## <a name="example"></a>Příklad

Tady je příklad obslužné rutiny výjimek a obslužné rutiny ukončení. Zobrazit [příkaz try-finally](../c-language/try-finally-statement-c.md) Další informace o obslužné rutiny ukončení.

```
.
.
.
puts("hello");
__try{
   puts("in try");
   __try{
      puts("in try");
      RAISE_AN_EXCEPTION();
   }__finally{
      puts("in finally");
   }
}__except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ){
   puts("in except");
}
puts("world");
```

Toto je výstup z příkladu, s komentářem přidán na pravé straně:

```
hello
in try              /* fall into try                     */
in try              /* fall into nested try                */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[try-except – příkaz](../cpp/try-except-statement.md)