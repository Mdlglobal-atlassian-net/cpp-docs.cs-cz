---
title: 'TN055: Migrace aplikací databázové třídy MFC rozhraní ODBC do tříd MFC rozhraní DAO'
ms.date: 06/20/2018
f1_keywords:
- vc.mfc.odbc
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
ms.openlocfilehash: f8e0d8e50f05e86c35e0f8b7f324533bffea6f25
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487097"
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055: Migrace aplikací databázové třídy MFC rozhraní ODBC do tříd MFC rozhraní DAO

> [!NOTE]
> Prostředí Visual C++ a Průvodce nepodporuje rozhraní DAO (i když jsou součástí třídy DAO a můžete stále použít). Microsoft doporučuje, abyste použili [šablony technologie OLE DB](../data/oledb/ole-db-templates.md) nebo [rozhraní ODBC a MFC](../data/odbc/odbc-and-mfc.md) pro nové projekty. DAO byste měli používat jenom v udržování existujících aplikací.

## <a name="overview"></a>Přehled

V mnoha situacích může být vhodné k migraci aplikace, které používají třídy databází MFC rozhraní ODBC pro databázové třídy DAO knihovny MFC. Tato technická Poznámka podrobně popisuje většina rozdílů mezi třídy knihovny MFC rozhraní ODBC a DAO. S rozdíly v úvahu by neměly být příliš obtížné migrace aplikací ze třídy rozhraní ODBC do tříd MFC v případě potřeby.

## <a name="why-migrate-from-odbc-to-dao"></a>Proč migrovat z rozhraní ODBC do DAO

Existuje mnoho důvodů, proč může být vhodné k migraci aplikace z databázových tříd rozhraní ODBC pro databázové třídy DAO, ale rozhodnutí není nutně jednoduché nebo zřejmý. Jedna věc, kterou je potřeba mít na paměti, je, že databázový stroj Microsoft Jet, který používá rozhraní DAO může číst libovolný zdroj dat rozhraní ODBC, pro který máte ovladač rozhraní ODBC. Může být efektivnější použít databázové třídy ODBC nebo volat rozhraní ODBC přímo sami, ale databázový stroj Microsoft Jet může číst ODBC data.

Případy jednoduchý usnadnění rozhraní ODBC a DAO rozhodnutí. Například když pouze potřebujete přístup k datům ve formátu, který stroj Microsoft Jet může číst přímo (přístup k formátu, formátu aplikace Excel a tak dále) je použít databázové třídy DAO jasnou volbou.

Složitějších případech vzniknout, když vaše data existuje na serveru nebo na celé řadě různých serverech. V takovém případě rozhodnutí o použití rozhraní ODBC databázové třídy nebo rozhraní DAO databázové třídy je obtížné. Pokud chcete provádět věci jako heterogenní spojení (spojení dat ze serverů ve více formátech, jako jsou SQL Server a Oracle), pak bude databázový stroj Microsoft Jet provedením příkazu join je místo takže jste museli dělat potřebné práce, když jste použili databáze ODBC Třídy nebo názvem ODBC přímo. Pokud používáte ovladač rozhraní ODBC, který podporuje kurzory ovladač, může být nejlepší volbou ODBC databázové třídy.

Volba může být složité, proto je vhodné ukázky kódu pro testování výkonu různých metodám zvláštními potřebami. Tato technická Poznámka se předpokládá, že jste provedli rozhodnutí migrovat z databázových tříd rozhraní ODBC do DAO databázové třídy.

## <a name="similarities-between-odbc-database-classes-and-mfc-dao-database-classes"></a>Podobnosti mezi databázové třídy ODBC a databázové třídy MFC rozhraní DAO

Původní návrhu tříd knihovny MFC rozhraní ODBC byl založen na objektový model rozhraní DAO, který je v aplikaci Microsoft Access a Microsoft Visual Basic. To znamená, že existuje mnoho běžných funkcí rozhraní ODBC a DAO knihovny MFC tříd, které budou všechny být uvedené v této části. Obecně platí programovacími modely jsou stejné.

Abyste měli na očích několik podobnosti:

- Rozhraní ODBC a DAO – třídy mají databázové objekty, které spravujete pomocí základního systému správy databáze (DBMS).

- Obě mají záznamů objekty, které představují sadu výsledky vrácené z této DBMS.

- Objekty databáze a sady záznamů rozhraní DAO obsahovat členy, které jsou téměř shodné s ODBC – třídy.

- Obě sady tříd kód k načtení dat je shodná s výjimkou některých změn názvů objektů a členů. Změny se bude vyžadovat, ale obvykle proces je jednoduchý název změnit, při přechodu z třídy rozhraní ODBC do DAO – třídy.

Například v obou modelech postup k načtení dat je vytvořit a otevřít databázový objekt, vytvořit a otevřít objekt sady záznamů a přejděte (přesunout), ale data provádění nějaké operace.

## <a name="differences-between-odbc-and-dao-mfc-classes"></a>Rozdíly mezi třídy knihovny MFC rozhraní DAO a ODBC

DAO – třídy zahrnují více objektů a bohatší sadu metod, ale tato část podrobně popisuje pouze rozdíly v podobné třídy a funkce.

Pravděpodobně Nejobvyklejšími rozdíly mezi třídami se změny názvů pro podobné třídy a globální funkce. Následující seznam uvádí změny názvů objektů, metody a globální funkce, které jsou přidružené k databázové třídy:

|Třída nebo funkce|Ekvivalent ve třídách knihovny MFC rozhraní DAO|
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
|`RFX_Date`<sup>1</sup>|`DFX_Date` (`COleDateTime`– na základě)|
|`RFX_Text`|`DFX_Text`|
|`RFX_Binary`|`DFX_Binary`|
|`RFX_LongBinary`|`DFX_LongBinary`|

<sup>1</sup> `RFX_Date` funkce je založena na `CTime` a `TIMESTAMP_STRUCT`.

Hlavních změn funkcí, které můžou ovlivnit vaši aplikaci a vyžadovat více než jednoduchý název změny jsou uvedeny níže.

- Konstanty a makra použitá k určení typu otevřete věci, jako je sada záznamů a záznamů možnosti byly změněny.

   ODBC – třídy knihovny MFC zapotřebí k definování těchto možností prostřednictvím makra nebo vytvořit výčet typů.

   DAO – třídy DAO obsahuje definici z těchto možností v hlavičkovém souboru (DBDAOINT. H). Proto typ sady záznamů je člen výčtu `CRecordset`, ale s objektem DAO jej místo toho je konstanta. Například byste použili **snímku** při určování typu `CRecordset` v rozhraní ODBC, ale **DB_OPEN_SNAPSHOT** při určování typu `CDaoRecordset`.

- Výchozí typ sady záznamů pro `CRecordset` je **snímku** while výchozí typ sady záznamů pro `CDaoRecordset` je **dynamická sada** (viz poznámka níže pro další problém o snímcích třídy rozhraní ODBC).

- Rozhraní ODBC `CRecordset` třída má možnost pro vytvoření typů záznamů s posouváním pouze vpřed. V `CDaoRecordset` třídy dopředné není typ sady záznamů, ale místo toho vlastnost (nebo možnost) určitého typu sady záznamů.

- Připojení záznamů s posouváním pouze při otevírání `CRecordset` objekt znamenalo, že sady záznamů dat by mohl přečíst a připojí. S `CDaoRecordset` objektu, možnost nabízí jen možnost připojovat doslova znamená, že sady záznamů dat může být pouze připojen (a číst).

- ODBC – třídy transakce členské funkce jsou členy `CDatabase` a reagovat na úrovni databáze. Ve třídách rozhraní DAO transakce členské funkce jsou členy třídy vyšší úrovni (`CDaoWorkspace`) a proto může mít vliv na více `CDaoDatabase` objekty, které sdílení stejného pracovního prostoru (místo transakce).

- Třída výjimky se změnil. `CDBExceptions` jsou vyvolány v ODBC – třídy a `CDaoExceptions` tříd DAO.

- `RFX_Date` používá `CTime` a `TIMESTAMP_STRUCT` objekty při `DFX_Date` používá `COleDateTime`. `COleDateTime` Je téměř shodná `CTime`, ale je založen na 8 bajtů OLE **datum** místo 4 bajty **time_t** tak může obsahovat mnohem většího rozsahu data.

   > [!NOTE]
   > Rozhraní DAO (`CDaoRecordset`) snímky jsou jen pro čtení při ODBC (`CRecordset`) snímků může být možné aktualizovat v závislosti na ovladač a použití knihovny kurzorů ODBC. Pokud používáte knihovna kurzorů rozhraní `CRecordset` snímky jsou aktualizovatelná. Pokud používáte některou ovladače Microsoft z Desktopu ovladač Pack 3.0 bez knihovna kurzorů rozhraní ODBC, `CRecordset` snímky jsou jen pro čtení. Pokud používáte jiný ovladač, vyhledejte v dokumentaci ovladače a zjistěte, jestli snímky (`STATIC_CURSORS`) jsou jen pro čtení.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
