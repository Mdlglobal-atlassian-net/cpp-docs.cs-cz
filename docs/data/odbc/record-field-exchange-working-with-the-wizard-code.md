---
title: 'Výměna polí záznamu: Práce s kódem průvodce'
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
ms.openlocfilehash: 81b26e61f64623d1e3da5ed207d0e8e43350229d
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708003"
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>Výměna polí záznamu: Práce s kódem průvodce

> [!NOTE] 
> Průvodce příjemcem ODBC knihovny MFC není k dispozici v aplikaci Visual Studio 2019 a novějším. Příjemce měli stále můžete vytvořit ručně.

Toto téma popisuje kód, který Průvodce aplikací knihovny MFC a **přidat třídu** (jak je popsáno v [přidání příjemce ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) zápisu pro podporu RFX a jak můžete chtít změnit kód.

> [!NOTE]
>  Toto téma platí pro třídy odvozené od `CRecordset` v který řádek hromadné načítání není implementovaná. Pokud používáte hromadné načítání řádků, je implementováno Hromadná výměna pole záznamu (Bulk RFX). Hromadné funkce RFX je podobný RFX. Pokud chcete znát rozdíly, přečtěte si téma [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Při vytváření třídy sady záznamů pomocí Průvodce aplikací knihovny MFC nebo **přidat třídu**, Průvodce provádí zápis následující elementy související s RFX je založené na zdroji dat tabulky a sloupce volby provedené v průvodci:

- Deklarace pole data členů sady záznamů ve třídě sady záznamů

- Přepsání `CRecordset::DoFieldExchange`

- Inicializace pole data členů sady záznamů v konstruktoru třídy sady záznamů

##  <a name="_core_the_field_data_member_declarations"></a> Deklarace pole datového člena

Průvodci zápis deklarace třídy sady záznamů v souboru .h, který se podobá následující třídy `CSections`:

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

Pokud chcete přidat parametry datových členů nebo nové pole datových členů, které můžete vytvořit vazbu sami, můžete je přidáte po ty generované v průvodci.

Také, Všimněte si, že průvodce přepíše `DoFieldExchange` členské funkce třídy `CRecordset`.

##  <a name="_core_the_dofieldexchange_override"></a> DoFieldExchange přepsání

[DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) je srdcem RFX. Rámec volá `DoFieldExchange` kdykoli potřebuje pro přesun dat do zdroje dat ze zdroje dat do sady záznamů nebo ze sady záznamů. `DoFieldExchange` také podporuje získávání informací o pole datových členů prostřednictvím [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) a [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) členské funkce.

Následující `DoFieldExchange` přepsání je pro `CSections` třídy. Průvodce funkce zapíše do souboru CPP pro třídu sady záznamů.

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

Všimněte si, že následující klíčové funkce funkce:

- V této části funkce se nazývá pole mapy.

- Volání `CFieldExchange::SetFieldType`, až `pFX` ukazatele. Toto volání Určuje, že všechny funkce RFX se volá na konec `DoFieldExchange` nebo další volání `SetFieldType` výstupní sloupce. Další informace najdete v tématu [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).

- Několik volání `RFX_Text` globální funkce – jeden do každého pole datového člena (vše jejíž `CString` proměnné v příkladu). Tato volání určit vztah mezi název sloupce ve zdroji dat a pole datového člena. Funkce RFX provést přenos skutečná data. Knihovna tříd poskytuje funkce RFX pro všechny běžné typy dat. Další informace o funkce RFX najdete v tématu [výměna polí záznamu: Použití funkcí RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).

    > [!NOTE]
    >  Pořadí sloupců v sadě výsledků musí odpovídat pořadí volání funkcí RFX v `DoFieldExchange`.

- `pFX` Ukazatel [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objekt, který předává rozhraní framework při volání `DoFieldExchange`. `CFieldExchange` Objekt určuje operaci, která `DoFieldExchange` je provedení, směr přenosu a další informace o kontextu.

##  <a name="_core_the_recordset_constructor"></a> Konstruktoru sady záznamů

Konstruktoru sady záznamů, který zapíše průvodce obsahuje související s RFX dvě věci:

- Inicializace pro každé pole datového člena

- Inicializace pro [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) datový člen, který obsahuje počet pole datových členů

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
>  Pokud chcete přidat žádné datové členy polí ručně, jak můžete, pokud svážete nové sloupce dynamicky, musíte zvýšit `m_nFields`. To tak, že připojení další řádek kódu, jako například:

```cpp
m_nFields += 3;
```

Toto je kód pro přidání tři nová pole. Pokud chcete přidat všechny parametry datových členů, musí se inicializovat [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) datový člen, který obsahuje číslo parametru datové členy. Vložit `m_nParams` inicializace mimo závorky.

## <a name="see-also"></a>Viz také:

[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)