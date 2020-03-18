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
ms.openlocfilehash: 38f0f383256a05c983fb7e7d7a498e16881c7b78
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446953"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Zdroj dat: Programové nakonfigurování zdroje dat ODBC

Toto téma vysvětluje, jak můžete programově nakonfigurovat názvy zdrojů dat rozhraní ODBC (Open Database Connectivity). Díky tomu získáte flexibilitu při přístupu k datům bez vynucení explicitního použití Správce rozhraní ODBC nebo jiných programů k určení názvů zdrojů dat.

Uživatel obvykle spouští správce rozhraní ODBC, aby vytvořil zdroj dat, pokud příslušný systém správy databáze (DBMS) tuto operaci podporuje.

Při vytváření zdroje dat ODBC Microsoft Access přes Správce rozhraní ODBC máte dvě možnosti: můžete vybrat existující soubor. mdb nebo můžete vytvořit nový soubor. mdb. Neexistuje žádný programový způsob vytvoření souboru. mdb z aplikace MFC ODBC. Proto pokud vaše aplikace vyžaduje, abyste umístili data do zdroje dat Microsoft Access (soubor. mdb), pravděpodobně budete chtít mít prázdný soubor. mdb, který můžete použít nebo zkopírovat vždy, když ho potřebujete.

Mnoho systémů DBMS však umožňuje programové vytvoření zdroje dat. Některé zdroje dat udržují specifikace adresáře pro databáze. To znamená, že adresář je zdroj dat a každá tabulka v rámci zdroje dat je uložena v samostatném souboru (v případě programu dBASE je každá tabulka soubor. dbf). Ovladače pro jiné databáze ODBC, jako je například Microsoft Access a SQL Server, vyžadují, aby před vytvořením zdroje dat byla splněna některá konkrétní kritéria. Například při použití ovladače SQL Server ODBC musíte navázat SQL Server počítač.

##  <a name="_core_sqlconfigdatasource_example"></a>Příklad SQLConfigDataSource

Následující příklad používá funkci `::SQLConfigDataSource` rozhraní ODBC API k vytvoření nového zdroje dat aplikace Excel s názvem nový zdroj dat aplikace Excel:

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

Všimněte si, že zdroj dat je ve skutečnosti adresář (C:\EXCELDIR); Tento adresář musí existovat. Ovladač aplikace Excel používá adresáře jako své zdroje dat a soubory jako jednotlivé tabulky (jedna tabulka na soubor. xls).

Další informace o vytváření tabulek najdete v tématu [zdroj dat: Programové vytvoření tabulky ve zdroji dat ODBC](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).

Následující informace popisuje parametry, které je třeba předat `::SQLConfigDataSource` funkci rozhraní API ODBC. Chcete-li použít `::SQLConfigDataSource`, je nutné zahrnout hlavičkový soubor Odbcinst. h a použít knihovnu importu Odbcinst. lib. Kromě toho musí být Odbccp32. dll v cestě v době běhu (nebo Odbcinst. dll pro 16 bitů).

Název zdroje dat ODBC můžete vytvořit pomocí Správce rozhraní ODBC nebo podobného nástroje. Někdy je však žádoucí vytvořit název zdroje dat přímo z vaší aplikace a získat tak přístup, aniž by uživatel musel spustit samostatný nástroj.

Správce rozhraní ODBC (obvykle nainstalovaný v Ovládacích panelech) vytvoří nový zdroj dat vložením položek do registru systému Windows (nebo pro 16 bitů v souboru ODBC. ini). Správce ovladačů rozhraní ODBC dotazuje tento soubor, aby získal požadované informace o zdroji dat. Je důležité zjistit, jaké informace musí být umístěny v registru, protože je třeba ji dodat voláním `::SQLConfigDataSource`.

I když tyto informace mohou být zapsány přímo do registru bez použití `::SQLConfigDataSource`, bude se žádná aplikace, která to dělá, spoléhat na aktuální techniku, kterou správce ovladačů používá k údržbě svých dat. Pokud pozdější revize správce ovladačů ODBC implementuje uchovávání záznamů o datových zdrojích jiným způsobem, všechny aplikace používající tuto techniku jsou poškozené. Je obecně vhodné použít funkci rozhraní API, pokud je k dispozici. Například váš kód je přenosný z 16 bitů na 32 bit, pokud použijete funkci `::SQLConfigDataSource`, protože funkce správně zapisuje do souboru ODBC. ini nebo do registru.

##  <a name="_core_sqlconfigdatasource_parameters"></a>Parametry SQLConfigDataSource

V následující části jsou vysvětleny parametry funkce `::SQLConfigDataSource`. Většina těchto informací je poskytována z *odkazu programátora* rozhraní ODBC dodaných v C++ jazyce Visual verze 1,5 a novějším.

###  <a name="_core_function_prototype"></a>Prototyp funkce

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Poznámky

####  <a name="_core_parameters_and_usage"></a>Parametry a použití

*hwndParent*<br/>
Okno zadané jako vlastník všech dialogových oken, které buď vytvoří Správce ovladačů ODBC, nebo konkrétní ovladač ODBC, aby od uživatele získal další informace o novém zdroji dat. Pokud parametr *lpszAttributes* neposkytuje dostatek informací, zobrazí se dialogové okno. Parametr *hwndParent* může mít hodnotu null.

*lpszDriver*<br/>
Popis ovladače. Toto je název, který se zobrazí uživatelům, nikoli fyzickému názvu ovladače (knihovny DLL).

*lpszAttributes*<br/>
Seznam atributů ve formátu "KeyName = hodnota". Tyto řetězce jsou odděleny prázdným znakem null se dvěma po sobě jdoucími nulami zakončenými na konci seznamu. Tyto atributy jsou primárně výchozími položkami konkrétního ovladače, které přejdou do registru nového zdroje dat. Jeden důležitý klíč, který není uveden v referenčních informacích k rozhraní ODBC API pro tuto funkci, je "DSN" ("název zdroje dat"), který určuje název nového zdroje dat. Zbývající položky jsou specifické pro ovladač nového zdroje dat. Často není nutné zadávat všechny položky, protože ovladač může vyzvat uživatele k zadání nových hodnot do dialogových oken. (Nastavte *hwndParent* na null, aby to způsobilo.) Je možné, že budete chtít explicitně poskytovat výchozí hodnoty, aby se uživateli nezobrazovala výzva.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Určení popisu ovladače pro parametr lpszDriver pomocí Správce rozhraní ODBC

1. Spusťte Správce rozhraní ODBC.

1. Klikněte na **Přidat**.

Získáte tak seznam nainstalovaných ovladačů a jejich popisů. Jako parametr *lpszDriver* použijte tento popis. Všimněte si, že používáte celý popis, jako je například "Souborů aplikace Excel (*.XLS)", včetně příponu názvu souboru a kulaté závorky, pokud existují v popisu.

Alternativně můžete ověřit registr (nebo pro 16 bitů soubor Odbcinst. ini), který obsahuje seznam všech záznamů a popisů ovladačů pod klíčem registru "ovladače ODBC" (nebo oddíl [ovladače ODBC] v souboru Odbcinst. ini).

Jedním ze způsobů, jak najít názvy a hodnoty pro parametr *lpszAttributes* , je prozkoumávat soubor ODBC. ini pro již nakonfigurovaný zdroj dat (třeba ten, který byl nakonfigurován správcem rozhraní ODBC).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Vyhledání názvů a hodnot a hodnot pro parametr lpszAttributes

1. Spusťte Editor registru systému Windows (nebo pro 16 bitů otevřete soubor ODBC. ini).

1. Vyhledejte informace o zdrojích dat ODBC pomocí jednoho z následujících postupů:

   - Pro 32 bit najděte klíč **HKEY_CURRENT_USER \software\odbc\odbc. INI\ODBC zdroje dat** v levém podokně.

      V pravém podokně jsou uvedeny položky formuláře: "pub: REG_SZ: *\<název zdroje dat >* ", kde *\<název zdroje dat >* je zdroj dat, který již byl nakonfigurován s požadovaným nastavením ovladače, který chcete použít. Vyberte zdroj dat, který chcete, například SQL Server. Položky, které následují za řetězcem "pub:", jsou v pořadí, hodnoty KeyName a Value, které mají být použity v parametru *lpszAttributes* .

   - U 16 bitů najděte část v souboru ODBC. ini označený jako [ *\<název zdroje dat >* ].

      Řádky následující po tomto řádku jsou ve formátu "KeyName = hodnota". Toto jsou přesně ty položky, které se mají použít ve vašem parametru *lpszAttributes* .

Můžete také prostudovat dokumentaci pro konkrétní ovladač, který budete používat. Užitečné informace najdete v online nápovědě k ovladači, ke kterému máte přístup spuštěním Správce rozhraní ODBC. Tyto soubory jsou obvykle umístěny v adresáři WINDOWS\SYSTEM pro systémy Windows NT, Windows 3,1 nebo Windows 95.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Získání online nápovědu pro ovladač ODBC

1. Spusťte Správce rozhraní ODBC.

1. Klikněte na **Přidat**.

1. Vyberte název ovladače.

1. Klikněte na tlačítko **OK**.

Když správce rozhraní ODBC zobrazí informace pro vytvoření nového zdroje dat pro tento konkrétní ovladač, klikněte na tlačítko **help**. Tím se otevře soubor s nápovědu pro tento konkrétní ovladač, který obecně obsahuje důležité informace týkající se použití ovladače.

## <a name="see-also"></a>Viz také

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)
