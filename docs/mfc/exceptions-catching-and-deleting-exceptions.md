---
title: 'Výjimky: Zachytávání a mazání | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5bd59cc19c80e305a7e57fb711a49f59a024d528
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46434762"
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Výjimky: Zachytávání a mazání

Následující pokyny a příklady ukazují, jak zachytit a odstranit výjimky. Další informace o **zkuste**, **catch**, a **throw** klíčová slova, naleznete v tématu [zpracování výjimek jazyka C++](../cpp/cpp-exception-handling.md).

Vaší obslužné rutiny výjimek musí objektech výjimek, které zpracovávají, odstranit, protože selhání odstranit výjimky způsobí, že nevracení paměti pokaždé, když se tento kód zachytí výjimku.

Vaše **catch** bloku musí odstranit výjimku při:

- **Catch** bloku vyvolá novou výjimku.

     Samozřejmě nesmí odstranit výjimku, pokud vyvoláte výjimku znovu:

     [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]

- Spuštění se vrátí v rámci **catch** bloku.

> [!NOTE]
>  Při odstraňování `CException`, použijte `Delete` členská funkce se odstranit výjimky. Nepoužívejte **odstranit** – klíčové slovo, protože může selhat, pokud výjimka není na haldě.

#### <a name="to-catch-and-delete-exceptions"></a>K zachycení a odstranit výjimky

1. Použití **zkuste** – klíčové slovo k nastavení **zkuste** bloku. Spustit všechny příkazy programu, které můžou vyvolat výjimku v rámci **zkuste** bloku.

     Použití **catch** – klíčové slovo k nastavení **catch** bloku. Kód zpracování výjimek v umístěte **catch** bloku. Kód v **catch** blok se spustí, pouze pokud kód v rámci **zkuste** bloku dojde k výjimce typu určeného v **catch** příkazu.

     Zobrazí se následující kostra jak **zkuste** a **catch** bloky, jsou obvykle seřazené:

     [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]

     Když je vyvolána výjimka, řízení se předá první **catch** bloku, deklarace výjimky odpovídá typu výjimky. Můžete selektivně zpracovávat různé druhy výjimek pomocí sekvenční **catch** blokuje, jak je uvedeno níže:

     [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]

Další informace najdete v tématu [výjimky: převádění z maker výjimek prostředí MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

