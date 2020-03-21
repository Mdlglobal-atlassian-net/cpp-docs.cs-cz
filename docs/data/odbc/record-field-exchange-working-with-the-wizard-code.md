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
ms.openlocfilehash: 1149ab2b85c9cd803da0cd2d2ed6d931a020764e
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077085"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>Výměna polí záznamu: Práce s kódem průvodce

> [!NOTE]
> Průvodce příjemcem knihovny MFC rozhraní ODBC není dostupný v aplikaci Visual Studio 2019 a novějším. Příjemce můžete přesto vytvořit ručně.

Toto téma vysvětluje kód, který průvodce aplikací knihovny MFC a **přidává třídu** (jak je popsáno v tématu [Přidání příjemce knihovny MFC rozhraní ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) pro podporu RFX a způsob, jakým je možné tento kód změnit.

> [!NOTE]
>  Toto téma se vztahuje na třídy odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Používáte-li hromadné načítání řádků, je implementováno hromadné výměny pole záznamu (Bulk RFX). Hromadná RFX je podobná RFX. Pro pochopení rozdílů si přečtěte téma [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Když vytvoříte třídu sady záznamů pomocí Průvodce aplikací knihovny MFC nebo **přidáte třídu**, průvodce zapíše následující prvky související s RFX pro vás na základě možností zdroje dat, tabulky a sloupce, které jste provedli v průvodci:

- Deklarace datových členů pole sady záznamů ve třídě sady záznamů

- Přepsání `CRecordset::DoFieldExchange`

- Inicializace datových členů pole sady záznamů v konstruktoru třídy sady záznamů

##  <a name="field-data-member-declarations"></a><a name="_core_the_field_data_member_declarations"></a>Deklarace datových členů pole

Průvodci zapisují deklaraci třídy sady záznamů v souboru. h, který se podobá následující třídě `CSections`:

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

Pokud přidáte datové členy parametru nebo nové pole datových členů, které svážete sami, přidejte je po vygenerování průvodce.

Všimněte si také, že Průvodce Přepisuje členskou funkci `DoFieldExchange` třídy `CRecordset`.

##  <a name="dofieldexchange-override"></a><a name="_core_the_dofieldexchange_override"></a>Potlačení DoFieldExchange

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) je srdcem funkce RFX. Rozhraní volá `DoFieldExchange` kdykoli, kdy potřebuje přesunout data buď ze zdroje dat do sady záznamů, nebo ze sady záznamů do zdroje dat. `DoFieldExchange` také podporuje získávání informací o polích datových členů prostřednictvím členských funkcí [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) a [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) .

Následující `DoFieldExchange` přepsání je určena pro třídu `CSections`. Průvodce zapíše funkci v souboru. cpp pro třídu sady záznamů.

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

Všimněte si, že tyto klíčové funkce funkce:

- Tato část funkce se nazývá mapa pole.

- Volání `CFieldExchange::SetFieldType`, prostřednictvím ukazatele `pFX`. Toto volání Určuje, že všechny funkce RFX volají až na konec `DoFieldExchange` nebo další volání `SetFieldType` jsou výstupní sloupce. Další informace naleznete v tématu [CFieldExchange:: SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

- Několik volání do globální funkce `RFX_Text` – jedna na pole datového člena (všechny jsou `CString` proměnných v příkladu). Tato volání určují vztah mezi názvem sloupce ve zdroji dat a datovým členem pole. RFX funkce vlastní přenos dat. Knihovna tříd poskytuje funkce RFX pro všechny běžné datové typy. Další informace o funkcích RFX naleznete v tématu [Výměna polí záznamu: použití funkcí RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).

    > [!NOTE]
    >  Pořadí sloupců v sadě výsledků dotazu musí odpovídat pořadí volání funkce RFX v `DoFieldExchange`.

- `pFX` ukazatel na objekt [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) , který rozhraní projde při volání `DoFieldExchange`. Objekt `CFieldExchange` určuje operaci, kterou má `DoFieldExchange` provádět, směr přenosu a další kontextové informace.

##  <a name="recordset-constructor"></a><a name="_core_the_recordset_constructor"></a>Konstruktor sady záznamů

Konstruktor sady záznamů, který průvodce zapisuje, obsahuje dvě věci související s RFX:

- Inicializace pro každý datový člen pole

- Inicializace pro datový člen [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) , který obsahuje počet datových členů pole

Konstruktor příkladu sady záznamů `CSections` vypadá takto:

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
>  Pokud přidáte jakékoli datové členy pole ručně, protože pokud budete chtít dynamicky navazovat nové sloupce, je nutné zvýšit `m_nFields`. Provedete to tak, že připojíte další řádek kódu, například:

```cpp
m_nFields += 3;
```

Toto je kód pro přidání tří nových polí. Pokud přidáte jakékoli datové členy parametru, je nutné inicializovat datový člen [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) , který obsahuje počet datových členů parametru. Inicializaci `m_nParams` umístit mimo hranaté závorky.

## <a name="see-also"></a>Viz také

[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)