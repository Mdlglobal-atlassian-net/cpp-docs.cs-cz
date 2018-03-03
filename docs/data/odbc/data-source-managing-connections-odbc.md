---
title: "Zdroj dat: Správa připojení (ODBC) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b83093496d355fdba8b5d714875d08040ae28ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="data-source-managing-connections-odbc"></a>Zdroj dat: Správa připojení (ODBC)
Toto téma se vztahuje na třídy knihovny MFC rozhraní ODBC.  
  
 Toto téma vysvětluje:  
  
-   [Postup konfigurace zdroje dat](#_core_configuring_a_data_source).  
  
-   [Jak ovlivňuje prostředí s více uživateli zdrojem dat a jeho sady záznamů](#_core_working_in_a_multiuser_environment).  
  
-   [Proč zobecnit řetězec připojení ke zdroji dat](#_core_generalizing_the_connection_string).  
  
-   [Jak se připojit ke zdroji dat](#_core_connecting_to_a_specific_data_source).  
  
-   [Jak se odpojit od zdroje dat](#_core_disconnecting_from_a_data_source).  
  
-   [Jak znovu použít objekt CDatabase](#_core_reusing_a_cdatabase_object).  
  
 Připojení ke zdroji dat znamená navazování komunikace s databázového systému pro přístup k datům. Při připojení ke zdroji dat z aplikace prostřednictvím ovladače ODBC ovladač navázalo připojení, místně nebo v síti.  
  
 Můžete připojit k libovolnému zdroji dat, pro které máte ovladače ODBC. Stejné ovladač ODBC pro jejich zdroje dat musí mít také uživatelů vaší aplikace. Další informace o redistribuci ovladačů ODBC najdete v tématu [Redistribuce součástí rozhraní ODBC vašim zákazníkům](../../data/odbc/redistributing-odbc-components-to-your-customers.md).  
  
##  <a name="_core_configuring_a_data_source"></a>Konfigurace zdroje dat  
 Správce rozhraní ODBC slouží ke konfiguraci zdroje dat. Můžete taky správce rozhraní ODBC po instalaci k přidání nebo odebrání datových zdrojů. Při vytváření aplikace, můžete nasměrovat uživatele pro správce rozhraní ODBC pro přidání zdroje dat nebo tuto funkci do své aplikace můžete vytvořit tak, že přímé volání rozhraní ODBC instalace. Další informace najdete v tématu [správce rozhraní ODBC](../../data/odbc/odbc-administrator.md).  
  
 Soubor aplikace Excel můžete použít jako zdroj dat a je nutné nakonfigurovat souboru tak, aby je zaregistrován a zobrazí se v **vybrat zdroj dat** dialogové okno.  
  
#### <a name="to-use-an-excel-file-as-a-data-source"></a>Chcete-li použít soubor aplikace Excel jako zdroj dat  
  
1.  Konfigurace souboru s správce zdrojů dat ODBC.  
  
2.  Na **souborové DSN** , klikněte na **přidat**.  
  
3.  V **vytvořit nový zdroj dat** dialogové okno, vyberte ovladač aplikace Excel a pak klikněte na tlačítko **Další**.  
  
4.  Klikněte na tlačítko **Procházet**a vyberte název souboru, který se použije jako zdroj.  
  
> [!NOTE]
>  Možná budete muset vybrat možnost **všechny soubory** v rozevírací nabídky k zobrazení souborů .xls.  
  
1.  Klikněte na tlačítko **Další**a potom klikněte na **Dokončit**.  
  
2.  V **nastavení rozhraní ODBC Microsoft Excel** dialogovém okně vyberte verzi a databáze sešitu.  
  
##  <a name="_core_working_in_a_multiuser_environment"></a>Práce v prostředí s více uživateli  
 Pokud více uživatelů připojení ke zdroji dat, data můžou změnit při manipulaci se ve vaší sady záznamů. Podobně změny může ovlivnit sady záznamů jiných uživatelů. Další informace najdete v tématu [sada záznamů: Jak sady záznamů aktualizace záznamů (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md) a [transakce (ODBC)](../../data/odbc/transaction-odbc.md).  
  
##  <a name="_core_generalizing_the_connection_string"></a>Zobecňování připojovacího řetězce  
 Průvodce použijte k navázání připojení ke zdroji dat výchozí připojovací řetězec. Toto připojení slouží k zobrazení tabulky a sloupce při vývoji aplikace. Tento výchozí připojovací řetězec však nemusí být vhodné pro vaši uživatelé připojení ke zdroji dat prostřednictvím vaší aplikace. Pro zdroje dat a cestu k umístění, kde může být například liší od verze použité při vývoji aplikace. V takovém případě by měl přeimplementovat [CRecordset::GetDefaultConnect](../../mfc/reference/crecordset-class.md#getdefaultconnect) člen funkce více obecné podoby a odstranit implementaci průvodcem. Například použijte jednu z následujících postupů:  
  
-   Registrovat a spravovat připojovací řetězce, pomocí Správce rozhraní ODBC.  
  
-   Upravit připojovací řetězec a název zdroje dat odeberte. Poskytuje rozhraní ODBC jako zdroj dat; v době běhu ODBC zobrazí dialogové okno s dotazem pro názvem a všechny ostatní požadované připojení zdroje dat.  
  
-   Zadejte název zdroje dat pouze. Rozhraní ODBC požádá o ID uživatele a heslo, pokud je to nutné. Před generalizací, například připojovací řetězec vypadat třeba takto:  
  
    ```  
    CString CApp1Set::GetDefaultConnect()  
    {  
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";  
    }  
    ```  
  
     Tento připojovací řetězec určuje důvěryhodné připojení, která používá integrované zabezpečení Windows NT. Neměli byste, nezakódovávejte heslo nebo zadáte prázdné heslo, protože tím vytvoří slabá místa zabezpečení hlavní. Místo toho můžete poskytnout `GetDefaultConnect` nový připojovací řetězec tak, že požádá o ID uživatele a heslo.  
  
    ```  
    // User must select data source and supply user ID and password:  
        return "ODBC;";  
    // User ID and password required:  
        return "ODBC;DSN=mydb;";  
    // Password required (myuserid must be replaced with a valid user ID):  
        return "ODBC;DSN=mydb;UID=myuserid;";  
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):  
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";  
    ```  
  
##  <a name="_core_connecting_to_a_specific_data_source"></a>Připojování ke konkrétní zdroj dat.  
 Pro připojení ke zdroji konkrétní data, zdroje dat musí již být nakonfigurován se [správce rozhraní ODBC](../../data/odbc/odbc-administrator.md).  
  
#### <a name="to-connect-to-a-specific-data-source"></a>Pro připojení k konkrétní zdroj dat.  
  
1.  Vytvořit `CDatabase` objektu.  
  
2.  Volání jeho `OpenEx` nebo **otevřete** – členská funkce.  
  
 Další informace o tom, jak zadat zdroj dat, pokud je jiný než ten, který jste zadali pomocí průvodce najdete v tématu [CDatabase::OpenEx](../../mfc/reference/cdatabase-class.md#openex) nebo [CDatabase::Open](../../mfc/reference/cdatabase-class.md#open) v *MFC Referenční dokumentace*.  
  
##  <a name="_core_disconnecting_from_a_data_source"></a>Odpojení od zdroje dat  
 Je nutné zavřít všechny otevřené sady záznamů před voláním **zavřete** členské funkce `CDatabase`. V sadách záznamů přidružené `CDatabase` objektu, kterou chcete zavřít, všechny čekající `AddNew` nebo **upravit** došlo ke zrušení příkazů a všechny čekající transakce jsou vráceny zpět.  
  
#### <a name="to-disconnect-from-a-data-source"></a>Odpojení od zdroje dat  
  
1.  Volání `CDatabase` objektu [Zavřít](../../mfc/reference/cdatabase-class.md#close) – členská funkce.  
  
2.  Objekt zrušte, pokud chcete znovu použít.  
  
##  <a name="_core_reusing_a_cdatabase_object"></a>Opětovné použití objektu CDatabase  
 Můžete opakovaně použít `CDatabase` objektu po odpojení od toho, zda používat se připojit ke stejnému zdroji dat nebo se připojit k jinému zdroji dat.  
  
#### <a name="to-reuse-a-cdatabase-object"></a>Chcete-li znovu použít objekt CDatabase  
  
1.  Zavřete původní připojení k objektu.  
  
2.  Namísto zničení objektu volat jeho `OpenEx` nebo **otevřete** – členská funkce znovu.  
  
## <a name="see-also"></a>Viz také  
 [Zdroj dat (ODBC)](../../data/odbc/data-source-odbc.md)   
 [Zdroj dat: Stanovení schématu zdroje dat (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)   
 [CRecordset – třída](../../mfc/reference/crecordset-class.md)