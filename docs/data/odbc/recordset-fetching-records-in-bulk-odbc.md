---
title: "Sada záznamů: Hromadné načítání záznamů (ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- bulk row fetching, implementing
- ODBC recordsets, bulk row fetching
- bulk record field exchange
- bulk row fetching
- bulk RFX functions
- recordsets, bulk row fetching
- DoBulkFieldExchange method
- fetching ODBC records in bulk
- RFX (ODBC), bulk
- rowsets, bulk row fetching
- RFX (ODBC), bulk row fetching
ms.assetid: 20d10fe9-c58a-414a-b675-cdf9aa283e4f
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c0eff5528d2b612fbeab4511f64341975791f3e1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Sada záznamů: Hromadné načítání záznamů (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Třída `CRecordset` poskytuje podporu pro hromadné načítání řádků, což znamená, že více záznamů můžete načíst najednou během jednoho načtení, namísto načítání jeden záznam v čase z datového zdroje. Můžete implementovat hromadné načítání řádků v odvozené `CRecordset` třídy. Proces přenosu dat ze zdroje dat do objektu sady záznamů se nazývá hromadná výměna pole záznamu (Bulk RFX). Všimněte si, že pokud nepoužíváte hromadné načítání řádků v `CRecordset`-odvozené třídy, data se přenáší přes pole záznamu (exchange – RFX). Další informace najdete v tématu [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).  
  
 Toto téma vysvětluje:  
  
-   [Jak podporuje CRecordset hromadné načítání řádků](#_core_how_crecordset_supports_bulk_row_fetching).  
  
-   [Některé zvláštní aspekty při používání hromadné načítání řádků](#_core_special_considerations).  
  
-   [Jak implementovat Hromadná výměna pole záznamu](#_core_how_to_implement_bulk_record_field_exchange).  
  
##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Jak podporuje CRecordset hromadné načítání řádků  
 Před otevřením objektu sady záznamů, můžete definovat velikost sady řádků pomocí `SetRowsetSize` – členská funkce. Velikost sady řádků určuje, kolik záznamy mají být načtena během jednoho načtení. Pokud se implementuje hromadné načítání řádků, výchozí velikost sady řádků je 25. Pokud není implementována hromadné načítání řádků, zůstává v 1 Pevná velikost sady řádků.  
  
 Poté, co jste inicializovali velikost sady řádků, volejte [otevřete](../../mfc/reference/crecordset-class.md#open) – členská funkce. Zde je nutné zadat `CRecordset::useMultiRowFetch` možnost **dwOptions** parametr implementovat hromadné načítání řádků. Kromě toho můžete nastavit **CRecordset::userAllocMultiRowBuffers** možnost. Mechanismus výměna pole záznamu pole používá k ukládání více řádků dat načteny. Vyrovnávací paměti úložiště může být přidělen automaticky rámcem nebo kterou můžete přidělit ručně. Určení **CRecordset::userAllocMultiRowBuffers** možnost znamená, že provedete přidělení.  
  
 Následující tabulka uvádí členské funkce poskytované `CRecordset` pro podporu hromadné načítání řádků.  
  
|Členská funkce|Popis|  
|---------------------|-----------------|  
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Virtuální funkce, která zpracovává všechny chyby, ke kterým došlo během načítání.|  
|[DoBulkFieldExchange –](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementuje hromadně – record field exchange. Volá se automaticky pro přenosy více řádků dat ze zdroje dat do objektu sady záznamů.|  
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Načte aktuální nastavení velikosti sady řádků.|  
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Určuje, kolik řádků byly načteny ve skutečnosti po daném načtení. Ve většině případů je velikost sady řádků, pokud se načetla nekompletní sada řádků.|  
|[GetRowStatus –](../../mfc/reference/crecordset-class.md#getrowstatus)|Vrátí stav načítání pro konkrétního řádku v rámci sady řádků.|  
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Aktualizuje data a stav konkrétního řádku v rámci sady řádků.|  
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Posune kurzor konkrétního řádku v rámci sady řádků.|  
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Virtuální funkce, která změní nastavení velikosti sady řádků se zadanou hodnotou.|  
  
##  <a name="_core_special_considerations"></a>Zvláštní upozornění  
 I když hromadné načítání řádků je výkonnější, některé funkce fungují odlišně. Předtím, než se rozhodnete implementovat hromadné načítání řádků, zvažte následující:  
  
-   Systém automaticky volá `DoBulkFieldExchange` – členská funkce k přenosu dat ze zdroje dat do objektu sady záznamů. Však není přenesená data ze sady záznamů zpět do zdroje dat. Volání `AddNew`, **upravit**, **odstranit**, nebo **aktualizace** členské funkce má za následek selhání kontrolního výrazu. I když `CRecordset` aktuálně neposkytuje mechanismus pro hromadnou aktualizaci řádků dat, můžete napsat vlastní funkce pomocí funkce rozhraní API ODBC **SQLSetPos**. Další informace o **SQLSetPos**, najdete v článku *referenční příručka programátora SDK ODBC* v dokumentaci k webu MSDN.  
  
-   Členské funkce `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty`, a `SetFieldNull` nelze použít na sady záznamů, který implementuje hromadné načítání řádků. Můžete však volat `GetRowStatus` místě `IsDeleted`, a `GetODBCFieldInfo` místě `IsFieldNullable`.  
  
-   **Přesunout** operace přemístí sadu záznamů podle řádků. Předpokládejme například, že otevřete sadu záznamů, který má 100 záznamů s velikostí počáteční řádků 10. **Otevřete** načte řádky 1 až 10 s aktuální záznam umístěn na řádku 1. Volání `MoveNext` načte další sadu řádků, ne na další řádek. Tato sada řádků se skládá z řádků 11 až 20, s aktuálním záznamem umístěn na řádek 11. Všimněte si, že `MoveNext` a **Move (1)** nejsou ekvivalentní, při hromadné načítání řádků je implementováno. **Přesunout (1)** načte sadu řádků, která začíná 1 řádek z aktuální záznam. V tomto příkladu volání **Move (1)** po volání **otevřete** načte sadu řádků, který se skládá z řádků 2 až 11, s aktuálním záznamem umístěn na řádek 2. Další informace najdete v tématu [přesunout](../../mfc/reference/crecordset-class.md#move) – členská funkce.  
  
-   Na rozdíl od – record field exchange nepodporují průvodců Hromadná výměna pole záznamu. To znamená, že je nutné ručně deklarovat pole datových členů a ručně přepsat `DoBulkFieldExchange` ve volání funkce RFX hromadného zápisu. Další informace najdete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md) v *knihovny tříd*.  
  
##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a>Jak implementovat Hromadná výměna pole záznamu  
 Hromadná výměna pole záznamu přenese sadu řádků dat ze zdroje dat do objektu sady záznamů. Funkce hromadné RFX použít pole pro uložení dat této, stejně jako pole k uložení délka každá položka dat v dané sadě řádků. V definici vaší třídy je nutné zadat pole datových členů jako ukazatele pro přístup k polím data. Kromě toho je nutné definovat sadu ukazatele pro přístup k polím délek. Všechny parametry datových členů by neměl být deklarována jako ukazatele; deklarování parametry datových členů při použití Hromadná výměna pole záznamu je stejný jako deklarace je při použití – record field exchange. Následující kód ukazuje jednoduchý příklad:  
  
```  
class MultiRowSet : public CRecordset  
{  
public:  
   // Field/Param Data  
      // field data members  
      long* m_rgID;  
      LPSTR m_rgName;  
  
      // pointers for the lengths  
      // of the field data  
      long* m_rgIDLengths;  
      long* m_rgNameLengths;  
  
      // input parameter data member  
      CString m_strNameParam;  
  
   .  
   .  
   .  
}  
```  
  
 Můžete buď ručně přidělení vyrovnávací paměti úložiště nebo aby systém provedl přidělení. Přidělení vyrovnávací paměti, je nutné zadat **CRecordset::userAllocMultiRowBuffers** možnost **dwOptions** parametr ve **otevřete** – členská funkce. Ujistěte se, že nastavení velikosti pole minimálně roven velikost sady řádků. Pokud chcete, aby systém provedl přidělení, musí inicializovat ukazatele na **hodnotu NULL.** To se obvykle provádí v konstruktoru objektu sada záznamů:  
  
```  
MultiRowSet::MultiRowSet( CDatabase* pDB )  
   : CRecordset( pDB )  
{  
   m_rgID = NULL;  
   m_rgName = NULL;  
   m_rgIDLengths = NULL;  
   m_rgNameLengths = NULL;  
   m_strNameParam = "";  
  
   m_nFields = 2;  
   m_nParams = 1;  
  
   .  
   .  
   .  
}  
```  
  
 Nakonec je nutné přepsat `DoBulkFieldExchange` – členská funkce. Pro pole datových členů volání funkce RFX hromadné; pro všechny parametry datových členů volání funkce RFX. Pokud jste otevřeli sadu záznamů předáním příkazu SQL nebo uloženou proceduru k **otevřete**, pořadí, ve kterém provedete volání hromadné RFX musí odpovídat pořadí sloupců v sadě záznamů; podobně pořadí RFX volání pro Parametry musí odpovídat pořadí parametrů v příkazu SQL nebo uloženou proceduru.  
  
```  
void MultiRowSet::DoBulkFieldExchange( CFieldExchange* pFX )  
{  
   // call the Bulk RFX functions  
   // for field data members  
   pFX->SetFieldType( CFieldExchange::outputColumn );  
   RFX_Long_Bulk( pFX, _T( "[colRecID]" ),  
                  &m_rgID, &m_rgIDLengths );  
   RFX_Text_Bulk( pFX, _T( "[colName]" ),  
                  &m_rgName, &m_rgNameLengths, 30 );  
  
   // call the RFX functions for  
   // for parameter data members  
   pFX->SetFieldType( CFieldExchange::inputParam );  
   RFX_Text( pFX, "NameParam", m_strNameParam );  
}  
```  
  
> [!NOTE]
>  Je třeba volat **Zavřít** – členská funkce před vaší odvozené `CRecordset` třída ocitne mimo rozsah. Tím se zajistí, že jsou uvolněny všechny paměti přidělené rozhraní. Je dobrým zvykem vždy explicitně volání programovacím **Zavřít**, bez ohledu na to, jestli jste implementovali hromadné načítání řádků.  
  
 Další informace o výměna pole záznamu (RFX) najdete v tématu [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Další informace o použití parametrů najdete v tématu [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) a [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)   
 [CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

