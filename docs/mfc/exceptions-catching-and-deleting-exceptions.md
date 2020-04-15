---
title: 'Výjimky: Zachytávání a mazání'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
ms.openlocfilehash: 74022c8bc6af1d2cdf74fa452d4e0483637e542e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365518"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Výjimky: Zachytávání a mazání

Následující pokyny a příklady ukazují, jak zachytit a odstranit výjimky. Další informace o klíčových slovech **try**, **catch**a **throw** naleznete v [tématu Modern C++ best practices for exceptions and error handling](../cpp/errors-and-exception-handling-modern-cpp.md).

Obslužné rutiny výjimek musí odstranit objekty výjimek, které zpracovávají, protože selhání odstranění výjimky způsobí nevracení paměti vždy, když tento kód zachytí výjimku.

Blok **catch** musí odstranit výjimku, pokud:

- Catch **catch** bloku vyvolá novou výjimku.

   Samozřejmě nesmíte odstranit výjimku, pokud znovu vyvoláte stejnou výjimku:

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Spuštění vrátí z v rámci bloku **catch.**

> [!NOTE]
> Při odstraňování `CException`, použijte `Delete` členská funkce k odstranění výjimky. Nepoužívejte **odstranit** klíčové slovo, protože může selhat, pokud výjimka není na haldě.

#### <a name="to-catch-and-delete-exceptions"></a>Zachycení a odstranění výjimek

1. Pomocí klíčového slova **try** nastavte blok **try.** Spusťte všechny příkazy programu, které mohou vyvolat výjimku v rámci **bloku try.**

   Pomocí klíčového slova **catch** nastavte blok **catch.** Umístěte kód zpracování výjimek do bloku **catch.** Kód v bloku **catch** je spuštěn pouze v případě, že kód v rámci bloku **try** vyvolá výjimku typu zadaného v příkazu **catch.**

   Následující kostra ukazuje, jak se běžně **uspořádány** bloky try a **catch:**

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Při vyvolání výjimky, ovládací prvek předá první **catch** bloku, jehož deklarace výjimky odpovídá typu výjimky. Můžete selektivně zpracovávat různé typy výjimek se sekvenčními bloky **catch,** jak je uvedeno níže:

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Další informace naleznete v [tématu Exceptions: Converting from Makra výjimek knihovny MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
