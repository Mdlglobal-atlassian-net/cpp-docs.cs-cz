---
title: 'Výjimky: Výjimky v konstruktorech'
ms.date: 11/04/2016
helpviewer_keywords:
- constructors [MFC], exceptions
- throwing exceptions [MFC], in constructors
- exceptions [MFC], in constructors
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
ms.openlocfilehash: 23d1f6a9a3c76cc9c0c1d4aebd5c0b0ea45c3154
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472265"
---
# <a name="exceptions-exceptions-in-constructors"></a>Výjimky: Výjimky v konstruktorech

Při vyvolání výjimky v konstruktoru, vyčistit libovolné objekty a přidělení paměti provedené před vyvolání výjimky, jak je vysvětleno v [výjimky: generování výjimek z vaše vlastní funkce](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).

Při vyvolání výjimky v konstruktoru, paměť pro samotný objekt již byl vytvořen v době, kdy je konstruktor volán. Proto kompilátor bude automaticky přidělení paměti obsazena objektu poté, co je vyvolána výjimka.

Další informace najdete v tématu [výjimky: uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

