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
ms.openlocfilehash: ec4d83481f6335d4c40ffb8f004b617f2ee09c62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367033"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Sada záznamů: Hromadné načítání záznamů (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Třída `CRecordset` poskytuje podporu pro hromadné načítání řádků, což znamená, že více záznamů lze načíst najednou během jednoho načtení, spíše než načítání jeden záznam najednou ze zdroje dat. Hromadné načítání řádků můžete implementovat pouze `CRecordset` v odvozené třídě. Proces přenosu dat ze zdroje dat do objektu sady záznamů se nazývá hromadná výměna pole záznamu (Bulk RFX). Všimněte si, že pokud nepoužíváte `CRecordset`hromadné načítání řádků v odvozené třídě, data se přenášejí prostřednictvím výměny pole záznamu (RFX). Další informace naleznete [v tématu Record Field Exchange (RFX)](../../data/odbc/record-field-exchange-rfx.md).

Toto téma vysvětluje:

- [Jak CRecordset podporuje hromadné načítání řádků](#_core_how_crecordset_supports_bulk_row_fetching).

- [Některé zvláštní aspekty při použití hromadného načítání řádků](#_core_special_considerations).

- [Jak implementovat hromadnou výměnu polí záznamu](#_core_how_to_implement_bulk_record_field_exchange).

## <a name="how-crecordset-supports-bulk-row-fetching"></a><a name="_core_how_crecordset_supports_bulk_row_fetching"></a>Jak CRecordset podporuje hromadné načítání řádků

Před otevřením objektu sady záznamů můžete definovat `SetRowsetSize` velikost sady řádků pomocí členské funkce. Velikost sady řádků určuje, kolik záznamů má být načteno během jednoho načtení. Při hromadné načítání řádků je implementováno, výchozí velikost sady řádků je 25. Pokud hromadné načítání řádků není implementováno, velikost sady řádků zůstane pevná na 1.

Po inicializace velikosti sady řádků volejte členovou funkci [Otevřít.](../../mfc/reference/crecordset-class.md#open) Zde je nutné `CRecordset::useMultiRowFetch` zadat možnost *parametru dwOptions* k implementaci hromadného načítání řádků. Můžete také nastavit `CRecordset::userAllocMultiRowBuffers` možnost. Mechanismus výměny polí hromadných záznamů používá pole k uložení více řádků dat načtených během načítání. Tyto vyrovnávací paměti úložiště mohou být přiděleny automaticky rámci nebo je můžete přidělit ručně. Zadání možnosti `CRecordset::userAllocMultiRowBuffers` znamená, že provedete přidělení.

V následující tabulce jsou uvedeny `CRecordset` členské funkce poskytované pro podporu hromadného načítání řádků.

|Členská funkce|Popis|
|---------------------|-----------------|
|[Chyba check-sad](../../mfc/reference/crecordset-class.md#checkrowseterror)|Virtuální funkce, která zpracovává všechny chyby, ke kterým dochází během načítání.|
|[Dobulkfieldexchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementuje výměnu polí hromadných záznamů. Automaticky voláno k přenosům více řádků dat ze zdroje dat do objektu sady záznamů.|
|[GetRowsetVelikost](../../mfc/reference/crecordset-class.md#getrowsetsize)|Načte aktuální nastavení pro velikost sady řádků.|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Informuje o tom, kolik řádků bylo skutečně načteno po daném načtení. Ve většině případů se jedná o velikost sady řádků, pokud nebyla načtena neúplná sada řádků.|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Vrátí stav načtení pro určitý řádek v rámci sady řádků.|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Aktualizuje data a stav určitého řádku v rámci sady řádků.|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Přesune kurzor na určitý řádek v rámci sady řádků.|
|[Velikost setrowset](../../mfc/reference/crecordset-class.md#setrowsetsize)|Virtuální funkce, která změní nastavení velikosti sady řádků na zadanou hodnotu.|

## <a name="special-considerations"></a><a name="_core_special_considerations"></a>Zvláštní aspekty

Přestože hromadné načítání řádků je zvýšení výkonu, některé funkce fungují odlišně. Než se rozhodnete implementovat hromadné načítání řádků, zvažte následující:

- Rozhraní Framework automaticky `DoBulkFieldExchange` volá členská funkce pro přenos dat ze zdroje dat do objektu sady záznamů. Data však nejsou přenesena ze sady záznamů zpět do zdroje dat. Volání `AddNew`, `Edit` `Delete`, `Update` , nebo členské funkce má za následek kontrolní výraz se nezdařilo. Přestože `CRecordset` v současné době neposkytuje mechanismus pro aktualizaci hromadných řádků dat, `SQLSetPos`můžete zapisovat vlastní funkce pomocí funkce ROZHRANÍ API ROZHRANÍ ODBC . Další informace `SQLSetPos`o tématu naleznete v *příručce ODBC SDK Programmer's Reference* v dokumentaci k msdn.

- Členské funkce `IsDeleted` `IsFieldDirty`, `IsFieldNull` `IsFieldNullable`, `SetFieldDirty`, `SetFieldNull` a nelze použít na sady záznamů, které implementují hromadné načítání řádků. Můžete však `GetRowStatus` volat místo `IsDeleted`, `GetODBCFieldInfo` a `IsFieldNullable`místo .

- Operace `Move` přemístí sadu záznamů podle sady řádků. Předpokládejme například, že otevřete sadu záznamů, která má 100 záznamů s počáteční velikostí sady řádků 10. `Open`načte řádky 1 až 10, s aktuálním záznamem umístěným na řádku 1. Volání načte `MoveNext` další sadu řádků, ne další řádek. Tato sada řádků se skládá z řádků 11 až 20, přičemž aktuální záznam je umístěn na řádku 11. Všimněte `MoveNext` `Move( 1 )` si, že a nejsou ekvivalentní při hromadné načítání řádků je implementováno. `Move( 1 )`načte sadu řádků, která začíná 1 řádek z aktuálního záznamu. V tomto příkladu `Move( 1 )` `Open` volání po volání načte sadu řádků skládající se z řádků 2 až 11, s aktuální záznam umístěn na řádku 2. Další informace naleznete v tématu [Přesunout](../../mfc/reference/crecordset-class.md#move) člennou funkci.

- Na rozdíl od výměny polí záznamů nepodporují průvodci hromadnou výměnu polí záznamu. To znamená, že je nutné ručně deklarovat `DoBulkFieldExchange` členy dat pole a ručně přepsat zápisem volání hromadné rfx funkce. Další informace naleznete v [tématu Funkce výměny polí záznamu](../../mfc/reference/record-field-exchange-functions.md) v *referenční příručce třídy*.

## <a name="how-to-implement-bulk-record-field-exchange"></a><a name="_core_how_to_implement_bulk_record_field_exchange"></a>Jak implementovat výměnu polí hromadných záznamů

Výměna polí hromadných záznamů přenáší sadu řádků dat ze zdroje dat do objektu sady záznamů. Funkce Hromadné RFX používají pole k uložení těchto dat, stejně jako pole pro uložení délky každé datové položky v sadě řádků. V definici třídy je nutné definovat datové členy pole jako ukazatele pro přístup k polím dat. Kromě toho je nutné definovat sadu ukazatelů pro přístup k polím délek. Všechny parametry datových členů by neměly být deklarovány jako ukazatele; deklarování datových členů parametrů při použití hromadné výměny polí záznamu je stejné jako jejich deklarování při použití výměny polí záznamu. Následující kód ukazuje jednoduchý příklad:

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

Můžete buď přidělit tyto vyrovnávací paměti úložiště ručně nebo mít rozhraní do přidělení. Chcete-li přidělit vyrovnávací paměti `CRecordset::userAllocMultiRowBuffers` sami, musíte zadat možnost `Open` parametru *dwOptions* v členské funkci. Nezapomeňte nastavit velikosti polí alespoň rovna velikosti sady řádků. Pokud chcete mít rozhraní do přidělení, měli byste inicializovat ukazatele na NULL. To se obvykle provádí v konstruktoru objektu sady záznamů:

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

Nakonec je nutné přepsat `DoBulkFieldExchange` členská funkce. Pro datové členy pole volejte funkce Hromadné RFX; pro všechny datové členy parametrů volejte funkce RFX. Pokud jste otevřeli sadu záznamů předáním příkazu SQL nebo uložené procedury `Open`, pořadí, ve kterém provedete hromadné RFX volání musí odpovídat pořadí sloupců v sadě záznamů; podobně pořadí RFX volání parametrů musí odpovídat pořadí parametrů v příkazu SQL nebo uložené procedury.

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
> Je nutné `Close` volat členské funkce `CRecordset` před odvozené třídy přejde mimo rozsah. Tím je zajištěno, že všechny paměti přidělené rámci jsou uvolněny. Je vhodné programovací praxe `Close`vždy explicitně volat , bez ohledu na to, zda jste implementovali hromadné načítání řádků.

Další informace o výměně pole záznamu (RFX) naleznete v [tématu Výměna pole záznamu: Jak rfx funguje](../../data/odbc/record-field-exchange-how-rfx-works.md). Další informace o použití parametrů naleznete v [tématech CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) a [Recordset: Parametrizace sady záznamů (ODBC).](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CSada záznamů::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)
