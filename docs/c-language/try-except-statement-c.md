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

Příkaz **try-except** je rozšířením společnosti Microsoft pro jazyk C, který aplikacím umožňuje převzít kontrolu nad programem, když dojde k událostem, které obvykle ukončí provádění. Tyto události jsou nazývány výjimkami a mechanismus, který se výjimkami zabývá, se nazývá strukturované zpracování výjimek.

Výjimky mohou být založené na hardwaru nebo softwaru. I v případech, kdy aplikace nemohou být zotaveny z hardwarových nebo softwarových výjimek, umožňuje strukturované zpracování výjimek zobrazit informace o chybě a zachytit vnitřní stav aplikace pro diagnostiku problému. To je užitečné zejména pro občasné problémy, které nelze snadno reprodukovat.

## <a name="syntax"></a>Syntaxe

*try-except-příkaz*: **__try***složený* příkaz  

*složený* příkaz **__except (***výraz***)**      

Složený příkaz za `__try` klauzulí je chráněný oddíl. Složený příkaz po klauzuli `__except` je obslužnou rutinou výjimky. Obslužná rutina určuje sadu akcí, které mají být provedeny, pokud je vyvolána výjimka během provádění chráněné části. Provádění pokračuje následujícím způsobem:

1. Chráněná část je spuštěna.

1. Nedojde-li za běhu chráněné části k žádné výjimce, pokračuje běh programu příkazem za klauzulí `__except`.

1. Pokud dojde k výjimce při provádění chráněného oddílu nebo v jakékoli rutině chráněného oddílu, je `__except` výraz vyhodnocen a vrácená hodnota určuje, jak je výjimka zpracována. Existují tři hodnoty:

   `EXCEPTION_CONTINUE_SEARCH`Výjimka nebyla rozpoznána. Pokračujte v hledání zásobníku pro obslužnou rutinu, nejprve pro příkazy **try-except** a potom pro obslužné rutiny s další nejvyšší prioritou.

   `EXCEPTION_CONTINUE_EXECUTION`Výjimka je rozpoznaná, ale byla zrušena. Program bude pokračovat tam, kde k výjimce došlo.

   `EXCEPTION_EXECUTE_HANDLER`Je rozpoznaná výjimka. Převeďte řízení na obslužnou rutinu výjimky spuštěním `__except` složeného příkazu a potom pokračujte v provádění v místě, kde došlo k výjimce.

Vzhledem k `__except` tomu, že výraz je vyhodnocen jako výraz jazyka C, je omezen na jedinou hodnotu, operátor podmíněného výrazu nebo operátor čárky. Je-li požadováno rozsáhlejší zpracování, může výraz zavolat rutinu, která vrátí jednu z výše uvedených tří hodnot.

> [!NOTE]
> Strukturované zpracování výjimek funguje se zdrojovými soubory C a C++. Pro jazyk C++ však není výslovně navrženo. Větší přenositelnost kódu lze zajistit použitím zpracování výjimek jazyka C++. Mechanismus zpracování výjimek jazyka C++ je také mnohem flexibilní, v tom případě může zpracovávat výjimky jakéhokoli typu.

> [!NOTE]
> Pro programy C++ by se namísto strukturovaného zpracování výjimek měla použít zpracování výjimek jazyka C++. Další informace naleznete v tématu [zpracování výjimek](../cpp/exception-handling-in-visual-cpp.md) v *Referenční příručce jazyka C++*.

Každá rutina v aplikaci může mít vlastní obslužnou rutinu výjimky. Výraz `__except` se spustí v rozsahu `__try` těla. To znamená, že má přístup k jakýmkoli místně deklarovaným proměnným.

`__leave` Klíčové slovo je platné v rámci bloku příkazu **try-except** . Účinek `__leave` je přejít na konec bloku **try-except** . Spuštění pokračuje po konci obslužné rutiny výjimky. Přestože lze `goto` použít příkaz k dosažení stejného výsledku, `goto` příkaz způsobí unwind zásobníku. `__leave` Příkaz je efektivnější, protože nezahrnuje odvíjení zásobníku.

Ukončení příkazu **try-except** pomocí `longjmp` běhové funkce se považuje za abnormální ukončení. Je neplatné přeskočit do `__try` příkazu, ale právním přechodem na jeden z nich. Obslužná rutina výjimky není volána, pokud je proces ukončen uprostřed provádění příkazu **try-except** .

## <a name="example"></a>Příklad

Následuje příklad obslužné rutiny výjimky a obslužné rutiny ukončení. Další informace o obslužných rutinách ukončení naleznete v [příkazu try-finally](../c-language/try-finally-statement-c.md) .

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

Toto je výstup z příkladu s komentářem přidaným na pravé straně:

```
hello
in try              /* fall into try                     */
in try              /* fall into nested try                */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[try-except – příkaz](../cpp/try-except-statement.md)
