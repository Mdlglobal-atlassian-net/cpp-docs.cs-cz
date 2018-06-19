---
title: Třídy výjimek | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.exception
dev_langs:
- C++
helpviewer_keywords:
- exception classes [MFC]
- exception handling [MFC], exception classes
- MFC, exceptions
ms.assetid: 1a2caf12-b3e9-4189-86d2-bf7a595bf025
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8ce4085d0f5f2dcc73d126d04b7560ef8360ffd9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344893"
---
# <a name="exception-classes"></a>Třídy výjimek
Knihovna tříd poskytuje mechanismus zpracování výjimek na základě třídy `CException`. Rozhraní používá výjimky v jeho kód; můžete je také použít v vaše. Další informace najdete v článku [výjimky](../mfc/exception-handling-in-mfc.md). Odvozujete vlastní typy výjimek z `CException`.  
  
 MFC poskytuje třídu výjimky, ze kterého odvodíte vlastní výjimky a také třídy výjimek pro všechny výjimky, kterou podporuje.  
  
 [CException](../mfc/reference/cexception-class.md)  
 Základní třída pro výjimky.  
  
 [CArchiveException](../mfc/reference/carchiveexception-class.md)  
 Výjimku archivu.  
  
 [CDaoException](../mfc/reference/cdaoexception-class.md)  
 Výjimku vyplývající z selhání v rámci operace databáze DAO.  
  
 [CDBException](../mfc/reference/cdbexception-class.md)  
 Výjimku vyplývající z chyby při zpracování databáze ODBC.  
  
 [CFileException](../mfc/reference/cfileexception-class.md)  
 Výjimka zaměřené na konkrétní soubor.  
  
 [CMemoryException](../mfc/reference/cmemoryexception-class.md)  
 Výjimku z důvodu nedostatku paměti.  
  
 [CNotSupportedException](../mfc/reference/cnotsupportedexception-class.md)  
 Výjimku vyplývající z pomocí nepodporované funkce.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Výsledkem chyba ve zpracování OLE výjimku. Tato třída se používá kontejnery a servery.  
  
 [COleDispatchException](../mfc/reference/coledispatchexception-class.md)  
 Výjimku vyplývající z chybu během automatizace. Automatizace výjimky vyvolané automatizační servery a zachytila klienti automatizace.  
  
 [CResourceException](../mfc/reference/cresourceexception-class.md)  
 Výjimku vyplývající z selhání načtení prostředků Windows.  
  
 [CUserException](../mfc/reference/cuserexception-class.md)  
 Výjimku použít k zastavení operace se uživatel spustil. Obvykle se uživatel ohlášení problému předtím, než je vyvolána výjimka.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

