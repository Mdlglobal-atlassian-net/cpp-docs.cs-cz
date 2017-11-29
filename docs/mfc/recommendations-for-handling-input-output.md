---
title: "Doporučení pro zpracování vstupu výstupu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 21febf38be647513ca58560078875691a82d22aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="recommendations-for-handling-inputoutput"></a>Doporučení pro zpracování vstupu a výstupu
Ať už používáte vstupně-výstupních operací na základě souborů nebo není závisí na tom, jak reagovat na otázky v rozhodovacím stromu následující:  
  
 **Primární dat v aplikaci se nacházejí v souboru na disku**  
  
-   Ano, primární data se nachází v souboru na disku:  
  
     **Aplikaci načíst celý soubor do paměti otevřít soubor a zpětný zápis celý soubor do disku na soubor uložit**  
  
    -   Ano: Jedná o případ výchozí MFC dokumentu. Použití **CDocument** serializace.  
  
    -   Ne: Toto je obvykle v případě založenou na transakcích aktualizace souboru. Aktualizovat soubor na základě jednotlivé transakce a nepotřebujete **CDocument** serializace.  
  
-   Ne, není primární data uložena v souboru na disku:  
  
     **Nacházejí data ve zdroji dat rozhraní ODBC**  
  
    -   Ano, data se nachází ve zdroji dat rozhraní ODBC:  
  
         Podpora MFC pro databázi použijte. Obsahuje standardní implementace MFC pro tento případ `CDatabase` objektu, jak je popsáno v článku [MFC: použití databázových tříd s dokumenty a zobrazeními](../data/mfc-using-database-classes-with-documents-and-views.md). Aplikace může také pro čtení a zápis pomocného souboru – účel "zobrazení databáze i soubor podporují" možnost Průvodce vytvořením aplikace. V takovém případě byste použili serializace pro pomocného souboru.  
  
    -   Ne, dat není uložena ve zdroji dat rozhraní ODBC.  
  
         Příklady tento případ: data nachází v jiný - ODBC databázového systému; data je pro čtení přes jiným mechanismem, jako je například OLE nebo DDE.  
  
         V takových případech nebudete používat serializace a aplikace nebude otevřena a uložit položky nabídky. Může nadále chcete používat **CDocument** jako základ home, stejně jako MFC ODBC aplikace používá dokument k uložení `CRecordset` objekty. Ale nebudete používat rozhraní framework výchozí soubor otevření nebo uložení dokumentu serializace.  
  
 Podpora Open, uložit, a uložit jako příkazy v nabídce Soubor, poskytuje rozhraní serializace dokumentu. Serializace čte a zapisuje data, včetně objektů odvozených od třídy `CObject`, do trvalého úložiště, obvykle soubor na disku. Serializace se snadno používá a obsluhuje řadu vašim potřebám, ale může být nevhodných v mnoha aplikacích přístup k datům. Přístup k datům aplikací obvykle aktualizace dat na základě jednotlivé transakce. Jejich aktualizaci záznamů postižené transakce nikoli čtení a zápis celý datový soubor najednou.  
  
 Informace o serializaci najdete v tématu [serializace](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Viz také  
 [Serializace: Serializace vs. Databáze vstupu a výstupu](../mfc/serialization-serialization-vs-database-input-output.md)