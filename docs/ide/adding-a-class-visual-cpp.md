---
title: Přidat třídu
ms.date: 11/08/2018
f1_keywords:
- vc.codewiz.classes.adding
- vc.addclass
helpviewer_keywords:
- ATL projects, adding classes
- classes [C++], creating
- classes [C++], adding
- Add Class dialog box
ms.assetid: c34b5f70-4e72-4faa-ba21-e2b05361c4d9
ms.openlocfilehash: 21dd4b1936eda201df8283146ba9f41fa81e11de
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375883"
---
# <a name="add-a-class"></a>Přidat třídu

Chcete-li přidat třídu v projektu v jazyce Visual C++ v **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt, zvolte **přidat**a klikněte na tlačítko **třídy**. Tím se otevře [dialogové okno Přidat třídu](#add-class-dialog-box).

Při přidání třídy, musíte zadat název, který se liší od třídy, které již existují v MFC ani ATL. Pokud zadáte název, který již existuje v knihovně, rozhraní IDE zobrazí chybovou zprávu.

Pokud váš projekt zásady vytváření názvů vyžaduje, abyste použili existující název, pak můžete pouze změnit velikost jeden nebo více písmen v názvu protože C++ je velká a malá písmena. Například i když nelze pojmenovat třídu `CDocument`, můžete ji nazvat `cdocument`.

## <a name="in-this-section"></a>V tomto oddílu

- [Jaký druh třídy chcete přidat?](#what-kind-of-class-do-you-want-to-add)
- [Přidat třídu – dialogové okno](#add-class-dialog-box)

## <a name="what-kind-of-class-do-you-want-to-add"></a>Jaký druh třídy chcete přidat?

V **přidat třídu** dialogové okno, když rozšiřujete **Visual C++** uzlu v levém podokně se zobrazí několik seskupení nainstalovaných šablon. Zahrnout skupiny **CLR**, **ATL**, **MFC**, a **C++**. Když vyberete skupinu, se v prostředním podokně zobrazí seznam dostupných šablon v této skupině. Každá šablona obsahuje soubory a zdrojový kód, který se vyžadují pro třídu.

Pokud chcete vygenerovat novou třídu, v prostředním podokně vyberte šablonu, zadejte název pro třídu v **název** a vyberte **přidat**. Tím se otevře **Průvodce přidáním třídy** tak, aby můžete určit možnosti pro třídu.

- Další informace o tom, jak vytvořit třídy knihovny MFC naleznete v tématu [třídy knihovny MFC](../mfc/reference/adding-an-mfc-class.md).

- Další informace o tom, jak vytvořit třídy ATL naleznete v tématu [jednoduchý objekt knihovny ATL](../atl/reference/adding-an-atl-simple-object.md).

> [!NOTE]
> Šablona **přidat podporu ATL do MFC** nevytváří žádné třídy, ale místo toho nakonfiguruje projekt, který používá knihovnu ATL. Další informace najdete v tématu [podpory knihovny ATL v projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

Chcete-li vytvořit třídu C++, které nepoužívají knihovnu MFC, ATL nebo CLR, použijte **třídy C++** šablony **C++** skupiny nainstalovaných šablon. Další informace najdete v tématu [Přidání generické třídy jazyka C++](../ide/adding-a-generic-cpp-class.md).

Jsou k dispozici dva druhy založené na formulářích třídy jazyka C++. První z nich, [třídy CFormView](../mfc/reference/cformview-class.md), vytvoří třídy knihovny MFC. Je druhý řádek vytvoří třídu CLR Windows Forms.

## <a name="add-class-dialog-box"></a>dialogové okno Přidat třídu

**Přidat třídu** dialogové okno obsahuje šablony, které vám umožní:

- Otevření odpovídajícího průvodce, pokud je k dispozici. Další informace najdete v tématu [přidat funkce pomocí průvodců kódem](../ide/adding-functionality-with-code-wizards-cpp.md).

   \- nebo –

- Automaticky vytvořte novou třídu do projektu přidejte příslušné soubory a zdrojový kód.

Můžete přistupovat **přidat třídu** dialogové **projektu** nabídce **Průzkumníka řešení**, nebo [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code).

> [!NOTE]
> Při pokusu přidat třídu, která není vhodné pro aktuální projekt, zobrazí se chybová zpráva. Vyberte **OK** se vrátíte **přidat třídu** dialogové okno.

### <a name="add-class-templates"></a>Přidání šablony třídy

Existují čtyři kategorie **přidat třídu** šablony: .NET, ATL, MFC a obecný. Když vyberete šablonu v **šablony** podokně text popisující, váš výběr se zobrazí v části **kategorie** a **šablony** podoken.

#### <a name="net"></a>.NET

|Šablona|Průvodce|
|--------------|------------|
|Webová služba ASP.NET|Není k dispozici|
|Komponentní třída (.NET)|Není k dispozici|
|Instalační program tříd (.NET)|Není k dispozici|
|Uživatelský ovládací prvek (.NET)|Není k dispozici|
|Windows Form (.NET)|Není k dispozici|

#### <a name="atl"></a>ATL

|Šablona|Průvodce|
|--------------|------------|
|Přidat podporu ATL do MFC|Není k dispozici|
|Komponenta knihovny ATL Active Server Page|[Průvodce komponentami ATL active server page](../atl/reference/atl-active-server-page-component-wizard.md)|
|Ovládací prvek ATL|[Průvodce ovládacími prvky ATL](../atl/reference/atl-control-wizard.md)|
|ATL Dialog|[Průvodce dialogem ATL](../atl/reference/atl-dialog-wizard.md)|
|Komponenta knihovny ATL modelu COM + 1.0|[Průvodce komponentami ATL COM + 1.0](../atl/reference/atl-com-plus-1-0-component-wizard.md)|
|Příjemce knihovny ATL OLEDB|[Průvodce příjemcem ATL OLE DB](../atl/reference/atl-ole-db-consumer-wizard.md)|
|Připojit zprostředkovatele služeb OLEDB knihovny ATL|[Průvodce zprostředkovatelem ATL OLE DB](../atl/reference/atl-ole-db-provider-wizard.md)|
|Stránka vlastností knihovny ATL|[Průvodce stránkou vlastností ATL](../atl/reference/atl-property-page-wizard.md)|
|Jednoduchý objekt knihovny ATL|[Průvodce jednoduchým objektem ATL](../atl/reference/atl-simple-object-wizard.md)|
|Zprostředkovatel události rozhraní WMI|Průvodce zprostředkovatele událostí WMI|
|Zprostředkovatel instancí rozhraní WMI|Průvodce instance zprostředkovatele rozhraní WMI|

#### <a name="mfc"></a>MFC

|Šablona|Průvodce|
|--------------|------------|
|Třída knihovny MFC|[Průvodce přidáním třídy MFC](../mfc/reference/mfc-add-class-wizard.md)|
|Třída knihovny MFC z ovládacího prvku ActiveX|[Přidání třídy z Průvodce ovládacím prvkem ActiveX](../ide/add-class-from-activex-control-wizard.md)|
|Třída knihovny MFC z TypeLib|[Přidání třídy z Průvodce knihovnou typů](../mfc/reference/add-class-from-typelib-wizard.md)|
|Příjemce ODBC knihovny MFC|[Průvodce příjemcem MFC ODBC](../mfc/reference/mfc-odbc-consumer-wizard.md)|

#### <a name="generic-classes"></a>Obecné třídy

|Šablona|Průvodce|
|--------------|------------|
|Generické třídy jazyka C++|[Průvodci obecnými třídami C++](../ide/generic-cpp-class-wizard.md)|
