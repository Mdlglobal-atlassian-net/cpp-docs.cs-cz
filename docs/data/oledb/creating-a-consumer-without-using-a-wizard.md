---
title: Vytvoření příjemce bez použití průvodce
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: e8241cfe-5faf-48f8-9de3-241203de020b
ms.openlocfilehash: fff4146681e31f0f1fea9fbaa559de7c722740d2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211455"
---
# <a name="creating-a-consumer-without-using-a-wizard"></a>Vytvoření příjemce bez použití průvodce

Následující příklad předpokládá, že přidáváte podporu OLE DB spotřebitelů do existujícího projektu ATL. Chcete-li přidat OLE DB podporu příjemce do aplikace knihovny MFC, měli byste spustit **Průvodce aplikací knihovny MFC**, který vytvoří veškerou potřebnou podporu a vyvolá rutiny MFC nezbytné ke spuštění aplikace.

Přidání zákaznické podpory OLE DB bez použití **Průvodce příjemcem OLE DB příjemce**:

- V souboru *PCH. h* přidejte následující příkazy `#include`:

    ```cpp
    #include <atlbase.h>
    #include <atldbcli.h>
    #include <atldbsch.h> // if you are using schema templates
    ```

Prostřednictvím kódu programu uživatel obvykle provádí následující posloupnost operací:

1. Vytvořte třídu záznamu uživatele, která sváže sloupce s lokálními proměnnými. V tomto příkladu je `CMyTableNameAccessor` třídy záznamu uživatele (viz [záznamy uživatelů](../../data/oledb/user-records.md)). Tato třída obsahuje mapu sloupce a mapování parametrů. Deklarujte datový člen v třídě záznamu uživatele pro každé pole, které zadáte v mapě sloupce. pro každý z těchto datových členů také deklarujte datový člen stavu a délku datového člena. Další informace najdete v tématu [datové členy stavu pole v přístupových průvodcích generovaných průvodcem](../../data/oledb/field-status-data-members-in-wizard-generated-accessors.md).

    > [!NOTE]
    > Pokud píšete vlastního příjemce, musí být datové proměnné před proměnnými s stavem a délkou.

- Vytvořte instanci zdroje dat a relace. Rozhodněte, jaký typ přistupujícího objektu a sady řádků chcete použít, a potom vytvořte instanci sady řádků pomocí [CCommand](../../data/oledb/ccommand-class.md) nebo [CTable](../../data/oledb/ctable-class.md):

    ```cpp
    CDataSource ds;
    CSession ss;
    class CMyTableName : public CCommand<CAccessor<CMyTableNameAccessor>>
    ```

- Zavolejte `CoInitialize` pro inicializaci modelu COM. Tato metoda je volána v hlavním kódu. Příklad:

    ```cpp
    HRESULT hr = CoInitialize(NULL);
    ```

- Zavolejte [CDataSource:: Open](../../data/oledb/cdatasource-open.md) nebo One z jeho variací.

- Otevřete připojení ke zdroji dat, otevřete relaci a otevřete a inicializujte sadu řádků (a pokud příkaz také spustí):

    ```cpp
    hr = ds.Open();
    hr = ss.Open(ds);
    hr = rs.Open();            // (Open also executes the command)
    ```

- Volitelně můžete nastavit vlastnosti sady řádků pomocí `CDBPropSet::AddProperty` a předat je jako parametr pro `rs.Open`. Příklad toho, jak to lze provést, naleznete v tématu `GetRowsetProperties` v tématu [metody vygenerované průvodcem příjemce](../../data/oledb/consumer-wizard-generated-methods.md).

- Nyní můžete sadu řádků použít k načtení nebo manipulaci s daty.

- Po dokončení aplikace zavřete připojení, relaci a sadu řádků:

    ```cpp
    rs.Close();
    ss.Close();
    ds.Close();
    ```

   Pokud používáte příkaz, může být vhodné volat `ReleaseCommand` po `Close`. Příklad kódu v [CCommand:: Close](../../data/oledb/ccommand-close.md) ukazuje, jak volat `Close` a `ReleaseCommand`.

- Zavolejte `CoUnInitialize` pro zrušení inicializace modelu COM. Tato metoda je volána v hlavním kódu.

    ```cpp
    CoUninitialize();
    ```

## <a name="see-also"></a>Viz také

[Vytvoření příjemce OLE DB](../../data/oledb/creating-an-ole-db-consumer.md)
