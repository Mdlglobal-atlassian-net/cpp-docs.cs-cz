---
title: 'Sada záznamů: Architektura (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, data members
- field data members, recordset architecture
- field data members
- m_nParams data member, recordsets
- recordsets, architecture
- parameter data members in recordsets
- m_nFields data member
- ODBC recordsets, architecture
- m_nParams data member
- m_nFields data member, recordsets
ms.assetid: 47555ddb-11be-4b9e-9b9a-f2931764d298
ms.openlocfilehash: bb4b67a4c534598a8e26eb9ab5f297b108b67b6d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212989"
---
# <a name="recordset-architecture-odbc"></a>Sada záznamů: Architektura (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Toto téma popisuje datové členy, které tvoří architekturu objektu sady záznamů:

- [Datové členy pole](#_core_field_data_members)

- [Datové členy parametru](#_core_parameter_data_members)

- [Použití datových členů m_nFields a m_nParams](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
>  Toto téma se vztahuje na objekty odvozené od `CRecordset`, ve kterých nebylo implementováno hromadné načítání řádků. Pokud je implementováno hromadné načítání řádků, je architektura podobná. Pro pochopení rozdílů si přečtěte téma [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="sample-class"></a><a name="_core_a_sample_class"></a>Sample – třída

> [!NOTE]
> Průvodce příjemcem knihovny MFC rozhraní ODBC není dostupný v aplikaci Visual Studio 2019 a novějším. Příjemce můžete přesto vytvořit ručně.

Použijete-li průvodce [příjemcem rozhraní ODBC knihovny MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z průvodce **přidáním třídy** k deklaraci třídy sady záznamů odvozené od `CRecordset`, výsledná třída má obecnou strukturu zobrazenou v následující jednoduché třídě:

```cpp
class CCourse : public CRecordset
{
public:
   CCourse(CDatabase* pDatabase = NULL);
   ...
   CString m_strCourseID;
   CString m_strCourseTitle;
   CString m_strIDParam;
};
```

Na začátku třídy Průvodce zapisuje sadu [datových členů pole](#_core_field_data_members). Při vytváření třídy je nutné zadat jeden nebo více datových členů pole. Pokud je třída parametrizovaná, protože ukázková třída je (s datovým členem `m_strIDParam`), musíte ručně přidat [datové členy parametrů](#_core_parameter_data_members). Průvodce nepodporuje přidávání parametrů do třídy.

##  <a name="field-data-members"></a><a name="_core_field_data_members"></a>Datové členy pole

Nejdůležitějšími členy vaší třídy sady záznamů jsou pole datových členů. Pro každý sloupec, který vyberete ze zdroje dat, třída obsahuje datový člen příslušného datového typu pro daný sloupec. Například [Třída vzorku](#_core_a_sample_class) zobrazená na začátku tohoto tématu má dva pole datových členů, jak typu `CString`, nazývané `m_strCourseID` a `m_strCourseTitle`.

Když sada záznamů vybere sadu záznamů, rozhraní automaticky váže sloupce aktuálního záznamu (po volání `Open`, první záznam je aktuální) k poli datových členů objektu. To znamená, že rozhraní používá příslušný datový člen pole jako vyrovnávací paměť, do které se ukládá obsah sloupce záznamu.

Když se uživatel posune k novému záznamu, používá rozhraní pole datových členů k reprezentaci aktuálního záznamu. Rozhraní aktualizuje pole datových členů a nahradí hodnoty předchozího záznamu. Datové členy pole se používají také k aktualizaci aktuálního záznamu a k přidávání nových záznamů. V rámci procesu aktualizace záznamu zadáte hodnoty aktualizace přiřazením hodnot přímo k příslušnému datovému členu nebo členům pole.

##  <a name="parameter-data-members"></a><a name="_core_parameter_data_members"></a>Datové členy parametru

Pokud je třída parametrizovaná, má jeden nebo více datových členů parametrů. Parametrizovaná třída umožňuje vytvořit dotaz sady záznamů pro informace získané nebo počítané za běhu.

Obvykle parametr umožňuje zúžit výběr, jak je uvedeno v následujícím příkladu. Na základě [Ukázkové třídy](#_core_a_sample_class) na začátku tohoto tématu může objekt sady záznamů spustit následující příkaz SQL:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

"?" Je zástupný symbol pro hodnotu parametru, který zadáte v době běhu. Při sestavování sady záznamů a nastavení jejího datového členu `m_strIDParam` na MATH101, bude platný příkaz jazyka SQL pro sadu záznamů:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

Definováním datových členů parametru říkáte rozhraní o parametrech v řetězci SQL. Rozhraní váže parametr, který umožňuje rozhraní ODBC zjistit, kde získat hodnoty, které nahradí zástupný symbol. V tomto příkladu Výsledná sada záznamů obsahuje pouze záznam z tabulky Course se sloupcem CourseID, jehož hodnota je MATH101. Jsou vybrány všechny zadané sloupce tohoto záznamu. Můžete zadat tolik parametrů (a zástupné symboly), kolik potřebujete.

> [!NOTE]
>  Knihovna MFC sama o sobě neprovede žádné parametry – konkrétně neprovádí substituci textu. Místo toho knihovna MFC oznamuje rozhraní ODBC, kde získat parametr; Rozhraní ODBC načte data a provede nezbytné Parametrizace.

> [!NOTE]
>  Pořadí parametrů je důležité. Informace o tomto a další informace o parametrech naleznete v tématu [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

##  <a name="using-m_nfields-and-m_nparams"></a><a name="_core_using_m_nfields_and_m_nparams"></a>Používání m_nFields a m_nParams

Když průvodce zapíše konstruktor pro třídu, inicializuje také datový člen [m_nFields](../../mfc/reference/crecordset-class.md#m_nfields) , který určuje počet [datových členů](#_core_field_data_members) v třídě. Pokud do své třídy přidáte žádné [parametry](#_core_parameter_data_members) , je nutné také přidat inicializaci pro datový člen [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) , který určuje počet datových členů parametrů. Rozhraní používá tyto hodnoty pro práci s datovými členy.

Další informace a příklady naleznete v tématu [Výměna polí záznamu: Použití RFX](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)
