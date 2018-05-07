---
title: 'Výměna polí záznamu: Použití funkcí RFX | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC [C++], data types
- data types [C++], ODBC record field exchange
- RFX (ODBC) [C++], function syntax and parameters
- DoFieldExchange method, and RFX functions
- ODBC [C++], RFX
- RFX (ODBC) [C++], data types
- function calls, RFX functions
ms.assetid: c594300b-5a29-4119-a68b-e7ca32def696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1f834f9f52c8d01dbd7eb3ff54b794afc11630ae
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="record-field-exchange-using-the-rfx-functions"></a>Výměna polí záznamu: Použití funkcí RFX
Toto téma vysvětluje, jak používat funkce RFX, které tvoří tělo vaší `DoFieldExchange` přepsat.  
  
> [!NOTE]
>  Toto téma se vztahuje na třídy odvozené od třídy [CRecordset](../../mfc/reference/crecordset-class.md) v který řádek hromadné načítání se neimplementovala. Pokud používáte hromadné načítání řádků, je implementováno Hromadná výměna pole záznamu (Bulk RFX). Hromadné RFX je podobná RFX. Chcete-li pochopit rozdíly, přečtěte si téma [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Globální funkce RFX výměnu dat mezi sloupce na datový zdroj a pole datových členů ve vaší sadě záznamů. Zápis funkce RFX volání do sady záznamů [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) – členská funkce. Toto téma popisuje funkce stručně a ukazuje datové typy, pro které RFX funkce jsou k dispozici. [Technická poznámka 43](../../mfc/tn043-rfx-routines.md) popisuje, jak napsat vlastní funkce RFX pro další datové typy.  
  
##  <a name="_core_rfx_function_syntax"></a> Syntaxe funkce RFX  
 Jednotlivé funkce RFX přijímá tři parametry (a některé si volitelný parametr čtvrtý nebo pátý):  
  
-   Ukazatel [CFieldExchange](../../mfc/reference/cfieldexchange-class.md) objektu. Jednoduše předáte `pFX` ukazatel předaný `DoFieldExchange`.  
  
-   Název sloupce tak, jak se zobrazí na datovém zdroji.  
  
-   Název odpovídající pole datových členů nebo parametr datového člena ve třídě sady záznamů.  
  
-   (Volitelné) V některých funkcí, maximální délka řetězce nebo pole přenosu. Toto výchozí nastavení 255 bajtů, ale chcete ho změnit. Maximální velikost je založena na maximální velikost `CString` objektu – **INT_MAX** (2 147 483 647) bajtů – ale pravděpodobně narazíte na omezení ovladače před této velikosti.  
  
-   (Volitelné) V `RFX_Text` funkce, se někdy používá pátý parametr k určení datový typ sloupce.  
  
 Další informace najdete v tématu v části funkce RFX [makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md) v *knihovny tříd*. Pro příklad, kdy budete chtít vytvořit speciální používání parametrů naleznete v tématu [sada záznamů: získávání součtů a jiných agregačních výsledků (ODBC)](../../data/odbc/recordset-obtaining-sums-and-other-aggregate-results-odbc.md).  
  
##  <a name="_core_rfx_data_types"></a> RFX datové typy  
 Knihovna tříd poskytuje funkce RFX pro přenos mezi zdroji dat a vaše sady záznamů mnoha různými datovými typy. Následující seznam shrnuje funkce RFX podle datového typu. V případech, kdy musíte napsat vlastní funkce RFX vyberte z těchto funkcí podle datového typu.  
  
|Funkce|Datový typ|  
|--------------|---------------|  
|`RFX_Bool`|**BOOL**|  
|`RFX_Byte`|**BAJTŮ**|  
|`RFX_Binary`|`CByteArray`|  
|`RFX_Double`|**double**|  
|`RFX_Single`|**float**|  
|`RFX_Int`|`int`|  
|`RFX_Long`|**long**|  
|`RFX_LongBinary`|`CLongBinary`|  
|`RFX_Text`|`CString`|  
|`RFX_Date`|`CTime`|  
  

 Další informace najdete v dokumentaci funkce RFX v [makra a globální prvky](../../mfc/reference/mfc-macros-and-globals.md) v *knihovny tříd*. Informace o mapování datové typy C++ do datových typů SQL, najdete v tabulce datových typů ANSI SQL na datové typy C++ v [SQL: SQL a datové typy C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md).  
  
## <a name="see-also"></a>Viz také  
 [Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [Výměna polí záznamu: Jak funkce RFX pracuje](../../data/odbc/record-field-exchange-how-rfx-works.md)   
 [Sada záznamů: Parametrizace sady záznamů (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)   
 [Sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)   
 [CFieldExchange – třída](../../mfc/reference/cfieldexchange-class.md)