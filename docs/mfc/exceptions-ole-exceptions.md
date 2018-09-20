---
title: 'Výjimky: Výjimky OLE | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE, exceptions
- OLE exceptions [MFC]
- exceptions [MFC], OLE
- exception handling [MFC], OLE
- OLE exceptions [MFC], classes for handling
ms.assetid: 2f8e0161-b94f-48bb-a5a2-6f644b192527
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6013caa79e21a305ba5ff8ad6266e960bb21504a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46395242"
---
# <a name="exceptions-ole-exceptions"></a>Výjimky: Výjimky OLE

Techniky a funkce pro zpracování výjimek v prostředí OLE jsou stejné jako pro zpracování jiných výjimek. Další informace o zpracování výjimek, najdete v článku [zpracování výjimek jazyka C++](../cpp/cpp-exception-handling.md).

Všechny výjimky objekty jsou odvozeny od abstraktní základní třída `CException`. Knihovna MFC poskytuje dvě třídy pro zpracování výjimek OLE:

- [Coleexception –](../mfc/reference/coleexception-class.md) pro zpracování obecné výjimky OLE.

- [Coledispatchexception –](../mfc/reference/coledispatchexception-class.md) pro generování a zpracování OLE odeslání výjimky (Automatizace).

Rozdíl mezi těmito dvěma třídami je množství informací poskytují, a kde jsou použity. `COleException` má data veřejného člena, který obsahuje OLE stavový kód výjimky. `COleDispatchException` poskytuje další informace, včetně následujících:

- Kód chyby specifické pro aplikaci

- Popis chyby, jako je například "Disk je plný"

- Kontextové nápovědy, které vaše aplikace může použít na další informace pro uživatele

- Název souboru nápovědy vaší aplikace

- Název aplikace, které generují výjimku

`COleDispatchException` poskytuje další informace, takže je možné s produkty, jako je Microsoft Visual Basicu. Popis slovní chyby lze použít v okně se zprávou nebo jiné oznámení; informace nápovědy je možné umožňující uživateli reagovat na podmínky, které způsobil výjimku.

Dvě globální funkce, které odpovídají dvě třídy výjimky OLE: [afxthrowoleexception –](../mfc/reference/exception-processing.md#afxthrowoleexception) a [afxthrowoledispatchexception –](../mfc/reference/exception-processing.md#afxthrowoledispatchexception). Je použijte k vyvolání obecné OLE výjimky a výjimky odbavení OLE, v uvedeném pořadí.

## <a name="see-also"></a>Viz také

[Zpracování výjimek](../mfc/exception-handling-in-mfc.md)

