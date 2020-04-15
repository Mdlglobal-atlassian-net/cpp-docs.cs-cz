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
ms.openlocfilehash: f1afded360cfeff564f1f3d8bb9b294aa33cb733
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367135"
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Výměna polí záznamu: Použití funkcí RFX

Toto téma vysvětluje, jak používat volání funkce RFX, `DoFieldExchange` které tvoří tělo přepsání.

> [!NOTE]
> Toto téma se vztahuje na třídy odvozené z [CRecordset,](../../mfc/reference/crecordset-class.md) ve kterém hromadné načítání řádků nebyla implementována. Pokud používáte hromadné načítání řádků, je implementována výměna pole hromadného záznamu (Bulk RFX). Hromadné RFX je podobný RFX. Rozdíly najdete v tématu [Sada záznamů: Hromadné načítání záznamů (ODBC).](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md)

Globální funkce RFX si vyměňují data mezi sloupci ve zdroji dat a datových členech polí ve vaší sadě záznamů. Volání funkce RFX v členské funkci [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) sady záznamů. Toto téma stručně popisuje funkce a zobrazuje datové typy, pro které jsou k dispozici funkce RFX. [Technická poznámka 43](../../mfc/tn043-rfx-routines.md) popisuje, jak napsat vlastní funkce RFX pro další datové typy.

## <a name="rfx-function-syntax"></a><a name="_core_rfx_function_syntax"></a>Syntaxe funkce RFX

Každá funkce RFX má tři parametry (a některé mají volitelný čtvrtý nebo pátý parametr):

- Ukazatel na objekt [CFieldExchange.](../../mfc/reference/cfieldexchange-class.md) Jednoduše předáte `pFX` ukazatel předaná . `DoFieldExchange`

- Název sloupce tak, jak je uveden ve zdroji dat.

- Název odpovídajícího datového člena pole nebo člena dat parametru ve třídě sady záznamů.

- (Nepovinné) V některých funkcích maximální délka řetězce nebo pole, které jsou přenášeny. Tato možnost je výchozí hodnota 255 bajtů, ale možná ji budete chtít změnit. Maximální velikost je založena na maximální `CString` velikosti objektu – **INT_MAX** (2,147,483,647) bajtů - ale pravděpodobně se setkáte s omezeními ovladačů před tuto velikostí.

- (Nepovinné) Ve `RFX_Text` funkci někdy použijete pátý parametr k určení datového typu sloupce.

Další informace naleznete v tématu Funkce RFX v části [Makra a globální v](../../mfc/reference/mfc-macros-and-globals.md) *odkazu knihovny tříd*. Příklad, kdy můžete provést zvláštní použití parametrů, naleznete v tématu [Recordset: Získání sumů a dalších souhrnných výsledků (ODBC).](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md)

## <a name="rfx-data-types"></a><a name="_core_rfx_data_types"></a>Datové typy RFX

Knihovna tříd poskytuje funkce RFX pro přenos mnoha různých datových typů mezi zdrojem dat a sadami záznamů. Následující seznam shrnuje funkce RFX podle datového typu. V případech, kdy je nutné napsat vlastní volání funkce RFX, vyberte z těchto funkcí podle datového typu.

|Funkce|Datový typ|
|--------------|---------------|
|`RFX_Bool`|**Bool**|
|`RFX_Byte`|**Bajt**|
|`RFX_Binary`|`CByteArray`|
|`RFX_Double`|**double**|
|`RFX_Single`|**float**|
|`RFX_Int`|**int**|
|`RFX_Long`|**long**|
|`RFX_LongBinary`|`CLongBinary`|
|`RFX_Text`|`CString`|
|`RFX_Date`|`CTime`|

Další informace naleznete v dokumentaci funkce RFX v části [Makra a globální soubory](../../mfc/reference/mfc-macros-and-globals.md) v *odkazu knihovny tříd*. Informace o tom, jak se datové typy jazyka C++ mapují na datové typy SQL, naleznete v tabulce ANSI SQL Datových typů mapovaných na datové typy jazyka C++ v [jazyce SQL: datové typy SQL a C++ (ODBC).](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)

## <a name="see-also"></a>Viz také

[Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)<br/>
[Výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md)<br/>
[Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)
