---
title: "Výměna polí záznamu: Použití funkce RFX | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- RFX (ODBC), implementing
ms.assetid: ada8f043-37e6-4d41-9db3-92c997a61957
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 28f1cd743a7ede904c99590e56f08b7020f77d82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="record-field-exchange-using-rfx"></a>Výměna polí záznamu: Použití funkce RFX
Toto téma vysvětluje, co provedete k použití RFX ve vztahu k jaké rozhraní.  
  
> [!NOTE]
>  Toto téma se vztahuje na třídy odvozené od třídy [CRecordset](../../mfc/reference/crecordset-class.md) v který řádek hromadné načítání se neimplementovala. Pokud používáte hromadné načítání řádků, je implementováno Hromadná výměna pole záznamu (Bulk RFX). Hromadné RFX je podobná RFX. Chcete-li pochopit rozdíly, přečtěte si téma [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Následující témata obsahují související informace:  
  
-   [Výměna polí záznamu: Práce s kódem průvodce](../../data/odbc/record-field-exchange-working-with-the-wizard-code.md) zavádí hlavní součásti RFX a vysvětluje kód, který Průvodce aplikací knihovny MFC a **přidat třídu** (jak je popsáno v [přidání příjemce rozhraní ODBC knihovny MFC ](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) zápis k podpoře RFX a jak můžete změnit kód průvodce.  
  
-   [Výměna polí záznamu: Použití funkcí RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md) vysvětluje psaní volání funkce RFX ve vaší `DoFieldExchange` přepsat.  
  
 Následující tabulka uvádí vaši roli ve vztahu k rozhraní provede za vás.  
  
### <a name="using-rfx-you-and-the-framework"></a>Použití funkce RFX: Vy a architektura  
  
|Vy|Rozhraní framework|  
|---------|-------------------|  

| Deklarace tříd sady záznamů pomocí průvodce. Zadejte názvy a typy dat pole datových členů. | Průvodce odvozuje `CRecordset` třídy a zápisy [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) přepsání pro vás, včetně RFX volání pro každé pole datového člena funkce. |  
| (Volitelné) Ručně přidejte všechny potřebné parametry datových členů do třídy. Ručně přidejte volání funkce RFX k `DoFieldExchange` pro každý parametr datového člena, že přidáte volání [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) pro skupinu parametrů a zadejte celkový počet parametrů v [m_nParams ](../../mfc/reference/crecordset-class.md#m_nparams). V tématu [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md). ||  
| (Volitelné) Ruční vytvoření vazby dalších sloupců s pole datových členů. Zvyšte ručně [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields). V tématu [sada záznamů: dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md). ||  

| Vytvořte objekt vaší třídy sady záznamů. Před použitím objektu, nastavte hodnoty jeho parametru datové členy, pokud existuje. | Rozhraní pro efektivitu, znovu naváže parametry, pomocí rozhraní ODBC. Pokud předáte hodnoty parametrů, předává je rozhraní ke zdroji dat. Pouze hodnoty parametrů jsou odesílány pro zopakování dotazu, pokud řazení nebo filtrování řetězce změnily. |  
| Otevřete objekt sady záznamů pomocí [CRecordset::Open](../../mfc/reference/crecordset-class.md#open). | Provede dotaz sady záznamů, sváže sloupce do pole datových členů sady záznamů a volání `DoFieldExchange` pro výměnu dat mezi první vybraný záznam a sady záznamů pole datových členů. |  
| Přejděte do sady záznamů pomocí [CRecordset::Move](../../mfc/reference/crecordset-class.md#move) nebo příkaz nabídky nebo panelu nástrojů. | Volání `DoFieldExchange` k přenosu dat do pole datových členů z nové aktuální záznam. |  
| Přidat, aktualizovat a odstranit záznamy. | Volání `DoFieldExchange` k přenosu dat do zdroje dat. |  
  
## <a name="see-also"></a>Viz také  
 [Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [Výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)   
 [Makra, globální funkce a globální proměnné](../../mfc/reference/mfc-macros-and-globals.md)

