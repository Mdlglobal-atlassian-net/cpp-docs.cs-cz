---
title: 'Výjimky: Výjimky v konstruktorech | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8336700cc0137efe3bc106871ebd76b8de7a99af
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342628"
---
# <a name="exceptions-exceptions-in-constructors"></a>Výjimky: Výjimky v konstruktorech
Při vyvolání k výjimce v konstruktoru, vyčistit ať objekty a přidělení paměti provedené před vyvolání výjimky, jak je popsáno v [výjimkami: vyvolání výjimky z funkce vaše vlastní](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).  
  
 Při vyvolání k výjimce v konstruktoru, již bylo přiděleno o dobu, kterou volání konstruktoru paměť pro odkaz sám na sebe. Ano bude kompilátor automaticky navrácení paměti obsazené objektem po vyvolání výjimky.  
  
 Další informace najdete v tématu [výjimky: uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md).  
  
## <a name="see-also"></a>Viz také  
 [Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

