---
title: "Výjimky: Výjimky v konstruktorech | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fc17821e2dd358a4b8f596492fa46c2b7412feed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="exceptions-exceptions-in-constructors"></a>Výjimky: Výjimky v konstruktorech
Při vyvolání k výjimce v konstruktoru, vyčistit ať objekty a přidělení paměti provedené před vyvolání výjimky, jak je popsáno v [výjimkami: vyvolání výjimky z funkce vaše vlastní](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).  
  
 Při vyvolání k výjimce v konstruktoru, již bylo přiděleno o dobu, kterou volání konstruktoru paměť pro odkaz sám na sebe. Ano bude kompilátor automaticky navrácení paměti obsazené objektem po vyvolání výjimky.  
  
 Další informace najdete v tématu [výjimky: uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

