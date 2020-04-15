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
ms.openlocfilehash: 107a5e20b70f67be74b6e6f861bd539446e9d4ee
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374534"
---
# <a name="data-source-managing-connections-odbc"></a>Zdroj dat: Správa připojení (ODBC)

Toto téma se vztahuje na třídy Knihovny MFC ODBC.

Toto téma vysvětluje:

- [Konfigurace zdroje dat](#_core_configuring_a_data_source).

- [Vliv víceuživatelského prostředí na zdroj dat a jeho sady záznamů](#_core_working_in_a_multiuser_environment).

- [Proč zobecňte připojovací řetězec ke zdroji dat](#_core_generalizing_the_connection_string).

- [Jak se připojit ke zdroji dat](#_core_connecting_to_a_specific_data_source).

- [Jak se odpojit od zdroje dat](#_core_disconnecting_from_a_data_source).

- [Opětovné použití objektu CDatabase](#_core_reusing_a_cdatabase_object).

Připojení ke zdroji dat znamená navázání komunikace s DBMS pro přístup k datům. Když se připojíte ke zdroji dat z aplikace prostřednictvím ovladače ODBC, ovladač vytvoří připojení za vás, místně nebo v síti.

Můžete se připojit k libovolnému zdroji dat, pro který máte ovladač ODBC. Uživatelé aplikace musí mít také stejný ovladač ROZHRANÍ ODBC pro svůj zdroj dat. Další informace o redistribuci ovladačů ROZHRANÍ ODBC naleznete [v tématu Redistributing ODBC Components to Your Customers](../../data/odbc/redistributing-odbc-components-to-your-customers.md).

## <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>Konfigurace zdroje dat

Správce rozhraní ODBC slouží ke konfiguraci zdrojů dat. K přidání nebo odebrání zdrojů dat můžete také použít správce rozhraní ODBC po instalaci. Při vytváření aplikací můžete uživatele buď nasměrovat na správce rozhraní ODBC, aby mohli přidávat zdroje dat, nebo můžete tuto funkci do aplikace vytvořit přímými instalačními hovory rozhraní ODBC. Další informace naleznete v tématu [SPRÁVCE ODBC](../../data/odbc/odbc-administrator.md).

Jako zdroj dat můžete použít soubor aplikace Excel a je třeba jej nakonfigurovat tak, aby byl zaregistrován a zobrazil se v dialogovém okně **Vybrat zdroj dat.**

#### <a name="to-use-an-excel-file-as-a-data-source"></a>Použití excelového souboru jako zdroje dat

1. Nakonfigurujte soubor pomocí správce zdroje dat ROZHRANÍ ODBC.

1. Na kartě **Soubor DSN** klepněte na tlačítko **Přidat**.

1. V dialogovém okně **Vytvořit nový zdroj dat** vyberte ovladač aplikace Excel a klepněte na tlačítko **Další**.

1. Klepněte na **tlačítko Procházet**a vyberte název souboru, který má být použit jako zdroj data.

> [!NOTE]
> Chcete-li zobrazit soubory XLS, může být nutné vybrat možnost **Všechny soubory** v rozevírací nabídce.

1. Klikněte na **Další** a pak klikněte na **Dokončit**.

1. V dialogovém okně **Instalace aplikace OdBC microsoft excel** vyberte databázi Verze a sešit.

## <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>Práce ve víceuživatelském prostředí

Pokud je ke zdroji dat připojeno více uživatelů, mohou měnit data, když s nimi manipulujete v sadách záznamů. Podobně změny mohou ovlivnit sady záznamů jiných uživatelů. Další informace naleznete v [tématu Recordset: How Recordsets Update Records (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) and [Transaction (ODBC)](../../data/odbc/transaction-odbc.md).

## <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>Zobecnění připojovacího řetězce

Průvodci používají k navázání připojení ke zdroji dat výchozí připojovací řetězec. Toto připojení slouží k zobrazení tabulek a sloupců při vývoji aplikace. Tento výchozí připojovací řetězec však nemusí být vhodný pro připojení uživatelů ke zdroji dat prostřednictvím aplikace. Například jejich zdroj dat a cesta k jeho umístění se mohou lišit od zdroje používaného při vývoji aplikace. V takovém případě byste měli znovu implementovat člennou funkci [CRecordset::GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) obecněji a zahodit implementaci průvodce. Použijte například jeden z následujících přístupů:

- Zaregistrujte a spravujte připojovací řetězce pomocí správce rozhraní ODBC.

- Upravte připojovací řetězec a odeberte název zdroje dat. Rozhraní Framework poskytuje rozhraní ODBC jako zdroj dat. Za běhu zobrazí rozhraní ODBC dialogové okno s žádostí o název zdroje dat a další požadované informace o připojení.

- Zařazuje pouze název zdroje dat. Rozhraní ODBC v případě potřeby požádá o ID uživatele a heslo. Například před generalizací vypadá připojovací řetězec takto:

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   Tento připojovací řetězec určuje důvěryhodné připojení, které používá integrované zabezpečení systému Windows NT. Měli byste se vyhnout pevnému kódování hesla nebo zadání prázdného hesla, protože tím vytváříte hlavní slabinu zabezpečení. Místo toho můžete `GetDefaultConnect` zadat nový připojovací řetězec tak, aby dotazy pro ID uživatele a heslo.

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

## <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>Připojení k určitému zdroji dat

Chcete-li se připojit ke konkrétnímu zdroji dat, musí být zdroj dat již nakonfigurován správcem [rozhraní ODBC](../../data/odbc/odbc-administrator.md).

#### <a name="to-connect-to-a-specific-data-source"></a>Připojení k určitému zdroji dat

1. Vytvořte `CDatabase` objekt.

1. Volání `OpenEx` jeho `Open` nebo členské funkce.

Další informace o tom, jak určit zdroj dat, pokud se jedná o něco jiného než ten, který jste zadali průvodcem, naleznete v [tématu CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) in the *MFC Reference*.

## <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>Odpojení od zdroje dat

Před voláním `Close` členské funkce aplikace `CDatabase`je nutné zavřít všechny otevřené sady záznamů. V sadách záznamů `CDatabase` přidružených k objektu, `Edit` který chcete zavřít, jsou všechny čekající nebo `AddNew` příkazy zrušeny a všechny čekající transakce jsou vráceny zpět.

#### <a name="to-disconnect-from-a-data-source"></a>Odpojení od zdroje dat

1. Volání `CDatabase` člena objektu [Close.](../../mfc/reference/cdatabase-class.md#close)

1. Zničte objekt, pokud jej nechcete znovu použít.

## <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>Opětovné použití objektu CDatabase

`CDatabase` Objekt můžete znovu použít po odpojení od něj, ať už jej použijete k opětovnému připojení ke stejnému zdroji dat nebo k připojení k jinému zdroji dat.

#### <a name="to-reuse-a-cdatabase-object"></a>Opětovné použití objektu CDatabase

1. Zavřete původní připojení objektu.

1. Namísto zničení objektu, `OpenEx` volání `Open` jeho nebo členské funkce znovu.

## <a name="see-also"></a>Viz také

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Zdroj dat: Stanovení schématu zdroje dat (rozhraní ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
