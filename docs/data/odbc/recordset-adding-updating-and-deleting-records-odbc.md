---
title: "Sada záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- records [C++], deleting
- AddNew method
- ODBC recordsets [C++], deleting records
- data in recordsets [C++]
- record editing [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: 760c8889-bec4-482b-a8f2-319792a6af98
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8f326a729485ddbc203e6efc04e45061bbbc08d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-adding-updating-and-deleting-records-odbc"></a>Seznam záznamů: Přidávání, aktualizace a odstranění záznamů (ODBC).
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
> [!NOTE]
>  Nyní můžete přidat záznamy hromadně efektivněji. Další informace najdete v tématu [sada záznamů: přidávání záznamů v hromadné (ODBC)](../../data/odbc/recordset-adding-records-in-bulk-odbc.md).  
  
> [!NOTE]
>  Toto téma se vztahuje na objekty, které jsou odvozené z `CRecordset` v který řádek hromadné načítání se neimplementovala. Pokud používáte hromadné načítání řádků, přečtěte si téma [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Aktualizovatelné snímky a dynamické sady vám umožní přidat, upravit (update) a odstranění záznamů. Toto téma vysvětluje:  
  
-   [Jak zjistit, zda je sady záznamů v aktualizovatelné](#_core_determining_whether_your_recordset_is_updatable).  
  
-   [Postup přidání nového záznamu](#_core_adding_a_record_to_a_recordset).  
  
-   [Postup úpravy záznamu existující](#_core_editing_a_record_in_a_recordset).  
  
-   [Jak odstranit záznam](#_core_deleting_a_record_from_a_recordset).  
  
 Další informace o způsobu zpracování aktualizací out a jak ostatním uživatelům se zobrazí vaše aktualizace, najdete v tématu [sada záznamů: Jak sady záznamů aktualizace záznamů (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md). Za normálních okolností pokud přidat, upravit nebo odstranit záznam sady záznamů se změní zdroj dat okamžitě. Skupiny související aktualizace můžete místo toho dávky do transakce. Pokud probíhá transakce, aktualizace nestane konečné dokud potvrzení transakce. To umožňuje vzít zpět nebo vrátit zpět změny. Informace o transakcích najdete v tématu [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
 Následující tabulka shrnuje dostupné možnosti pro sady záznamů s různými vlastnostmi aktualizace.  
  
### <a name="recordset-readupdate-options"></a>Možnosti pro čtení nebo aktualizace sady záznamů  
  
|Typ|Číst|Úpravy záznamů|Odstranit záznam|Přidat nové (připojit)|  
|----------|----------|-----------------|-------------------|------------------------|  
|jen pro čtení|A|N|N|N|  
|Pouze připojení|A|N|N|A|  
|Plně aktualizovat|A|A|A|A|  
  
##  <a name="_core_determining_whether_your_recordset_is_updatable"></a>Určení zda sady záznamů je aktualizovatelná  
 Objekt sady záznamů je možné aktualizovat, pokud je možné aktualizovat zdroj dat a otevřít sadu záznamů jako lze aktualizovat. Jeho aktualizovatelnosti závisí také na příkazu SQL můžete použít, možnosti ovladač rozhraní ODBC a jestli je knihovna kurzorů rozhraní ODBC v paměti. Jen pro čtení sady záznamů nebo zdroj dat nelze aktualizovat.  
  
#### <a name="to-determine-whether-your-recordset-is-updatable"></a>Chcete-li určit, zda je aktualizovat sady záznamů  
  
1.  Volání objektu sady záznamů [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) – členská funkce.  
  
     `CanUpdate`vrátí nenulovou hodnotu, pokud je sada záznamů aktualizovatelná.  
  
 Ve výchozím nastavení jsou sady záznamů plně aktualizovatelné (můžete provádět `AddNew`, **upravit**, a **odstranit** operations). Ale můžete také použít [pouze přidat](../../mfc/reference/crecordset-class.md#open) možnost otevření aktualizovatelné sady záznamů. Sady záznamů, otevřené tímto způsobem umožňuje pouze přidávání nových záznamů s `AddNew`. Nelze upravit nebo odstranit existující záznamy. Můžete zkontrolovat, zda je otevřena pouze pro přidávání voláním sady záznamů [CanAppend](../../mfc/reference/crecordset-class.md#canappend) – členská funkce. `CanAppend`vrátí nenulovou hodnotu, pokud je plně aktualizovatelná nebo otevřít pouze pro přidávání záznamů.  
  
 Následující kód ukazuje, jak je možné použít `CanUpdate` pro objekt sady záznamů názvem `rsStudentSet`:  
  
```  
if( !rsStudentSet.Open( ) )  
    return FALSE;  
if( !rsStudentSet.CanUpdate( ) )  
{  
    AfxMessageBox( "Unable to update the Student recordset." );  
    return;  
}  
```  
  
> [!CAUTION]
>  Když připravujete aktualizovat sadu záznamů voláním **aktualizace**, vezměte v potaz, že vaše sada záznamů obsahuje všechny sloupce, které představují primární klíč tabulky (nebo všechny sloupce všech jedinečný index pro tabulku). V některých případech rozhraní slouží k identifikaci, který záznam v tabulce aktualizovat pouze vybrané sloupce ve vaší sadě záznamů. Bez všechny potřebné sloupce může být aktualizováno více záznamů v tabulce, případně poškození referenční integrity tabulky. V takovém případě vyvolá architektura výjimky při volání **aktualizace**.  
  
##  <a name="_core_adding_a_record_to_a_recordset"></a>Přidání záznamu do sady záznamů  
 Můžete přidat nové záznamy do sady záznamů, pokud jeho [CanAppend](../../mfc/reference/crecordset-class.md#canappend) – členská funkce vrátí nenulovou hodnotu.  
  
#### <a name="to-add-a-new-record-to-a-recordset"></a>Chcete-li přidat nový záznam do sady záznamů  
  
1.  Ujistěte se, že je připojitelná záznamů.  
  
2.  Volání objektu sady záznamů [AddNew](../../mfc/reference/crecordset-class.md#addnew) – členská funkce.  
  
     `AddNew`připraví sadu záznamů tak, aby fungoval jako vyrovnávací paměť úprav. Všechna pole datových členů jsou nastaveny speciální hodnotu Null a označeny jako beze změny, pouze změny (dirty) hodnoty jsou zapsány ke zdroji dat při volání [aktualizace](../../mfc/reference/crecordset-class.md#update).  
  
3.  Nastavte hodnoty nový záznam pole datových členů.  
  
     Přiřadíte hodnoty pole datových členů. Ty, které nepřiřadíte nezapisují ke zdroji dat.  
  
4.  Volání objektu sady záznamů **aktualizace** – členská funkce.  
  
     **Aktualizace** dokončí přidání zapsáním nový záznam ke zdroji dat. Pro informace o se stane, pokud se nepodaří volání **aktualizace**, najdete v části [sada záznamů: Jak sady záznamů aktualizace záznamů (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Informace o tom, jak funguje přidávání záznamů a kdy jsou přidané záznamy viditelné ve vaší sadě záznamů najdete v tématu [sada záznamů: jak AddNew, Edit a odstranit pracovní (ODBC)](../../data/odbc/recordset-how-addnew-edit-and-delete-work-odbc.md).  
  
 Následující příklad ukazuje, jak přidat nový záznam:  
  
```  
if( !rsStudent.Open( ) )  
    return FALSE;  
if( !rsStudent.CanAppend( ) )  
    return FALSE;                      // no field values were set  
rsStudent.AddNew( );  
rsStudent.m_strName = strName;  
rsStudent.m_strCity = strCity;  
rsStudent.m_strStreet = strStreet;  
if( !rsStudent.Update( ) )  
{  
    AfxMessageBox( "Record not added; no field values were set." );  
    return FALSE;  
}  
```  
  
> [!TIP]
>  Zrušit `AddNew` nebo **upravit** volání, jednoduše proveďte jiné volání `AddNew` nebo **upravit** nebo volání **přesunout** s **AFX_MOVE_REFRESH**  parametr. Datové členy se resetují na předchozí hodnoty a můžete se pořád ještě v **upravit** nebo **přidat** režimu.  
  
##  <a name="_core_editing_a_record_in_a_recordset"></a>Úprava záznamů v sadě záznamů  
 Pokud můžete upravit existující záznamy sady záznamů [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) – členská funkce vrátí nenulovou hodnotu.  
  
#### <a name="to-edit-an-existing-record-in-a-recordset"></a>Chcete-li upravit existující záznam v sadě záznamů  
  
1.  Ujistěte se, že je sada záznamů aktualizovatelná.  
  
2.  Přejděte na záznam, který chcete aktualizovat.  
  
3.  Volání objektu sady záznamů [upravit](../../mfc/reference/crecordset-class.md#edit) – členská funkce.  
  
     **Upravit** připraví sadu záznamů tak, aby fungoval jako vyrovnávací paměť úprav. Všechna pole datových členů jsou označeny tak, aby sada záznamů poznali později, zda byly změněny. Nové hodnoty pro pole datových členů zapisují ke zdroji dat při volání [aktualizace](../../mfc/reference/crecordset-class.md#update).  
  
4.  Nastavte hodnoty nový záznam pole datových členů.  
  
     Přiřadíte hodnoty pole datových členů. Ty, že které nepřiřadíte hodnoty zůstanou beze změny.  
  
5.  Volání objektu sady záznamů **aktualizace** – členská funkce.  
  
     **Aktualizace** dokončí úpravy zapsáním změněné záznamu ke zdroji dat. Pro informace o se stane, pokud se nepodaří volání **aktualizace**, najdete v části [sada záznamů: Jak sady záznamů aktualizace záznamů (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
 Po úpravě záznam zůstane upravený záznam na aktuální záznam.  
  
 Následující příklad ukazuje **upravit** operaci. Předpokládá se, že se uživatel přesunul na záznam, který potvrdí chce upravit.  
  
```  
rsStudent.Edit( );  
rsStudent.m_strStreet = strNewStreet;  
rsStudent.m_strCity = strNewCity;  
rsStudent.m_strState = strNewState;  
rsStudent.m_strPostalCode = strNewPostalCode;  
if( !rsStudent.Update( ) )  
{  
    AfxMessageBox( "Record not updated; no field values were set." );  
    return FALSE;  
}  
```  
  
> [!TIP]
>  Zrušit `AddNew` nebo **upravit** volání, jednoduše proveďte jiné volání `AddNew` nebo **upravit** nebo volání **přesunout** s **AFX_MOVE_REFRESH**  parametr. Datové členy se resetují na předchozí hodnoty a můžete se pořád ještě v **upravit** nebo **přidat** režimu.  
  
##  <a name="_core_deleting_a_record_from_a_recordset"></a>Odstranění záznamu z sady záznamů  
 Pokud odstraníte záznamy sady záznamů [CanUpdate](../../mfc/reference/crecordset-class.md#canupdate) – členská funkce vrátí nenulovou hodnotu.  
  
#### <a name="to-delete-a-record"></a>Odstranit záznam  
  
1.  Ujistěte se, že je sada záznamů aktualizovatelná.  
  
2.  Přejděte na záznam, který chcete aktualizovat.  
  
3.  Volání objektu sady záznamů [odstranit](../../mfc/reference/crecordset-class.md#delete) – členská funkce.  
  
     **Odstranit** okamžitě označí záznam jako odstranit, v sadě záznamů i na datovém zdroji.  
  
     Na rozdíl od `AddNew` a **upravit**, **odstranit** nemá odpovídající **aktualizace** volání.  
  
4.  Přechod na jiný záznam.  
  
    > [!NOTE]
    >  Při procházení sadou záznamů, nemusí být přeskočeny odstraněné záznamy. Další informace najdete v tématu [IsDeleted](../../mfc/reference/crecordset-class.md#isdeleted) – členská funkce.  
  
 Následující příklad ukazuje **odstranit** operaci. Přitom se předpokládá, že se uživatel přesunul na záznam, který chce uživatel odstranit. Po **odstranit** je volána, je důležité pro přesun do nového záznamu.  
  
```  
rsStudent.Delete( );  
rsStudent.MoveNext( );  
```  
  
 Další informace o důsledcích `AddNew`, **upravit**, a **odstranit** členské funkce, najdete v části [sada záznamů: Jak sady záznamů aktualizace záznamů (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Zamykání záznamů (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)