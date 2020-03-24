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
ms.openlocfilehash: b7cf40ca3b0c8e415368772063aee61008a52764
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212781"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje, jak můžete použít objekt sady záznamů k opakovanému spuštění dotazu (to znamená aktualizace) z databáze a kdy to můžete udělat pomocí členské funkce [Requery](../../mfc/reference/crecordset-class.md#requery) .

Hlavní důvody pro dotazování sady záznamů:

- Přiveďte sadu záznamů v aktuálním stavu s ohledem na záznamy přidané vámi nebo jinými uživateli a záznamy odstraněné jinými uživateli (ty, které odstraníte, se už v sadě záznamů odrážejí).

- Aktualizuje sadu záznamů na základě změn hodnot parametrů.

##  <a name="bringing-the-recordset-up-to-date"></a><a name="_core_bringing_the_recordset_up_to_date"></a>Uvedení sady záznamů do aktuálního stavu

Často budete chtít znovu spustit dotaz na svůj objekt sady záznamů, abyste ho mohli uvést v aktuálním stavu. V prostředí databáze s více uživateli může další uživatelé provádět změny dat během životnosti vaší sady záznamů. Další informace o tom, zda vaše sada záznamů odráží změny provedené jinými uživateli a pokud sady záznamů jiných uživatelů odráží vaše změny, naleznete v tématu [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) a [dynamické sady](../../data/odbc/dynaset.md).

##  <a name="requerying-based-on-new-parameters"></a><a name="_core_requerying_based_on_new_parameters"></a>Dotazování na základě nových parametrů

Další časté – a stejně důležité – použití [dotazu Requery](../../mfc/reference/crecordset-class.md#requery) je výběr nové sady záznamů na základě změny hodnot parametrů.

> [!TIP]
>  Rychlost dotazu je pravděpodobně výrazně rychlejší, pokud zavoláte `Requery` se změnou hodnot parametrů, než Pokud zavoláte `Open` znovu.

##  <a name="requerying-dynasets-vs-snapshots"></a><a name="_core_requerying_dynasets_vs.._snapshots"></a>Dotazování na dynamické sady vs. snímky

Vzhledem k tomu, že dynamické sady mají představovat sadu záznamů s dynamickými aktuálními daty, chcete dynamické opakované dotazování znovu spustit, pokud chcete odrážet přidané uživatele. Snímky na druhé straně jsou užitečné, protože se můžete bezpečně spoléhat na jejich statický obsah, zatímco budete připravovat sestavy, počítat souhrny a tak dále. Stále můžete chtít znovu spustit dotaz i na snímek. Ve víceuživatelském prostředí může data snímku přijít o synchronizaci se zdrojem dat, protože ostatní uživatelé databázi změnili.

#### <a name="to-requery-a-recordset-object"></a>Opakované spuštění objektu sady záznamů

1. Zavolejte členskou funkci [ZnovuSpustitDotaz](../../mfc/reference/crecordset-class.md#requery) objektu.

Alternativně můžete zavřít a znovu otevřít původní sadu záznamů. V obou případech nová sada záznamů představuje aktuální stav zdroje dat.

Příklad naleznete v tématu [zobrazení záznamů: vyplnění seznamu z druhé sady záznamů](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).

> [!TIP]
>  Pro optimalizaci výkonu `Requery` neměňte [Filtr](../../data/odbc/recordset-filtering-records-odbc.md) nebo [řazení](../../data/odbc/recordset-sorting-records-odbc.md)sady záznamů. Před voláním `Requery`změňte pouze hodnotu parametru.

Pokud se `Requery` volání nepovede, můžete volání opakovat; v opačném případě by aplikace měla skončit řádným způsobem. Volání `Requery` nebo `Open` může z několika důvodů selhat. Možná dojde k chybě sítě; nebo během hovoru, po vydání stávajících dat, ale před získáním nových dat, může získat výhradní přístup jiný uživatel. nebo tabulka, na které vaše sada záznamů závisí, by mohla být odstraněna.

## <a name="see-also"></a>Viz také

[Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)<br/>
[Sada záznamů: Vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)
