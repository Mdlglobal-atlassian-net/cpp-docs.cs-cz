---
title: 'Sada záznamů: Hromadné načítání záznamů (ODBC)'
ms.date: 11/04/2016
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
ms.openlocfilehash: cd9597da7ab4c405f90a145182d63945cef48c53
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079828"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Sada záznamů: Hromadné načítání záznamů (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Třída `CRecordset` poskytuje podporu pro hromadné načítání řádků, což znamená, že více záznamů lze načíst najednou během jednoho načtení, nikoli během načítání jednoho záznamu ze zdroje dat. Hromadné načítání řádků lze implementovat pouze v odvozené `CRecordset` třídě. Proces přenosu dat ze zdroje dat do objektu sady záznamů se nazývá hromadná výměna pole záznamu (Bulk RFX). Všimněte si, že pokud nepoužíváte hromadné načítání řádků v `CRecordset`odvozené třídy, data se přenesou prostřednictvím výměny pole záznamu (RFX). Další informace najdete v tématu [Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

Toto téma vysvětluje:

- [Jak CRecordset podporuje hromadné načítání řádků](#_core_how_crecordset_supports_bulk_row_fetching).

- [Některé zvláštní okolnosti při použití hromadného načítání řádků](#_core_special_considerations).

- [Jak implementovat hromadnou výměnu pole záznamu](#_core_how_to_implement_bulk_record_field_exchange)

##  <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Jak CRecordset podporuje hromadné načítání řádků

Před otevřením objektu sady záznamů můžete definovat velikost sady řádků pomocí členské funkce `SetRowsetSize`. Velikost sady řádků určuje, kolik záznamů by mělo být načteno během jednoho načtení. Když je implementováno hromadné načítání řádků, je výchozí velikost sady řádků 25. Pokud není implementováno hromadné načítání řádků, zůstane velikost sady řádků opravena na 1.

Po inicializaci velikosti sady řádků volejte [otevřenou](../../mfc/reference/crecordset-class.md#open) členskou funkci. Tady musíte zadat možnost `CRecordset::useMultiRowFetch` parametru *dwOptions* pro implementaci hromadného načítání řádků. Můžete také nastavit možnost `CRecordset::userAllocMultiRowBuffers`. Mechanizmus výměny pole se hromadným záznamem používá pole k uložení více řádků dat načtených během načítání. Tyto vyrovnávací paměti úložiště lze automaticky přidělit rozhraním nebo je můžete přidělit ručně. Zadáním možnosti `CRecordset::userAllocMultiRowBuffers` znamená, že budete provádět přidělení.

V následující tabulce jsou uvedeny členské funkce, které poskytuje `CRecordset` pro podporu hromadného načítání řádků.

|Členská funkce|Popis|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Virtuální funkce, která zpracovává všechny chyby, ke kterým došlo během načítání.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementuje hromadnou výměnu pole záznamu. Volána automaticky pro přenos více řádků dat ze zdroje dat do objektu sady záznamů.|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Načte aktuální nastavení pro velikost sady řádků.|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Určuje, kolik řádků bylo skutečně načteno po daném načtení. Ve většině případů je to velikost sady řádků, pokud nebyla neúplná sada řádků načtena.|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Vrátí stav načtení pro určitý řádek v rámci sady řádků.|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Aktualizuje data a stav konkrétního řádku v rámci sady řádků.|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Přesune kurzor na konkrétní řádek v rámci sady řádků.|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Virtuální funkce, která změní nastavení pro velikost sady řádků na zadanou hodnotu.|

##  <a name="special-considerations"></a><a name="_core_special_considerations"></a>Zvláštní požadavky

I když hromadné načítání řádků je zvýšení výkonu, určité funkce fungují jinak. Než se rozhodnete implementovat hromadné načítání řádků, vezměte v úvahu následující skutečnosti:

- Rozhraní automaticky volá `DoBulkFieldExchange` členskou funkci pro přenos dat ze zdroje dat do objektu sady záznamů. Data však nebudou přenesena ze sady záznamů zpět do zdroje dat. Volání `AddNew`, `Edit`, `Delete`nebo `Update` členské funkce vede k selhání kontrolního výrazu. I když `CRecordset` aktuálně neposkytuje mechanismus pro aktualizaci hromadných řádků dat, můžete napsat vlastní funkce pomocí funkce rozhraní ODBC API `SQLSetPos`. Další informace o `SQLSetPos`najdete v referenčních informacích o *programátorech rozhraní ODBC SDK* v dokumentaci MSDN.

- Členské funkce `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty`a `SetFieldNull` nelze použít pro sady záznamů, které implementují hromadné načítání řádků. Můžete však volat `GetRowStatus` místo `IsDeleted`a `GetODBCFieldInfo` místo `IsFieldNullable`.

- Operace `Move` přemístí sadu záznamů podle sady řádků. Předpokládejme například, že jste otevřeli sadu záznamů s 100 záznamy s počáteční velikostí sady řádků 10. `Open` načte řádky 1 až 10 s aktuálním záznamem umístěným na řádku 1. Volání `MoveNext` načte další sadu řádků, nikoli další řádek. Tato sada řádků se skládá z řádků 11 až 20 s aktuálním záznamem umístěným na řádku 11. Všimněte si, že `MoveNext` a `Move( 1 )` nejsou ekvivalentní, když je implementováno hromadné načítání řádků. `Move( 1 )` načte sadu řádků, která od aktuálního záznamu začíná 1 řádek. V tomto příkladu volání `Move( 1 )` po volání `Open` načte sadu řádků sestávající z řádků 2 až 11 s aktuálním záznamem umístěným na řádku 2. Další informace naleznete v tématu funkce [Move](../../mfc/reference/crecordset-class.md#move) member.

- Na rozdíl od výměny pole záznamu nepodporují Průvodci hromadnou výměnu pole záznamu. To znamená, že je nutné ručně deklarovat datové členy pole a ručně přepsat `DoBulkFieldExchange` zapsáním volání funkce hromadného RFX. Další informace najdete v tématu informace o [funkcích výměny pole záznamu](../../mfc/reference/record-field-exchange-functions.md) v *knihovně tříd*.

##  <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>Implementace hromadné výměny pole záznamu

Hromadná výměna pole záznamu přenáší sadu řádků dat ze zdroje dat do objektu sady záznamů. Hromadné funkce RFX používají pole k uložení těchto dat a také pole pro uložení délky každé položky dat v sadě řádků. V definici třídy je nutné definovat pole datových členů jako ukazatele pro přístup k polím dat. Kromě toho je nutné definovat sadu ukazatelů pro přístup k polím délek. Žádné datové členy parametru by neměly být deklarovány jako ukazatelé. deklarace datových členů parametrů při použití hromadné výměny pole záznamu je stejná jako při použití výměny pole záznamu. Následující kód ukazuje jednoduchý příklad:

```cpp
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

Tyto vyrovnávací paměti úložiště můžete buď přidělit ručně, nebo mít rozhraní přidělení. Chcete-li přidělovat vyrovnávací paměti sami, je nutné zadat možnost `CRecordset::userAllocMultiRowBuffers` parametru *dwOptions* ve `Open` členské funkci. Nezapomeňte nastavit velikosti polí alespoň se stejnou velikostí sady řádků. Pokud chcete, aby rozhraní převedlo alokaci, měli byste inicializovat ukazatele na hodnotu NULL. To se obvykle provádí v konstruktoru objektu sady záznamů:

```cpp
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

Nakonec musíte přepsat členskou funkci `DoBulkFieldExchange`. Pro pole datových členů zavolejte funkce hromadného RFX; u všech datových členů parametrů volejte funkce RFX. Pokud jste sadu záznamů otevřeli předáním příkazu jazyka SQL nebo uložené procedury do `Open`, pořadí, ve kterém provedete volání hromadného RFX, musí odpovídat pořadí sloupců v sadě záznamů. Podobně pořadí volání RFX pro parametry musí odpovídat pořadí parametrů v příkazu SQL nebo uložené proceduře.

```cpp
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
>  Před vyvoláním odvozené `CRecordset` třídy z oboru je třeba zavolat členskou funkci `Close`. Tím se zajistí uvolnění paměti přidělené rozhraním. Je dobrým programovacím postupem, který vždy explicitně volá `Close`bez ohledu na to, jestli jste implementovali hromadné načítání řádků.

Další informace o výměně pole záznamu (RFX) najdete v tématu [Výměna pole záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md). Další informace o použití parametrů naleznete v tématu [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) a [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset:: m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset:: m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
