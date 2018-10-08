---
title: Průvodce příjemcem ATL OLE DB | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/31/2018
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- connection strings [C++], OLE DB consumers
- ATL OLE DB Consumer Wizard
ms.assetid: dcb68ed1-2224-422f-9f7b-108a74864204
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 163949c4421cca8e4d5e414a18bda4ed98f32d3d
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48861639"
---
# <a name="atl-ole-db-consumer-wizard"></a>Průvodce příjemcem ATL OLE DB

Tento průvodce nastaví třída příjemce technologie OLE DB pomocí datové vazby potřebné pro přístup k danému zdroji dat pomocí zadaného zprostředkovatele OLE DB.

> [!NOTE]
> Tohoto průvodce, musíte kliknout **zdroj dat** tlačítko Vybrat zdroj dat před zadáním názvů v `Class` a **souboru .h** pole.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Zdroj dat**

   **Zdroj dat** tlačítko umožňuje nastavit zadaný zdroj dat pomocí zadaného zprostředkovatele OLE DB. Po kliknutí na toto tlačítko **vlastnosti propojení dat** zobrazí se dialogové okno. Další informace o vytváření připojovacích řetězců a **vlastnosti propojení dat** dialogovém okně naleznete v tématu [Data přehled rozhraní API odkazu](/previous-versions/windows/desktop/ms718102\(v=vs.85\)) v dokumentaci Windows SDK.

   Popisuje následující doplňkové informace na kartách v **vlastnosti propojení dat** dialogové okno.

   - **Zprostředkovatel** kartu

      Vyberte příslušné poskytovatele spravovat připojení ke zdroji dat. Typ zprostředkovatele se běžně Určuje typ databáze, ke kterému se připojujete. Klikněte na tlačítko **Další** tlačítko nebo klikněte na tlačítko **připojení** kartu.

   - **Připojení** kartu

      Obsah na této kartě záviset na poskytovateli, kterou jste vybrali. I když existuje mnoho typů poskytovatelů, tato část popisuje připojení pro dva nejběžnější: data SQL a ODBC. Ostatní jsou podobné varianty pole popsaná zde.

      Pro SQL data:

      1. **Vyberte nebo zadejte název serveru:** klikněte na nabídku rozevíracího seznamu zobrazíte všechny registrované datové servery v síti a vyberte jednu.

      1. **Zadejte informace pro přihlášení k serveru:** zadejte uživatelské jméno a heslo pro přihlášení k serveru data.

         > [!NOTE]
         > Dojde k problému zabezpečení s funkcí "Povolit uložení hesla" dialogové okno Vlastnosti datového připojení. V "Zadejte informace pro přihlášení k serveru", existují dva přepínače:
         >
         > - **Pomocí zabezpečení systému Windows NT integrované**
         > - **Použít konkrétní uživatelské jméno a heslo**
         >
         > Pokud vyberete **použít konkrétní uživatelské jméno a heslo**, mají možnost uložení hesla (pomocí zaškrtávací políčko "Povolit uložení hesla"), ale tato možnost není zabezpečený. Doporučuje se, že vyberete **integrované zabezpečení Windows NT použití**; tato možnost je bezpečná, protože je heslo zašifruje.
         > Můžou nastat situace, ve kterých chcete možnost "Povolit uložení hesla." Například pokud uvolnění knihovny s privátní databázového řešení vám by měl není přímý přístup k databázi, ale místo toho použít k ověření uživatele (pomocí libovolné zvolíte schéma ověřování) a pak omezit druh dat aplikace střední vrstvy k dispozici pro uživatele.

      1. **Vyberte databázi na serveru:** klikněte na nabídku rozevíracího seznamu zobrazíte všechny registrované databází na serveru pro data a vyberte jednu.

         \- nebo –

         **Připojit soubor databáze jako název databáze:** zadejte soubor, který má být použit jako databáze; zadejte explicitní název cesty.

      U dat rozhraní ODBC:

      1. **Zdroj dat:** můžete použít název zdroje dat nebo připojovací řetězec.

         **Použijte název zdroje dat:** Tento rozevírací seznam zobrazuje zdroje dat registrované ve vašem počítači. Můžete nastavit zdroje dat předem pomocí Správce zdrojů dat ODBC

         \- nebo –

         **Použijte připojovací řetězec:** buď zadejte připojovací řetězec už získali, nebo klikněte na tlačítko **sestavení** tlačítko; **vybrat zdroj dat** zobrazí se dialogové okno. Vyberte zdroj dat souboru nebo počítače a klikněte na tlačítko **OK**.

         > [!NOTE]
         > Připojovací řetězec můžete získat zobrazením vlastností existujícího připojení v **Průzkumníka serveru**, nebo můžete vytvořit připojení na něj poklikejte **přidat připojení** v **serveru Průzkumník**.

      1. **Zadejte informace pro přihlášení k serveru:** zadejte uživatelské jméno a heslo pro přihlášení k serveru data.

      1. Zadejte počáteční katalog.

      1. Klikněte na tlačítko **Test připojení**; Pokud je test úspěšný, klikněte na tlačítko **OK**. V opačném případě zkontrolujte vaše přihlašovací údaje, zkuste jiné databáze nebo zkuste jiný datový server.

   - **Pokročilé** kartu

      **Nastavení sítě:** zadejte **úroveň zosobnění** (úroveň zosobnění, které může používat při zosobňování klienta serveru; odpovídá úrovní zosobnění RPC) a  **Úroveň ochrany** (stupeň ochrany dat odeslány mezi klientem a serverem; odpovídá přímo na úrovních ochrany RPC).

      **Ostatní:** v **časový limit připojení**, zadejte dobu v sekundách nečinnosti před dojde k vypršení časového limitu. V **přístupová oprávnění**, zadejte oprávnění k přístupu na datové připojení.

       Další informace o vlastnostech pokročilé inicializace naleznete v dokumentaci dodávané s každou zprostředkovatele OLE DB.

   - **Všechny** kartu

      Tato karta zobrazuje souhrn inicializační vlastnosti pro zdroj dat a připojení, které jste zadali. Můžete upravit tyto hodnoty.

   Klikněte na tlačítko **OK** na dokončení. **Vyberte databázový objekt** zobrazí se dialogové okno. V tomto dialogovém okně vyberte tabulky, zobrazení nebo uložené procedury, která bude používat příjemce.

- **Třída**

   Po výběru zdroje dat, toto pole se vyplní výchozí název třídy na základě tabulky nebo uloženou proceduru, která jste vybrali (viz **vyberte zdroj dat** níže). Můžete upravit název třídy.

- **soubor .h**

   Po výběru zdroje dat, toto pole se vyplní výchozí název třídy hlavičky na základě tabulky nebo uloženou proceduru, která jste vybrali (viz **vyberte zdroj dat** níže). Můžete upravit název souboru hlaviček nebo vybrat existující hlavičkový soubor.

- **S atributy**

   Tato možnost určuje, zda má průvodce vytvořit pomocí atributů nebo deklarací šablony třídy příjemce. Když vyberete tuto možnost, Průvodce místo deklarací šablony (Toto je výchozí možnost) používá atributy. Pokud výběr této možnosti zrušíte, používá Průvodce místo atributů deklarace šablony.

   - Pokud vyberete příjemce **typ** z **tabulky**, použije průvodce `db_source` a `db_table` atributy k vytvoření tabulky a přistupující k tabulce deklarace tříd a používá `db_column` do Vytvoření mapy sloupce. Například vytvoří toto mapování:

        ```cpp
        // Inject table class and table accessor class declarations
        [db_source("<initialization_string>"), db_table("dbo.Orders")]
        ...
        // Column map
        [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;
        [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];
        ...
        ```

      namísto použití `CTable` třída šablony, chcete-li deklarovat v tabulce a třída přistupující objekt tabulky a makra BEGIN_COLUMN_MAP a END_COLUMN_MAP chcete vytvořit mapování sloupců, jako v následujícím příkladu:

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

   - Pokud vyberete příjemce **typ** z **příkaz**, použije průvodce `db_source` a `db_command` atributy a používá `db_column` k vytvoření mapy sloupce. Například vytvoří toto mapování:

        ```cpp
        [db_source("<initialization_string>"), db_command("SQL_command")]
        ...
        // Column map using db_column is the same as for consumer type of 'table'
        ```

      namísto použití příkazu a deklarace třídy přistupujícího objektu příkazu v souboru .h třídy příkazu, například:

        ```cpp
        // Command accessor class:
            class CListOrdersAccessor;
        // Command class:
            class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;
        // ...
        // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
        // for consumer type of 'table'
        ```

      Zobrazit [základní mechanismy atributů](../../windows/basic-mechanics-of-attributes.md) Další informace.

- **Typ**

   Vyberte jednu z těchto přepínačů, chcete-li určit, zda se třída příjemce odvozena z `CTable` nebo `CCommand` (výchozí).

   - **Tabulka**

      Tuto možnost vyberte, pokud chcete použít `CTable` nebo `db_table` vytvoření tabulky a přistupující k tabulce deklarace tříd.

   - **Příkaz**

      Tuto možnost vyberte, pokud chcete použít `CCommand` nebo `db_command` vytvořit příkaz a přístupový objekt příkazu deklarace tříd. Toto je výchozí výběr.

- **Podpora**

   Vyberte zaškrtávací políčka a určete typy aktualizací, aby se podporoval příjemce (výchozí hodnota je none). Každý z těchto nastaví [DBPROP_IRowsetChange](/previous-versions/windows/desktop/ms715892\(v=vs.85\)) a odpovídající položky pro [DBPROP_UPDATABILITY](/previous-versions/windows/desktop/ms722676\(v=vs.85\)) ve vlastnosti nastavit mapování.

   - **Změna**

      Určuje, že příjemci podporuje aktualizace řádek dat v dané sadě řádků.

   - **Vložit**

      Určuje, že příjemce nepodporuje vkládání řádků do sady řádků.

   - **Delete**

      Určuje, že příjemci podporuje odstranění řádků ze sady řádků.

## <a name="see-also"></a>Viz také:

[Příjemce knihovny ATL technologie OLE DB](../../atl/reference/adding-an-atl-ole-db-consumer.md)<br/>
[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Připojovací řetězce a propojení dat (OLE DB)](/previous-versions/windows/desktop/ms718376\(v=vs.85\))
