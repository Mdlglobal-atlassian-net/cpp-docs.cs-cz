---
title: "Průvodce příjemce OLE DB ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d12020b6adfca2c23dc610b5e596ff883bb9e7ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="atl-ole-db-consumer-wizard"></a>Průvodce příjemce ATL OLE DB
Tento průvodce nastavuje třída příjemce technologie OLE DB pomocí vazby dat potřebné pro přístup k zadaný zdroj dat pomocí zadaného zprostředkovatele OLE DB.  
  
> [!NOTE]
>  Tohoto průvodce, musíte kliknout na odkaz **zdroj dat** tlačítko vyberte zdroj dat před vstupem názvy v `Class` a **soubor h** pole.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Zdroj dat**  
 **Zdroj dat** tlačítko umožňuje nastavit zadaný zdroj dat pomocí zadaného zprostředkovatele OLE DB. Po kliknutí na toto tlačítko **vlastnosti propojení dat** zobrazí se dialogové okno. Další informace o vytváření připojovacích řetězců a **vlastnosti propojení dat** dialogové okno, najdete v části [Data Link Přehled rozhraní API](https://msdn.microsoft.com/library/ms718102.aspx) v dokumentaci k Windows SDK.  
  
> [!NOTE]
>  V předchozích verzích Shift a kliknutí na **zdroj dat** tlačítko Otevřít soubor otevřete dialogové okno a umožní vám vybrat soubor dat propojení (UDL). Tato funkce již není podporována.  
  
 Dialogové okno obsahuje čtyři karty:  
  
- **Zprostředkovatel** karta  
  
- **Připojení** karta  
  
- **Rozšířené** karta  
  
- **Všechny** karta  
  
     Popisuje následující doplňkové informace na kartách v **vlastnosti propojení dat** dialogové okno.  
  
     Klikněte na tlačítko **OK** ukončíte. **Vyberte objekt databáze** zobrazí se dialogové okno. Toto dialogové okno Vyberte tabulky, zobrazení nebo uložené procedury, která se použije k příjemce.  
  
 **Zprostředkovatel**  
     Vyberte příslušného poskytovatele ke správě připojení ke zdroji dat. Typ zprostředkovatele, se běžně Určuje typ databáze, ke kterému se chcete připojit. Klikněte `Next` tlačítko nebo klikněte na tlačítko **připojení** kartě.  
  
 **Připojení**  
     Obsah na této kartě závisí na zprostředkovateli, které jste vybrali. I když existuje mnoho typů poskytovatelů, tato část popisuje připojení dvě nejběžnější: data SQL a rozhraní ODBC. Ostatní jsou podobné varianty pole zde popsané.  
  
     Pro SQL data:  
  
    1. **Vyberte nebo zadejte název serveru:** klikněte na nabídku rozevíracího seznamu zobrazíte všechny registrované datové servery v síti a vyberte jednu.  
  
    2. **Zadejte informace pro přihlášení k serveru:** zadejte uživatelské jméno a heslo pro přihlášení k serveru data.  
  
    3. **Vyberte databázi na serveru:** klikněte na nabídku rozevíracího seznamu zobrazíte všechny registrované databáze na serveru dat a vyberte jednu.  
  
         -nebo-  
  
 **Připojit soubor databáze jako název databáze:** zadejte soubor, který chcete použít jako databázi; zadejte explicitní názvu cesty.  
  
        > [!NOTE]
        >  There is a security problem with the "Allow saving of password" feature of the Data Link Properties dialog box. In "Enter information to log on to the server," there are two radio buttons:  
  
 **Použít integrované zabezpečení Windows NT**  
  
 **Použít určité uživatelské jméno a heslo**  
  
         If you select **Use a specific user name and password**, you have the option of saving the password (using the check box for "Allow saving password"); however, this option is not secure. It is recommended that you select **Use Windows NT integrated security**; this option is secure because it encrypts the password.  
  
         There might be situations in which you want to select "Allow saving password." For example, if you are releasing a library with a private database solution, you should not access the database directly but instead use a middle-tier application to verify the user (through whatever authentication scheme you choose) and then limit the sort of data available to the user.  
  
         For ODBC data:  
  
         1. **Specify the source of data:** You can use a data source name or a connection string.  
  
 **Použijte název zdroje dat:** tohoto rozevíracího seznamu zobrazí zdroje dat registrované ve vašem počítači. Můžete nastavit zdroje dat předem pomocí Správce zdrojů dat ODBC- nebo -**použít připojovací řetězec:** buď zadejte připojovací řetězec jste už získali, nebo klikněte na tlačítko **sestavení** tlačítko; **Vybrat zdroj dat** zobrazí se dialogové okno. Vyberte zdroj dat souboru nebo počítače a klikněte na tlačítko **OK**.  
  
        > [!NOTE]
        >  You can obtain a connection string by viewing the properties of an existing connection in Server Explorer, or you can create a connection by double-clicking **Add Connection** in Server Explorer.  
  
         2. **Enter information to log on to the server:** Enter a user name and password to log on to the data server.  
  
         3. Enter the initial catalog to use.  
  
         4. Click **Test Connection**; if the test succeeds, click **OK**. If not, check your logon information, try another database, or try another data server.  
  
 **Pokročilé**  
 **Nastavení síťového:** zadejte **úroveň zosobnění** (úroveň zosobnění, který server se může použít při zosobňování klienta; odpovídá úrovní zosobnění RPC) a  **Úroveň ochrany** (úroveň ochrany dat odeslaných mezi klientem a serverem; odpovídá přímo na úrovních ochrany RPC).  
  
 **Ostatní:** v **časový limit připojení**, zadejte počet sekund nečinnosti před dojde k vypršení časového limitu. V **přístupová oprávnění**, zadejte oprávnění k přístupu na datové připojení.  
  
     Další informace o pokročilé inicializační vlastnosti naleznete v dokumentaci daného zprostředkovatele OLE DB.  
  
 **Všechny**  
     Tato karta zobrazuje souhrn inicializační vlastnosti pro zdroj dat a připojení, které jste zadali. Můžete upravit tyto hodnoty.  
  
     Klikněte na tlačítko **OK** ukončíte. **Vyberte objekt databáze** zobrazí se dialogové okno. Toto dialogové okno Vyberte tabulky, zobrazení nebo uložené procedury, která se použije k příjemce.  
  
 `Class`  
 Po výběru zdroje dat, je výchozí název třídy na základě tabulky nebo uložené procedury, kterou jste vybrali naplněný toto políčko (viz **vyberte zdroj dat** níže). Můžete upravit název třídy.  
  
 **soubor h**  
 Po výběru zdroje dat, je výchozí název třídy hlavičky na základě tabulky nebo uložené procedury, kterou jste vybrali naplněný toto políčko (viz **vyberte zdroj dat** níže). Můžete upravit název hlavičky souboru nebo vyberte existující soubor hlavičky.  
  
 **S atributy**  
 Tato možnost určuje, zda má průvodce vytvořit třídy příjemce pomocí atributů nebo deklarací šablon. Když vyberete tuto možnost, používá průvodce atributy namísto deklarace šablon (Toto je výchozí možnost). Při dalším tuto možnost, používá průvodce deklarace šablon místo atributy.  
  
-   Pokud vyberete příjemce **typ** tabulky, používá průvodce `db_source` a **db_table** atributy pro vytvoření tabulky a přistupující k tabulce deklarace tříd a používá **db_column**  k vytvoření mapy sloupce, například:  
  
 ``` 
 // Inject table class and table accessor class declarations  
 [db_source("<initialization_string>"), db_table("dbo.Orders")]  
 ... 
 // Column map  
 [ db_column(1, status=m_dwOrderIDStatus, length=m_dwOrderIDLength) ] LONG m_OrderID;  
 [ db_column(2, status=m_dwCustomerIDStatus, length=m_dwCustomerIDLength) ] TCHAR m_CustomerID[6];  
 ...  
 ```  
  
     místo použití `CTable` šablony třídy k deklaraci tabulky a třídu přistupující a makra BEGIN_COLUMN_MAP a END_COLUMN_MAP k vytvoření mapy sloupce, například:  
  
 ``` 
 // Table accessor class  
    class COrdersAccessor; *// Table class  
    class COrders : public CTable<CAccessor<COrdersAccessor>>;  
 ... 
 // Column map  
    BEGIN_COLUMN_MAP(COrderDetailsAccessor) 
    COLUMN_ENTRY_LENGTH_STATUS(1, m_OrderID, m_dwOrderIDLength, m_dwOrderIDStatus)  
    COLUMN_ENTRY_LENGTH_STATUS(2, m_CustomerID, m_dwCustomerIDLength, m_dwCustomerIDStatus)  
 ...  
    END_COLUMN_MAP() 
 ```  
  
-   Pokud vyberete příjemce **typ** příkazu, používá průvodce `db_source` a **db_command** atributy a používá **db_column** k vytvoření mapy sloupce, například :  
  
 ```  
 [db_source("<initialization_string>"), db_command("SQL_command")]  
 ... 
 // Column map using db_column is the same as for consumer type of 'table'  
 ```  
  
     místo použití příkazu a příkazu přistupující třídy deklarací v příkazu třídy .h souboru, například:  
  
 ```  
    Command accessor class:  
    class CListOrdersAccessor;  
    Command class:  
    class CListOrders : public CCommand<CAccessor<CListOrdersAccessor>>;  
 ... 
 // Column map using BEGIN_COLUMN_MAP ... END_COLUMN_MAP is the same as
 // for consumer type of 'table'  
 ```  
  
 V tématu [základní mechanismy atributů](../../windows/basic-mechanics-of-attributes.md) Další informace.  
  
 **Typ**  
 Vyberte jednu z těchto přepínačů, chcete-li určit, zda se třída spotřebitele odvozena z `CTable` nebo `CCommand` (výchozí).  
  
 **Tabulka**  
 Tuto možnost vyberte, pokud chcete použít `CTable` nebo **db_table** k vytvoření tabulky a přistupující k tabulce deklarace tříd.  
  
 **Příkaz**  
 Tuto možnost vyberte, pokud chcete použít `CCommand` nebo **db_command** k vytvoření příkazu a příkazu přistupující deklarace tříd. Toto je výchozí výběr.  
  
 **Podpora**  
 Vyberte pole a určete typy aktualizací, které mají být podporovány v příjemci (výchozí hodnota je žádný). Každý z těchto nastaví [DBPROP_IRowsetChange](https://msdn.microsoft.com/library/ms715892.aspx) a odpovídající položky pro [DBPROP_UPDATABILITY](https://msdn.microsoft.com/library/ms722676.aspx) ve vlastnosti nastavit mapy.  
  
 **Změna**  
 Určuje, že příjemce podporuje aktualizace řádek dat v dané sadě řádků.  
  
 **Vložení**  
 Určuje, že příjemce podporuje vložení řádků do sady řádků.  
  
 **Odstranit**  
 Určuje, že příjemce podporuje odstranění řádků ze sady řádků.  
  
## <a name="see-also"></a>Viz také  
 [ATL technologie OLE DB](../../atl/reference/adding-an-atl-ole-db-consumer.md)   
 [Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Připojovací řetězce a Data odkazy (OLE DB)](https://msdn.microsoft.com/library/ms718376.aspx)
