---
title: Třídy výjimek
ms.date: 11/04/2016
f1_keywords:
- vc.classes.exception
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
ms.openlocfilehash: 99a2764dcad15267b1aab8a60951f99f21352726
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392866"
---
# <a name="exception-classes"></a>Třídy výjimek

Knihovna tříd poskytuje mechanismus zpracování výjimek založené na třídě `CException`. Aplikační framework používá výjimky v jeho kód; Můžete také využít v té vaší. Další informace najdete v článku [výjimky](../mfc/exception-handling-in-mfc.md). Můžete odvozovat vlastní typy výjimek z `CException`.

Knihovna MFC poskytuje třídu výjimky, ze které odvozujete vlastní výjimky, stejně jako třídy výjimky pro všechny výjimky, které podporuje.

[Cexception –](../mfc/reference/cexception-class.md)<br/>
Základní třída pro výjimky.

[Carchiveexception –](../mfc/reference/carchiveexception-class.md)<br/>
Výjimku archivu.

[CDaoException](../mfc/reference/cdaoexception-class.md)<br/>
Výjimka výsledkem selhání v rámci operace databáze DAO.

[CDBException](../mfc/reference/cdbexception-class.md)<br/>
Výjimka vyplývající z chyby ve zpracování databáze ODBC.

[CFileException](../mfc/reference/cfileexception-class.md)<br/>
Soubor objektově orientovaný výjimky.

[CMemoryException](../mfc/reference/cmemoryexception-class.md)<br/>
Výjimka mimo z důvodu nedostatku paměti.

[CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)<br/>
Výjimka vyplývající z použití nepodporované funkce.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Výjimka vyplývající z chyby ve zpracování OLE. Tato třída se používá tak, že kontejnery a servery.

[COleDispatchException](../mfc/reference/coledispatchexception-class.md)<br/>
Výjimka vyplývající z chybu během automatizace. Automatizace výjimky jsou vyvolané automatizační servery a zachytit klientům automatizace.

[CResourceException](../mfc/reference/cresourceexception-class.md)<br/>
Výjimka výsledkem selhání při načítání prostředků Windows.

[CUserException](../mfc/reference/cuserexception-class.md)<br/>
Výjimka použít k zastavení operace iniciovaná uživatelem. Obvykle uživatel má byl informován o problém předtím, než je vyvolána výjimka.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../mfc/class-library-overview.md)
