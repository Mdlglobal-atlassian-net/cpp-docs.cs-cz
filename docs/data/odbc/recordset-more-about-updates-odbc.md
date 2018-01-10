---
title: "Sada záznamů: Další informace o aktualizace (rozhraní ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- records, updating
- transactions, updating recordsets
- ODBC recordsets, updating
- multiuser environments, updates to recordsets
- scrolling, updates to recordsets
- updating recordsets
- recordsets, updating
ms.assetid: 0353a742-d226-4fe2-8881-a7daeffe86cd
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1ad9042c4001fc1a0e0c8c8d19e5ac53b6312875
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-more-about-updates-odbc"></a>Sada záznamů: Další informace o aktualizacích (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma vysvětluje:  
  
-   [Vliv na jiné operace, jako je například transakce, aktualizace](#_core_how_transactions_affect_updates).  
  
-   [Vaše aktualizace a ty jiných uživatelů](#_core_your_updates_and_the_updates_of_other_users).  
  
-   [Další informace o funkcích aktualizace a odstranění](#_core_more_about_update_and_delete).  
  
> [!NOTE]
>  Toto téma se vztahuje na objekty, které jsou odvozené z `CRecordset` v který řádek hromadné načítání se neimplementovala. Pokud jste implementovali hromadné načítání řádků, tak se nevztahuje na některé z informací. Například nelze volat `AddNew`, **upravit**, **odstranit**, a **aktualizace** členské funkce; však můžete provádět transakce. Další informace o hromadné načítání řádků najdete v tématu [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_how_other_operations_affect_updates"></a>Vliv na jiné operace aktualizace  
 Vaše aktualizace jsou postižené transakce platit v době aktualizace uzavření sady záznamů před dokončením transakce a posouvání před dokončením transakce.  
  
###  <a name="_core_how_transactions_affect_updates"></a>Vliv transakcí na aktualizace  
 Nad rámec pochopení jak `AddNew`, **upravit**, a **odstranit** práce, je důležité pochopit, jak **metody BeginTrans**, **CommitTrans**, a **vrácení zpět** členské funkce [CDatabase](../../mfc/reference/cdatabase-class.md) práce s funkcí aktualizace [CRecordset](../../mfc/reference/crecordset-class.md).  
  
 Ve výchozím nastavení, volá, aby se `AddNew` a **upravit** vliv zdroj dat okamžitě při volání **aktualizace**. **Odstranit** volání projeví okamžitě. Ale můžete vytvořit transakci a provedení dávky těchto volání. Aktualizace nejsou trvalé, dokud je nepotvrdíte. Pokud změníte své rozhodnutí, můžete transakci místo potvrzení vrátit zpět.  
  
 Další informace o transakcích najdete v tématu [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
###  <a name="_core_how_closing_the_recordset_affects_updates"></a>Jak uzavření sady záznamů ovlivňuje aktualizace  
 Pokud zavřete sadu záznamů nebo jeho přidružené `CDatabase` objekty, s probíhající (ještě volána [CDatabase::CommitTrans](../../mfc/reference/cdatabase-class.md#committrans) nebo [CDatabase::Rollback](../../mfc/reference/cdatabase-class.md#rollback)), transakce je vrácena Zálohujte automaticky (Pokud vaše databáze back-end je databázový stroj Microsoft Jet).  
  
> [!CAUTION]
>  Pokud používáte databázový stroj Microsoft Jet, uzavření sady záznamů uvnitř explicitní transakce nemá za následek uvolnění řádků, které byly upraveny nebo zámky, které byly umístěny, dokud je explicitní transakce potvrzena nebo vrácena zpět. Doporučujeme tuto můžete vždy otevřít i zavřít sady záznamů uvnitř nebo vně explicitní transakce Jet.  
  
###  <a name="_core_how_scrolling_affects_updates"></a>Jak posouvání ovlivňuje aktualizace  
 Pokud jste [sada záznamů: posouvání (ODBC)](../../data/odbc/recordset-scrolling-odbc.md) upravené vyrovnávací paměti je v sadě záznamů vyplněn každý nový aktuální záznam (předchozího záznamu není uložen). Posouvání přeskakuje záznamy byly dříve odstraněny. Pokud se posunete po `AddNew` nebo **upravit** volání bez volání **aktualizace**, **CommitTrans**, nebo **vrácení zpět** první, všechny změny dojde ke ztrátě (s žádné upozornění), nový záznam budou přeneseny do vyrovnávací paměti pro úpravy. Vyrovnávací paměti pro úpravy, naplní se záznam přechod na, uložené záznam jsou uvolněny a ve zdroji dat nedošlo k žádné změně. To platí pro obě `AddNew` a **upravit**.  
  
##  <a name="_core_your_updates_and_the_updates_of_other_users"></a>Vaše aktualizace a aktualizace jiných uživatelů  
 Pokud používáte sadu záznamů k aktualizaci dat, vliv na vaše aktualizace jiných uživatelů. Podobně aktualizace jiných uživatelů po dobu životnosti sady záznamů ovlivní vás.  
  
 V prostředí můžete otevřít jiní uživatelé sady záznamů, které obsahují některé stejné záznamy, které jste vybrali v sady záznamů. Změny k záznamu před jejich načtení se projeví ve vaší sadě záznamů. Protože dynamické sady načíst záznam pokaždé, když jste posuňte se k němu, dynamické sady projevily změny pokaždé, když se posunete se záznamem. Snímky načíst záznam prvním posunete, takže snímky odráží pouze ty změny, které udělat předtím, než přejděte k záznamu původně.  
  
 Zaznamenává přidat další uživatelé po otevření sady záznamů se nezobrazí ve vaší sadě záznamů, pokud se znovu spustí dotaz. Pokud vaše sada záznamů je dynamická sada, úprav existující záznamy jinými uživateli se zobrazí ve vaší dynamické sadě při posouvání na daný záznam. Pokud sady záznamů je snímek, úpravy se nezobrazí, dokud requery snímku. Pokud chcete zobrazit záznamy při přidání nebo odstranění jiných uživatelů ve snímku, nebo záznamy přidané jinými uživateli ve vaší dynamické sadě, zavolejte [CRecordset::Requery](../../mfc/reference/crecordset-class.md#requery) opětovné vytvoření sady záznamů. (Všimněte si, že odstranění jiných uživatelů objeví ve vaší dynamické sadě.) Může se také zavolat **Requery** zobrazíte záznamy přidáte, ale ne k zobrazit vaše odstranění.  
  
> [!TIP]
>  Chcete-li vynutit, ukládání do mezipaměti pro celou snímek najednou, volejte `MoveLast` okamžitě po otevření snímku. Potom zavolejte **MoveFirst** začněte záznamy. `MoveLast`je ekvivalentní posouvání přes všechny záznamy, ale získává je všechny najednou. Upozorňujeme však, že se může snížit výkon a nemusí být požadována pro některé ovladače.  
  
 Účinky aktualizace na jiné uživatele jsou podobné jejich účinky na vás.  
  
##  <a name="_core_more_about_update_and_delete"></a>Další informace o aktualizaci a odstranění  
 Tato část poskytuje dodatečné informace, které vám pomohou při práci s **aktualizace** a **odstranit**.  
  
### <a name="update-success-and-failure"></a>Aktualizace úspěchy a chyby  
 Pokud **aktualizace** úspěšné, `AddNew` nebo **upravit** režimu zakončení. Chcete-li začít `AddNew` nebo **upravit** režim znovu, volání `AddNew` nebo **upravit**.  
  
 Pokud **aktualizace** selže (vrátí **FALSE** nebo vyvolá výjimku), zůstanou v `AddNew` nebo **upravit** režim, v závislosti na funkci, která jste označuje jako poslední. Potom můžete provést jednu z následujících:  
  
-   Upravte pole datových členů a **aktualizace** znovu.  
  
-   Volání `AddNew` resetovat pole datových členů na hodnotu Null, nastavte hodnoty pole datových členů a pak zavolají **aktualizace** znovu.  
  
-   Volání **upravit** znovu načíst hodnoty, které byly v sadě záznamů před prvním volání `AddNew` nebo **upravit**, nastavte hodnoty pole datových členů a pak zavolají **aktualizovat**znovu. Po úspěšně **aktualizace** volání (s výjimkou po `AddNew` volání), pole datových členů zachovat jejich nové hodnoty.  
  
-   Volání **přesunout** (včetně **přesunout** s parametrem **AFX_MOVE_REFRESH**, nebo 0), která vyprázdní všechny změny a ukončí všechny `AddNew` nebo **upravit** režimu v platnost.  
  
### <a name="update-and-delete"></a>Aktualizace a odstranění  
 Tato část platí pro obě **aktualizace** a **odstranit**.  
  
 Na **aktualizace** nebo **odstranit** operace, je třeba aktualizovat jenom jeden záznam. Je tento záznam na aktuální záznam, který odpovídá datových hodnot v polích pro sady záznamů. Pokud pro nějakého důvodu nejsou ovlivněny žádné záznamy vliv na jeden nebo více než jeden záznam je, je vyvolána výjimka obsahující jednu z následujících **RETCODE** hodnoty:  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED**  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED, KTERÁ**  
  
 Pokud jsou tyto výjimky vyvolány, zůstat v `AddNew` nebo **upravit** stavu byly jste volali metodu **aktualizace** nebo **odstranit**. Tady jsou nejběžnějších scénářů, ve kterých můžete vidět tyto výjimky. Jste pravděpodobně zobrazíte:  
  
-   **AFX_SQL_ERROR_NO_ROWS_AFFECTED** při použití režimu optimistické zamykání a jiný uživatel změnil záznam způsobem, který brání rozhraní identifikaci správného záznamu aktualizovat nebo odstranit.  
  
-   **AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED, která** při v tabulce, jsou aktualizace nemá žádný primární klíč nebo jedinečný index a nemáte dostatečný počet sloupců v sadě záznamů k jednoznačné identifikaci řádku tabulky.  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Jak sady záznamů vybírají záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)   
 [Výměna pole záznamu (RFX)](../../data/odbc/record-field-exchange-rfx.md)   
 [SQL](../../data/odbc/sql.md)   
 [Výjimky: Výjimky databáze](../../mfc/exceptions-database-exceptions.md)