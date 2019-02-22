---
title: 'Postupy: Vytvoření prostředků (C++)'
ms.date: 02/14/2019
f1_keywords:
- vc.editors.resource
- vc.resvw.add.MFC
- vs.resourceview.F1
- vc.editors.insertresource
- vc.editors.newcustomresource
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
- resources [C++], viewing
- rc files [C++], viewing resources
- .rc files [C++], viewing resources
- resource script files [C++], viewing resources
- resource script files [C++], opening in text format
- .rc files [C++], opening in text format
- rc files [C++], opening in text format
- rc files [C++], adding MFC support
- .rc files [C++], adding MFC support
- MFC, adding support to resource scripts files
- resource script files [C++], adding MFC support
- toolbars [C++], resources
- resource toolbars
- resources [C++], creating
- Resource View window
- resources [C++], adding
- Add Resource dialog box [C++]
- Custom Resource Type dialog box [C++]
- language-specific template files [C++]
- resource templates
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: 768675a878891ebb75c7f42c12eae8dfcfa3510b
ms.sourcegitcommit: e540706f4e2675e7f597cfc5b4f8dde648b007bb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2019
ms.locfileid: "56676484"
---
# <a name="how-to-create-resources-c"></a>Postupy: Vytvoření prostředků (C++)

Může vytvářet prostředky pro váš projekt podle:

- Pomocí souboru skriptu prostředků. Tento krok je nezbytný, předtím, než přidáte prostředky.

- Přidávání prostředků do vašeho projektu. Tento krok ukazuje, jak používat **zobrazení prostředků**.

- Pomocí šablony resource vytvářet vlastní prostředky.

> [!NOTE]
> **Editor prostředků** a **zobrazení prostředků** nejsou k dispozici ve verzích Express.

## <a name="use-resource-script-files"></a>Použít soubory skriptu prostředků

Předtím, než vytvoříte a přidáte nové prostředky do projektu, musíte nejprve vytvořit soubor prostředků skriptů (.rc).

> [!NOTE]
> Skript prostředků můžete přidat pouze do existujícího projektu načten do integrovaného vývojového prostředí sady Visual Studio. Samostatné skriptu prostředků mimo projekt, nelze vytvořit, když šablony prostředků (soubory .rct) lze vytvořit kdykoli.

### <a name="to-create-a-resource-script-file"></a>K vytvoření souboru skriptu prostředků

1. Přesuňte fokus na složku existujícího projektu v **Průzkumníka řešení**, například *MyProject*.

   > [!NOTE]
   > Nepleťte si složku projektu se složkou řešení v **Průzkumníka řešení**. Pokud přesunete fokus na **řešení** složky, nebudete mít stejné **přidat novou položku** volby.

1. V nabídce, přejít na **projektu** > **přidat novou položku**.

1. Vyberte **Visual C++** složky a vyberte **soubor prostředků (.rc)** v pravém podokně.

1. Zadejte název souboru skriptu prostředku v **název** textového pole a vyberte **otevřít**.

### <a name="to-open-a-resource-script-file"></a>K otevření souboru skriptu prostředků

Prostředky můžete zobrazit v souboru skriptu prostředků bez nutnosti otevřít projekt. Soubor skriptu se otevře v okně dokumentu, nikoli **zobrazení prostředků**.

> [!NOTE]
> Některé příkazy jsou pouze k dispozici, pokud je soubor otevřený samostatně, což znamená mimo projekt nebo bez první načtení projektu. Chcete-li například použít **uložit jako** příkazu Uložit soubor pod jiným názvem formátu nebo soubor, soubor musí být otevřené samostatné.

- K otevření souboru skriptu prostředků mimo projekt, v nabídce, přejít na **souboru** > **otevřete**a zvolte **souboru**. Přejděte do souboru skriptu prostředků, zvýrazněte soubor a zvolte **otevřít**.

  - K otevření souboru skriptu prostředků v textovém formátu, použijte rozevírací šipku na pravé straně **otevřete** tlačítko v předchozím kroku a zvolte **otevřít v programu**. Vyberte **Editor zdrojového kódu (textu)** a od **otevřít jako** rozevíracího seznamu vyberte **Text**, a prostředek se otevře v **zdrojový kód**editoru.

    > [!NOTE]
    > Může nastat situace, kdy budete chtít zobrazit obsah souboru skriptu prostředků projektu bez použití editory prostředků Chcete-li otevřít prostředek. Můžete například hledání řetězce napříč všechna dialogová okna v souboru prostředků, aniž byste museli otevřít každý z nich samostatně. Snadno můžete otevřít soubor prostředků v textovém formátu zobrazit všechny prostředky, které obsahuje a dokončete globální operací podporované textového editoru.

- Chcete-li spustit více prostředků skripty, postupujte podle výše uvedené kroky pro každý soubor, který chcete otevřít, například *Source1.rc* a *Source2.rc*. Potom, když oba soubory .rc jsou spuštěné v systému windows v samostatných dokumentech, použít **okno** nabídku nebo klikněte pravým tlačítkem na jeden ze souborů .rc a zvolte **Nová vodorovná skupina karet** nebo **nové vertikální tabulátor Skupiny**. Systému windows jsou teď vedle sebe, je možné současně zobrazit.

> [!TIP]
> Soubory skriptu prostředků můžete otevřít také kliknutím pravým tlačítkem myši soubor .rc v **Průzkumníka řešení**zvolíte možnost **otevřít pomocí...**  a vyberete **Editor zdrojového kódu (textu)**.

### <a name="to-edit-a-resource-script-file"></a>Úprava souboru skriptu prostředků

- Chcete-li převést existující soubor prostředků do šablony, pomocí souboru skriptu prostředků v nabídce otevřít, přejděte na **souboru** > **Uložit \< *filename*> jako**. Potom zadejte umístění a zvolte **OK**.

Při vytvoření aplikace Microsoft Foundation Class (MFC) pro Windows pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md), průvodce vygeneruje základní sadu souborů, včetně skriptů (.rc) soubor prostředků), která obsahuje základní funkce knihovny MFC. Ale tyto funkce specifické pro knihovny MFC nejsou k dispozici při úpravách souboru .rc pro aplikace Windows není založena na knihovně MFC. To zahrnuje, průvodci kódem, řetězce výzev nabídky, obsah seznamu pro pole se seznamem a hostování ovládacího prvku ActiveX.

- Přidání podpory knihovny MFC, s otevření souboru skriptu prostředků v **zobrazení prostředků**, zvýrazněte složku prostředků (například *MFC.rc*). Pak v [okno vlastností](/visualstudio/ide/reference/properties-window), nastavte **MFC režimu** k **True**.

  > [!NOTE]
  > Kromě nastavení **MFC režimu**, není soubor .rc, musí být součástí projektu knihovny MFC. Pouhé nastavení **MFC režimu** k **True** na který #zahrnuje soubor v projektu Win32 vám neposkytne funkcí knihovny MFC.

## <a name="create-resources"></a>Vytvoření prostředků

Prostředek můžete vytvořit jako nové výchozí prostředek, to znamená prostředek, který není založen na šabloně, nebo jako prostředek vzorované po šablony.

Použití **zobrazení prostředků** okno k zobrazení soubory prostředků zahrnuté ve vašich projektech. Rozbalení horní složku, například *Project1.rc*, ukazuje typy prostředků v rámci tohoto souboru. Rozbalte jednotlivé typy prostředků Chcete-li zobrazit jednotlivé prostředky daného typu.

> [!TIP]
> Chcete-li otevřít **zobrazení prostředků** okno, přejděte do nabídky **zobrazení** > **zobrazení prostředků** nebo stiskněte klávesu **Ctrl** +  **SHIFT**+**E**.

Můžete použít kliknutím pravým tlačítkem na **zobrazení prostředků** okno místní nabídku příkazů nebo dvakrát klikněte na záhlaví okna ukotvení a uvolnit okna. Klikněte pravým tlačítkem na záhlaví okna pro další příkazy, které řídí chování okna. Další informace najdete v tématu [Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

**Zobrazení prostředků** zahrnuje windows **přidat prostředek** dialogové okno s následující vlastnosti, které chcete přidat prostředky do projektu aplikace klasické pracovní plochy Windows C++:

| Vlastnost | Popis |
|---|---|
| **Typ prostředku** | Zadejte typ prostředku, který chcete vytvořit.<br/><br/>Můžete rozbalit kategorie prostředků kurzoru a dialogového okna pole čímž odhalíte další prostředky, které jsou umístěny v ...\Microsoft Visual Studio \<verze\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Pokud je potřeba přidat soubory .rct, sem vložte nebo zadejte jiný [zahrnout cestu](../windows/how-to-specify-include-directories-for-resources.md).<br/><br/>Prostředky zobrazené na nejvyšší úrovni stromové struktury jsou výchozí prostředky poskytovaný sadou Visual Studio. Prostředky v souborech .rct objeví na druhé úrovni pod příslušnou kategorií. Není nijak omezený počet souborů .rct, můžete přidat.<br/><br/> |
| **Nové** | Vytvořit prostředek v závislosti na typu vybraného v **typ prostředku** pole a otevřít prostředek ve vhodném editoru.<br/><br/>Například pokud vytvoříte prostředek dialogového okna, otevře se v prostředku [editoru dialogového okna](../windows/dialog-editor.md). |
| **Import** | Otevřít **importovat** dialogové okno Přejít k prostředku, kterou chcete importovat do aktuálního projektu.<br/><br/>Můžete importovat bitmapy, ikony, kurzor, HTML, zvuku (. WAV), nebo soubory vlastních prostředků. |
| **Vlastní** | Otevřít **nový vlastní prostředek** dialogové okno vytvořit vlastní prostředek.<br/><br/>Zahrnuje také **typ prostředku** vlastnost, která obsahuje textové pole pro zadání názvu typu vlastního prostředku. Visual C++ automaticky změní na velké název při ukončení.<br/><br/>Vlastní prostředky jsou upravit jen v binárním editoru. |

Při vytváření nového prostředku jazyka Visual C++ přiřadí jedinečný název, například `IDD_Dialog1`. Toto ID prostředku lze přizpůsobit úpravou vlastností prostředků v editoru přidružený prostředek nebo v [okno vlastností](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> Nezadávejte název prostředku nebo ID, který je vyhrazený pro Visual Studio. Vyhrazené názvy jsou `DESIGNINFO`, `HWB`, a `TEXTINCLUDE`, a vyhrazené ID je `255`.

Chcete-li vytvořit využití prostředků, jeden z následujících akcí:

- V **zobrazení prostředků**, vyberte soubor .rc, pak použijte **upravit** > **přidat prostředek** a vyberte typ prostředku, které chcete přidat do projektu.

   > [!TIP]
   > Můžete také kliknout pravým tlačítkem soubor .rc v **zobrazení prostředků** a zvolte **přidat prostředek** z místní nabídky.

- V **Průzkumníka řešení**, klikněte pravým tlačítkem na složku projektu, vyberte **přidat** > **přidat prostředek** a vyberte typ prostředku, které chcete přidat do projektu.

   > [!NOTE]
   > Pokud ještě nemáte souboru .rc v projektu, tento krok ho vytvoří. Opakujte tento krok a přidejte konkrétní typy prostředků do nového souboru .rc.

- V [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na třídu, vyberte **přidat** > **přidat prostředek** a vyberte typ prostředku, které chcete přidat do projektu.

- Pomocí nabídky **projektu** > **přidat prostředek**.

## <a name="use-resource-templates"></a>Použití šablon prostředků

Prostředek šablony je vlastní prostředek, který jste uložili jako soubor .rct. Šablony prostředků pak slouží jako výchozí bod pro vytváření prostředků. Šablony prostředků ušetřit čas při vývoji další prostředky nebo skupiny prostředků, které sdílejí funkce, jako je například standardní ovládací prvky nebo opakované prvků. Pokud chcete zahrnout tlačítko nápovědy s ikonou logo společnosti v několika dialogových oknech, vytvořte novou šablonu pole dialogové okno a přizpůsobit pomocí tlačítka nápovědy a logo.

Po přizpůsobení šablony prostředků, uložte změny do složky šablony nebo umístění zadaná do cesty zahrnutí a tak, aby nového prostředku šablony se zobrazí v části jeho typ prostředku v **přidat prostředek** dialogové okno. Nyní můžete nového prostředku šablony tak často, podle potřeby.

> [!NOTE]
> Editor prostředků automaticky poskytuje jedinečné prostředku. Můžete zkontrolovat, jestli [vlastnosti prostředku](../windows/changing-the-properties-of-a-resource.md) podle potřeby.

> [!NOTE]
> Umístěte soubory šablon specifické pro jazyk v podadresářích adresáře hlavní šablony. Například soubory šablon anglické přejděte... \\< adresář prostředků šablony\>\1033. Visual Studio vyhledá nové soubory .rct v sadě Visual Studio \Program Files\Microsoft \<verze\>\VC\VCResourceTemplates \Program Files\Microsoft sady Visual Studio \<verze > \VC\VCResourceTemplates\\< LCID\> (například LCID 1033 pro angličtinu), nebo kdekoli [zahrnout cestu](../windows/how-to-specify-include-directories-for-resources.md). Pokud chcete uložit soubory .rct do jiného umístění, je nutné přidat do cesty zahrnutí umístění.

### <a name="to-create-and-use-a-resource-template"></a>Vytvoření a použití prostředku šablony

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt.

1. V místní nabídce vyberte **přidat** > **přidat novou položku**.

1. V **šablony:** vyberte **soubor šablony zdrojů (.rct)**.

1. Zadejte název a umístění souboru nového .rct a zvolte **otevřít**.

   Nový soubor .rct se přidá do vašeho projektu a zobrazí se v **Průzkumníka řešení** pod **prostředky** složky.

1. Poklikejte na soubor .rct, otevřete ho v okně dokumentu. Pokud chcete přidat prostředky, klikněte pravým tlačítkem na soubor v okně dokumentu a zvolte **přidat prostředek**.

   Můžete přizpůsobit vložené materiály a uložte soubor .rct.

1. V **zobrazení prostředků** podokně klikněte pravým tlačítkem na soubor .rc a zvolte **přidat prostředek**.

1. Vyberte znaménko plus (**+**) u prostředků, rozbalte uzel zdroje a zobrazit šablony, které jsou k dispozici pro daný prostředek.

1. Dvakrát klikněte na šablonu, kterou chcete použít.

   Přidání prostředku lze upravovat podle potřeby v jeho editor prostředků.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Postupy: Spravovat prostředky](../windows/how-to-copy-resources.md)<br/>
[Postupy: Zahrnutí prostředků v čase kompilace](../windows/how-to-include-resources-at-compile-time.md)<br/>