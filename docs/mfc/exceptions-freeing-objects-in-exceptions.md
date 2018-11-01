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
ms.openlocfilehash: 6e03d46a2600458f3107efa6e0b6b0d643c9b160
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442468"
---
# <a name="exceptions-freeing-objects-in-exceptions"></a>Výjimky: Uvolnění objektů ve výjimkách

Tento článek vysvětluje potřeba a metodu uvolnění objektů, když dojde k výjimce. Mezi témata patří:

- [Zpracování výjimek místně](#_core_handling_the_exception_locally)

- [Vyvolávání výjimek po zničení objektů](#_core_throwing_exceptions_after_destroying_objects)

Výjimky vyvolané rozhraním, nebo ve vaší aplikaci přerušení normálního toku programu. Proto je velmi důležité zaznamenávat zavřít objekty tak, že můžete správně vyřazení je v případě, že dojde k výjimce.

Existují dvě základní metody, chcete-li to provést.

- Zpracování výjimek pomocí místně **zkuste** a **catch** klíčová slova, pak zničilo všechny objekty pomocí jednoho příkazu.

- Odstranit libovolný objekt v **catch** blok před vygenerováním výjimky mimo blok pro další zpracování.

Tyto dvě metody jsou jako řešení v následujícím příkladu problematické znázorněno níže:

[!code-cpp[NVC_MFCExceptions#14](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_1.cpp)]

Jak je uvedená výše, `myPerson` nebudou odstraněny, pokud je vyvolána výjimka ve `SomeFunc`. Spuštění přejde přímo na další vnější obslužnou rutinu výjimky, vynechání ukončení normální funkce a kód, který odstraní objekt. Ukazatel na objekt dostane mimo rozsah, pokud tato výjimka zanechá funkce a paměti obsazena objekt se obnoví nikdy tak dlouho, dokud je aplikace spuštěna. Toto je nevrácená paměť; by se zjistilo pomocí diagnostiky paměti.

##  <a name="_core_handling_the_exception_locally"></a> Zpracování výjimek místně

**Bloku try/catch** paradigma poskytuje obranné programovací metodu pro zabránění nevracení paměti a zajišťuje, že objekty jsou zničeny při výskytu výjimky. Například v příkladu zmíněném výše v tomto článku měl by být přepsán následujícím způsobem:

[!code-cpp[NVC_MFCExceptions#15](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_2.cpp)]

Tento nový příklad nastaví obslužnou rutinu výjimky zachytit výjimku a zpracovat místně. Potom obvykle ukončí funkce a odstraní objekt. Důležitý aspekt jazyka v tomto příkladu je, že se kontext pro zachycení výjimky naváže s **bloku try/catch** bloky. Bez blok lokálních výjimek by funkce nikdy vědět, kdyby byla vyvolána a nebude mít možnost ukončit normálně a zničte objekt výjimka.

##  <a name="_core_throwing_exceptions_after_destroying_objects"></a> Vyvolávání výjimek po zničení objektů

Jiný způsob zpracování výjimek je předat do další vnější kontext zpracování výjimek. Ve vaší **catch** blok, můžete si udělat trochu pořádek místně přidělených objektů a poté vyvolají výjimku k dalšímu zpracování.

Aktivační funkce může nebo nemusí být nutné zrušit přidělení objektů haldy. Pokud funkce vždycky uvolní objekt haldy návrat zpět v případě, Normální, pak funkce by měl také uvolnit objekt haldy před vygenerováním výjimky. Na druhé straně Pokud funkce není uvolnění obvykle objekt před vrácením v případě, Normální, pak musíte se rozhodnout případ od případu, zda by měla být odebrána objekt haldy.

Následující příklad ukazuje, jak místně přidělené objekty je možné vymazat:

[!code-cpp[NVC_MFCExceptions#16](../mfc/codesnippet/cpp/exceptions-freeing-objects-in-exceptions_3.cpp)]

Mechanismus výjimek automaticky zruší přidělení rámce objekty. také je volán destruktor objektu rámce.

Při volání funkce, které můžou vyvolat výjimku, můžete použít **bloku try/catch** bloky, abyste měli jistotu, že zachycovat výjimky a mít možnost zničit všechny objekty, které jste vytvořili. Zejména mějte na paměti, že mnoho funkcí knihovny MFC může vyvolat výjimky.

Další informace najdete v tématu [výjimky: výjimky zachycení a odstraňování](../mfc/exceptions-catching-and-deleting-exceptions.md).

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

