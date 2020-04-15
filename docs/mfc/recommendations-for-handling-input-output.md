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
ms.openlocfilehash: c365120a385c440f09f0ee4c0a2fc52afb55834f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371727"
---
# <a name="recommendations-for-handling-inputoutput"></a>Doporučení pro zpracování vstupu a výstupu

To, zda používáte vstupně-tonové vstupně-videa založené na souborech nebo ne, závisí na tom, jak odpovíte na otázky v následujícím rozhodovacím stromu:

**Jsou primární data v aplikaci umístěna v souboru disku**

- Ano, primární data jsou uložena v souboru disku:

   **Čte aplikace celý soubor do paměti v aplikaci File Open a zapisuje celý soubor zpět na disk při ukládání souborů**

  - Ano: Toto je výchozí případ dokumentu knihovny MFC. Použijte `CDocument` serializaci.

  - Ne: Obvykle se jedná o případ aktualizace souboru na základě transakcí. Soubor aktualizujete na základě transakce a nepotřebujete `CDocument` serializaci.

- Ne, primární data nejsou umístěna v souboru disku:

   **Jsou data umístěna ve zdroji dat ODBC**

  - Ano, data jsou uložena ve zdroji dat ODBC:

      Použijte podporu databáze knihovny MFC. Standardní implementace knihovny MFC `CDatabase` pro tento případ obsahuje objekt, jak je popsáno v článku [Knihovna MFC: Použití tříd databáze s dokumenty a zobrazení](../data/mfc-using-database-classes-with-documents-and-views.md). Aplikace může také číst a zapisovat pomocný soubor – účel průvodce aplikací "zobrazení databáze a podpora souborů". V takovém případě byste použili serializaci pro pomocný soubor.

  - Ne, data nejsou umístěna ve zdroji dat ODBC.

      Příklady tohoto případu: data jsou umístěna v non-ODBC DBMS; data jsou čtena prostřednictvím jiného mechanismu, například OLE nebo DDE.

      V takových případech nebudete používat serializaci a aplikace nebude mít položky nabídky Otevřít a Uložit. Stále můžete chtít použít `CDocument` jako domovskou základnu, stejně jako aplikace Knihovny MFC ODBC používá dokument k ukládání `CRecordset` objektů. Ale nebudete používat rozhraní výchozí soubor otevřít/ uložit serializaci dokumentu.

Pro podporu příkazů Otevřít, Uložit a Uložit jako v nabídce Soubor poskytuje architektura serializaci dokumentu. Serializace čte a zapisuje `CObject`data, včetně objektů odvozených z třídy , do trvalého úložiště, obvykle do souboru disku. Serializace je snadno použitelná a slouží mnoha vašim potřebám, ale může být nevhodná v mnoha aplikacích pro přístup k datům. Aplikace pro přístup k datům obvykle aktualizují data na základě transakcí. Aktualizují záznamy ovlivněné transakcí, nikoli čtení a zápis celého datového souboru najednou.

Informace o serializaci naleznete v tématu [Serializace](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Viz také

[Serializace: Serializace vs. databázový vstup/výstup](../mfc/serialization-serialization-vs-database-input-output.md)
