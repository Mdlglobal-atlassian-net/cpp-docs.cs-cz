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
ms.openlocfilehash: 2ca5299a5ab20b8985a520f25bb654ead0c25e2b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81349745"
---
# <a name="try-except-statement-c"></a>try-except – příkaz (C)

**Specifické pro Microsoft**

Příkaz **try-except** je rozšíření společnosti Microsoft k jazyku C, které umožňuje aplikacím získat kontrolu nad programem, když dojde k událostem, které obvykle ukončí spuštění. Tyto události jsou nazývány výjimkami a mechanismus, který se výjimkami zabývá, se nazývá strukturované zpracování výjimek.

Výjimky mohou být založené na hardwaru nebo softwaru. I v případech, kdy aplikace nemohou být zotaveny z hardwarových nebo softwarových výjimek, umožňuje strukturované zpracování výjimek zobrazit informace o chybě a zachytit vnitřní stav aplikace pro diagnostiku problému. To je užitečné zejména pro občasné problémy, které nelze snadno reprodukovat.

## <a name="syntax"></a>Syntaxe

*try-except-statement*: **__try**  *složený příkaz*

**__except (***výraz***)** složený*příkaz*      

Složený příkaz za `__try` klauzulí je střežené části. Složený příkaz po klauzuli `__except` je obslužnou rutinou výjimky. Obslužná rutina určuje sadu akcí, které mají být přijata, pokud je vyvolána výjimka během provádění hlídané části. Exekuce probíhá takto:

1. Chráněná část je spuštěna.

1. Nedojde-li za běhu chráněné části k žádné výjimce, pokračuje běh programu příkazem za klauzulí `__except`.

1. Pokud dojde k výjimce během provádění střežené části nebo v `__except` jakékoli rutině, kterou volá chráněná část, výraz je vyhodnocen a vrácená hodnota určuje způsob zpracování výjimky. Existují tři hodnoty:

   `EXCEPTION_CONTINUE_SEARCH`Výjimka není rozpoznána. Pokračujte v hledání do zásobníku pro obslužnou rutinu, nejprve pro obsahující **příkazy try-except,** pak pro obslužné rutiny s další nejvyšší prioritou.

   `EXCEPTION_CONTINUE_EXECUTION`Výjimka je rozpoznána, ale zamítnuta. Program bude pokračovat tam, kde k výjimce došlo.

   `EXCEPTION_EXECUTE_HANDLER`Výjimka je rozpoznána. Přeneste řízení na obslužnou rutinu výjimky spuštěním složeného příkazu `__except` a pokračujte v provádění v okamžiku, kdy došlo k výjimce.

Vzhledem `__except` k tomu, že výraz je vyhodnocen jako výraz C, je omezen na jednu hodnotu, operátor podmíněného výrazu nebo operátor čárky. Je-li požadováno rozsáhlejší zpracování, může výraz zavolat rutinu, která vrátí jednu z výše uvedených tří hodnot.

> [!NOTE]
> Strukturované zpracování výjimek funguje se zdrojovými soubory C a C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Také mechanismus zpracování výjimek Jazyka C++ je mnohem flexibilnější v tom, že může zpracovávat výjimky libovolného typu.

> [!NOTE]
> Pro programy jazyka C++ by mělo být místo strukturovaného zpracování výjimek použito zpracování výjimek jazyka C++. For more information, see [Exception Handling](../cpp/exception-handling-in-visual-cpp.md) in the *C++ Language Reference*.

Každá rutina v aplikaci může mít vlastní obslužnou rutinu výjimky. Výraz `__except` se provede v rozsahu `__try` těla. To znamená, že má přístup ke všem místním proměnným, které jsou zde deklarovány.

Klíčové `__leave` slovo je platné v rámci **try-except** bloku příkazu. Efekt `__leave` je přejít na konec **try-except** bloku. Spuštění pokračuje po ukončení obslužné rutiny výjimky. Přestože `goto` příkaz lze použít k dosažení `goto` stejného výsledku, příkaz způsobí, že unwinding zásobníku. Příkaz `__leave` je efektivnější, protože nezahrnuje odvíjení zásobníku.

Ukončení **příkazu try-except** `longjmp` pomocí funkce run-time je považováno za abnormální ukončení. Je nezákonné skočit do `__try` prohlášení, ale legální skočit z jednoho. Obslužná rutina výjimky není volána, pokud je proces usmrcený uprostřed provádění příkazu **try-except.**

## <a name="example"></a>Příklad

Následuje příklad obslužné rutiny výjimky a obslužné rutiny ukončení. Další informace o obslužných rutinách ukončení naleznete [v příkazu try-finally.](../c-language/try-finally-statement-c.md)

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

Toto je výstup z příkladu s komentářem přidaným vpravo:

```
hello
in try              /* fall into try                     */
in try              /* fall into nested try                */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**END Microsoft Specifické**

## <a name="see-also"></a>Viz také

[try-except Příkaz](../cpp/try-except-statement.md)
