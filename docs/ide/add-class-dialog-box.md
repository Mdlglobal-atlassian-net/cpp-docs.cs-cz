---
title: Dialogové okno Přidat třídu
ms.date: 11/04/2016
f1_keywords:
- vc.addclass
helpviewer_keywords:
- Add Class dialog box
ms.assetid: 916259b8-8e5f-4267-bd10-313483beba67
ms.openlocfilehash: 405f88f7f77ea75584ec3cfd76af1ea9a0457ed6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643193"
---
# <a name="add-class-dialog-box"></a>Dialogové okno Přidat třídu

**Přidat třídu** dialogové okno obsahuje šablony, které vám umožní:

- Otevření odpovídajícího průvodce, pokud je k dispozici. Další informace najdete v tématu [přidání funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md).

   \- nebo –

- Automaticky vytvořte novou třídu do projektu přidejte příslušné soubory a zdrojový kód.

Můžete přistupovat **přidat třídu** dialogové **projektu** nabídce **Průzkumníka řešení**, nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
>  Při pokusu přidat třídu, která není vhodné pro aktuální projekt, zobrazí se chybová zpráva. Klikněte na tlačítko **OK** se vrátíte **přidat třídu** dialogové okno.

## <a name="add-class-templates"></a>Přidání šablony třídy

Existují čtyři kategorie **přidat třídu** šablony: .NET, ATL, MFC a obecný. Když vyberete šablonu v **šablony** podokně text popisující, váš výběr se zobrazí v části **kategorie** a **šablony** podoken.

### <a name="net"></a>.NET

|Šablony|Průvodce|
|--------------|------------|
|Webová služba ASP.NET|Není k dispozici|
|Komponentní třída (.NET)|Není k dispozici|
|Instalační program tříd (.NET)|Není k dispozici|
|Uživatelský ovládací prvek (.NET)|Není k dispozici|
|Formuláře Windows (.NET)|Není k dispozici|

### <a name="atl"></a>ATL

|Šablony|Průvodce|
|--------------|------------|
|Přidat podporu ATL do MFC|Není k dispozici|
|Komponenta knihovny ATL Active Server Page|[Průvodce komponentami ATL Active Server Pages](../atl/reference/atl-active-server-page-component-wizard.md)|
|Ovládací prvek ATL|[Průvodce ovládacími prvky ATL](../atl/reference/atl-control-wizard.md)|
|ATL Dialog|[Průvodce dialogem ATL](../atl/reference/atl-dialog-wizard.md)|
|Komponenta knihovny ATL modelu COM + 1.0|[Průvodce komponentami ATL COM+ 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)|
|Příjemce knihovny ATL OLEDB|[Průvodce příjemcem ATL OLE DB](../atl/reference/atl-ole-db-consumer-wizard.md)|
|Připojit zprostředkovatele služeb OLEDB knihovny ATL|[Průvodce zprostředkovatelem ATL OLE DB](../atl/reference/atl-ole-db-provider-wizard.md)|
|Stránka vlastností knihovny ATL|[Průvodce stránkou vlastností ATL](../atl/reference/atl-property-page-wizard.md)|
|Jednoduchý objekt knihovny ATL|[Průvodce jednoduchým objektem ATL](../atl/reference/atl-simple-object-wizard.md)|
|Zprostředkovatel události rozhraní WMI|Průvodce zprostředkovatele událostí WMI|
|Zprostředkovatel instancí rozhraní WMI|Průvodce Instance zprostředkovatele rozhraní WMI|

### <a name="mfc"></a>MFC

|Šablony|Průvodce|
|--------------|------------|
|Třída knihovny MFC|[Průvodce přidáním třídy MFC](../mfc/reference/mfc-add-class-wizard.md)|
|Třída knihovny MFC z ovládacího prvku ActiveX|[Přidání třídy z průvodce ovládacím prvkem ActiveX](../ide/add-class-from-activex-control-wizard.md)|
|Třída knihovny MFC z TypeLib|[Přidání třídy z Průvodce knihovnou typů](../mfc/reference/add-class-from-typelib-wizard.md)|
|Příjemce ODBC knihovny MFC|[Průvodce příjemcem ODBC knihovny MFC](../mfc/reference/mfc-odbc-consumer-wizard.md)|

### <a name="generic-classes"></a>Obecné třídy

|Šablony|Průvodce|
|--------------|------------|
|Generické třídy jazyka C++|[Průvodce obecnými třídami C++](../ide/generic-cpp-class-wizard.md)|

## <a name="see-also"></a>Viz také

[Přidání členské funkce](../ide/adding-a-member-function-visual-cpp.md)<br>
[Přidání členské proměnné](../ide/adding-a-member-variable-visual-cpp.md)<br>
[Přepisování virtuální funkce](../ide/overriding-a-virtual-function-visual-cpp.md)<br>
[Popisovače zpráv knihovny MFC](../mfc/reference/adding-an-mfc-message-handler.md)<br>
[Navigace strukturou třídy](../ide/navigating-the-class-structure-visual-cpp.md)