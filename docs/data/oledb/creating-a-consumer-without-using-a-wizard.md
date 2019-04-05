---
title: Vytvoření příjemce bez použití průvodce
ms.date: 10/12/2018
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: 029fe6866df81d366cc3bc15096f638791faa413
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030417"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Vytvoření příjemce bez použití průvodce

V následujícím příkladu se předpokládá, že přidáváte podporu příjemce technologie OLE DB do existujícího projektu ATL. Pokud chcete přidat podporu příjemce technologie OLE DB pro aplikace knihovny MFC, měli byste spustit **Průvodce aplikací knihovny MFC**, který vytvoří nezbytné veškerou podporu a vyvolá rutiny knihovny MFC, které jsou nezbytné ke spuštění aplikace.

Chcete-li přidat podporu příjemce technologie OLE DB bez použití **průvodce příjemcem ATL OLE DB**:

- V souboru soubor pch.h, připojte `#include` příkazy:

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

Příjemce prostřednictvím kódu programu, obvykle provádí následující pořadí operací:

1. Vytvořte třídu záznam uživatele, který váže sloupce pro lokální proměnné. V tomto příkladu `CMyTableNameAccessor` je třída záznamu uživatele (viz [uživatelských záznamů](../../data/oledb/user-records.md)). Tato třída obsahuje mapování sloupců a parametr mapy. Deklarovat v třídě uživatelského záznamu pro každé pole, které zadáte v mapě sloupců; datový člen pro každou z těchto datových členů také deklarujte datový člen stav a délku datového člena. Další informace najdete v tématu [Datoví členové stavu pole v přístupových objektech generovaných průvodcem](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

    > [!NOTE]
    > Pokud píšete vlastní příjemce, datových proměnných musí předcházet proměnné stavu a délky.

- Vytvořit instanci zdroje dat a relace. Rozhodnout, jaký typ přístupového objektu a sady řádků a potom vytvořte instanci sady řádků pomocí [CCommand](../../data/oledb/ccommand-class.md) nebo [CTable](../../data/oledb/ctable-class.md):

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- Volání `CoInitialize` inicializovat COM. Tomu se říká v hlavní kód. Příklad:

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- Volání [CDataSource::Open](../../data/oledb/cdatasource-open.md) nebo jednu z jeho variant.

- Otevřete připojení ke zdroji dat, otevřete relaci a otevřete a inicializaci sady řádků (a pokud příkaz, také ho spustit):

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- Volitelně můžete nastavit vlastnosti sady řádků pomocí `CDBPropSet::AddProperty` a předat je jako parametr `rs.Open`. Příklad, jak to lze provést, naleznete v tématu `GetRowsetProperties` v [vygenerované metody](../../data/oledb/consumer-wizard-generated-methods.md).

- Nyní můžete v sadě řádků načtení/práce s daty.

- Po dokončení se vaše aplikace, ukončete připojení, relace a sady řádků:

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   Pokud použijete příkaz, můžete chtít volat `ReleaseCommand` po `Close`. Příklad kódu v [CCommand::Close](../../data/oledb/ccommand-close.md) ukazuje, jak volat `Close` a `ReleaseCommand`.

- Volání `CoUnInitialize` k inicializaci modelu COM. Tomu se říká v hlavní kód.

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>Viz také:

[Vytvoření příjemce technologie OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)