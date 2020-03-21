---
title: 'Výměna polí záznamu: Použití funkcí RFX'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
ms.openlocfilehash: a54dbc10e80e19f744bb58c23639a4376156d2e7
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80077097"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Výměna polí záznamu: Použití funkcí RFX

Toto téma vysvětluje, jak používat volání funkce RFX, které tvoří tělo vaší `DoFieldExchange` přepsání.

> [!NOTE]
>  Toto téma se vztahuje na třídy odvozené od [CRecordset](../../mfc/reference/crecordset-class.md) , ve kterých nebylo implementováno hromadné načítání řádků. Používáte-li hromadné načítání řádků, je implementováno hromadné výměny pole záznamu (Bulk RFX). Hromadná RFX je podobná RFX. Pro pochopení rozdílů si přečtěte téma [Sada záznamů: hromadné načítání záznamů (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Funkce RFX globálních funkcí vyměňuje data mezi sloupci ve zdroji dat a datovými členy pole v sadě záznamů. Napíšete volání funkce RFX v členské funkci [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) vaší sady záznamů. Toto téma stručně popisuje funkce a zobrazuje datové typy, pro které jsou k dispozici RFX funkce. [Technická poznámka 43](../../mfc/tn043-rfx-routines.md) popisuje, jak napsat vlastní RFX funkce pro další datové typy.

##  <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>Syntaxe funkce RFX

Každá funkce RFX používá tři parametry (a některé z nich vybírají volitelný čtvrtý nebo pátý parametr):

- Ukazatel na objekt [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) . Jednoduše předáte společně ukazatel `pFX` předaný do `DoFieldExchange`.

- Název sloupce, který se zobrazí ve zdroji dat.

- Název odpovídajícího pole datového členu nebo datového členu parametru ve třídě sady záznamů.

- Volitelné V některých funkcích je maximální délka přenášeného řetězce nebo pole. Výchozí hodnota je 255 bajtů, ale je možné, že ji budete chtít změnit. Maximální velikost je založena na maximální velikosti `CString`ho objektu – **INT_MAX** (2 147 483 647) bajtů, ale pravděpodobně narazíte na omezení ovladače před touto velikostí.

- Volitelné Ve funkci `RFX_Text` se někdy používá pátý parametr k určení datového typu sloupce.

Další informace naleznete v tématu funkce RFX v části [makra a globální](../../mfc/reference/mfc-macros-and-globals.md) informace v *knihovně tříd*. Příklad, kdy může být vhodné použít parametry, naleznete v tématu [Sada záznamů: získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

##  <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>RFX – datové typy

Knihovna tříd poskytuje funkce RFX pro přenos mnoha různých typů dat mezi zdrojem dat a vašimi sadami záznamů. Následující seznam shrnuje funkce RFX podle datového typu. V případech, kdy je nutné napsat vlastní volání funkce RFX, vyberte z těchto funkcí podle datového typu.

|Funkce|Datový typ|
|--------------|---------------|
|`RFX_Bool`|**LOGICK**|
|`RFX_Byte`|**BYTOVÉ**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

Další informace naleznete v dokumentaci funkce RFX v části [makra a globální](../../mfc/reference/mfc-macros-and-globals.md) *informace v knihovně tříd*. Informace o způsobu C++ mapování datových typů na datové typy SQL najdete v tématu Tabulka ANSI SQL datových typů mapovaných na C++ datové typy v [SQL: SQL a C++ datové typy (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Viz také

[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)