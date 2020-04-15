---
title: Průvodce příjemcem ATL OLE DB
ms.date: 07/02/2019
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
ms.openlocfilehash: 16b2863bc3919edadeef29691c4588838010d9dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319275"
---
# <a name="atl-ole-db-consumer-wizard"></a>Průvodce příjemcem ATL OLE DB

::: moniker range="vs-2019"

Tento průvodce není k dispozici v sadě Visual Studio 2019 a novějších.

::: moniker-end

::: moniker range="<=vs-2017"

Tento průvodce nastaví třídu příjemce technologie OLE DB s datovými vazbami potřebnými pro přístup k zadanému zdroji dat prostřednictvím zadaného zprostředkovatele technologie OLE DB.

> [!NOTE]
> Tento průvodce vyžaduje, abyste před zadáním názvů do polí `Class` souboru **A H** vyberte zdroj dat klepnutím na tlačítko **Zdroj dat.**

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Zdroj dat**

   Tlačítko **Zdroj dat** umožňuje nastavit zadaný zdroj dat pomocí zadaného zprostředkovatele TECHNOLOGIE OLE DB. Po klepnutí na toto tlačítko se zobrazí dialogové okno **Vlastnosti datového propojení.** Další informace o vytváření připojovacích řetězců a dialogové okno **Vlastnosti datového propojení** naleznete v tématu [Přehled rozhraní API datového propojení](/previous-versions/windows/desktop/ms718102(v=vs.85)) v dokumentaci k programu Windows SDK.

   Následující další informace popisují karty v dialogovém okně **Vlastnosti datového spojení.**

  - Karta **Zprostředkovatel**

      Vyberte vhodného zprostředkovatele pro správu připojení ke zdroji dat. Typ zprostředkovatele je obvykle určen typem databáze, ke které se připojujete. Klepněte na tlačítko **Další** nebo na kartu **Připojení.**

  - Karta **Připojení**

      Obsah této karty závisí na vybraném zprostředkovateli. Přestože existuje mnoho typů zprostředkovatelů, tato část se týká připojení pro dva nejběžnější: SQL a ODBC data. Ostatní jsou podobné variace na pole zde popsané.

      Pro data SQL:

      1. **Vyberte nebo zadejte název serveru:** Kliknutím na rozevírací seznam zobrazte všechny registrované datové servery v síti a vyberte jeden z nich.

      1. **Zadejte informace pro přihlášení k serveru:** Zadejte uživatelské jméno a heslo pro přihlášení k datovému serveru.

         > [!NOTE]
         > V dialogovém okně Vlastnosti datového spojení došlo k potížím se zabezpečením s funkcí Povolit ukládání hesla. V části "Zadejte informace pro přihlášení k serveru", existují dvě přepínací tlačítka:
         >
         > - **Použití integrovaného zabezpečení systému Windows NT**
         > - **Použití konkrétního uživatelského jména a hesla**
         >
         > Pokud vyberete **použít konkrétní uživatelské jméno a heslo**, máte možnost uložit heslo (pomocí zaškrtávacího políčka "Povolit ukládání hesla"); Tato možnost však není zabezpečená. Doporučujeme vybrat **možnost Použít integrované zabezpečení systému Windows NT**. Tato možnost je bezpečná, protože šifruje heslo.
         > Může nastat situace, ve kterých chcete vybrat možnost Povolit ukládání hesla. Například pokud vydáváte knihovnu s řešením soukromé databáze, neměli byste přistupovat k databázi přímo, ale místo toho použít aplikaci střední vrstvy k ověření uživatele (prostřednictvím libovolného schématu ověřování, které zvolíte) a potom omezit druh dat, které jsou k dispozici pro uživatele.

      1. **Vyberte databázi na serveru:** Kliknutím na rozevírací seznam zobrazte všechny registrované databáze na datovém serveru a jednu vyberte.

         \-nebo -

         **Připojte databázový soubor jako název databáze:** Zadejte soubor, který má být použit jako databáze; zadejte explicitní název cesty.

      Pro data ODBC:

      1. **Zadejte zdroj dat:** Můžete použít název zdroje dat nebo připojovací řetězec.

         **Použít název zdroje dat:** V tomto rozevíracím seznamu jsou uvedeny zdroje dat registrované ve vašem počítači. Zdroje dat můžete nastavit předem pomocí správce zdroje dat ROZHRANÍ ODBC.

         \-nebo -

         **Použijte připojovací řetězec:** Zadejte připojovací řetězec, který jste již získali, nebo klepněte na tlačítko **Sestavit;** zobrazí se dialogové okno **Vybrat zdroj dat.** Vyberte soubor nebo zdroj dat počítače a klepněte na **tlačítko OK**.

         > [!NOTE]
         > Připojovací řetězec můžete získat zobrazením vlastností existujícího připojení v **Průzkumníku serveru**nebo můžete vytvořit připojení poklepáním na **přidat připojení** v **Průzkumníku serveru**.

      1. **Zadejte informace pro přihlášení k serveru:** Zadejte uživatelské jméno a heslo pro přihlášení k datovému serveru.

      1. Zadejte počáteční katalog, který chcete použít.

      1. Klepněte na **možnost Testovat připojení**; Pokud je test úspěšný, klepněte na tlačítko **OK**. Pokud ne, zkontrolujte přihlašovací informace, zkuste jinou databázi nebo zkuste jiný datový server.

  - **Karta Upřesnit**

      **Nastavení sítě:** Zadejte **úroveň zosobnění** (úroveň zosobnění, kterou může server použít při zosobnění klienta; odpovídá přímo úrovním zosobnění vzdáleného volání procedur) a **úroveň ochrany** (úroveň ochrany dat odeslaných mezi klientem a serverem; odpovídá přímo úrovním ochrany vzdáleného volání procedur).

      **Ostatní:** V **poli Časový limit připojení**zadejte počet sekund doby nečinnosti povolené před vypršením časového limitu. V **poli Přístupová oprávnění**zadejte přístupová oprávnění k datovému připojení.

      Další informace o rozšířených vlastnostech inicializace naleznete v dokumentaci dodané s každým konkrétním zprostředkovatelem technologie OLE DB.

  - **Karta Vše**

      Na této kartě se zobrazí souhrn vlastností inicializace pro zadaný zdroj dat a připojení. Tyto hodnoty můžete upravit.

      Kliknutím na **OK** vytváření dokončete. Zobrazí se dialogové okno **Vybrat databázový objekt.** V tomto dialogovém okně vyberte tabulku, zobrazení nebo uloženou proceduru, kterou bude spotřebitel používat.

- **Třída**

   Po výběru zdroje dat je toto pole vyplněno výchozím názvem třídy na základě vybrané tabulky nebo uložené procedury (viz **Výběr zdroje dat** níže). Název třídy můžete upravit.

- **Soubor H**

   Po výběru zdroje dat je toto pole naplněno výchozím názvem třídy záhlaví na základě vybrané tabulky nebo uložené procedury (viz **Výběr zdroje dat** níže). Můžete upravit název souboru záhlaví nebo vybrat existující soubor záhlaví.

- **Připsat**

   Tato možnost určuje, zda průvodce vytvoří třídy příjemce pomocí atributů nebo deklarací šablony. Když vyberete tuto možnost, průvodce použije atributy místo deklarací šablony (toto je výchozí možnost). Když tuto volbu zrušíte, průvodce místo atributů použije deklarace šablony.

  - Pokud vyberete příjemce **Typ** **tabulky**, `db_source` průvodce `db_table` použije atributy a k vytvoření deklarací třídy přistupujícího k tabulce a tabulky a použije `db_column` se k vytvoření mapy sloupců. Například vytvoří tuto mapu:

    ```cpp
    // Inject table class and table accessor class declarations
    [db_source("<initialization_string>"), db_table("dbo.Orders")]
    ...
    // Column map
    [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
    [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
    ...
    ```

     místo použití `CTable` třídy šablony deklarovat třídu přistupujícího k tabulce a tabulce a BEGIN_COLUMN_MAP a END_COLUMN_MAP makra k vytvoření mapy sloupců, jako v tomto příkladu:

    ```cpp
    // Table accessor class
        class COrdersAccessor; // Table class
        class COrders : public CTable<CAccessor<COrdersAccessor>>;
    // ...
    // Column map
        BEGIN_COLUMN_MAP(COrderDetailsAccessor)
            COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)
            COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)
            // ...
        END_COLUMN_MAP()
    ```

  - Pokud vyberete příjemce **Typ** **příkazu**, `db_source` `db_command` průvodce použije atributy a a použije `db_column` k vytvoření mapy sloupců. Například vytvoří tuto mapu:

    ```cpp
    [db_source("<initialization_string>"), db_command("SQL_command")]
    ...
    // Column map using db_column is the same as for consumer type of 'table'
    ```

     místo použití deklarací třídy přistupujícího příkazu a příkazu v souboru .h command class, například:

    ```cpp
    // Command accessor class:
        class CListOrdersAccessor;
    // Command class:
        class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
    // ...
    // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
    // for consumer type of 'table'
    ```

     Další informace naleznete [v části Základní mechanika atributů.](../../windows/basic-mechanics-of-attributes.md)

- **Typ**

   Vyberte jedno z těchto přepínacích tlačítek a `CTable` `CCommand` určete, zda bude třída příjemce odvozena od nebo (výchozí).

  - **Table**

      Tuto možnost vyberte, `CTable` pokud `db_table` chcete použít nebo vytvořit deklarace třídy přistupujícího k tabulce a tabulce.

  - **Příkaz**

      Tuto možnost vyberte, `CCommand` pokud `db_command` chcete použít nebo vytvořit deklarace třídy přistupujícího příkazu a příkazu. Toto je výchozí výběr.

- **Podpora**

   Zaškrtnutím políček určete druhy aktualizací, které mají být ve spotřebiteli podporovány (výchozí hodnota je žádná). Každá z následujících možností nastaví [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892(v=vs.85)) a příslušné položky pro [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676(v=vs.85)) v mapě sady vlastností.

  - **Změnit**

      Určuje, že příjemce podporuje aktualizace dat řádků v sadě řádků.

  - **Vložit**

      Určuje, že příjemce podporuje vkládání řádků do sady řádků.

  - **Odstranit**

      Určuje, že příjemce podporuje odstranění řádků ze sady řádků.

::: moniker-end

## <a name="see-also"></a>Viz také

[Příjemce KNIHOVNY OLE DB](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[Přidání funkce pomocí Průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Připojovací řetězce a datová propojení (OLE DB)](/previous-versions/windows/desktop/ms718376(v=vs.85))
