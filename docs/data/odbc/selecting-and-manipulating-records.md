---
title: Výběr a manipulace s nimi záznamy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records, selecting
- record selection, MFC ODBC classes
- ODBC recordsets, selecting records
ms.assetid: 7f0b3a4a-9941-4475-a612-9ec8d15b7691
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2a4b76d0b4273e5afb32206336b4aabbfe9294eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090075"
---
# <a name="selecting-and-manipulating-records"></a>Výběr záznamů a manipulace s nimi
Za normálních okolností když vyberete záznamy ze zdroje dat pomocí SQL **vyberte** příkaz získat sadu výsledků, což je sada záznamů z tabulky nebo dotazu. S třídami databází použít objekt sady záznamů a vyberte přístup sadu výsledků dotazu. Toto je objekt třídy specifické pro aplikaci, která je odvozena od třídy [CRecordset](../../mfc/reference/crecordset-class.md). Když definujete třídy sady záznamů, je třeba zadat zdroj dat pro její přidružení, tabulku, kterou chcete použít a sloupců tabulky. Průvodce aplikací knihovny MFC nebo **přidat třídu** (jak je popsáno v [přidání příjemce rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) vytvoří připojení ke zdroji dat konkrétní třídu. Průvodci zápis [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) funkce člena třídy `CRecordset` vrátit název tabulky. Další informace o vytvoření sady záznamů tříd pomocí průvodců najdete v tématu [Podpora databáze, Průvodce aplikací knihovny MFC](../../mfc/reference/database-support-mfc-application-wizard.md) a [přidání příjemce rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).  
  
 Použití [CRecordset](../../mfc/reference/crecordset-class.md) objektu v době běhu, můžete:  
  
-   Zkontrolujte pole data na aktuální záznam.  
  
-   Třídit nebo filtrovat sadu záznamů.  
  
-   Přizpůsobit výchozí SQL **vyberte** příkaz.  
  
-   Procházet vybraných záznamů.  
  
-   Přidání, aktualizace nebo odstranění záznamů (pokud jsou zdroje dat a sady záznamů v aktualizovatelné).  
  
-   Otestovat, zda sada záznamů umožňuje opětovné spuštění dotazu a aktualizovat obsah sady záznamů.  
  
 Po dokončení práce objekt sady záznamů, zavřete a zničte jej. Další informace o sadách záznamů najdete v tématu [záznamů (ODBC)](../../data/odbc/recordset-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní ODBC a knihovna MFC](../../data/odbc/odbc-and-mfc.md)