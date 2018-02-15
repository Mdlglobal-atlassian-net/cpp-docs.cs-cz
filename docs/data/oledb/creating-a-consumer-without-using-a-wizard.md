---
title: "Vytvoření příjemce bez použití Průvodce | Microsoft Docs"
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
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a61de0a4621f6f9387da23093f9f450749129ac3
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Vytvoření příjemce bez použití průvodce
V následujícím příkladu se předpokládá, že přidáváte podporu příjemce technologie OLE DB do existujícího projektu knihovny ATL. Pokud chcete přidat do aplikace MFC podporu příjemce technologie OLE DB, byste měli spustit Průvodce aplikací MFC, který vytvoří nezbytné všechny podporu a vyvolá MFC rutiny, které jsou nezbytné ke spuštění aplikace.  
  
 Chcete-li přidat podporu příjemce technologie OLE DB bez použití průvodce příjemcem knihovny ATL technologie OLE DB:  
  
-   V souboru Stdafx.h připojte následující `#include` příkazy:  
  
    ```  
    #include <atlbase.h>  
    #include <atldbcli.h>  
    #include <atldbsch.h> // if you are using schema templates  
    ```  
  
 Příjemce prostřednictvím kódu programu, obvykle provádí následující posloupnost operací:  
  
-   Vytvořte třídu záznam uživatele, která sváže sloupce do místní proměnné. V tomto příkladu `CMyTableNameAccessor` je třída uživatelského záznamu (viz [uživatelských záznamů](../../data/oledb/user-records.md)). Tato třída obsahuje mapu sloupce a parametr mapy. Declare – datový člen v třídě uživatelského záznamu pro každé pole, které zadáte v mapě sloupců; pro každou z těchto datových členů deklarujte také datového člena a délku datového člena. Další informace najdete v tématu [Datoví členové stavu pole v přístupových objektech generovaných průvodcem](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).  
  
    > [!NOTE]
    >  Pokud píšete vlastní příjemce, data proměnné musí předcházet proměnné stavu a délka.  
  
-   Vytvoří instanci zdroje dat a relace. Rozhodnout, jaký typ přistupujícího objektu a sady řádků používat, a potom vytvořte instanci sady řádků pomocí [CCommand](../../data/oledb/ccommand-class.md) nebo [CTable](../../data/oledb/ctable-class.md):  
  
    ```  
    CDataSource ds;  
    CSession ss;  
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>  
    ```  
  
-   Volání **funkce CoInitialize** k inicializaci modelu COM. To se obvykle nazývá v hlavní kódu. Příklad:  
  
    ```  
    HRESULT hr = CoInitialize(NULL);  
    ```  
  
-   Volání [CDataSource::Open](../../data/oledb/cdatasource-open.md) nebo jednu z jeho variant.  
  
-   Otevřít připojení ke zdroji dat, otevřete relaci a otevřete a inicializaci sady řádků (a pokud příkaz, také provést):  
  
    ```  
    hr = ds.Open();  
    hr = ss.Open(ds);  
    hr = rs.Open();            // (Open also executes the command)  
    ```  
  
-   Volitelně můžete nastavit vlastnosti sady řádků pomocí `CDBPropSet::AddProperty` a předávat je jako parametr, který se `rs.Open`. Příklad způsobu provedení, naleznete v GetRowsetProperties v [vygenerované metody](../../data/oledb/consumer-wizard-generated-methods.md).  
  
-   Sada řádků teď můžete načíst nebo manipulovat s daty.  
  
-   Pokud vaše aplikace se provádí, zavře připojení, relace a sady řádků:  
  
    ```  
    rs.Close();  
    ss.Close();  
    ds.Close();  
    ```  
  
     Pokud používáte příkaz, můžete chtít volání `ReleaseCommand` po **Zavřít**. Příklad kódu v [CCommand::Close](../../data/oledb/ccommand-close.md) ukazuje způsob volání **Zavřít** a `ReleaseCommand`.  
  
-   Volání **CoUnInitialize** k inicializaci modelu COM. To se obvykle nazývá v hlavní kódu.  
  
    ```  
    CoUninitialize();  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření příjemce OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)