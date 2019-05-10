---
title: Vytvoření jednoduchého příjemce
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
ms.openlocfilehash: f72363478696baccb0473e37104427b1516b39c3
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525004"
---
# <a name="creating-a-simple-consumer"></a>Vytvoření jednoduchého příjemce

::: moniker range="vs-2019"

Průvodce spotřebitele ATL OLE DB není k dispozici v aplikaci Visual Studio 2019 a novějším. Funkce můžete přesto přidat ručně. Další informace najdete v tématu [vytvoření příjemce bez použití průvodce](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="vs-2017"

Použití **Průvodce projektem ATL** a **průvodce příjemcem ATL OLE DB** ke generování šablony příjemce OLE DB.

## <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>K vytvoření konzolové aplikace pro příjemce technologie OLE DB

1. Na **souboru** nabídky, klikněte na tlačítko **nový**a potom klikněte na tlačítko **projektu**.

   Zobrazí se dialogové okno **Nový projekt**.

1. V **typy projektů** podokně klikněte na tlačítko **nainstalováno** > **Visual C++** > **Windows Desktop** složce a pak klikněte na tlačítko **desktopový Průvodce pro Windows** ikonu **šablony** podokně. V **název** zadejte název projektu, například *MyCons*.

1. Klikněte na **OK**.

   **Desktopový projekt Windows** průvodce se zobrazí.

1. Na **nastavení aplikace** stránce **konzolovou aplikaci**a pak vyberte **přidat společné soubory hlaviček pro knihovnu ATL**.

1. Klikněte na tlačítko **OK** zavřete průvodce a generování projektu.

Pak pomocí **průvodce příjemcem ATL OLE DB** přidání objektu příjemce technologie OLE DB.

## <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Vytvoření příjemce pomocí průvodce příjemcem ATL OLE DB

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem myši `MyCons` projektu.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **nová položka**.

   Zobrazí se dialogové okno **Přidat novou položku**.

1. V **kategorie** podokně klikněte na tlačítko **nainstalováno** > **Visual C++**  > **ATL**, klikněte na tlačítko  **Spotřebitele OLEDB knihovny ATL** ikonu **šablony** podokně a pak klikněte na tlačítko **přidat**.

   **Průvodce příjemcem ATL OLEDB** se zobrazí.

1. Klikněte na tlačítko **zdroj dat** tlačítko.

   **Vlastnosti propojení dat** zobrazí se dialogové okno.

1. V **vlastnosti propojení dat** dialogové okno pole, postupujte takto:

   1. Na **poskytovatele** kartu, zadejte zprostředkovatele OLE DB.

   1. Na **připojení** kartu, zadejte požadované informace, jako je například název serveru, přihlašovací jméno a heslo pro zdroj dat a databáze na serveru.

      > [!NOTE]
      > Existuje problém zabezpečení s **povolit uložení hesla** funkce **vlastnosti propojení dat** dialogové okno. V **zadejte informace pro přihlášení k serveru**, existují dva přepínače: **Použití Windows NT integrované zabezpečení** a **použít konkrétní uživatelské jméno a heslo**.

      > [!NOTE]
      > Pokud vyberete **použít konkrétní uživatelské jméno a heslo**, máte možnost uložení hesla (pomocí **povolit uložení hesla** zaškrtávací políčko), ale tato možnost není zabezpečený. Doporučuje se, že vyberete **integrované zabezpečení Windows NT použití**; tato možnost používá k ověření vaší identity systému Windows NT.

      > [!NOTE]
      > Pokud nemůžete použít Windows NT integrované zabezpečení, používejte aplikace střední vrstvy vyzvat uživatele k zadání hesla nebo k uložení hesla v umístění s mechanismy zabezpečení, které zvýší jeho ochranu (místo ve zdrojovém kódu).

   1. Po výběru poskytovatele a další nastavení, klikněte na **Test připojení** ověření výběru z předchozího stránek dialogového okna. Pokud **výsledky** pole sestavy `Test connection succeeded`, klikněte na tlačítko **OK** pro vytvoření odkazu data.

   **Vyberte databázový objekt** zobrazí se dialogové okno.

1. Výběr tabulky, zobrazení nebo uložené procedury pomocí ovládacího prvku stromu. V tomto příkladu vyberte `Products` tabulce `Northwind` databáze.

1. Klikněte na **OK**. Tím se vrátíte do **průvodce příjemcem ATL OLE DB**.

1. Názvy pro dokončení průvodce `Class` a **souboru .h** na základě názvu tabulky, zobrazení nebo uložené procedury, kterou jste vybrali. Pokud chcete, můžete upravit tyto názvy.

1. Zrušte **Atributovaný** zaškrtněte políčko, aby průvodce vytvoří příjemce kódu pomocí [tříd šablon technologie OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) místo výchozího [atributy příjemce technologie OLE DB](../../windows/ole-db-consumer-attributes.md).

1. V části **typ**vyberte **příkaz**.

   Průvodce vytvoří [CCommand](../../data/oledb/ccommand-class.md)– na základě uživatelů, pokud vyberete **příkaz** nebo [CTable](../../data/oledb/ctable-class.md)– na základě uživatelů, pokud vyberete **tabulky**. Vybraný objekt má stejný název třídy příkazu nebo tabulky, ale můžete upravit název.

1. V části **podporu**, nechat **změnu**, **vložit**, a **odstranit** políčka prázdná.

   Vyberte **změnu**, **vložit**, a **odstranit** zaškrtávací políčka pro podporu změn, vkládání a odstraňování záznamů v dané sadě řádků. Další informace o zápisu dat do dat úložiště, najdete v článku [aktualizace sad řádků](../../data/oledb/updating-rowsets.md).

1. Klikněte na tlačítko **Dokončit** vytvořte příjemce.

Průvodce vygeneruje třídu příkazu nebo třída záznamů uživatelů, jak je znázorněno v [vygenerované třídy](../../data/oledb/consumer-wizard-generated-classes.md). Třídy příkazů bude mít název, který jste zadali v `Class` pole v průvodci (v tomto případě `CProducts`), a třídu záznamů uživatele bude mít název ve tvaru "*ClassName*přístupového objektu" (v tomto případě `CProductsAccessor`).

> [!NOTE]
> Průvodce umístí následující řádek do `Products.h`:

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> Tento řádek znemožňuje spotřebitele aplikaci v kompilaci a vám připomene zkontrolovat pevně kódovaná hesla v připojovacím řetězci. Po kontrole připojovací řetězec, můžete odebrat tento řádek kódu.

::: moniker-end

## <a name="see-also"></a>Viz také:

[Vytvoření příjemce OLE DB pomocí průvodce](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
