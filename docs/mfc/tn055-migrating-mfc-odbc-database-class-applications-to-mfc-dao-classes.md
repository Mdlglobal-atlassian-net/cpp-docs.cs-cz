---
title: 'TN055: Migrace aplikací databázové třídy MFC rozhraní ODBC do tříd MFC rozhraní DAO'
ms.date: 09/17/2019
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
ms.openlocfilehash: 7107964cc894a0aa45be5de362c9edd166dc0af1
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095962"
---
# <a name="tn055-migrating-mfc-odbc-database-class-applications-to-mfc-dao-classes"></a>TN055: Migrace aplikací databázové třídy MFC rozhraní ODBC do tříd MFC rozhraní DAO

> [!NOTE]
> Rozhraní DAO se používá s databázemi Access a je podporované prostřednictvím sady Office 2013. 3,6 je finální verze, která je považována za zastaralou. Vizuální C++ prostředí a Průvodci nepodporují rozhraní DAO (i když třídy rozhraní DAO jsou zahrnuty a je možné je nadále používat). Společnost Microsoft doporučuje, abyste pro nové projekty používali [šablony OLE DB](../data/oledb/ole-db-templates.md) nebo [rozhraní ODBC a knihovnu MFC](../data/odbc/odbc-and-mfc.md) . V údržbě stávajících aplikací byste měli používat jenom rozhraní DAO.

## <a name="overview"></a>Přehled

V mnoha situacích může být žádoucí migrovat aplikace, které používají databázové třídy rozhraní ODBC knihovny MFC, na databázové třídy DAO knihovny MFC. Tato technická Poznámka podrobně popisuje většinu rozdílů mezi třídami rozhraní ODBC knihovny MFC a rozhraní DAO. V případě rozdílů v tom, že v případě potřeby nesmí být migrace aplikací z tříd rozhraní ODBC do tříd knihovny MFC příliš náročná.

## <a name="why-migrate-from-odbc-to-dao"></a>Proč migrovat z rozhraní ODBC na rozhraní DAO

Existuje několik důvodů, proč možná budete chtít migrovat aplikace z databázových tříd rozhraní ODBC na databázové třídy DAO, ale rozhodnutí není nutně jednoduché nebo zřejmé. Mějte na paměti, že databázový stroj Microsoft Jet, který je používán rozhraním DAO, může číst libovolný zdroj dat ODBC, pro který máte ovladač ODBC. Může být efektivnější používat databázové třídy ODBC nebo přímo volat rozhraní ODBC, ale databázový stroj Microsoft Jet může číst data rozhraní ODBC.

V některých jednoduchých případech je rozhodnutí ODBC/DAO snadné. Například když potřebujete přístup k datům ve formátu, který může stroj Microsoft Jet přímo číst (formát přístupu, formát aplikace Excel atd.), je zřejmé, že použijete databázové třídy DAO.

Složitější případy se projeví, když data existují na serveru nebo na nejrůznějších různých serverech. V takovém případě je obtížné použít databázové třídy ODBC nebo databázové třídy DAO. Pokud chcete provádět akce, jako jsou heterogenní spojení (připojovat data ze serverů ve více formátech, jako je SQL Server a Oracle), pak se v databázovém stroji Microsoft Jet provede spojení, a to i v případě, že jste použili databázi ODBC. Třídy nebo nazývané rozhraní ODBC přímo. Pokud používáte ovladač ODBC, který podporuje kurzory ovladačů, nejlepší volbou můžou být databázové třídy ODBC.

Volba může být složitá, takže možná budete chtít napsat ukázkový kód pro otestování výkonu různých metod podle vašich speciálních potřeb. Tato technická Poznámka předpokládá, že jste provedli rozhodnutí migrovat z databázových tříd rozhraní ODBC na databázové třídy DAO.

## <a name="similarities-between-odbc-database-classes-and-mfc-dao-database-classes"></a>Podobnosti mezi databázovými třídami rozhraní ODBC a databázovými třídami MFC DAO

Původní návrh tříd knihovny MFC rozhraní ODBC byl založen na objektovém modelu DAO, který se používá v aplikacích Microsoft Access a Microsoft Visual Basic. To znamená, že existuje mnoho běžných funkcí tříd MFC rozhraní ODBC a DAO, které nebudou uvedeny v této části. Obecně jsou programovací modely stejné.

Zvýraznění několika podobností:

- Třídy rozhraní ODBC i rozhraní DAO mají databázové objekty, které se spravují pomocí základního systému správy databáze (DBMS).

- Oba mají objekty sady záznamů reprezentující sadu výsledků vrácených z tohoto systému DBMS.

- Databáze rozhraní DAO a objekty sady záznamů mají členy téměř identické s třídami rozhraní ODBC.

- U obou sad tříd je kód pro načtení dat stejný, s výjimkou změn některých objektů a názvů členů. Změny se vyžadují, ale při přepnutí z tříd rozhraní ODBC na třídy DAO se obvykle jedná o přímočarý postupná Změna názvu.

Například v obou modelech procedura, jak načíst data, je vytvořit a otevřít databázový objekt, vytvořit a otevřít objekt sady záznamů a přejít (přesunout) i když data provádějící určitou operaci.

## <a name="differences-between-odbc-and-dao-mfc-classes"></a>Rozdíly mezi třídami ODBC a DAO knihovny MFC

Třídy DAO obsahují více objektů a bohatší sadu metod, ale v této části se budou podrobná pouze rozdíly v podobných třídách a funkcích.

Nejpravděpodobnější rozdíly mezi třídami jsou pravděpodobně změny názvů pro podobné třídy a globální funkce. V následujícím seznamu jsou uvedeny změny názvů objektů, metod a globálních funkcí přidružených k databázovým třídám:

|Třída nebo funkce|Ekvivalent v třídách MFC DAO|
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
|`RFX_Date`<sup>1</sup>|`DFX_Date`(`COleDateTime`založené na)|
|`RFX_Text`|`DFX_Text`|
|`RFX_Binary`|`DFX_Binary`|
|`RFX_LongBinary`|`DFX_LongBinary`|

1 funkce je založena na `CTime` a. <sup></sup> `RFX_Date` `TIMESTAMP_STRUCT`

Hlavní změny funkčnosti, které mohou ovlivnit vaši aplikaci a vyžadují více než jednoduché změny názvů, jsou uvedeny níže.

- Konstanty a makra sloužící k určení akcí, jako je typ otevřené sady záznamů a otevřené možnosti sady záznamů, byly změněny.

   Pomocí tříd rozhraní ODBC MFC potřebných k definování těchto možností prostřednictvím maker nebo výčtových typů.

   Pomocí tříd DAO poskytuje rozhraní DAO definici těchto možností v hlavičkovém souboru (DBDAOINT. H). Proto je typ sady záznamů výčet členem `CRecordset`, ale s rozhraním DAO je místo toho konstantní. Můžete například použít **snímek** při určení typu `CRecordset` v rozhraní ODBC, ale **DB_OPEN_SNAPSHOT** při určení typu `CDaoRecordset`.

- Výchozí typ sady záznamů pro `CRecordset` je **snímek** , zatímco výchozí typ sady záznamů `CDaoRecordset` pro je **dynamická sada** (viz poznámka níže pro další problém týkající se snímků třídy rozhraní ODBC).

- Třída rozhraní `CRecordset` ODBC má možnost vytvořit pouze dopředný typ sady záznamů. `CDaoRecordset` Ve třídě není pouze typ sady záznamů typu Recordset, ale spíše vlastnost (nebo možnost) určitých typů sad záznamů.

- Sada záznamů s připojením pouze při otevření `CRecordset` objektu, která je určena k načtení a připojení dat sady záznamů. S `CDaoRecordset` objektem, možnost připojení pouze znamená, že data sady záznamů lze připojit pouze (a nikoli číst).

- Funkce členů transakce třídy rozhraní ODBC jsou členy `CDatabase` a fungují na úrovni databáze. Ve třídách rozhraní DAO jsou členské funkce transakce členy třídy vyšší úrovně (`CDaoWorkspace`), a proto mohou ovlivnit více `CDaoDatabase` objektů sdílející stejný pracovní prostor (místo transakce).

- Třída výjimky byla změněna. `CDBExceptions`jsou vyvolány ve třídách `CDaoExceptions` rozhraní ODBC a v třídách DAO.

- `RFX_Date`používá `CTime` objekty `TIMESTAMP_STRUCT` a při `DFX_Date` použití .`COleDateTime` Je téměř totožný s `CTime`, ale je založen na 8bitovém **datu** OLE, nikoli na 4 bajtové time_t, takže může obsahovat mnohem větší rozsah dat. `COleDateTime`

   > [!NOTE]
   > Snímky DAO`CDaoRecordset`() jsou jen pro čtení, zatímco snímky`CRecordset`ODBC () můžou být aktualizovatelné v závislosti na ovladači a použití knihovny kurzorů ODBC. Pokud používáte knihovnu kurzorů, můžete `CRecordset` snímky aktualizovat. Pokud používáte některý z ovladačů Microsoft z Desktop Driver Pack 3,0 bez knihovny kurzorů ODBC, `CRecordset` snímky jsou jen pro čtení. Pokud používáte jiný ovladač, podívejte se do dokumentace k ovladači a zjistěte, jestli jsou snímky`STATIC_CURSORS`() jen pro čtení.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
