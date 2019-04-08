---
title: 'Zdroj dat: Správa připojení (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], multiuser environments
- generalizing connection strings
- ODBC [C++], disconnecting from data sources
- connection strings [C++], generalizing
- database connections [C++], creating
- GetDefaultConnect method
- connections [C++], data source
- ODBC connections [C++], configuring
- disconnecting from data sources
- databases [C++], connecting to
- ODBC connections [C++], disconnecting
- data sources [C++], connecting to
- ODBC connections [C++], connecting to data source
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
ms.openlocfilehash: 5b646ca0eb86d3addabaad59ca23f56cfe914114
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041160"
---
# <a name="data-source-managing-connections-odbc"></a>Zdroj dat: Správa připojení (ODBC)

Toto téma platí pro třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje:

- [Konfigurace zdroje dat](#_core_configuring_a_data_source).

- [Jak ovlivňuje víceuživatelské prostředí zdroj dat a jeho sady záznamů](#_core_working_in_a_multiuser_environment).

- [Proč zobecnit připojovací řetězec pro zdroj dat](#_core_generalizing_the_connection_string).

- [Jak se připojit ke zdroji dat](#_core_connecting_to_a_specific_data_source).

- [Jak se odpojit od zdroje dat](#_core_disconnecting_from_a_data_source).

- [Postup opětovné použití objektu CDatabase](#_core_reusing_a_cdatabase_object).

Připojení ke zdroji dat znamená navázání komunikací se systémem DBMS pro přístup k datům. Když se připojíte ke zdroji dat z aplikace prostřednictvím ovladače rozhraní ODBC, ovladač díky spojení za vás, místně nebo v síti.

Můžete připojit k libovolnému zdroji dat, pro který máte ovladač rozhraní ODBC. Uživatelům vaší aplikace musí mít také stejný ovladač rozhraní ODBC pro svůj zdroj dat. Další informace o redistribuci ovladačů rozhraní ODBC naleznete v tématu [Redistribuce součástí rozhraní ODBC vašim zákazníkům](../../data/odbc/redistributing-odbc-components-to-your-customers.md).

##  <a name="_core_configuring_a_data_source"></a> Konfigurace zdroje dat

Správce rozhraní ODBC se používá ke konfiguraci zdroje dat. Správce rozhraní ODBC můžete také použít po instalaci k přidání nebo odebrání zdroje dat. Při vytváření aplikací můžete nasměrovat uživatele na správce rozhraní ODBC a umožnit jim přidat zdroje dat nebo můžete začlenit tuto funkcionalitu do aplikace vytvořením přímého volání instalace rozhraní ODBC. Další informace najdete v tématu [správce rozhraní ODBC](../../data/odbc/odbc-administrator.md).

Soubor aplikace Excel můžete použít jako zdroj dat a je potřeba nakonfigurovat soubor tak, aby byl zaregistrován a zobrazí se v **vybrat zdroj dat** dialogové okno.

#### <a name="to-use-an-excel-file-as-a-data-source"></a>Chcete-li použít soubor aplikace Excel jako zdroj dat

1. Nakonfigurujte soubor pomocí Správce zdrojů dat ODBC.

1. Na **DSN souboru** klikněte na tlačítko **přidat**.

1. V **vytvořit nový zdroj dat** dialogovém okně vyberte ovladač aplikace Excel a potom klikněte na tlačítko **Další**.

1. Klikněte na tlačítko **Procházet**a vyberte název souboru, který se použije jako zdroj.

> [!NOTE]
>  Musíte vybrat **všechny soubory** v rozevírací nabídce pro zobrazení .xls souborů.

1. Klikněte na tlačítko **Další**a potom klikněte na tlačítko **Dokončit**.

1. V **nastavení rozhraní ODBC Microsoft Excel** dialogového okna, vyberte verzi a sešit databáze.

##  <a name="_core_working_in_a_multiuser_environment"></a> Práce ve víceuživatelském prostředí

Pokud více uživatelů připojeno ke zdroji dat, mohou změnit data, zatímco manipulujete v sadě záznamů. Podobně mohou změny ovlivnit sady záznamů jiných uživatelů. Další informace najdete v tématu [sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) a [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="_core_generalizing_the_connection_string"></a> Zobecňování připojovacího řetězce

Průvodce používá výchozí propojovací řetězec k navázání připojení ke zdroji dat. Toto připojení použijete k zobrazení tabulky a sloupce, zatímco vyvíjíte aplikaci. Tento výchozí připojovací řetězec však nemusí být vhodný pro připojení vašich uživatelů ke zdroji dat prostřednictvím vaší aplikace. Například jejich zdroj dat a cesta k umístění může lišit od identifikátoru použitému při vývoji vaší aplikace. V takovém případě měli znovu implementovat [CRecordset::GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) členské funkce v obecnější podoby a odstranit implementaci průvodce. Například použijte jednu z následujících postupů:

- Registrace a správa připojovacích řetězců pomocí Správce rozhraní ODBC.

- Upravit připojovací řetězec a odeberte název datového zdroje. Architektura dodává rozhraní ODBC jako zdroj dat; v době běhu zobrazí dialogové okno s dotazem pro název a všechny ostatní požadované připojení zdroje dat rozhraní ODBC.

- Zadejte název zdroje dat pouze. Rozhraní ODBC požádá o ID uživatele a heslo, pokud je to nutné. Například před zobecněním připojovací řetězec vypadá takto:

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   Tento připojovací řetězec určuje důvěryhodné připojení, která používá Windows NT integrované zabezpečení. Měli byste se vyhnout pevně kódováno pomocí hesla nebo zadání prázdného hesla, protože se tím vytvoří slabým zabezpečením. Místo toho můžete poskytnout `GetDefaultConnect` nový připojovací řetězec tak, aby se dotázal na ID uživatele a heslo.

    ```cpp
    // User must select data source and supply user ID and password:
        return "ODBC;";
    // User ID and password required:
        return "ODBC;DSN=mydb;";
    // Password required (myuserid must be replaced with a valid user ID):
        return "ODBC;DSN=mydb;UID=myuserid;";
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";
    ```

##  <a name="_core_connecting_to_a_specific_data_source"></a> Připojení ke konkrétnímu zdroji dat

Pokud chcete připojit ke konkrétnímu zdroji dat, zdroji dat musí již být nakonfigurován se [správce rozhraní ODBC](../../data/odbc/odbc-administrator.md).

#### <a name="to-connect-to-a-specific-data-source"></a>K připojení ke konkrétnímu zdroji dat

1. Vytvoření `CDatabase` objektu.

1. Volat jeho `OpenEx` nebo `Open` členskou funkci.

Další informace o způsobu určení zdroje dat, pokud je jiný než ten, který jste zadali pomocí průvodce najdete v tématu [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) v *knihovny MFC Referenční dokumentace*.

##  <a name="_core_disconnecting_from_a_data_source"></a> Odpojení od zdroje dat

Je nutné zavřít všechny otevřené sady záznamů před zavoláním funkce `Close` členskou funkci `CDatabase`. V přidružené sadě záznamů s `CDatabase` objektu, kterou chcete zavřít všechny čekající `AddNew` nebo `Edit` zrušení příkazů a všechny čekající transakce jsou vrácena zpět.

#### <a name="to-disconnect-from-a-data-source"></a>Odpojení od zdroje dat

1. Volání `CDatabase` objektu [Zavřít](../../mfc/reference/cdatabase-class.md#close) členskou funkci.

1. Zničte objekt, pokud chcete znovu použít.

##  <a name="_core_reusing_a_cdatabase_object"></a> Opětovné použití objektu CDatabase

Můžete opakovaně použít `CDatabase` objektu po odpojení od ho, ať už používáte ho chcete znovu připojit ke stejnému zdroji dat nebo se připojit k jinému zdroji dat.

#### <a name="to-reuse-a-cdatabase-object"></a>Pro opětovné použití objektu CDatabase

1. Ukončete původní připojení objektu.

1. Namísto zničení objektu zavolejte jeho `OpenEx` nebo `Open` členskou funkci znovu.

## <a name="see-also"></a>Viz také:

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Zdroj dat: Stanovení schématu zdroje dat (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)