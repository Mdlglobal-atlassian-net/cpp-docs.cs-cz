---
title: 'Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- recordsets, requerying
- requerying recordsets
- Requery method
- ODBC recordsets, requerying
- refreshing recordsets
ms.assetid: 4ebc3b5b-5b91-4f51-a967-245223c6b8e1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a3157f416cf6fb7e0fd3b5ad4797b83de218c9ef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091573"
---
# <a name="recordset-requerying-a-recordset-odbc"></a>Sada záznamů: Opětovné spuštění dotazu na sadu záznamů (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma vysvětluje, jak můžete objekt sady záznamů Requery – (to znamená, obnovit) sám sebe z databáze a chcete to udělat pomocí [Requery –](../../mfc/reference/crecordset-class.md#requery) – členská funkce.  
  
 Hlavní důvody pro opětovné spuštění dotazu na sadu záznamů je:  
  
-   Aktualizovat sadu záznamů s ohledem na přidaných vy nebo jiní uživatelé záznamů a záznamy byly odstraněny jinými uživateli (ty, které odstraníte odrazí se to už v sadě záznamů).  
  
-   Aktualizujte sadu záznamů na základě změny hodnot parametrů.  
  
##  <a name="_core_bringing_the_recordset_up_to_date"></a> Datum aktualizování sady záznamů  
 Často budete chtít requery objektu sady záznamů a převeďte ho do aktuální. V prostředí s více uživateli databáze jiných uživatelů můžete provést změny dat během doby platnosti sady záznamů. Další informace o při sady záznamů odráží změny provedené jinými uživateli a když jiné uživatelů promítne změny najdete v tématu [sada záznamů: Jak sady záznamů aktualizace záznamů (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) a [dynamická sada](../../data/odbc/dynaset.md).  
  
##  <a name="_core_requerying_based_on_new_parameters"></a> Opětovné spuštění dotazu na základě nových parametrů  
 Jiné časté – a stejně důležité – použití [Requery –](../../mfc/reference/crecordset-class.md#requery) je výběr novou sadu záznamů na základě změny hodnot parametrů.  
  
> [!TIP]
>  Rychlost dotazu je pravděpodobně mnohem rychlejší, když zavoláte **Requery –** se změnou hodnoty parametrů, než pokud provádíte volání **otevřete** znovu.  
  
##  <a name="_core_requerying_dynasets_vs.._snapshots"></a> Opětovné spuštění dotazu dynamické sady vs. Snímky  
 Protože dynamické sady jsou určené k vytvoření sady záznamů s dynamickými daty aktuální, budete chtít requery dynamické sady často, pokud chcete, aby odrážela dodatky jiných uživatelů. Snímky na druhé straně jsou užitečné, protože můžete bezpečně spoléhat na jejich statický obsah, zatímco Příprava sestavy vypočítat celkové a tak dále. Přesto můžete někdy chtít Requery – snímek také. V prostředí s více uživateli data snímku může dojít ke ztrátě synchronizace se zdrojem dat jako ostatní uživatelé změnit databázi.  
  
#### <a name="to-requery-a-recordset-object"></a>Chcete-li znovu spustit dotaz objekt sady záznamů  
  
1.  Volání [Requery –](../../mfc/reference/crecordset-class.md#requery) – členská funkce objektu.  
  
 Alternativně můžete zavřít a znovu otevřete původní sady záznamů. Nová sada záznamů v obou případech představuje aktuální stav zdroje dat.  
  
 Příklad, naleznete v části [zobrazení záznamů: naplnění seznamu z druhé sady záznamů](../../data/filling-a-list-box-from-a-second-recordset-mfc-data-access.md).  
  
> [!TIP]
>  K optimalizaci **Requery –** výkonu, vyhnout změně sady záznamů [filtru](../../data/odbc/recordset-filtering-records-odbc.md) nebo [řazení](../../data/odbc/recordset-sorting-records-odbc.md). Měnit pouze hodnotu parametru před voláním **Requery –**.  
  
 Pokud **Requery** volání selže, můžete zkusit volání; jinak, by měla aplikace řádně ukončit. Volání **Requery –** nebo **otevřete** může selhat z několika příčin. Pravděpodobně dojde k chybě sítě; nebo v průběhu hovoru, po vydání stávající data, ale předtím, než je získat nová data, může jiný uživatel získat výhradní přístup; nebo může být odstraněné v tabulce, na kterém závisí sady záznamů.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Dynamické vazby datových sloupců (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md)   
 [Sada záznamů: Vytváření a uzavírání sad záznamů (ODBC)](../../data/odbc/recordset-creating-and-closing-recordsets-odbc.md)