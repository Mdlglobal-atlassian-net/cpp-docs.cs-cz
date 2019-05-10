---
title: Přidání funkce pomocí průvodců kódem (C++)
ms.date: 05/09/2019
helpviewer_keywords:
- code wizards [C++]
ms.assetid: 6afb7ef9-7056-423d-b244-91bb4236d1d7
ms.openlocfilehash: 3050b3e2d2a188c2465cd454325e458cd8cc4047
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525480"
---
# <a name="adding-functionality-with-code-wizards-c"></a>Přidání funkce pomocí průvodců kódem (C++)

Po vytvoření projektu můžete změnit nebo přidat funkce tohoto projektu. Mezi tyto úlohy patří vytváření nových tříd, přidává nové členské funkce a proměnné a přidání automatizace metody a vlastnosti. Průvodci kódem jsou navržené tak, aby šlo dělat tyto věci.

> [!NOTE]
> V aplikaci Visual Studio 2019 odeberou se následující průvodci kódem zřídka používají. Obecné podpory knihovny ATL a MFC nemá žádný vliv, odebrání těchto průvodců. Ukázkový kód pro tyto technologie v Microsoft Docs a úložišti VCSamples GitHub archivuje.

- Průvodce komponentami 1.0 knihovny ATL modelu COM +
- Průvodce komponentami ATL Active Server Pages
- Průvodce zprostředkovatelem ATL OLE DB
- Průvodce stránkou vlastností ATL
- Průvodce příjemcem ATL OLE DB
- Příjemce ODBC knihovny MFC
- Třída knihovny MFC z ovládacího prvku ActiveX
- Třída knihovny MFC z typu Lib.


> [!NOTE]
>  Teď můžete přidat obslužné rutiny zpráv a mapování zpráv na ně a přepsat virtuální funkce MFC pomocí [okno vlastností](/visualstudio/ide/reference/properties-window).

## <a name="accessing-visual-c-code-wizards"></a>Přístup k Průvodci kódem jazyka Visual C++

Existují tři umístění, kam máte přístup průvodců kódem jazyka Visual C++:

- Na **projektu** nabídky, **přidat novou položku** příkazu můžete zobrazit `Add New Item` dialogové okno, které vám pomůžou při přidávání nové soubory do projektu. **Přidat třídu** příkaz zobrazí [přidat třídu](../ide/add-class-dialog-box.md) dialogové okno, které pak otevřete Průvodce pro každou třídu typů můžete přidat do projektu. **Přidat prostředek** příkaz zobrazí [přidat prostředek](../windows/add-resource-dialog-box.md) dialogové okno, ze kterého můžete vytvořit nebo vybrat prostředek pro přidání do projektu.

   Pokud je zvýraznění třídu nebo rozhraní v projektu v zobrazení tříd **projektu** nabídka zobrazí následující příkazy:

   - **Implementovat rozhraní** (z třídy ovládacího prvku jenom)

   - **Přidat funkci**

   - **Přidat proměnnou**

   - **Přidat připojovací bod** (pouze třídy ATL)

   - **Přidejte metodu** (z rozhraní jenom)

   - **Přidat vlastnost** (z rozhraní jenom)

   - **Přidat událost** (z třídy ovládacího prvku jenom)

- V **Průzkumníka řešení**, pravým tlačítkem myši na libovolné složky a kliknutím na **přidat** ze zástupce nabídky vám umožní přidávat nové nebo existující soubory, další složky, položky, tříd, prostředky a webové odkazy na projekt.

- Z [okno Zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), že kliknete pravým tlačítkem na příslušný uzel a kliknutím na **přidat** ze zástupce v nabídce vám umožní přidávat funkce, proměnné, třídy, vlastnosti, metody, události, rozhraní, body připojení, nebo jiný kód do vašeho projektu.

   > [!NOTE]
   > Visual Studio neposkytuje průvodce můžete přidat rozhraní do projektu. Můžete přidat rozhraní do projektu knihovny ATL nebo do [přidání podpory knihovny ATL do projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) tak Přidání jednoduchého objektu pomocí [Průvodce jednoduchý objekt knihovny ATL](../atl/reference/atl-simple-object-wizard.md). Můžete také otevřít soubor .idl projektu a vytvořte rozhraní tak, že zadáte:

    ```IDL
    interface IMyInterface {
    };
    ```

   Zobrazit [implementace rozhraní](../ide/implementing-an-interface-visual-cpp.md) a [přidání objektů a ovládacích prvků do projektu ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) Další informace.

   |Průvodce přístupový kód|Popis|
   |-----------------------------|-----------------|
   |Přidat novou položku|Průvodci kódem přidat novou položku přidat zdrojové soubory do projektu. V případě potřeby další adresáře jsou vytvořeny tak, aby obsahovala soubory, kde se očekává, že modul sestavení projektu je najít. Průvodci kódem, které jsou k dispozici ikona přidání položky patří:<br /><br />-Přidáte zdrojové soubory C++ (.cpp, .h, .idl, .rc, .srf, .def, .rgs).<br />-Přidáte soubory vývojového webového (HTML, ASP, CSS, .xml).<br />-Přidáte nástroj pro soubory a soubory prostředků (.bmp, .cur, ICO, .rct, .sql, txt).<br /><br />Tito průvodci kódu obecně nepožadují žádné informace, ale přidejte soubor do vašeho vývojového stromu. Může přejmenování souboru v okně Vlastnosti.|
   |Průzkumník řešení|Průvodci kódem, který je k dispozici v Průzkumníku řešení závisí na místě, kde kurzoru při klikněte pravým tlačítkem na položku. Pokud **přidat** možnost se nezobrazí, klikněte pravým tlačítkem na položku, přesuňte ukazatel myši nahoru o jednu úroveň ve stromové struktuře vývoje a zkuste to znovu. Průvodci kódem vždy umístí další kód na příslušné místo ve stromové struktuře vývoj bez ohledu na to kdy je ukazatel myši. Průvodci kódem, které jsou k dispozici z Průzkumníka řešení, patří:<br /><br />-Přidat třídě (otevře **přidat třídu** dialogové okno obsahuje Průvodce kódem).<br />-Přidat prostředek (nové, Import, nebo vlastní).<br />-Přidáte webový odkaz.|
   |zobrazení tříd|Průvodci kódem, který je k dispozici ze zobrazení tříd, závisí na místě, kde kurzoru při klikněte pravým tlačítkem myši klikněte na položku. Pokud **přidat** možnost se nezobrazí, klikněte pravým tlačítkem myši klikněte na položku, přesuňte ukazatel myši nahoru o jednu úroveň ve stromu tříd a zkuste to znovu. Průvodci kódem vždy umístí další kód na příslušné místo ve stromové struktuře vývoj bez ohledu na to kdy je ukazatel myši. Průvodci kódem, které jsou k dispozici ze zobrazení tříd patří:<br /><br />- [Přidat členskou funkci](../ide/adding-a-member-function-visual-cpp.md).<br />- [Přidat členskou proměnnou](../ide/adding-a-member-variable-visual-cpp.md).<br />- [Přidejte třídu](../ide/adding-a-class-visual-cpp.md).<br />- [Implementovat rozhraní](../ide/implement-interface-wizard.md) (z třídy ovládacího prvku jenom)<br />- [Přidat připojovací bod](../ide/implement-connection-point-wizard.md) (pouze třídy ATL)<br />- [Přidejte metodu](../ide/add-method-wizard.md) (z rozhraní jenom)<br />- [Přidat vlastnost](../ide/names-add-property-wizard.md) (z rozhraní jenom)<br />- [Přidat událost](../ide/add-event-wizard.md) (z třídy ovládacího prvku jenom)<br /><br />Přidat třídu výběr otevře **přidat třídu** dialogové okno, které vám umožňuje přístup ke všem přidat třídu Průvodce kódem.|

## <a name="see-also"></a>Viz také:

[Přepisování virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[Navigace strukturou třídy](../ide/navigating-the-class-structure-visual-cpp.md)<br>
[C++typy projektů v sadě Visual Studio](../build/reference/visual-cpp-project-types.md)<br>
[Soubor typy vytvořené pro vizuál C++ projekty](../build/reference/file-types-created-for-visual-cpp-projects.md)
