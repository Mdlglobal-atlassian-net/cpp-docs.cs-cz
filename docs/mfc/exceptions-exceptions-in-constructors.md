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
ms.openlocfilehash: 0fb42a88c60b89909f104873ff20e36192b13c69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="exceptions-exceptions-in-constructors"></a>Výjimky: Výjimky v konstruktorech
Při vyvolání k výjimce v konstruktoru, vyčistit ať objekty a přidělení paměti provedené před vyvolání výjimky, jak je popsáno v [výjimkami: vyvolání výjimky z funkce vaše vlastní](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).  
  
 Při vyvolání k výjimce v konstruktoru, již bylo přiděleno o dobu, kterou volání konstruktoru paměť pro odkaz sám na sebe. Ano bude kompilátor automaticky navrácení paměti obsazené objektem po vyvolání výjimky.  
  
 Další informace najdete v tématu [výjimky: uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

