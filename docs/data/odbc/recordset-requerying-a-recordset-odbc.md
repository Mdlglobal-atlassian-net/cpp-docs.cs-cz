---
title: 'Recordset: Opětovné spuštění dotazu na sadu záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: 7edc1c04da617f96165b25a47ce169b266ae0003
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59024592"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Recordset: Opětovné spuštění dotazu na sadu záznamů (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje, jak můžete pomocí objektu sady záznamů requery (to znamená, aktualizujte) z databáze a můžete to udělat takto [Requery](../../mfc/reference/crecordset-class.md#requery) členskou funkci.

Hlavní důvody pro opětovné spuštění dotazu na sadu záznamů jsou:

- Používání sady záznamů aktuální s ohledem na přidání vámi nebo jiným uživatelům a záznamy odstraněné jinými uživateli (ty, které se při odstranění se už projeví v sadě záznamů).

- Aktualizujte sadu záznamů na základě změny hodnot parametrů.

##  <a name="_core_bringing_the_recordset_up_to_date"></a> K datu aktualizování sady záznamů

Často budete chtít requery objektu sady záznamů, abyste je připojili k aktuální. V prostředí s více uživateli databáze, další uživatelé můžete provádět změny dat během existence vaší sady záznamů. Další informace o při sady záznamů odráží změny provedené jinými uživateli, a pokud provedené změny se sady záznamů jiných uživatelů najdete v tématu [sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) a [dynamická sada](../../data/odbc/dynaset.md).

##  <a name="_core_requerying_based_on_new_parameters"></a> Opětovné spuštění dotazu na základě nových parametrů

Další časté – a stejně důležité – použití [Requery](../../mfc/reference/crecordset-class.md#requery) je vybrat novou sadu záznamů na základě změny hodnot parametrů.

> [!TIP]
>  Rychlost dotazu je pravděpodobně výrazně rychlejší při volání `Requery` se změnou hodnoty parametrů, než pokud zavoláte `Open` znovu.

##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> Opětovné spuštění dotazu dynamické sady vs. Snímky

Protože dynamické sady jsou určené k vytvoření sady záznamů s dynamickými daty aktuální, budete chtít requery dynamické sady často potřebujete tak, aby odrážely přidání dalších uživatelů. Snímky, na druhé straně jsou užitečné, protože můžete bezpečně spolehnout na jejich statický obsah připravit sestavy, vypočítá celkový počet položek a tak dále. I nadále můžete někdy chtít requery také snímek. V prostředí data snímku může dojít ke ztrátě synchronizace se zdrojem dat jiným uživatelům změnit databázi.

#### <a name="to-requery-a-recordset-object"></a>Chcete-li requery objekt sady záznamů

1. Volání [Requery](../../mfc/reference/crecordset-class.md#requery) členské funkce objektu.

Alternativně můžete zavřete a znovu původní sadu záznamů. V obou případech se nová sada záznamů představuje aktuální stav datového zdroje.

Příklad najdete v tématu [zobrazení záznamů: Naplnění seznamu druhou sadou záznamů](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
>  K optimalizaci `Requery` výkonu, neměňte sady záznamů [filtr](../../data/odbc/recordset-filtering-records-odbc.md) nebo [řazení](../../data/odbc/recordset-sorting-records-odbc.md). Změňte hodnotu parametru pouze před voláním `Requery`.

Pokud `Requery` volání selže, můžete opakovat volání; v opačném případě by měla řádně ukončit aplikaci. Volání `Requery` nebo `Open` může selhat z mnoha důvodů. Pravděpodobně dojde k chybě sítě; nebo během volání, po vydání existující data, ale předtím, než je získat nová data, získat jiný uživatel možná výhradní přístup; nebo v tabulce, na kterém závisí sady záznamů není možné odstranit.

## <a name="see-also"></a>Viz také:

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Recordset: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Recordset: Vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)