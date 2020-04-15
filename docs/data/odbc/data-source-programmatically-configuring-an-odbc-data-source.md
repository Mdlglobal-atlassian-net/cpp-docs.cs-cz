---
title: 'Zdroj dat: Programové nakonfigurování zdroje dat ODBC'
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: ba0224d166795b34d636ace610265e115209e49c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81358864"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Zdroj dat: Programové nakonfigurování zdroje dat ODBC

Toto téma vysvětluje, jak můžete programově konfigurovat názvy zdrojů dat připojení k otevřené databázi (ODBC). To poskytuje flexibilitu při přístupu k datům bez vynucení uživatele explicitně použít správce ODBC nebo jiné programy k určení názvů zdrojů dat.

Uživatel obvykle spustí správce rozhraní ODBC a vytvoří zdroj dat, pokud přidružený systém správy databáze (DBMS) tuto operaci podporuje.

Při vytváření zdroje dat ODBC aplikace Microsoft Access prostřednictvím správce rozhraní ODBC máte dvě možnosti: můžete vybrat existující soubor MDB nebo vytvořit nový soubor MDB. Neexistuje žádný programový způsob vytváření souboru MDB z aplikace MFC ODBC. Pokud tedy aplikace vyžaduje umístění dat do zdroje dat aplikace Microsoft Access (soubor MDB), budete s největší pravděpodobností chtít mít prázdný soubor MDB, který můžete použít nebo zkopírovat, kdykoli jej budete potřebovat.

Mnoho DBMS však umožňuje vytváření programových zdrojů dat. Některé zdroje dat udržují specifikaci adresáře pro databáze. To znamená, že adresář je zdroj dat a každá tabulka v rámci zdroje dat je uložena v samostatném souboru (v případě dBASE je každá tabulka souborem .dbf). Ovladače pro jiné databáze ODBC, jako je například Microsoft Access a SQL Server, vyžadují, aby byla před vytvořením zdroje dat splněna některá konkrétní kritéria. Například při použití ovladače SQL Server ODBC, musíte mít vytvořený počítač SQL Server.

## <a name="sqlconfigdatasource-example"></a><a name="_core_sqlconfigdatasource_example"></a>Příklad zdroje SQLConfigDataSource

Následující příklad používá `::SQLConfigDataSource` funkci ROZHRANÍ API ROZHRANÍ ODBC k vytvoření nového zdroje dat aplikace Excel nazvaného Nový zdroj dat aplikace Excel:

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

Všimněte si, že zdroj dat je ve skutečnosti adresář (C:\EXCELDIR); tento adresář musí existovat. Ovladač aplikace Excel používá adresáře jako zdroje dat a soubory jako jednotlivé tabulky (jedna tabulka na soubor XLS).

Další informace o vytváření tabulek naleznete v [tématu Zdroj dat: Programově vytvoření tabulky ve zdroji dat ODBC](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).

Následující informace popisují parametry, které je třeba `::SQLConfigDataSource` předat funkci ROZHRANÍ API ROZHRANÍ ODBC. Chcete-li použít `::SQLConfigDataSource`, musíte zahrnout soubor záhlaví Odbcinst.h a použít knihovnu importu Odbcinst.lib. Také Odbccp32.dll musí být v cestě za běhu (nebo Odbcinst.dll pro 16 bit).

Název zdroje dat ODBC můžete vytvořit pomocí správce rozhraní ODBC nebo podobného nástroje. Někdy je však žádoucí vytvořit název zdroje dat přímo z vaší aplikace získat přístup bez nutnosti uživatele spustit samostatný nástroj.

Správce rozhraní ODBC (obvykle nainstalovaný v Ovládacích panelech) vytvoří nový zdroj dat vložením položek do registru systému Windows (nebo u 16 bitů do souboru Odbc.ini). Správce ovladačů ROZHRANÍ ODBC dotazuje tento soubor, aby získal požadované informace o zdroji dat. Je důležité vědět, jaké informace je třeba umístit do registru, protože `::SQLConfigDataSource`je třeba zadat volání .

Přestože tyto informace mohou být zapsány přímo do registru bez použití `::SQLConfigDataSource`, všechny aplikace, které tak činí, se spoléhá na aktuální techniku, kterou Správce ovladačů používá k udržování svých dat. Pokud pozdější revize Správce ovladačů ODBC implementuje vedení záznamů o zdrojích dat jiným způsobem, jakákoli aplikace, která používá tuto techniku, je přerušena. Obecně je vhodné použít funkci rozhraní API, pokud je k dispozici. Například váš kód je přenosný od 16 bitů `::SQLConfigDataSource` do 32 bitů, pokud používáte funkci, protože funkce správně zapíše do souboru Odbc.ini nebo do registru.

## <a name="sqlconfigdatasource-parameters"></a><a name="_core_sqlconfigdatasource_parameters"></a>Parametry SQLConfigDataSource

Následující vysvětluje parametry `::SQLConfigDataSource` funkce. Velká část informací je převzata z *odkazu programátora ROZHRANÍ* API ROZHRANÍ ODBC, který je dodáván s visual c++ verze 1.5 a novější.

### <a name="function-prototype"></a><a name="_core_function_prototype"></a>Prototyp funkce

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Poznámky

#### <a name="parameters-and-usage"></a><a name="_core_parameters_and_usage"></a>Parametry a použití

*hwndParent*<br/>
Okno určené jako vlastník všech dialogových oken, které vytvoří Správce ovladačů ROZHRANÍ ODBC nebo konkrétní ovladač ODBC, aby získaly od uživatele další informace o novém zdroji dat. Pokud parametr *lpszAttributes* neposkytuje dostatek informací, zobrazí se dialogové okno. Parametr *hwndParent* může být NULL.

*lpszDriver*<br/>
Popis ovladače. Toto je název prezentovaný uživatelům spíše než název fyzického ovladače (DLL).

*lpszAtributy*<br/>
Seznam atributů ve tvaru "keyname=value". Tyto řetězce jsou odděleny null zakončení se dvěma po sobě jdoucími zakončeními null na konci seznamu. Tyto atributy jsou především výchozí položky specifické pro ovladač, které přejdou do registru pro nový zdroj dat. Jeden důležitý klíč, který není uveden v odkazu rozhraní API ROZHRANÍ ODBC pro tuto funkci je "DSN" ("název zdroje dat"), který určuje název nového zdroje dat. Zbývající položky jsou specifické pro ovladač pro nový zdroj dat. Často není nutné zadat všechny položky, protože ovladač může vyzvat uživatele s dialogovými okny pro nové hodnoty. (Nastavte *hwndParent* na HODNOTU NULL, která to způsobí.) Můžete chtít explicitně zadat výchozí hodnoty, aby uživatel nebyl vyzván.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Určení popisu ovladače parametru lpszDriver pomocí správce rozhraní ODBC

1. Spusťte správce rozhraní ODBC.

1. Klikněte na **Přidat**.

Získáte tak seznam nainstalovaných ovladačů a jejich popisy. Tento popis použijte jako parametr *lpszDriver.* Všimněte si, že používáte celý popis, například "Soubory aplikace Excel (*.xls)", včetně přípony názvu souboru a závorek, pokud existují v popisu.

Alternativně můžete zkontrolovat registr (nebo pro 16 bit, soubor Odbcinst.ini), který obsahuje seznam všech položek ovladače a popisy pod klíčem registru "OVLADAČE ODBC" (nebo část [OVLADAČE ODBC] v Odbcinst.ini).

Jedním ze způsobů, jak najít názvy klíčů a hodnoty parametru *lpszAttributes,* je zkontrolovat soubor Odbc.ini pro již nakonfigurovaný zdroj dat (možná ten, který byl nakonfigurován správcem ODBC).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Vyhledání názvů klíčů a hodnot parametru lpszAttributes

1. Spusťte editor registru systému Windows (nebo u 16 bitů otevřete soubor Odbc.ini).

1. Informace o zdrojích dat rozhraní ODBC naleznete pomocí jedné z následujících možností:

   - Pro 32 bitů vyhledejte klíč **HKEY_CURRENT_USER\Software\ODBC\ODBC. Zdroje dat INI\ODBC** v levém podokně.

      V pravém podokně jsou uvedeny položky*\< *formuláře: "pub: REG_SZ: název zdroje dat>", kde * \<název zdroje dat>* je zdroj dat, který již byl nakonfigurován s požadovaným nastavením ovladače, který chcete použít. Vyberte požadovaný zdroj dat, například SQL Server. Položky následující za řetězcem "pub:" jsou v pořadí název klíče a hodnota, která má být v parametru *lpszAttributes.*

   - Pro 16 bitů vyhledejte oddíl v souboru Odbc.ini označeným*\<[název zdroje dat>*].

      Řádky za tímto řádkem jsou ve tvaru "keyname=value". Jedná se přesně o položky, které mají být v parametru *lpszAttributes používány.*

Můžete také zkontrolovat dokumentaci pro konkrétní ovladač, který budete používat. Užitečné informace naleznete v nápovědě k ovladači online, ke které máte přístup spuštěním správce rozhraní ODBC. Tyto soubory nápovědy jsou obvykle umístěny v adresáři WINDOWS\SYSTEM pro systémy Windows NT, Windows 3.1 nebo Windows 95.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Získání online nápovědy k ovladači ROZHRANÍ ODBC

1. Spusťte správce rozhraní ODBC.

1. Klikněte na **Přidat**.

1. Vyberte název ovladače.

1. Klikněte na tlačítko **OK**.

Pokud správce rozhraní ODBC zobrazí informace o vytvoření nového zdroje dat pro daný ovladač, klepněte na tlačítko **Nápověda**. Tím se otevře soubor nápovědy pro daný ovladač, který obvykle obsahuje důležité informace týkající se použití ovladače.

## <a name="see-also"></a>Viz také

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)
