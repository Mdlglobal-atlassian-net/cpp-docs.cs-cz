---
title: 'Výjimky: Výjimky v konstruktorech | Dokumentace Microsoftu'
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
ms.openlocfilehash: 3cab21255698c19046cfca185a0d8d7e7c530112
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421931"
---
# <a name="exceptions-exceptions-in-constructors"></a>Výjimky: Výjimky v konstruktorech

Při vyvolání výjimky v konstruktoru, vyčistit libovolné objekty a přidělení paměti provedené před vyvolání výjimky, jak je vysvětleno v [výjimky: generování výjimek z vaše vlastní funkce](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).

Při vyvolání výjimky v konstruktoru, paměť pro samotný objekt již byl vytvořen v době, kdy je konstruktor volán. Proto kompilátor bude automaticky přidělení paměti obsazena objektu poté, co je vyvolána výjimka.

Další informace najdete v tématu [výjimky: uvolnění objektů ve výjimkách](../mfc/exceptions-freeing-objects-in-exceptions.md).

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

