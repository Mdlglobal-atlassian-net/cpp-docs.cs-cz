---
title: "TN055: Migrace aplikací databázové třídy MFC rozhraní ODBC do tříd MFC rozhraní DAO | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.odbc
dev_langs: C++
helpviewer_keywords:
- DAO [MFC], migration
- TN055
- migration [MFC], ODBC database applications
- ODBC classes [MFC], DAO classes
- migrating ODBC database applications [MFC]
- porting database applications to DAO
- ODBC [MFC], DAO
- porting ODBC database applications to DAO
- migrating database applications [MFC]
ms.assetid: 0f858bd1-e168-4e2e-bcd1-8debd82856e4
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: bb9b4041f9c288b40a6efb1ef7978d323bad2fb4
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055: Migrace aplikací databázové třídy MFC rozhraní ODBC do tříd MFC rozhraní DAO
> [!NOTE]
>  Prostředí Visual C++ a průvodců nepodporují rozhraní DAO (i když jsou zahrnuté třídy DAO a můžete je dál používat). Microsoft doporučuje používat [šablony technologie OLE DB](../data/oledb/ole-db-templates.md) nebo [rozhraní ODBC a MFC](../data/odbc/odbc-and-mfc.md) pro nové projekty. DAO byste měli používat jenom pro údržbu existujících aplikací.  
  
 **Přehled**  
  
 V mnoha situacích může být žádoucí k migraci aplikace, které používají třídami databází MFC na rozhraní ODBC do tříd MFC rozhraní DAO databáze. Tato technická Poznámka podrobně většinu rozdíly mezi třídy knihovny MFC rozhraní ODBC a DAO. S rozdíly v úvahu by neměl být zbytečně složité aplikace migrovat z třídy rozhraní ODBC do tříd MFC v případě potřeby.  
  
 **Proč migrovat z rozhraní ODBC do DAO**  
  
 Existuje řada důvodů, proč můžete chtít aplikace migrovat z databázové třídy rozhraní ODBC pro databázové třídy DAO, ale rozhodnutí není nutně jednoduchý nebo zřejmé. Jednou z věcí třeba vzít v úvahu je, můžete databázový stroj Microsoft Jet, který je používán DAO číst všechny zdroje dat ODBC, pro které máte ovladače ODBC. To může být efektivnější použít databázové třídy ODBC nebo volání rozhraní ODBC přímo sami, ale databázový stroj Microsoft Jet může číst dat ODBC.  
  
 Některé jednoduché případů, které zajistit rozhodnutí rozhraní ODBC/DAO snadné. Například když potřebujete jenom přístup k datům ve formátu, který stroje Microsoft Jet může číst přímo (přístup k formátu, formátu aplikace Excel a tak dále) je zřejmé volba použít databázové třídy DAO.  
  
 Složitější případech nastat, pokud vaše data existuje na serveru nebo na celou řadu různých serverech. V takovém případě rozhodnutí o použití rozhraní ODBC databázové třídy nebo rozhraní DAO databázové třídy je obtížné. Pokud chcete provést věci jako heterogenní spojení (připojení dat ze serverů ve více formátů, jako SQL Server a Oracle), pak databázový stroj Microsoft Jet dojde ke spojení pro můžete místo vynucení lze provádět práce nezbytné, pokud jste použili databázi ODBC Třídy nebo názvem ODBC přímo. Pokud používáte ovladač ODBC, který podporuje kurzory ovladač, může být nejlepší volbou ODBC databázové třídy.  
  
 Volba může být složité, proto je vhodné k zápisu některé ukázkový kód pro testování výkonu různé metody, které jsou zadané zvláštními potřebami. Tento Technická poznámka předpokládá, že jste udělali rozhodnutí při migraci z databázové třídy rozhraní ODBC do DAO databázové třídy.  
  
 **Podobnosti mezi databázové třídy rozhraní ODBC a databázové třídy MFC rozhraní DAO**  
  
 Původní návrh tříd MFC rozhraní ODBC bylo založeno na rozhraní DAO objektový model, který byl používán v aplikaci Microsoft Access a Microsoft Visual Basic. To znamená, že existuje mnoho běžných funkcí rozhraní ODBC a MFC rozhraní DAO tříd, které budou všechny uvedené v této části. Obecně platí s programovacími modely jsou stejné.  
  
 Abyste měli na očích několik podobnosti:  
  
-   Jak rozhraní ODBC a DAO třídy mají databázové objekty, které spravujete pomocí základního systému správy databáze (databázového systému).  
  
-   Mají obě sady záznamů objekty, které představují sadu výsledků vrácená z tohoto databázového systému.  
  
-   Objekty databáze a sady záznamů rozhraní DAO mít členy, do třídy ODBC.  
  
-   S obě sady třídy se shoduje s výjimkou některé změny název objektu a člen kódem, který chcete načíst data. Změny se bude vyžadovat, ale obvykle probíhá změna přehledné názvu při přepnutí z třídy rozhraní ODBC do tříd rozhraní DAO.  
  
 V obou modelech například postup k načtení dat se vytvořit a otevřít databázový objekt, vytvořit a otevřít objekt sady záznamů a přejít (přesunout), ale data provádění nějaké operace.  
  
 **Rozdíly mezi třídy MFC rozhraní DAO a ODBC**  
  
 Třídy DAO zahrnovat další objekty a širší metod, ale tato část podrobně popisuje pouze rozdíly v podobné třídy a funkce.  
  
 Pravděpodobně nejobvyklejší rozdíly mezi třídami jsou změny názvu pro podobné třídy a globální funkce. V následujícím seznamu jsou změny názvu objektů, metod a globální funkce související s třídami databází:  
  
|Třída nebo funkce|Ekvivalent v tříd MFC rozhraní DAO|  
|-----------------------|-----------------------------------|  
|`CDatabase`|`CDaoDatabase`|  
|`CDatabase::ExecuteSQL`|`CDaoDatabase::Execute`|  
|`CRecordset`|`CDaoRecordset`|  
|`CRecordset::GetDefaultConnect`|`CDaoRecordset::GetDefaultDBName`|  
|`CFieldExchange`|`CDaoFieldExchange`|  
|`RFX_Bool`|`DFX_Bool`|  
|`RFX_Byte`|`DFX_Byte`|  
|`RFX_Int`|`DFX_Short`|  
|`RFX_Long`|`DFX_Long`|  
||`DFX_Currency`|  
|`RFX_Single`|`DFX_Single`|  
|`RFX_Double`|`DFX_Double`|  
|**RFX_Date –\***|**DFX_Date** (`COleDateTime`– na základě)|  
|`RFX_Text`|`DFX_Text`|  
|`RFX_Binary`|`DFX_Binary`|  
|`RFX_LongBinary`|`DFX_LongBinary`|  
  
 \*`RFX_Date` Funkce je založena na `CTime` a **TIMESTAMP_STRUCT z**.  
  
 Hlavní změny na funkce, které můžou ovlivnit vaše aplikace a vyžadují více než jednoduchý název změny jsou uvedeny níže.  
  
-   Konstanty a makra použít k určení typu otevřete takové věci, jako sada záznamů a záznamů otevřít panel Možnosti se změnily.  
  
     Třídy ODBC knihovny MFC potřebné k definování těchto možností prostřednictvím makra nebo výčet typů.  
  
     Pomocí třídy DAO DAO poskytuje definici z těchto možností v záhlaví souboru (DBDAOINT. H). Proto je sada záznamů typu výčtové členem `CRecordset`, ale DAO je konstanta místo. Například byste použili **snímku** při zadávání typ `CRecordset` v rozhraní ODBC, ale **DB_OPEN_SNAPSHOT** při zadávání typ `CDaoRecordset`.  
  
-   Výchozí typ záznamů pro `CRecordset` je **snímku** při výchozí typ záznamů pro `CDaoRecordset` je **dynamická sada** (viz poznámka níže další problému, o snímky třídy rozhraní ODBC).  
  
-   ODBC `CRecordset` třída má možnost pro vytvoření typ dopředné sady záznamů. V `CDaoRecordset` třída, dopředné není typu sady záznamů, ale místo vlastnosti (nebo možnost) určitých typů sady záznamů.  
  
-   Připojení sada záznamů při otevírání `CRecordset` objekt znamenalo, že data sady záznamů by mohl přečíst a připojí. S `CDaoRecordset` objektu, možnost připojovacím oznámena znamená, že jsou data sady záznamů lze pouze připojí (a číst).  
  
-   Funkce člena třídy rozhraní ODBC transakce jsou členy `CDatabase` a provádění akcí na úrovni databáze. V třídy DAO členské funkce transakce jsou členy vyšší úrovně třídy (`CDaoWorkspace`) a proto může ovlivnit více `CDaoDatabase` objekty sdílení ve stejném pracovním prostoru (transakce místa).  
  
-   Třídy výjimek byl změněn. **CDBExceptions** jsou vyvolány v třídy rozhraní ODBC a **CDaoExceptions** v třídy DAO.  
  
-   `RFX_Date`používá `CTime` a **TIMESTAMP_STRUCT z** objekty při **DFX_Date** používá `COleDateTime`. `COleDateTime` Je téměř shodná `CTime`, ale je založena na 8 bajtů OLE **datum** místo 4 bajtů `time_t` tak může uchovávat mnohem větší rozsah data.  
  
    > [!NOTE]
    >  Rozhraní DAO (`CDaoRecordset`) snímky jsou jen pro čtení při ODBC (`CRecordset`) snímky mohou být v aktualizovatelné v závislosti na ovladače a použití knihovny kurzorů ODBC. Pokud používáte knihovna kurzorů `CRecordset` snímky jsou lze aktualizovat. Pokud používáte některou z plochy ovladač Pack 3.0 ovladače společnosti Microsoft bez knihovna kurzorů rozhraní ODBC `CRecordset` snímky jsou jen pro čtení. Pokud používáte jiný ovladač, podívejte se do dokumentace ovladače a zjistěte, zda snímků (**STATIC_CURSORS**) jsou jen pro čtení.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

