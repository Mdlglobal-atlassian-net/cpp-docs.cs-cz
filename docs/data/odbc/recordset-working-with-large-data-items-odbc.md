---
title: 'Sada záznamů: Práce s velkými datovými položkami (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- BLOB (binary large object), recordsets
- ODBC recordsets, binary large objects
- recordsets, binary large objects
- binary large objects
- CLongBinary class, using in recordsets
ms.assetid: 3e80b5a8-b6e7-43c6-a816-e54befc513a3
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bf82e1fabd45e9bccd63e4ba46068b75d2c2a0a7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-working-with-large-data-items-odbc"></a>Sada záznamů: Práce s velkými datovými položkami (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC a tříd MFC rozhraní DAO.  
  
> [!NOTE]
>  Pokud používáte tříd MFC rozhraní DAO, spravovat vaše velkými datovými položkami s třídou [CByteArray](../../mfc/reference/cbytearray-class.md) místo třída [CLongBinary](../../mfc/reference/clongbinary-class.md). Pokud používáte třídy knihovny MFC rozhraní ODBC se hromadné načítání řádků, použijte `CLongBinary` místo `CByteArray`. Další informace o hromadné načítání řádků najdete v tématu [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Předpokládejme, že vaše databáze může ukládat velké částí dat, jako je například Bitmap (zaměstnanec fotografií, map, obrázky produktů, objekty OLE a tak dále). Tento typ dat je často označovány jako binární rozsáhlý objekt (nebo objektů BLOB), protože:  
  
-   Hodnota každého pole je velká.  
  
-   Na rozdíl od jiných jednoduché datové typy a čísla nemá žádné předvídatelné velikost.  
  
-   Data jsou formless z hlediska vašeho programu.  
  
 Toto téma vysvětluje, co podporu databázové třídy poskytují pro práci s tyto objekty.  
  
##  <a name="_core_managing_large_objects"></a>Správa rozsáhlé objekty  
 Sady záznamů mít dva způsoby, jak vyřešit speciální potíže správy binární rozsáhlé objekty. Třídu můžete použít [CByteArray](../../mfc/reference/cbytearray-class.md) nebo můžete použít třídu [CLongBinary](../../mfc/reference/clongbinary-class.md). Obecně platí `CByteArray` je upřednostňovaný způsob, jak spravovat velké binární data.  
  
 `CByteArray`vyžaduje další režii než `CLongBinary` , ale je více možností, jak je popsáno v [CByteArray třída](#_core_the_cbytearray_class). `CLongBinary`v stručně popisuje [The CLongBinary – třída](#_core_the_clongbinary_class).  
  
 Podrobné informace o používání `CByteArray` pracovat s velkými datovými položkami, najdete v tématu [Technická poznámka 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).  
  
##  <a name="_core_the_cbytearray_class"></a>CByteArray – třída  
 `CByteArray`je jedním z třídy knihovny MFC kolekce. A `CByteArray` objekt ukládá dynamické pole bajtů – pole můžou růst podle potřeby. Třída poskytuje rychlý přístup podle indexu, stejně jako u předdefinované pole v jazyce C++. `CByteArray`objekty lze serializovat a zálohované k diagnostickým účelům. Třída poskytuje členské funkce pro získání a nastavení zadaných bajtů, vkládání a připojením bajtů a odebrání jednoho bajtu nebo všechny bajty. Tato zařízení zkontrolujte analýza jednodušší binární data. Pokud je binární objekt objekt OLE, můžete chtít fungovat prostřednictvím některé bajtů hlavičky k dosažení vlastním objektu.  
  
##  <a name="_core_using_cbytearray_in_recordsets"></a>Použití CByteArray v sadách záznamů  
 Tím, že členem pole datové sady záznamů typu `CByteArray`, poskytovat pevné základ, ze kterého [RFX](../../data/odbc/record-field-exchange-rfx.md) můžete spravovat přenos takového objektu sady záznamů a zdroje dat a prostřednictvím kterého můžete upravit data v objektu. RFX vyžaduje konkrétní lokality pro načtená data a budete potřebovat přístup k základní data.  
  
 Podrobné informace o používání `CByteArray` pracovat s velkými datovými položkami, najdete v tématu [Technická poznámka 45](../../mfc/tn045-mfc-database-support-for-long-varchar-varbinary.md).  
  
##  <a name="_core_the_clongbinary_class"></a>CLongBinary – třída  
 A [CLongBinary](../../mfc/reference/clongbinary-class.md) objektu je jednoduché prostředí kolem `HGLOBAL` zpracování na blok úložiště přidělené v haldě. Když se váže sloupec tabulky obsahující binární rozsáhlý objekt, RFX přiděluje `HGLOBAL` zpracování při potřebuje k přenosu dat na sadu záznamů a uloží popisovač v `CLongBinary` pole sady záznamů.  
  
 Pak použijete `HGLOBAL` zpracování, `m_hData`, pracovat s daty, samostatně, provozní na něm jako na žádném data. To je, kdy [CByteArray](../../mfc/reference/cbytearray-class.md) přidává funkce.  
  
> [!CAUTION]
>  CLongBinary objekty nelze použít jako parametry ve volání funkce. Kromě toho, implementace, které zavolá **:: SQLGetData**, nutně zpomalí posouvání výkon posouvatelného snímku. To může také být pravdivá, když použijete **:: SQLGetData** volání sami načíst dynamické schéma sloupce.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)   
 [Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)