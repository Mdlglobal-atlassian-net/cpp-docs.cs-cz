---
title: 'Výměna polí záznamu: Práce s kódem průvodce | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7d4f817ebfc3e6bb72865b4fc71fd5c5ebe5f671
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="record-field-exchange-working-with-the-wizard-code"></a>Výměna polí záznamu: Práce s kódem průvodce
Toto téma vysvětluje kód, který Průvodce aplikací knihovny MFC a **přidat třídu** (jak je popsáno v [přidání příjemce rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)) zápis k podpoře RFX a jak můžete změnit kód.  
  
> [!NOTE]
>  Toto téma se vztahuje na třídy odvozené od třídy `CRecordset` v který řádek hromadné načítání se neimplementovala. Pokud používáte hromadné načítání řádků, je implementováno Hromadná výměna pole záznamu (Bulk RFX). Hromadné RFX je podobná RFX. Chcete-li pochopit rozdíly, přečtěte si téma [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Při vytváření třídy sady záznamů pomocí Průvodce aplikací knihovny MFC nebo **přidat třídu**, průvodce zapíše následující prvky související s RFX pro vás, založené na zdroji dat, tabulky a sloupce volby, které provedete v průvodci:  
  
-   Deklarace záznamů pole datových členů ve třídě sady záznamů  
  
-   Přepsání `CRecordset::DoFieldExchange`  
  
-   Inicializace záznamů pole datových členů v konstruktoru třídy sady záznamů  
  
##  <a name="_core_the_field_data_member_declarations"></a> Deklarace pole datového člena  
 Průvodci zápis deklaraci třídy sady záznamů v souboru .h podobný následujícímu pro třídu `CSections`:  
  
```  
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
  
 Pokud přidáte parametry datových členů nebo nové pole datových členů, které navážete sami, můžete je přidáte po vygenerování průvodcem.  
  
 Navíc Všimněte si, že průvodce přepíše `DoFieldExchange` funkce člena třídy `CRecordset`.  
  
##  <a name="_core_the_dofieldexchange_override"></a> DoFieldExchange – přepsat  

 [DoFieldExchange –](../../mfc/reference/crecordset-class.md#dofieldexchange) je jádrem RFX. Volání framework `DoFieldExchange` vždy, když je pro přesun dat do zdroje dat ze zdroje dat do sady záznamů nebo ze sady záznamů. `DoFieldExchange` také podporuje získat informace o pole datových členů, prostřednictvím [IsFieldDirty](../../mfc/reference/crecordset-class.md#isfielddirty) a [IsFieldNull](../../mfc/reference/crecordset-class.md#isfieldnull) členské funkce.  
  
 Následující `DoFieldExchange` přepsání je `CSections` třídy. Průvodce zapíše funkci v souboru pro třídu sady záznamů.  
  
```  
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
  
 Všimněte si následujících klíčových funkcí funkce:  
  
-   Tato část funkce je volána pole mapy.  
  
-   Volání `CFieldExchange::SetFieldType`, až `pFX` ukazatel. Toto volání Určuje, že všechny funkce RFX volání do konce `DoFieldExchange` nebo další volání `SetFieldType` výstupní sloupce. Další informace najdete v tématu [CFieldExchange::SetFieldType](../../mfc/reference/cfieldexchange-class.md#setfieldtype).  
  
-   Několik volání `RFX_Text` globální funkce – jeden na každého pole datových členů (všechny, které jste `CString` proměnné v příkladu). Tyto volání určit vztah mezi název sloupce ve zdroji dat a pole datových členů. Funkce RFX provést přenos skutečná data. Knihovna tříd poskytuje funkce RFX pro všechny běžné typy dat. Další informace o funkce RFX najdete v tématu [výměna polí záznamu: použití funkcí RFX](../../data/odbc/record-field-exchange-using-the-rfx-functions.md).  
  
    > [!NOTE]
    >  Pořadí sloupců v sady výsledků musí odpovídat pořadí volání funkce RFX v `DoFieldExchange`.  
  
-   `pFX` Ukazatel na [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objekt, který předává rozhraní při volání `DoFieldExchange`. `CFieldExchange` Objektu určuje operaci, `DoFieldExchange` je provést, směr přenosu a další informace o kontextu.  
  
##  <a name="_core_the_recordset_constructor"></a> Konstruktor sady záznamů  
 Sada záznamů konstruktor, který zapíše průvodce obsahuje dvě věci týkající se RFX:  
  
-   Inicializaci pro každé pole datového člena  
  
-   Inicializaci pro [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) datového člena, který obsahuje počet pole datových členů  
  
 V konstruktoru pro `CSections` příklad sady záznamů vypadá takto:  
  
```  
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
>  Pokud chcete přidat žádné pole datových členů ručně, jak můžete, pokud dynamicky navázat nové sloupce, musíte zvýšit `m_nFields`. Přidáním další řádky kódu, například postupujte následovně:  
  
```  
m_nFields += 3;  
```  

 Toto je kód pro přidání tři nové pole. Pokud chcete přidat všechny parametry datových členů, je třeba inicializovat [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) datového člena, který obsahuje počet parametry datových členů. Umístit `m_nParams` inicializace mimo závorky.  

  
## <a name="see-also"></a>Viz také  
 [Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)