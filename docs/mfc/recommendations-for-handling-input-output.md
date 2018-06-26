---
title: Doporučení pro zpracování vstupu výstupu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ee88b7784abb6ca622e72a9dfb31efc39fa7816
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930937"
---
# <a name="recommendations-for-handling-inputoutput"></a>Doporučení pro zpracování vstupu a výstupu
Ať už používáte vstupně-výstupních operací na základě souborů nebo není závisí na tom, jak reagovat na otázky v rozhodovacím stromu následující:  
  
 **Primární dat v aplikaci se nacházejí v souboru na disku**  
  
-   Ano, primární data se nachází v souboru na disku:  
  
     **Aplikaci načíst celý soubor do paměti otevřít soubor a zpětný zápis celý soubor do disku na soubor uložit**  
  
    -   Ano: Jedná o případ výchozí MFC dokumentu. Použití `CDocument` serializace.  
  
    -   Ne: Toto je obvykle v případě založenou na transakcích aktualizace souboru. Aktualizovat soubor na základě jednotlivé transakce a nepotřebujete `CDocument` serializace.  
  
-   Ne, není primární data uložena v souboru na disku:  
  
     **Nacházejí data ve zdroji dat rozhraní ODBC**  
  
    -   Ano, data se nachází ve zdroji dat rozhraní ODBC:  
  
         Podpora MFC pro databázi použijte. Obsahuje standardní implementace MFC pro tento případ `CDatabase` objektu, jak je popsáno v článku [MFC: použití databázových tříd s dokumenty a zobrazeními](../data/mfc-using-database-classes-with-documents-and-views.md). Aplikace může také pro čtení a zápis pomocného souboru – účel "zobrazení databáze i soubor podporují" možnost Průvodce vytvořením aplikace. V takovém případě byste použili serializace pro pomocného souboru.  
  
    -   Ne, dat není uložena ve zdroji dat rozhraní ODBC.  
  
         Příklady tento případ: data nachází v jiný - ODBC databázového systému; data je pro čtení přes jiným mechanismem, jako je například OLE nebo DDE.  
  
         V takových případech nebudete používat serializace a aplikace nebude otevřena a uložit položky nabídky. Může nadále chcete používat `CDocument` jako základ home, stejně jako MFC ODBC aplikace používá dokument k uložení `CRecordset` objekty. Ale nebudete používat rozhraní framework výchozí soubor otevření nebo uložení dokumentu serializace.  
  
 Podpora Open, uložit, a uložit jako příkazy v nabídce Soubor, poskytuje rozhraní serializace dokumentu. Serializace čte a zapisuje data, včetně objektů odvozených od třídy `CObject`, do trvalého úložiště, obvykle soubor na disku. Serializace se snadno používá a obsluhuje řadu vašim potřebám, ale může být nevhodných v mnoha aplikacích přístup k datům. Přístup k datům aplikací obvykle aktualizace dat na základě jednotlivé transakce. Jejich aktualizaci záznamů postižené transakce nikoli čtení a zápis celý datový soubor najednou.  
  
 Informace o serializaci najdete v tématu [serializace](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Serializace: Porovnání serializace a Databáze vstupu a výstupu](../mfc/serialization-serialization-vs-database-input-output.md)
