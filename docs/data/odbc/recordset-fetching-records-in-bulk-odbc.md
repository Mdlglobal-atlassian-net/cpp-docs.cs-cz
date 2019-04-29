---
title: 'Recordset: (ODBC) hromadné načítání záznamů'
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
ms.openlocfilehash: 2fdcbf18fcb0d97ba7b2a39aa9bbbd79e65a4112
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397845"
---
# <a name="recordset-fetching-records-in-bulk-odbc"></a>Recordset: (ODBC) hromadné načítání záznamů

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Třída `CRecordset` poskytuje podporu pro hromadné načítání řádků, což znamená, že několik záznamů lze načíst najednou během jednoho načtení, nikoli při načítání jednoho záznamu postupně ze zdroje dat. Můžete implementovat hromadné načítání řádků v odvozené `CRecordset` třídy. Proces přenosu dat ze zdroje dat do objektu sady záznamů se nazývá hromadná výměna pole záznamu (Bulk RFX). Všimněte si, že pokud nepoužíváte hromadné načítání řádků v `CRecordset`-odvozené třídy, data se přenáší přes výměna pole záznamu (RFX). Další informace najdete v tématu [výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md).

Toto téma vysvětluje:

- [Jak podporuje CRecordset hromadné načítání řádků](#_core_how_crecordset_supports_bulk_row_fetching).

- [Některé zvláštní aspekty při používání hromadné načítání řádků](#_core_special_considerations).

- [Jak implementovat Hromadná výměna polí záznamu](#_core_how_to_implement_bulk_record_field_exchange).

##  <a name="_core_how_crecordset_supports_bulk_row_fetching"></a> Jak podporuje CRecordset hromadné načítání řádků

Před otevřením objektu sady záznamů, můžete definovat velikost řádků s `SetRowsetSize` členskou funkci. Velikost řádků určuje, kolik záznamů by měly být načteny během jednoho načtení. Po implementaci hromadné načítání řádků výchozí velikost sady řádků je 25. Pokud není implementována hromadné načítání řádků, velikost řádků zůstane pevně 1.

Po inicializaci velikost řádků volání [otevřít](../../mfc/reference/crecordset-class.md#open) členskou funkci. Tady je nutné zadat `CRecordset::useMultiRowFetch` možnost *dwOptions* parametr implementujících hromadné načítání řádků. Můžete také nastavit `CRecordset::userAllocMultiRowBuffers` možnost. Mechanismus exchange pole záznamu používá pole pro uložení více řádky dat, které jsou načteny. Tyto vyrovnávací paměti úložišť mohou být přiděleny automaticky rozhraním, nebo můžete přiřadit ručně. Zadání `CRecordset::userAllocMultiRowBuffers` možnost znamená, že provedete přidělení.

V následující tabulce jsou uvedeny členské funkce poskytované `CRecordset` pro podporu hromadné načítání řádků.

|Členská funkce|Popis|
|---------------------|-----------------|
|[CheckRowsetError](../../mfc/reference/crecordset-class.md#checkrowseterror)|Virtuální funkce, která zpracovává všechny chyby, ke kterým dojde během načítání.|
|[DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange)|Implementuje Hromadná výměna polí záznamu. Volá se, automaticky se přenosy několik řádků dat ze zdroje dat do objektu sady záznamů.|
|[GetRowsetSize](../../mfc/reference/crecordset-class.md#getrowsetsize)|Načte aktuální nastavení pro velikost řádků.|
|[GetRowsFetched](../../mfc/reference/crecordset-class.md#getrowsfetched)|Určuje, kolik řádků ve skutečnosti načetlo po daném načtení. Ve většině případů je velikost řádků, pokud se načetla neúplné sady řádků.|
|[GetRowStatus](../../mfc/reference/crecordset-class.md#getrowstatus)|Vrátí stav načítání pro konkrétního řádku v rámci sady řádků.|
|[RefreshRowset](../../mfc/reference/crecordset-class.md#refreshrowset)|Aktualizuje data a stav konkrétního řádku v rámci sady řádků.|
|[SetRowsetCursorPosition](../../mfc/reference/crecordset-class.md#setrowsetcursorposition)|Přesune kurzor na konkrétní řádek v rámci sady řádků.|
|[SetRowsetSize](../../mfc/reference/crecordset-class.md#setrowsetsize)|Virtuální funkce, která změní nastavení velikosti sady řádků se zadanou hodnotou.|

##  <a name="_core_special_considerations"></a> Zvláštní upozornění

I když hromadné načítání řádků je zvýšení výkonu, některé funkce fungují odlišně. Předtím, než se rozhodnete implementovat hromadné načítání řádků, zvažte následující:

- Rozhraní automaticky zavolá `DoBulkFieldExchange` členskou funkci pro přenos dat ze zdroje dat do objektu sady záznamů. Však není přenesená data ze sady záznamů zpět do zdroje dat. Volání `AddNew`, `Edit`, `Delete`, nebo `Update` členské funkce výsledkem neplatnost kontrolního výrazu. I když `CRecordset` aktuálně neposkytuje mechanismus pro hromadnou aktualizaci řádků dat, můžete napsat vlastní funkce pomocí funkce ODBC API `SQLSetPos`. Další informace o `SQLSetPos`, najdete v článku *SDK Programátorská Reference ODBC* v dokumentaci MSDN.

- Členské funkce `IsDeleted`, `IsFieldDirty`, `IsFieldNull`, `IsFieldNullable`, `SetFieldDirty`, a `SetFieldNull` nelze použít v sadách záznamů implementujících hromadné načítání řádků. Můžete však volat `GetRowStatus` místo `IsDeleted`, a `GetODBCFieldInfo` místo `IsFieldNullable`.

- `Move` Operace přemístí sady záznamů v sadě řádků. Předpokládejme například, že otevřít sadu záznamů, který má 100 záznamů řádků počáteční velikost 10. `Open` načte řádky 1 až 10 s aktuálním záznamem umístěn na řádku 1. Volání `MoveNext` načte další sadu řádků, nikoli na další řádek. Tato sada řádků se skládá z řádky 11 až 20, s aktuálním záznamem umístěn na řádku 11. Všimněte si, že `MoveNext` a `Move( 1 )` nejsou ekvivalentní, je-li hromadné načítání řádků je implementována. `Move( 1 )` načte sadu řádků, které začíná 1 řádek z aktuální záznam. V tomto příkladu volání `Move( 1 )` po volání `Open` načte sadu řádků, který se skládá z řádky 2 až 11, s aktuálním záznamem umístěn na řádku 2. Další informace najdete v tématu [přesunout](../../mfc/reference/crecordset-class.md#move) členskou funkci.

- Na rozdíl od výměna polí záznamu průvodců nepodporují Hromadná výměna polí záznamu. To znamená, že musíte ručně deklarovat pole datových členů a ručně přepsat `DoBulkFieldExchange` napsáním volání funkcí Bulk RFX. Další informace najdete v tématu [funkce výměny polí v záznamu](../../mfc/reference/record-field-exchange-functions.md) v *knihovny tříd*.

##  <a name="_core_how_to_implement_bulk_record_field_exchange"></a> Jak implementovat Hromadná výměna pole záznamu

Hromadná výměna polí záznamu přenese sadu řádků dat ze zdroje dat do objektu sady záznamů. Funkce Bulk RFX použijte pole pro ukládání těchto dat, stejně jako pole k uložení délky jednotlivých datových položek v dané sadě řádků. V definici třídy je nutné definovat jako ukazatele pro přístup k polím data pole datových členů. Kromě toho je nutné definovat sadu ukazatele pro přístup k polím délky. Všechny parametry datových členů by neměl být deklarovány jako ukazatele; deklarace parametru datové členy, při použití Hromadná výměna polí záznamu je stejné jako deklarování je při použití výměna polí záznamu. Následující kód ukazuje jednoduchý příklad:

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

Můžete přidělit vyrovnávací paměti úložiště ručně, nebo mít systém, který provedl přidělení. Přidělení vyrovnávací paměti, je nutné zadat `CRecordset::userAllocMultiRowBuffers` možnost *dwOptions* parametr `Open` členskou funkci. Ujistěte se, že nastavení velikosti pole minimálně roven velikost řádků. Pokud chcete mít systém, který provedl přidělení, by měl inicializovat ukazatele na hodnotu NULL. To se obvykle provádí v konstruktoru objektu sada záznamů:

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

A konečně, je nutné přepsat `DoBulkFieldExchange` členskou funkci. Pole datových členů volání funkce Bulk RFX. pro všechny parametry datových členů volání funkcí RFX. Při otevření sady záznamů předáním příkaz SQL nebo uloženou proceduru pro `Open`, pořadí, ve kterém můžete provádět volání Bulk RFX musí odpovídat pořadí sloupců v sadě záznamů; podobně pořadí funkcí RFX volání pro parametry musí odpovídat. pořadí parametrů v příkazu SQL nebo uloženou proceduru.

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
>  Je třeba zavolat `Close` členskou funkci před vaší odvozené `CRecordset` třídy dostane mimo rozsah. Tím se zajistí, že jsou uvolněny rámec přidělení paměti. Vždy explicitně volat při programování je dobrým `Close`, bez ohledu na to, zda jste implementovali hromadné načítání řádků.

Další informace o výměna pole záznamu (RFX) najdete v tématu [výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md). Další informace o použití parametrů najdete v tématu [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype) a [sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="see-also"></a>Viz také:

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[CRecordset::m_nFields](../../mfc/reference/crecordset-class.md#m_nfields)<br/>
[CRecordset::m_nParams](../../mfc/reference/crecordset-class.md#m_nparams)

