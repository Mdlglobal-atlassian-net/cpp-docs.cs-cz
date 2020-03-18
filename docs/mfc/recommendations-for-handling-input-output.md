---
title: Doporučení pro zpracování vstupu a výstupu
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: 956a92fd1761f61081afa2eb9c6cb35fe72b46d6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446907"
---
# <a name="recommendations-for-handling-inputoutput"></a>Doporučení pro zpracování vstupu a výstupu

Bez ohledu na to, jestli použijete vstupně-výstupní operace na bázi souborů, nebo ne, záleží na tom, jak reagujete na otázky v následujícím rozhodovacím stromu:

**Je primární data v aplikaci uložena v souboru na disku**

- Ano, primární data se nachází v souboru na disku:

     **Načte aplikace celý soubor do paměti v otevřeném souboru a zapíše celý soubor zpátky na disk při uložení souboru.**

   - Ano: Toto je výchozí případ dokumentu knihovny MFC. Použijte serializaci `CDocument`.

   - Ne: obvykle se jedná o případ aktualizace souboru založeného na transakcích. Aktualizujete soubor pro jednotlivé transakce a nepotřebujete `CDocument` serializaci.

- Ne, primární data se nenacházejí v souboru na disku:

     **Jsou data uložena ve zdroji dat rozhraní ODBC**

   - Ano, data se nachází ve zdroji dat ODBC:

      Použijte podporu databáze knihovny MFC. Standardní implementace knihovny MFC pro tento případ zahrnuje objekt `CDatabase`, jak je popsáno v článku [MFC: použití databázových tříd s dokumenty a zobrazeními](../data/mfc-using-database-classes-with-documents-and-views.md). Aplikace může také číst a zapisovat pomocný soubor – účel Průvodce aplikací jak možnost zobrazení databáze, tak podpora souborů. V tomto případě použijete serializaci pro pomocný soubor.

   - Ne, data se nenacházejí ve zdroji dat ODBC.

      Příklady tohoto případu: data se nacházejí v systému DBMS, který není rozhraním ODBC. data se čtou přes nějaký jiný mechanismus, jako je například OLE nebo DDE.

      V takových případech nepoužijete serializaci a vaše aplikace nebude mít položky nabídky otevřít a uložit. Můžete přesto chtít použít `CDocument` jako domovskou základnu, stejně jako aplikace MFC ODBC používá dokument k ukládání objektů `CRecordset`. Ale nepoužijete výchozí serializaci souboru Open/Save dokumentu.

Pro podporu příkazů otevřít, Uložit a uložit jako v nabídce soubor poskytuje rozhraní serializaci dokumentu. Serializace čte a zapisuje data, včetně objektů odvozených z třídy `CObject`, do trvalého úložiště, obvykle souboru na disku. Serializace se snadno používá a obsluhuje spoustu vašich potřeb, ale může být nevhodná v mnoha aplikacích pro přístup k datům. Aplikace pro přístup k datům obvykle aktualizují data v závislosti na transakci. Aktualizují záznamy ovlivněné transakcí a nikoli čtením a zápisem celého datového souboru najednou.

Informace o serializaci naleznete v tématu [serializace](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Viz také

[Serializace: serializace vs. vstup/výstup databáze](../mfc/serialization-serialization-vs-database-input-output.md)
