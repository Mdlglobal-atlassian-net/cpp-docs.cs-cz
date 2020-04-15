---
title: 'Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
ms.openlocfilehash: cdae28f81eebe8427bc829072e0d9a83c6ec1722
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366950"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Toto téma vysvětluje, jak můžete použít objekt sady záznamů k opětovnému dotazování (tj. aktualizovat) z databáze a kdy to můžete chtít provést pomocí členské funkce [Requery.](../../mfc/reference/crecordset-class.md#requery)

Hlavní důvody pro opětovné dotazování sady záznamů jsou:

- Aktuální sadu záznamů s ohledem na záznamy přidané vámi nebo jinými uživateli a záznamy odstraněné jinými uživateli (ty, které odstraníte, se již projeví v sadě záznamů).

- Aktualizujte sadu záznamů na základě změny hodnot parametrů.

## <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>Aktuální nastavení záznamů

Často budete chtít znovu zadat objekt sady záznamů, aby byl aktuální. V databázovém prostředí s více uživateli mohou ostatní uživatelé provádět změny dat během životnosti sady záznamů. Další informace o tom, kdy sada záznamů odráží změny provedené jinými uživateli a kdy sady záznamů jiných uživatelů odrážejí vaše změny, naleznete v [tématu Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) a [Dynaset](../../data/odbc/dynaset.md).

## <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>Opětovné dotazování na základě nových parametrů

Dalším častým – a neméně důležitým – použitím [requery](../../mfc/reference/crecordset-class.md#requery) je výběr nové sady záznamů na základě změny hodnot parametrů.

> [!TIP]
> Rychlost dotazu je pravděpodobně `Requery` výrazně rychlejší, pokud voláte se změnami hodnot parametrů, než když zavoláte `Open` znovu.

## <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>Opětovné dotazování dynasadvs. snímky

Vzhledem k tomu, že dynamické sady mají prezentovat sadu záznamů s dynamickými aktuálními daty, chcete dynamické sady často znovu zařazovat, pokud chcete odrážet dodatky ostatních uživatelů. Snímky, na druhé straně jsou užitečné, protože můžete bezpečně spolehnout na jejich statický obsah při přípravě sestav, vypočítat součty a tak dále. Přesto můžete někdy chtít requery snímek stejně. Ve víceuživatelském prostředí mohou data snímku ztratit synchronizaci se zdrojem dat, protože ostatní uživatelé mění databázi.

#### <a name="to-requery-a-recordset-object"></a>Opětovný dotaz na objekt sady záznamů

1. Volání členské funkce [Requery](../../mfc/reference/crecordset-class.md#requery) objektu.

Případně můžete zavřít a znovu otevřít původní sadu záznamů. V obou případech představuje nová sada záznamů aktuální stav zdroje dat.

Příklad najdete v tématu [Zobrazení záznamů: Vyplnění seznamu z druhé sady záznamů](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
> Chcete-li optimalizovat `Requery` výkon, neměňte [filtr](../../data/odbc/recordset-filtering-records-odbc.md) nebo [řazení](../../data/odbc/recordset-sorting-records-odbc.md)sady záznamů . Před voláním `Requery`změňte pouze hodnotu parametru .

Pokud `Requery` volání selže, můžete hovor opakovat. v opačném případě by měla být aplikace řádně ukončena. Volání `Requery` nebo `Open` může selhat z mnoha důvodů. Možná dojde k chybě sítě; nebo během hovoru po uvolnění existujících dat, ale před získáním nových dat může získat výhradní přístup jiný uživatel; nebo tabulka, na které závisí sada záznamů, může být odstraněna.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Sada záznamů: Vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
