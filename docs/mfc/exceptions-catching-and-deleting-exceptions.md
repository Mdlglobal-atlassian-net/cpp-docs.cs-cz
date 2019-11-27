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
ms.openlocfilehash: 0142ffddfb391ae8da878d9e5fe34629cf16cb52
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246695"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Výjimky: Zachytávání a mazání

Následující pokyny a příklady vám ukážou, jak zachytit a odstranit výjimky. Další informace o klíčových slovech **Try**, **catch**a **throw** naleznete v tématu [moderní C++ osvědčené postupy pro výjimky a zpracování chyb](../cpp/errors-and-exception-handling-modern-cpp.md).

Obslužné rutiny výjimek musí odstranit objekty výjimek, které zpracovávají, protože chyba při odstranění výjimky způsobí nevracení paměti vždy, když kód zachytí výjimku.

Blok **catch** musí odstranit výjimku, když:

- Blok **catch** vyvolá novou výjimku.

   Proto nesmíte výjimku odstranit, pokud znovu vyvoláte stejnou výjimku:

   [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Spuštění se vrátí z bloku **catch** .

> [!NOTE]
>  Při odstraňování `CException`lze výjimku odstranit pomocí členské funkce `Delete`. Nepoužívejte klíčové slovo **Delete** , protože může selhat, pokud výjimka není na haldě.

#### <a name="to-catch-and-delete-exceptions"></a>Zachycení a odstranění výjimek

1. K nastavení **testovaného** bloku použijte klíčové slovo **Try** . Spusťte všechny příkazy programu, které mohou vyvolat výjimku v rámci bloku **Try** .

   Pomocí klíčového slova **catch** nastavte blok **catch** . Do bloku **catch** umístěte kód pro zpracování výjimek. Kód v bloku **catch** je proveden pouze v případě, že kód v bloku **Try** vyvolá výjimku typu určeného v příkazu **catch** .

   Následující kostra ukazuje, jak jsou bloky **Try** a **catch** normálně uspořádány:

   [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

   Je-li vyvolána výjimka, řízení předá do prvního bloku **catch** , jehož deklarace výjimky odpovídá typu výjimky. Můžete selektivně zpracovat různé typy výjimek pomocí sekvenčních bloků **catch** , jak je uvedeno níže:

   [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Další informace naleznete v tématu [výjimky: převod z makra výjimek knihovny MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
