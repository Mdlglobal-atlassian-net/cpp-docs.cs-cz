---
title: 'Výjimky: Výjimky OLE'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
ms.openlocfilehash: 1606a0f5a86996345e12024cf6416afdf6bdc82b
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246709"
---
# <a name="exceptions-ole-exceptions"></a>Výjimky: Výjimky OLE

Techniky a zařízení pro zpracování výjimek v technologii OLE jsou stejné jako pro zpracování jiných výjimek. Další informace o zpracování výjimek naleznete v článku [ C++ moderní osvědčené postupy pro výjimky a zpracování chyb](../cpp/errors-and-exception-handling-modern-cpp.md).

Všechny objekty výjimek jsou odvozeny z abstraktní základní třídy `CException`. Knihovna MFC poskytuje dvě třídy pro zpracování výjimek OLE:

- [COleException](../mfc/reference/coleexception-class.md) Pro zpracování obecných výjimek OLE.

- [COleDispatchException](../mfc/reference/coledispatchexception-class.md) Pro generování a manipulaci s výjimkami odeslání OLE (automatizace).

Rozdíl mezi těmito dvěma třídami je množství informací, které poskytují a kde se používají. `COleException` má veřejný datový člen, který obsahuje kód stavu OLE pro výjimku. `COleDispatchException` poskytuje další informace, včetně následujících:

- Kód chyby specifický pro aplikaci

- Popis chyby, například "plný disk"

- Kontext pro nápovědu, který může vaše aplikace používat k poskytnutí dalších informací pro uživatele

- Název souboru Help vaší aplikace

- Název aplikace, která vygenerovala výjimku.

`COleDispatchException` poskytuje další informace, aby je bylo možné použít s produkty, jako je Microsoft Visual Basic. Popis ústní chyby lze použít v okně se zprávou nebo v jiném oznámení. informace o nápovědě lze použít k zajištění reakce uživatele na podmínky, které způsobily výjimku.

Dvě globální funkce odpovídají dvěma třídám výjimek OLE: [AfxThrowOleException](../mfc/reference/exception-processing.md#afxthrowoleexception) a [AfxThrowOleDispatchException](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Použijte je k vyvolání obecných výjimek OLE a výjimek odeslání OLE, v uvedeném pořadí.

## <a name="see-also"></a>Viz také:

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)
