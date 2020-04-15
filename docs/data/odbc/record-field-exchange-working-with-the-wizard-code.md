---
title: 'Výměna polí záznamu: Práce s kódem průvodce'
ms.date: 05/09/2019
helpviewer_keywords:
- DoFieldExchange method, overriding
- Unicode, with database classes
- field data members, declaring
- RFX (ODBC), wizard code
- RFX (ODBC), implementing
- field data members
- ODBC, RFX
- m_nParams data member, initializing
- m_nFields data member
- m_nParams data member
- overriding, DoFieldExchange
- m_nFields data member, initializing
ms.assetid: f00d882a-ff1b-4a75-9717-98d8762bb237
ms.openlocfilehash: 8e42fc9da672ca4ef97e775776935650ab7f545a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367117"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>Výměna polí záznamu: Práce s kódem průvodce

> [!NOTE]
> Průvodce příjemcem knihovny MFC ODBC není k dispozici v sadě Visual Studio 2019 a novějších. Stále můžete vytvořit příjemce ručně.

Toto téma vysvětluje kód, který Průvodce aplikací knihovny MFC a **Přidat třídy** (jak je popsáno v [přidání příjemce Knihovny MFC ODBC)](../../mfc/reference/adding-an-mfc-odbc-consumer.md)psát na podporu RFX a jak můžete chtít změnit tento kód.

> [!NOTE]
> Toto téma se vztahuje `CRecordset` na třídy odvozené z, ve kterém hromadné načítání řádků nebyla implementována. Pokud používáte hromadné načítání řádků, je implementována výměna pole hromadného záznamu (Bulk RFX). Hromadné RFX je podobný RFX. Rozdíly najdete v tématu [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Když vytvoříte třídu sady záznamů pomocí Průvodce aplikací knihovny MFC nebo **Přidat třídu**, průvodce za vás na základě voleb zdroje dat, tabulky a sloupců, které provedete v průvodci, zapíše následující prvky související s rfx:

- Deklarace datových členů pole sady záznamů ve třídě sady záznamů

- Přepsání`CRecordset::DoFieldExchange`

- Inicializace datových členů pole sady záznamů v konstruktoru třídy sady záznamů

## <a name="field-data-member-declarations"></a><a name="_core_the_field_data_member_declarations"></a>Deklarace datových údajů v terénu

Průvodci zapisují deklaraci třídy sady záznamů do `CSections`souboru H, která se podobá následujícímu pro třídu :

```cpp
class CSections : public CRecordset
{
public:
   CSections(CDatabase* pDatabase = NULL);
   DECLARE_DYNAMIC(CSections)

// Field/Param Data
   CString   m_strCourseID;
   CString   m_strInstructorID;
   CString   m_strRoomNo;
   CString   m_strSchedule;
   CString   m_strSectionNo;

// Overrides
   // Wizard generated virtual function overrides
   protected:
   virtual CString GetDefaultConnect();  // Default connection string
   virtual CString GetDefaultSQL();      // Default SQL for Recordset
   virtual void DoFieldExchange(CFieldExchange* pFX);  // RFX support

// Implementation
#ifdef _DEBUG
   virtual void AssertValid() const;
   virtual void Dump(CDumpContext& dc) const;
#endif

};
```

Pokud přidáte členy dat parametru nebo nové datové členy pole, které sami svážete, přidejte je za členy generovaných průvodcem.

Všimněte si také, že `DoFieldExchange` průvodce přepíše členská funkce třídy `CRecordset`.

## <a name="dofieldexchange-override"></a><a name="_core_the_dofieldexchange_override"></a>DoFieldExchange Přepsat

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) je srdcem RFX. Rozhraní framework `DoFieldExchange` volá kdykoli, kdy potřebuje přesunout data ze zdroje dat do sady záznamů nebo ze sady záznamů do zdroje dat. `DoFieldExchange`také podporuje získávání informací o členech dat pole prostřednictvím členských funkcí [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) a [IsFieldNull.](../../mfc/reference/crecordset-class.md#isfieldnull)

Následující `DoFieldExchange` přepsání je `CSections` pro třídu. Průvodce zapíše funkci do souboru CPP pro vaši třídu sady záznamů.

```cpp
void CSections::DoFieldExchange(CFieldExchange* pFX)
{
   pFX->SetFieldType(CFieldExchange::outputColumn);
   RFX_Text(pFX, "CourseID", m_strCourseID);
   RFX_Text(pFX, "InstructorID", m_strInstructorID);
   RFX_Text(pFX, "RoomNo", m_strRoomNo);
   RFX_Text(pFX, "Schedule", m_strSchedule);
   RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

Všimněte si následujících klíčových vlastností funkce:

- Tato část funkce se nazývá mapa pole.

- Volání do `CFieldExchange::SetFieldType`, `pFX` prostřednictvím ukazatele. Toto volání určuje, že všechny funkce RFX volání až do konce `DoFieldExchange` nebo další volání `SetFieldType` jsou výstupní sloupce. Další informace naleznete v tématu [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

- Několik volání `RFX_Text` globální funkce – jeden na člena dat `CString` pole (všechny z nich jsou proměnné v příkladu). Tato volání určují vztah mezi názvem sloupce ve zdroji dat a datovým členem pole. Funkce RFX provést skutečný přenos dat. Knihovna tříd poskytuje funkce RFX pro všechny běžné datové typy. Další informace o funkcích RFX naleznete v [tématu Záznam pole Exchange: Pomocí funkce RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).

    > [!NOTE]
    >  Pořadí sloupců v sadě výsledků se musí shodovat `DoFieldExchange`s pořadím volání funkce RFX v aplikaci .

- Ukazatel `pFX` na [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objektu, který prochází `DoFieldExchange`rámci při volání . Objekt `CFieldExchange` určuje operaci, `DoFieldExchange` která má být vykonána, směr přenosu a další kontextové informace.

## <a name="recordset-constructor"></a><a name="_core_the_recordset_constructor"></a>Konstruktor sady záznamů

Konstruktor sady záznamů, který průvodci zapíší, obsahuje dvě věci související s RFX:

- Inicializace pro každého datového člena pole

- Inicializace pro datový člen [m_nFields,](../../mfc/reference/crecordset-class.md#m_nfields) který obsahuje počet datových členů pole

Konstruktor pro `CSections` příklad sady záznamů vypadá takto:

```cpp
CSections::CSections(CDatabase* pdb)
   : CRecordset(pdb)
{
   m_strCourseID = "";
   m_strInstructorID = "";
   m_strRoomNo = "";
   m_strSchedule = "";
   m_strSectionNo = "";
   m_nFields = 5;
}
```

> [!NOTE]
> Pokud přidáte libovolnou členy dat pole ručně, jako byste mohli, pokud dynamicky svážete nové sloupce, je nutné zvýšit . `m_nFields` Proveďte připojením jiného řádku kódu, například:

```cpp
m_nFields += 3;
```

Toto je kód pro přidání tří nových polí. Pokud přidáte všechny datové členy parametru, musíte inicializovat [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) datový člen, který obsahuje počet datových členů parametru. Vložte `m_nParams` inicializaci mimo závorky.

## <a name="see-also"></a>Viz také

[Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)
