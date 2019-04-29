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
ms.openlocfilehash: dc717336a5279e7eda1b7c39b19a7c76f9055cd3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395680"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Výměna polí záznamu: Použití funkcí RFX

Toto téma vysvětluje, jak používat funkce RFX tvořící tělo vaše `DoFieldExchange` přepsat.

> [!NOTE]
>  Toto téma platí pro třídy odvozené od [CRecordset](../../mfc/reference/crecordset-class.md) v který řádek hromadné načítání není implementovaná. Pokud používáte hromadné načítání řádků, je implementováno Hromadná výměna pole záznamu (Bulk RFX). Hromadné funkce RFX je podobný RFX. Pokud chcete znát rozdíly, přečtěte si téma [sada záznamů: Načítání záznamů (ODBC) hromadné](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Globální funkce RFX výměnu dat mezi sloupce na datový zdroj a pole datové členy do sady záznamů. Zápis funkce RFX volá ve vaší sadě záznamů [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) členskou funkci. Toto téma stručně popisuje funkce a jsou uvedeny datové typy, pro které RFX funkce jsou k dispozici. [Technická poznámka 43](../../mfc/tn043-rfx-routines.md) popisuje, jak psát vlastní funkce RFX pro další datové typy.

##  <a name="_core_rfx_function_syntax"></a> Syntaxe funkce RFX

Každá funkce RFX přijímá tři parametry (a některé provést volitelný parametr čtvrtého nebo pátého):

- Ukazatel [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objektu. Jednoduše předáte `pFX` předán ukazatel `DoFieldExchange`.

- Název sloupce tak, jak se objeví ve zdroji dat.

- Název odpovídající pole datový člen nebo parametr datový člen ve třídě sady záznamů.

- (Volitelné) V některých funkcí, maximální délka řetězce nebo pole přenosu. Výchozí hodnota 255 bajtů, ale můžete ho změnit. Maximální velikost je založena na maximální velikost `CString` objektu – **INT_MAX** bajtů (2 147 483 647) – ale pravděpodobně narazíte na omezení ovladače před této velikosti.

- (Volitelné) V `RFX_Text` funkci, někdy vám pátého parametru zadejte datový typ sloupce.

Další informace najdete v tématu funkce RFX pod [makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md) v *knihovny tříd*. Když budete chtít vytvořit zvláštní příklad použití těchto parametrů naleznete v tématu [sada záznamů: Získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).

##  <a name="_core_rfx_data_types"></a> Typy dat RFX

Knihovna tříd poskytuje funkce RFX pro přenos mnoho různých typů dat mezi zdrojem dat a sadě záznamů. Následující seznam shrnuje funkce RFX podle datového typu. V případech, kdy musíte napsat vlastní volání funkcí RFX vyberte z těchto funkcí podle datového typu.

|Funkce|Datový typ|
|--------------|---------------|
|`RFX_Bool`|**BOOL**|
|`RFX_Byte`|**BYTE**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|


Další informace najdete v dokumentaci funkce RFX v [makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md) v *knihovny tříd*. Informace o mapování datových typů jazyka C++ na datové typy SQL najdete v tabulce datové typy ANSI SQL na datové typy jazyka C++ v [SQL: SQL a datové typy C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).

## <a name="see-also"></a>Viz také:

[Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Výměna polí záznamu (Record Field Exchange – RFX): Jak RFX funguje](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)