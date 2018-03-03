---
title: "Snímek | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- ODBC cursor library [ODBC], snapshots
- cursors [ODBC], static
- recordsets, snapshots
- snapshots, support in ODBC
- static cursors
- ODBC recordsets, snapshots
- cursor library [ODBC], snapshots
- snapshots
ms.assetid: b5293a52-0657-43e9-bd71-fe3785b21c7e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c31e08fdda3cef526f46946e45ef956f9ad1adaa
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="snapshot"></a>Snímek
Snímek je sada záznamů, které odráží statické zobrazení dat, která existovala v době vytvoření snímku. Když otevřete snímku a přesunout do všech záznamů, obsahuje sadu záznamů a jejich hodnoty se nezmění, dokud znovu sestavit snímku voláním **Requery –**.  
  
> [!NOTE]
>  Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC. Pokud používáte tříd MFC rozhraní DAO místo třídy knihovny MFC rozhraní ODBC, přečtěte si téma [CDaoRecordset::Open](../../mfc/reference/cdaorecordset-class.md#open) popis sady záznamů typu snímek.  
  
 Snímky v aktualizovatelné nebo jen pro čtení můžete vytvořit s třídami databází. Na rozdíl od dynamická sada lze aktualizovat snímek nezohledňuje změny k zaznamenání hodnoty od jiných uživatelů, ale ji zobrazit aktualizace a odstranění provedené vašeho programu. Záznamy přidané do snímku nebudou viditelné ve snímku dokud zavoláte **Requery –**.  
  
> [!TIP]
>  Snímek se statickým kurzorem rozhraní ODBC. Statický kurzor Nezískávat ve skutečnosti řádek dat. dokud přejděte na tento záznam. Aby se zajistilo, že jsou všechny záznamy okamžitě načíst, můžete posuňte na konec sady záznamů a posuňte se k první záznam, který chcete zobrazit. Upozorňujeme však, že posouvání na konec vyžaduje další režii a může snížit výkon.  
  
 Snímky jsou nejužitečnější, pokud je nutné pevné data během operací, jako jsou při generování sestavy nebo provádění výpočtů. I tak zdroj dat může značně rozcházejí ze snímku, takže je vhodné k opětovnému sestavení čas od času.  
  
 Podpora snímků je založena na knihovny kurzorů ODBC, která poskytuje statické kurzory a umístěné aktualizace (vyžaduje aktualizovatelnosti) pro všechny ovladače úrovně 1. Knihovna kurzorů DLL musí být načtena v paměti pro tuto podporu. Když vytvoříte `CDatabase` objekt a volání jeho `OpenEx` – členská funkce, je nutné zadat **CDatabase::useCursorLib** možnost `dwOptions` parametr. Když zavoláte **otevřete** ve výchozím nastavení je načtena – členská funkce knihovna kurzorů. Pokud používáte dynamické sady místo snímky, nechcete způsobit kurzoru knihovnu, která má být načten.  
  
 Snímky jsou k dispozici pouze v případě, že byl načten knihovny kurzorů ODBC, kdy `CDatabase` objekt byl zkonstruován nebo ovladač ODBC používáte podporuje statické kurzory.  
  
> [!NOTE]
>  Pro některé ovladače ODBC snímků (statické kurzory) nemusí být možné aktualizovat. Zkontrolujte dokumentaci ovladače pro podporované typy kurzorů a souběžnosti typy, které podporují. Chcete-li zaručit aktualizovatelné snímky, ujistěte se, načtení knihovna kurzorů do paměti při vytváření `CDatabase` objektu. Další informace najdete v tématu [ODBC: knihovny kurzorů ODBC](../../data/odbc/odbc-the-odbc-cursor-library.md).  
  
> [!NOTE]
>  Pokud chcete použít snímky a dynamické sady, musíte je založit na dva různé `CDatabase` objekty (dvě různá připojení).  
  
 Další informace o sdílené složce snímky vlastnosti s všechny sady záznamů najdete v tématu [záznamů (ODBC)](../../data/odbc/recordset-odbc.md). Další informace o rozhraní ODBC a snímky, včetně knihovny kurzorů ODBC, najdete v části [ODBC](../../data/odbc/odbc-basics.md).  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)