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
ms.openlocfilehash: 6186199ea51c1fc966783ed3c0a73496c6a307ee
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213289"
---
# <a name="data-source-managing-connections-odbc"></a>Zdroj dat: Správa připojení (ODBC)

Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.

Toto téma vysvětluje:

- [Jak nakonfigurovat zdroj dat](#_core_configuring_a_data_source)

- [Jak víceuživatelské prostředí ovlivňuje zdroj dat a jeho sady záznamů](#_core_working_in_a_multiuser_environment).

- [Proč zobecnit připojovací řetězec ke zdroji dat](#_core_generalizing_the_connection_string).

- [Jak se připojit ke zdroji dat](#_core_connecting_to_a_specific_data_source).

- [Odpojení od zdroje dat](#_core_disconnecting_from_a_data_source).

- [Způsob opětovného použití objektu CDatabase](#_core_reusing_a_cdatabase_object).

Připojení ke zdroji dat znamená, že se pro přístup k datům navazování komunikace s DBMS. Když se připojíte ke zdroji dat z aplikace prostřednictvím ovladače ODBC, ovladač vám navede připojení, a to buď místně, nebo přes síť.

Můžete se připojit k libovolnému zdroji dat, pro který máte ovladač ODBC. Uživatelé vaší aplikace musí mít také stejný ovladač ODBC pro svůj zdroj dat. Další informace o redistribuci ovladačů rozhraní ODBC najdete v tématu [Redistribuce součástí rozhraní ODBC vašim zákazníkům](../../data/odbc/redistributing-odbc-components-to-your-customers.md).

##  <a name="configuring-a-data-source"></a><a name="_core_configuring_a_data_source"></a>Konfigurace zdroje dat

Správce rozhraní ODBC se používá ke konfiguraci zdrojů dat. Po instalaci můžete také použít Správce rozhraní ODBC a přidat nebo odebrat zdroje dat. Když vytváříte aplikace, můžete uživatele buď nasměrovat na správce rozhraní ODBC, aby mohli přidávat zdroje dat, nebo můžete tuto funkci vytvořit do své aplikace tím, že vytvoříte přímé volání instalace rozhraní ODBC. Další informace najdete v tématu [Správce rozhraní ODBC](../../data/odbc/odbc-administrator.md).

Můžete použít excelový soubor jako zdroj dat a musíte ho nakonfigurovat tak, aby byl zaregistrovaný a zobrazený v dialogovém okně **Vybrat zdroj dat** .

#### <a name="to-use-an-excel-file-as-a-data-source"></a>Použití excelového souboru jako zdroje dat

1. Nakonfigurujte soubor pomocí Správce zdrojů dat ODBC.

1. Na kartě **SOUBOROVÉ DSN** klikněte na **Přidat**.

1. V dialogovém okně **vytvořit nový zdroj dat** vyberte ovladač aplikace Excel a potom klikněte na tlačítko **Další**.

1. Klikněte na **Procházet**a vyberte název souboru, který se má použít jako zdroj dat.

> [!NOTE]
>  Je možné, že v rozevírací nabídce budete muset vybrat **všechny soubory** , aby se zobrazily soubory. xls.

1. Klikněte na **Další**a potom na **Dokončit**.

1. V dialogovém okně **Nastavení ODBC pro Microsoft Excel** vyberte verzi databáze a sešit.

##  <a name="working-in-a-multiuser-environment"></a><a name="_core_working_in_a_multiuser_environment"></a>Práce ve víceuživatelském prostředí

Pokud je k datovému zdroji připojeno více uživatelů, může změnit data při manipulaci s nimi ve vašich sadách záznamů. Podobně mohou vaše změny ovlivnit sady záznamů jiných uživatelů. Další informace naleznete v tématu [Sada záznamů: Jak sady záznamů aktualizují záznamy (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) a [transakce (ODBC)](../../data/odbc/transaction-odbc.md).

##  <a name="generalizing-the-connection-string"></a><a name="_core_generalizing_the_connection_string"></a>Generalizace připojovacího řetězce

K navázání připojení ke zdroji dat používají průvodci výchozí připojovací řetězec. Pomocí tohoto připojení můžete zobrazit tabulky a sloupce při vývoji aplikace. Tento výchozí připojovací řetězec ale nemusí být vhodný pro připojení vašich uživatelů ke zdroji dat prostřednictvím vaší aplikace. Například zdroj dat a cesta k jeho umístění se mohou lišit od toho, který se používá při vývoji aplikace. V takovém případě byste měli znovu implementovat členskou funkci [CRecordset:: GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) v obecnější podobě a zahodit implementaci průvodce. Použijte například jeden z následujících přístupů:

- Zaregistrujte a spravujte připojovací řetězce pomocí Správce rozhraní ODBC.

- Upravte připojovací řetězec a odeberte název zdroje dat. Rozhraní dodává rozhraní ODBC jako zdroj dat; v době běhu zobrazí ODBC dialogové okno s výzvou k zadání názvu zdroje dat a dalších požadovaných informací o připojení.

- Zadejte pouze název zdroje dat. Rozhraní ODBC požádá o ID uživatele a heslo, pokud je to nutné. Například před generalizací vypadá připojovací řetězec takto:

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   Tento připojovací řetězec Určuje důvěryhodné připojení, které používá integrované zabezpečení systému Windows NT. Měli byste se vyhnout hardwarovému kódování hesla nebo zadání prázdného hesla, protože tím dojde k vytvoření závažného slabého zabezpečení. Místo toho můžete dát `GetDefaultConnect` nový připojovací řetězec, aby se dotazoval na ID uživatele a heslo.

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

##  <a name="connecting-to-a-specific-data-source"></a><a name="_core_connecting_to_a_specific_data_source"></a>Připojení ke konkrétnímu zdroji dat

Aby bylo možné se připojit ke konkrétnímu zdroji dat, musí být váš zdroj dat již nakonfigurován se [správcem rozhraní ODBC](../../data/odbc/odbc-administrator.md).

#### <a name="to-connect-to-a-specific-data-source"></a>Připojení ke konkrétnímu zdroji dat

1. Sestavte objekt `CDatabase`.

1. Zavolejte jeho `OpenEx` nebo členskou funkci `Open`.

Další informace o tom, jak určit zdroj dat, pokud je jiný než ten, který jste zadali pomocí průvodce, naleznete v tématu [CDatabase:: OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [CDatabase:: Open](../../mfc/reference/cdatabase-class.md#open) v *Referenci knihovny MFC*.

##  <a name="disconnecting-from-a-data-source"></a><a name="_core_disconnecting_from_a_data_source"></a>Odpojení od zdroje dat

Před voláním členské funkce `Close` `CDatabase`je nutné zavřít všechny otevřené sady záznamů. V sadách záznamů přidružených k objektu `CDatabase`, který chcete zavřít, jsou zrušeny všechny probíhající příkazy `AddNew` nebo `Edit` a všechny probíhající transakce jsou vráceny zpět.

#### <a name="to-disconnect-from-a-data-source"></a>Odpojení od zdroje dat

1. Zavolejte členskou funkci [Close](../../mfc/reference/cdatabase-class.md#close) objektu `CDatabase`.

1. Zničit objekt, pokud jej nechcete znovu použít.

##  <a name="reusing-a-cdatabase-object"></a><a name="_core_reusing_a_cdatabase_object"></a>Znovu použití objektu CDatabase

`CDatabase` objekt můžete znovu použít po odpojení od něj, ať už ho použijete pro opětovné připojení ke stejnému zdroji dat nebo k připojení k jinému zdroji dat.

#### <a name="to-reuse-a-cdatabase-object"></a>Opětovné použití objektu CDatabase

1. Zavřete původní připojení objektu.

1. Místo zničení objektu volejte znovu jeho `OpenEx` nebo `Open` členskou funkci.

## <a name="see-also"></a>Viz také

[Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[Zdroj dat: Stanovení schématu zdroje dat (rozhraní ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset – třída](../../mfc/reference/crecordset-class.md)
