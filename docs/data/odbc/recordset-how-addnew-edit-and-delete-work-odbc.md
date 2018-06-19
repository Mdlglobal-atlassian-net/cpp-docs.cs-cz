---
title: 'Sada záznamů: Jak AddNew, Edit a Delete (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- records [C++], updating
- record editing [C++], in recordsets
- recordsets [C++], adding records
- records [C++], adding
- ODBC recordsets [C++], adding records
- recordsets [C++], editing records
- recordsets [C++], updating
- AddNew method
- ODBC recordsets [C++], deleting records
- records [C++], deleting in recordsets
- data in recordsets [C++]
- recordsets [C++], deleting records
- ODBC recordsets [C++], editing records
- records [C++], editing
ms.assetid: cab43d43-235a-4bed-ac05-67d10e94f34e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e3d9dc82f4ea31557c4ec330b9737579021a8d35
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094127"
---
# <a name="recordset-how-addnew-edit-and-delete-work-odbc"></a>Sada záznamů: Funkce operací AddNew, Edit a Delete (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma vysvětluje, jak `AddNew`, **upravit**, a **odstranit** členské funkce třídy `CRecordset` fungovat. Obsahuje následující témata:  
  
-   [Jak funguje přidávání záznamů](#_core_adding_a_record)  
  
-   [Viditelnost přidaných záznamů](#_core_visibility_of_added_records)  
  
-   [Jak funguje úpravy záznamů](#_core_editing_an_existing_record)  
  
-   [Princip odstraňování záznamů](#_core_deleting_a_record)  
  
> [!NOTE]
>  Toto téma se vztahuje na objekty, které jsou odvozené z `CRecordset` v který řádek hromadné načítání se neimplementovala. Pokud používáte hromadné načítání řádků, přečtěte si téma [sada záznamů: načítání záznamů v hromadné (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Jako doplněk si můžete přečíst [výměna polí záznamu: Jak funguje RFX](../../data/odbc/record-field-exchange-how-rfx-works.md), který popisuje odpovídající roli RFX v operacích aktualizace.  
  
##  <a name="_core_adding_a_record"></a> Přidání záznamu  

 Přidávání nového záznamu do sady záznamů zahrnuje volání sady záznamů [AddNew](../../mfc/reference/crecordset-class.md#addnew) – členská funkce, nastavení hodnoty nový záznam pole datových členů a volání [aktualizace](../../mfc/reference/crecordset-class.md#update) – členská funkce pro zápis záznam ke zdroji dat.  
  
 Podmínkou pro volání `AddNew`, sadě záznamů nesmí být otevřena jen pro čtení. `CanUpdate` a `CanAppend` členské funkce umožňují určit tyto podmínky.  
  
 Při volání `AddNew`:  
  
-   Záznam v upravené vyrovnávací paměti je uložený, tak jeho obsah může být obnovena, pokud byla operace zrušena.  
  
-   Pole datových členů jsou označeny, takže je možné detekovat změny v nich později. Pole dat, jsou označeny také členy čisté (beze změny) a nastavte na hodnotu Null.  
  
 Po zavolání metody `AddNew`vyrovnávací paměť pro úpravu představuje nový, prázdný záznam, připravený k vyplnění hodnotami. To provedete ručně nastavte hodnoty přiřazením k nim. Místo zadání aktuální hodnoty dat pro pole, můžete volat `SetFieldNull` zadejte hodnotu Null.  
  
 Chcete-li potvrdit změny, zavolejte **aktualizace**. Při volání **aktualizace** pro nový záznam:  
  
-   Pokud ovladač ODBC podporuje **:: SQLSetPos** funkce rozhraní API ODBC, MFC přidat záznam ve zdroji dat pomocí funkce. S **:: SQLSetPos**, může MFC přidat záznam efektivněji, protože nemá sestavit a zpracování příkazu jazyka SQL.  
  
-   Pokud **:: SQLSetPos** nelze použít, MFC provádí následující:  
  
    1.  Pokud nejsou nalezeny žádné změny, **aktualizace** neprovede žádnou akci a vrátí hodnotu 0.  
  
    2.  Pokud se změní, **aktualizace** vytvoří SQL **vložit** příkaz. Sloupce reprezentované všechny změny pole datových členů jsou uvedeny v **vložit** příkaz. Chcete-li vynutit zahrnutí sloupce, zavolejte [SetFieldDirty](../../mfc/reference/crecordset-class.md#setfielddirty) – členská funkce:  
  
        ```  
        SetFieldDirty( &m_dataMember, TRUE );  
        ```  
  
    3.  **Aktualizace** potvrdí nový záznam – **vložit** spustit příkaz a záznam je potvrzen do tabulky zdroje dat (a sada záznamů, pokud není snímek), pokud probíhá transakce.  
  
    4.  Je obnoven uložené záznam do vyrovnávací paměti pro úpravy. Záznam, který byl aktuální před `AddNew` volání je aktuální znovu bez ohledu na to jestli **vložit** úspěšně spustit příkaz.  
  
    > [!TIP]
    >  Pro úplnou kontrolu nad nový záznam, proveďte následující postup: nastavte hodnoty všechna pole, které budou mít hodnoty a explicitně nastavit všechna pole, které zůstanou Null voláním `SetFieldNull` pomocí ukazatele na pole a parametr **TRUE**  (výchozí). Pokud chcete zajistit, že pole není zapsáno do zdroje dat, volání `SetFieldDirty` pomocí ukazatele na pole a parametr **FALSE**a neměňte hodnotu pole. Pokud chcete zjistit, zda pole může mít hodnotu Null, volání `IsFieldNullable`.  
  
    > [!TIP]
    >  Zjistit, kdy datových členů sady záznamů, změňte hodnotu, používá MFC **PSEUDO_NULL** hodnotu pro každý typ dat, který chcete uložit v sadě záznamů. Pokud musíte explicitně nastavit pole na **PSEUDO_NULL** hodnota a pole se stane již označeno jako Null, musíte také zavolat `SetFieldNull`, předávání na adresu v poli první parametr a **FALSE**v druhý parametr.  
  
##  <a name="_core_visibility_of_added_records"></a> Viditelnost přidaných záznamů  
 Když je přidaný záznam viditelné pro sady záznamů Přidání záznamů se někdy zobrazují a někdy nejsou viditelné v závislosti na dvě věci:  
  
-   Jaké ovladače je schopen.  
  
-   Jaké rozhraní můžete využít výhod.  
  
 Pokud ovladač ODBC podporuje **:: SQLSetPos** funkce rozhraní API ODBC, MFC pomocí funkce přidat záznamy. S **:: SQLSetPos**, přidat záznamy jsou viditelné pro žádné aktualizovat sadu záznamů MFC. Bez podpory pro tuto funkci přidat záznamy nejsou viditelné a musíte **Requery** k jejich zobrazení. Pomocí **:: SQLSetPos** je také efektivnější.  
  
##  <a name="_core_editing_an_existing_record"></a> Úprava existujícího záznamu  
 Úprava existujícího záznamu v sadě záznamů zahrnuje posunutí na záznam, volání sady záznamů [upravit](../../mfc/reference/crecordset-class.md#edit) – členská funkce, nastavení hodnoty nový záznam pole datových členů a volání [aktualizovat](../../mfc/reference/crecordset-class.md#update)– členská funkce zapsat změněné záznam ke zdroji dat.  
  
 Podmínkou pro volání **upravit**, musí být sady záznamů, aktualizovat a na záznam. `CanUpdate` a `IsDeleted` členské funkce umožňují určit tyto podmínky. Záznam na aktuální záznam nesmí mít smazaný a musí být záznamy v sadě záznamů (obě `IsBOF` a `IsEOF` vrátit 0).  
  
 Při volání **upravit**, záznam v upravené vyrovnávací paměti (aktuální záznam) je uložen. Hodnoty uložené záznam později slouží ke zjištění, zda pole byly změněny.  
  
 Po zavolání metody **upravit**, vyrovnávací paměť pro úpravu stále představuje záznam na aktuální záznam, ale je nyní připravena přijímat změny pole datových členů. Chcete-li změnit záznam, ručně nastavit hodnoty žádné pole datových členů, které chcete upravit. Místo zadání aktuální hodnoty dat pro pole, můžete volat `SetFieldNull` zadejte hodnotu Null. Chcete-li potvrdit změny, volejte **aktualizace**.  
  
> [!TIP]
>  Chcete-li získat z `AddNew` nebo **upravit** režim, volání **přesunout** s parametrem **AFX_MOVE_REFRESH**.  
  
 Podmínkou pro volání **aktualizace**, sadě záznamů nesmí být prázdný a nesmí byl odstraněn záznam na aktuální záznam. `IsBOF`, `IsEOF`, a `IsDeleted` by měla vrátit 0.  
  
 Při volání **aktualizace** pro upravený záznam:  
  
-   Pokud ovladač ODBC podporuje **:: SQLSetPos** funkce rozhraní API ODBC, MFC aktualizovat záznam ve zdroji dat pomocí funkce. S **:: SQLSetPos**, porovná ovladač Vaši upravenou vyrovnávací paměť s odpovídající záznam na serveru, aktualizace záznamu na serveru, pokud jsou dva různé. S **:: SQLSetPos**, může MFC upravit záznam efektivněji, protože nemá sestavit a zpracování příkazu jazyka SQL.  
  
     -nebo-  
  
-   Pokud **:: SQLSetPos** nelze použít, MFC provádí následující:  
  
    1.  Pokud zde nejsou žádné změny **aktualizace** neprovede žádnou akci a vrátí hodnotu 0.  
  
    2.  Pokud se změní, **aktualizace** vytvoří SQL **aktualizace** příkaz. Sloupce, uvedené v **aktualizace** příkaz jsou založené na pole datových členů, které se změnily.  
  
    3.  **Aktualizace** potvrdí změny – provede **aktualizace** příkaz – a záznam je změněn na datovém zdroji, ale není potvrzen pokud transakce probíhá (najdete v části [transakce: provádění transakcí v Sada záznamů (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md) informace o tom, jak transakce na aktualizaci). Rozhraní ODBC uchovává kopii na záznam, který také změní.  
  
    4.  Na rozdíl od proces `AddNew`, **upravit** procesu neobnoví uložené záznam. Upravený záznam zůstává na místě jako záznam na aktuální záznam.  
  
    > [!CAUTION]
    >  Když připravujete aktualizovat sadu záznamů voláním **aktualizace**, vezměte v potaz, že vaše sada záznamů obsahuje všechny sloupce, které představují primární klíč tabulky (nebo všechny sloupce všechny jedinečný index v tabulce nebo dostatečný počet sloupců na jednoznačně Určete řádek). V některých případech rozhraní slouží k identifikaci, který záznam v tabulce aktualizovat pouze vybrané sloupce ve vaší sadě záznamů. Bez všechny potřebné sloupce může být aktualizováno více záznamů v tabulce. V takovém případě vyvolá architektura výjimky při volání **aktualizace**.  
  
    > [!TIP]
    >  Když zavoláte `AddNew` nebo **upravit** po zavolání funkce dřív, ale před volání **aktualizace**, vyrovnávací paměť pro úpravu se aktualizují s uložené záznam, nových nebo upravených v nahrazení záznamu průběh. Toto chování poskytuje způsob k přerušení `AddNew` nebo **upravit** a začít další: Pokud zjistíte, že záznam v průběhu chybný, jednoduše volání **upravit** nebo `AddNew` znovu.  
  
##  <a name="_core_deleting_a_record"></a> Odstranění záznamu  
 Odstranění záznamu z sady záznamů zahrnuje posunutí na záznam a volání sady záznamů [odstranit](../../mfc/reference/crecordset-class.md#delete) – členská funkce. Na rozdíl od `AddNew` a **upravit**, **odstranit** nevyžaduje odpovídající volání **aktualizace**.  
  
 Podmínkou pro volání **odstranit**, musí být aktualizovat sadu záznamů a musí být na záznam. `CanUpdate`, `IsBOF`, `IsEOF`, A `IsDeleted` členské funkce umožňují určit tyto podmínky.  
  
 Při volání **odstranit**:  
  
-   Pokud ovladač ODBC podporuje **:: SQLSetPos** funkce rozhraní API ODBC, MFC odstranit záznam ve zdroji dat pomocí funkce. Pomocí **:: SQLSetPos** obvykle je efektivnější než při použití SQL.  
  
     -nebo-  
  
-   Pokud **:: SQLSetPos** nelze použít, MFC provádí následující:  
  
    1.  Na aktuální záznam v upravené vyrovnávací paměti není zálohován jako v `AddNew` a **upravit**.  
  
    2.  **Odstranit** vytvoří SQL **odstranit** příkaz, který odstraní záznam.  
  
         Aktuální záznam v upravené vyrovnávací paměti není uložen jako v `AddNew` a **upravit**.  
  
    3.  **Odstranit** potvrdí odstranění – provede **odstranit** příkaz. Záznam je označen odstraněné ve zdroji dat a je-li záznam snímku v ODBC.  
  
    4.  Odstraněný záznam hodnoty jsou stále v pole datových členů sady záznamů, ale jsou označené pole datových členů, hodnotu Null a sady záznamů `IsDeleted` – členská funkce vrátí nenulovou hodnotu.  
  
    > [!NOTE]
    >  Po odstranění záznamu, měli přechod na jiný záznam k doplnění vyrovnávací paměti pro úpravy s daty v novém záznamu. Jedná se o chybu volat **odstranit** znovu nebo volat **upravit**.  
  
 Informace o příkazech SQL použít v operacích aktualizace najdete v tématu [SQL](../../data/odbc/sql.md).  
  
## <a name="see-also"></a>Viz také  
 [Sada záznamů (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Sada záznamů: Další informace o aktualizacích (ODBC)](../../data/odbc/recordset-more-about-updates-odbc.md)   
 [Výměna polí záznamu (Record Field Exchange – RFX)](../../data/odbc/record-field-exchange-rfx.md)