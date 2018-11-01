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
ms.openlocfilehash: 1144337df9657d63c53a13e03cf31eb487ce4068
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50585455"
---
# <a name="recommendations-for-handling-inputoutput"></a>Doporučení pro zpracování vstupu a výstupu

Určuje, zda se ale nemusíte používat souborových vstupně-výstupní operace závisí na reakce na dotazy ve stromové struktuře následující rozhodnutí:

**Primární data ve vaší aplikaci se nacházejí v souboru na disku**

- Ano, jsou primární data uložená v souboru na disku:

     **Probíhá aplikace načíst celý soubor do paměti otevřít soubor a zapsat celý soubor na disk na soubor uložit**

   - Ano: Toto je výchozí případ dokumentu MFC. Použití `CDocument` serializace.

   - Ne: Obvykle se jedná o založenou na transakcích aktualizaci souboru. Aktualizace souboru na základě za transakce a nemusíte `CDocument` serializace.

- Ne, není primární data uložena v souboru na disku:

     **Nacházejí data ve zdroji dat rozhraní ODBC**

   - Ano, data uložená ve zdroji dat rozhraní ODBC:

         Use MFC's database support. The standard MFC implementation for this case includes a `CDatabase` object, as discussed in the article [MFC: Using Database Classes with Documents and Views](../data/mfc-using-database-classes-with-documents-and-views.md). The application might also read and write an auxiliary file — the purpose of the application wizard "both a database view and file support" option. In this case, you'd use serialization for the auxiliary file.

   - Ne, dat není uložena ve zdroji dat rozhraní ODBC.

         Examples of this case: the data resides in a non-ODBC DBMS; the data is read via some other mechanism, such as OLE or DDE.

         In such cases, you won't use serialization, and your application won't have Open and Save menu items. You might still want to use a `CDocument` as a home base, just as an MFC ODBC application uses the document to store `CRecordset` objects. But you won't use the framework's default File Open/Save document serialization.

Pro podporu Open, uložit a uložit jako příkazy v nabídce Soubor, poskytuje rozhraní serializace dokumentu. Serializace čte a zapisuje data, včetně objektů odvozené od třídy `CObject`, do trvalého úložiště, obvykle souboru na disku. Serializace se snadno používá a zajišťuje řadu vašim potřebám, ale může být nevhodné v mnoha aplikacích přístup k datům. Přístup k datům aplikace obvykle aktualizace dat na jednotlivých transakcích. Aktualizují záznamy ovlivněny transakce místo čtení a zápis do souboru celé datové najednou.

Informace o serializaci naleznete v tématu [serializace](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Viz také

[Serializace: Porovnání serializace a Databázový vstup/výstup](../mfc/serialization-serialization-vs-database-input-output.md)
