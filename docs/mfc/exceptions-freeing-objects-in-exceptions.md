---
title: 'Výjimky: Uvolnění objektů ve výjimkách'
ms.date: 11/04/2016
helpviewer_keywords:
- throwing exceptions [MFC], freeing objects in exceptions
- local exception handling
- memory leaks, caused by exception
- try-catch exception handling [MFC], destroying objects
- destroying objects [MFC]
- freeing objects [MFC]
- throwing exceptions [MFC], after destroying
- exception handling [MFC], destroying objects
ms.assetid: 3b14b4ee-e789-4ed2-b8e3-984950441d97
ms.openlocfilehash: 49c7c6b0481f90baa23609c1bb1596deda49f7bd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371987"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Výjimky: Uvolnění objektů ve výjimkách

Tento článek vysvětluje potřebu a způsob uvolnění objektů, když dojde k výjimce. Témata:

- [Zpracování výjimky místně](#_core_handling_the_exception_locally)

- [Vyvolání výjimek po zničení objektů](#_core_throwing_exceptions_after_destroying_objects)

Výjimky vyzývané rámci nebo aplikace přerušit normální tok programu. Proto je velmi důležité sledovat objekty, abyste je mohli správně vyřadit v případě, že je vyvolána výjimka.

Existují dvě primární metody k tomu.

- Zpracování výjimek místně pomocí try **a** **catch** klíčová slova, pak zničit všechny objekty s jedním příkazem.

- Zničit libovolný objekt v bloku **catch** před vyvoláním výjimky mimo blok pro další zpracování.

Tyto dva přístupy jsou znázorněny níže jako řešení následující problematický příklad:

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Jak je `myPerson` uvedeno výše, nebudou odstraněny, pokud `SomeFunc`je vyvolána výjimka . Spuštění přeskočí přímo na další obslužnou rutinu vnější výjimky, vynechání normální funkce ukončení a kód, který odstraní objekt. Ukazatel na objekt přejde mimo rozsah, když výjimka opustí funkci a paměť obsazená objektem nebude nikdy obnovena, dokud je spuštěn program. Toto je nevracení paměti; by byla zjištěna pomocí diagnostiky paměti.

## <a name="handling-the-exception-locally"></a><a name="_core_handling_the_exception_locally"></a>Zpracování výjimky místně

**Try/catch** paradigma poskytuje metodu obrannéprogramování pro zamezení nevracení paměti a zajištění, že vaše objekty jsou zničeny, když dojde k výjimkám. Příklad zobrazený dříve v tomto článku může být například přepsán následujícím způsobem:

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

Tento nový příklad nastaví obslužnou rutinu výjimky zachytit výjimku a zpracovat místně. Potom ukončí funkci normálně a zničí objekt. Důležitým aspektem tohoto příkladu je, že kontext zachytit výjimku je vytvořen s **try/catch** bloky. Bez rámce místní výjimky by funkce nikdy vědět, že výjimka byla vyvolána a nebude mít možnost ukončit normálně a zničit objekt.

## <a name="throwing-exceptions-after-destroying-objects"></a><a name="_core_throwing_exceptions_after_destroying_objects"></a>Vyvolání výjimek po zničení objektů

Dalším způsobem, jak zpracovat výjimky, je předat je do dalšího kontextu zpracování vnější výjimky. V bloku **catch** můžete provést vyčištění místně přidělených objektů a potom vyvolat výjimku pro další zpracování.

Funkce vyvolání může nebo nemusí být nutné navrátit objekty haldy. Pokud funkce vždy navrátí objekt haldy před návratem v normálním případě, pak funkce by měla také navrátit objekt haldy před vyvoláním výjimky. Na druhou stranu pokud funkce obvykle nenavrací objekt před vrácením v normálním případě, musíte se případ od případu rozhodnout, zda by měl být objekt haldy přidělen.

Následující příklad ukazuje, jak lze vyčistit místně přidělené objekty:

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

Mechanismus výjimek automaticky navrací objekty rámce; destruktor objektu rámečku se také nazývá.

Pokud voláte funkce, které mohou vyvolat výjimky, můžete použít **try/catch** bloky a ujistěte se, že zachytíte výjimky a máte šanci zničit všechny objekty, které jste vytvořili. Zejména uvědomte si, že mnoho funkcí knihovny MFC může vyvolat výjimky.

Další informace naleznete v [tématu Výjimky: Zachycení a odstranění výjimek](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
