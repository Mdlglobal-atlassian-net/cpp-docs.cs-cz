---
title: "Výjimky: Zachytávání a odstraňování výjimek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- exceptions [MFC], deleting
- AND_CATCH macro [MFC]
- try-catch exception handling [MFC], catching and deleting exceptions
- exception handling [MFC], catching and deleting exceptions
- catch blocks [MFC], catching and deleting exceptions
- execution [MFC], returns from within catch block
ms.assetid: 7c233ff0-89de-4de0-a68a-9e9cdb164311
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 23988e9d8669bee558ec5418f44921d60bec08d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="exceptions-catching-and-deleting-exceptions"></a>Výjimky: Zachytávání a mazání
Následující pokyny a příklady ukazují, jak zachytit a odstranit výjimky. Další informace o **zkuste**, **catch**, a `throw` klíčová slova, najdete v části [zpracování výjimek C++](../cpp/cpp-exception-handling.md).  
  
 Vaše obslužné rutiny výjimek musí objekty výjimek, které se budou zpracovávat, odstranit, protože se nezdařilo odstranit výjimka způsobuje nevracení paměti vždy, když tento kód zachytí výjimku.  
  
 Vaše **catch** bloku musí odstranit výjimku při:  
  
-   **Catch** bloku vyvolá novou výjimku.  
  
     Samozřejmě nesmí odstranit výjimku, pokud throw znovu bude stejná výjimka:  
  
     [!code-cpp[NVC_MFCExceptions#3](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_1.cpp)]  
  
-   Provádění vrátí uvnitř **catch** bloku.  
  
> [!NOTE]
>  Při odstraňování `CException`, použijte **odstranit** – členská funkce odstranit výjimku. Nepoužívejte **odstranit** – klíčové slovo, protože může selhat, pokud výjimka není v haldě.  
  
#### <a name="to-catch-and-delete-exceptions"></a>Catch – a odstraňovat výjimky  
  
1.  Použití **zkuste** – klíčové slovo nastavit **zkuste** bloku. Spustí žádné program příkazy, které může vyvolat výjimku v rámci **zkuste** bloku.  
  
     Použití **catch** – klíčové slovo nastavit **catch** bloku. Umístěte kód zpracování výjimek v **catch** bloku. Kód v **catch** bloku se spustí pouze v případě, kód v rámci **zkuste** bloku vyvolá výjimku zadaného v typu **catch** příkaz.  
  
     Následující kostru ukazuje jak **zkuste** a **catch** bloky jsou obvykle uspořádané:  
  
     [!code-cpp[NVC_MFCExceptions#4](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_2.cpp)]  
  
     Pokud je vyvolána výjimka, ovládací prvek předává do první **catch** bloku, jejíž výjimky deklarace odpovídá typu výjimky. Můžete selektivně zpracovávat různé typy výjimek s po sobě jdoucích **catch** blokuje, jak je uvedeno dále:  
  
     [!code-cpp[NVC_MFCExceptions#5](../mfc/codesnippet/cpp/exceptions-catching-and-deleting-exceptions_3.cpp)]  
  
 Další informace najdete v tématu [výjimky: převádění z maker výjimek prostředí MFC](../mfc/exceptions-converting-from-mfc-exception-macros.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

