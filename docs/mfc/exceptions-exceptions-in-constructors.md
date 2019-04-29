---
title: 'Výjimky: Výjimky v konstruktorech'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 0b11f5be18879d5ad4b9e204bb02e18b4617c6b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405869"
---
# <a name="exceptions-exceptions-in-constructors"></a>Výjimky: Výjimky v konstruktorech

Při vyvolání výjimky v konstruktoru, vyčistit libovolné objekty a přidělení paměti provedené před vyvolání výjimky, jak je vysvětleno v [výjimky: Generování výjimek ve vašich vlastních funkcích](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).

Při vyvolání výjimky v konstruktoru, paměť pro samotný objekt již byl vytvořen v době, kdy je konstruktor volán. Proto kompilátor bude automaticky přidělení paměti obsazena objektu poté, co je vyvolána výjimka.

Další informace najdete v tématu [výjimky: Uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
