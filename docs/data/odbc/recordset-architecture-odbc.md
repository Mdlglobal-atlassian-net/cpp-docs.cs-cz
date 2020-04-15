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
ms.openlocfilehash: 3ed6a862cda769769cd07d2dcd72007292068dc3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367088"
---
# <a name="recordset-architecture-odbc"></a>Sada záznamů: Architektura (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Toto téma popisuje datové členy, které tvoří architekturu objektu sady záznamů:

- [Členové dat pole](#_core_field_data_members)

- [Parametr datové členy](#_core_parameter_data_members)

- [Použití datových m_nFields a m_nParams členů](#_core_using_m_nfields_and_m_nparams)

> [!NOTE]
> Toto téma se vztahuje `CRecordset` na objekty odvozené od, ve kterém hromadné načítání řádků nebyla implementována. Pokud hromadné načítání řádků je implementováno, architektura je podobná. Rozdíly najdete v tématu [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

## <a name="sample-class"></a><a name="_core_a_sample_class"></a>Vzorová třída

> [!NOTE]
> Průvodce příjemcem knihovny MFC ODBC není k dispozici v sadě Visual Studio 2019 a novějších. Stále můžete vytvořit příjemce ručně.

Při použití [Průvodce příjemcem knihovny MFC ODBC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) z průvodce **přidáním třídy** k deklarování třídy sady záznamů odvozené z `CRecordset`, má výsledná třída obecnou strukturu zobrazenou v následující jednoduché třídě:

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

Na začátku třídy průvodce zapíše sadu [datových členů pole](#_core_field_data_members). Při vytváření třídy je nutné zadat jeden nebo více datových členů pole. Pokud je třída parametrizována, jako je ukázková `m_strIDParam`třída (s datovým členem ), musíte ručně přidat [datové členy parametru](#_core_parameter_data_members). Průvodce nepodporuje přidávání parametrů do třídy.

## <a name="field-data-members"></a><a name="_core_field_data_members"></a>Členové dat pole

Nejdůležitějšími členy vaší třídy sady záznamů jsou datové členy pole. Pro každý sloupec, který vyberete ze zdroje dat, třída obsahuje datový člen příslušného datového typu pro daný sloupec. Například [ukázková třída](#_core_a_sample_class) zobrazená na začátku tohoto tématu má `CString`dva `m_strCourseID` `m_strCourseTitle`datové členy pole, jak typ , volané a .

Když sada záznamů vybere sadu záznamů, rozhraní automaticky sváže sloupce aktuálního `Open` záznamu (po volání, první záznam je aktuální) s datovými členy pole objektu. To znamená, že rozhraní framework používá příslušný datový člen pole jako vyrovnávací paměť, ve které chcete uložit obsah sloupce záznamu.

Jako uživatel posouvá na nový záznam, rozhraní používá pole datových členů představují aktuální záznam. Rozhraní framework aktualizuje datové členy pole a nahradí hodnoty předchozího záznamu. Datové členy pole se také používají k aktualizaci aktuálního záznamu a k přidávání nových záznamů. V rámci procesu aktualizace záznamu zadáte hodnoty aktualizace přiřazením hodnot přímo příslušnému datovému členu nebo členům pole.

## <a name="parameter-data-members"></a><a name="_core_parameter_data_members"></a>Členové dat parametrů

Pokud je třída parametrizována, má jeden nebo více datových členů parametru. Parametrizovaná třída umožňuje založit dotaz sady záznamů na informacích získaných nebo vypočtených za běhu.

Obvykle parametr pomáhá zúžit výběr, jako v následujícím příkladu. Na základě [ukázkové třídy](#_core_a_sample_class) na začátku tohoto tématu může objekt sady záznamů spustit následující příkaz SQL:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = ?
```

"?" je zástupný symbol pro hodnotu parametru, kterou zadáte za běhu. Když vytvoříte sadu záznamů `m_strIDParam` a nastavíte její datový člen na MATH101, efektivní příkaz SQL pro sadu záznamů se stane:

```sql
SELECT CourseID, CourseTitle FROM Course WHERE CourseID = MATH101
```

Definováním datových členů parametru sdělíte rámci parametry v řetězci SQL. Rozhraní framework váže parametr, který umožňuje ODBC vědět, kde získat hodnoty nahradit zástupný symbol. V příkladu obsahuje výsledná sada záznamů pouze záznam z tabulky Kurz se sloupcem CourseID, jehož hodnota je MATH101. Jsou vybrány všechny zadané sloupce tohoto záznamu. Můžete zadat tolik parametrů (a zástupných symbolů), kolik potřebujete.

> [!NOTE]
> Knihovna MFC neprovede nic sama s parametry – zejména neprovede nahrazení textu. Místo toho knihovna MFC sděluje rozhraní ODBC, kde má parametr získat. ROZHRANÍ ODBC načte data a provede potřebnou parametrizaci.

> [!NOTE]
> Pořadí parametrů je důležité. Informace o tomto a další informace o parametrech naleznete v [tématu Recordset: Parameterizing a Recordset (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

## <a name="using-m_nfields-and-m_nparams"></a><a name="_core_using_m_nfields_and_m_nparams"></a>Používání m_nFields a m_nParams

Když průvodce zapíše konstruktor pro vaši třídu, inicializuje také datový člen [m_nFields,](../../mfc/reference/crecordset-class.md#m_nfields) který určuje počet [datových členů polí](#_core_field_data_members) ve třídě. Pokud přidáte všechny parametry do vaší [třídy,](#_core_parameter_data_members) musíte také přidat inicializaci pro [m_nParams](../../mfc/reference/crecordset-class.md#m_nparams) datový člen, který určuje počet datových členů parametru. Rozhraní framework používá tyto hodnoty pro práci s datovými členy.

Další informace a příklady naleznete [v tématu Výměna polí záznamu: Použití rfx](../../data/odbc/record-field-exchange-using-rfx.md).

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Deklarování třídy pro tabulku (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md)<br/>
[Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)
