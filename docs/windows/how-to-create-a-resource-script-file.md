---
title: 'Postupy: vytváření prostředků (C++)'
ms.date: 02/14/2019
f1_keywords:
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
ms.openlocfilehash: 93bee6319d356128f56c1886d395cf25db372e80
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79443868"
---
# <a name="how-to-create-resources-c"></a>Postupy: vytváření prostředků (C++)

Prostředky pro svůj projekt můžete vytvořit takto:

- Pomocí souboru skriptu prostředků.

   > [!NOTE]
   > Tento krok je nezbytný, než přidáte prostředky.

- Přidání prostředků do projektu a použití **prostředky**.

- Vytváření přizpůsobených prostředků pomocí šablony prostředků

## <a name="use-resource-script-files"></a>Použití souborů skriptu prostředků

Před vytvořením a přidáním nových prostředků do projektu je nutné nejprve vytvořit soubor skriptu prostředků (. RC).

> [!NOTE]
> Soubor skriptu prostředků můžete přidat do existujícího projektu načteného do integrovaného vývojového prostředí sady Visual Studio. Nemůžete vytvořit samostatný skript prostředku mimo projekt, i když soubory šablony prostředků (. RCT) je možné vytvořit kdykoli.

### <a name="to-create-a-resource-script-file"></a>Vytvoření souboru skriptu prostředků

1. Umístěte fokus na svou existující složku projektu v **Průzkumník řešení**, například *MyProject*.

   > [!NOTE]
   > Nepleťte si složku projektu se složkou řešení v **Průzkumník řešení**. Pokud umístíte fokus do složky **řešení** , nebudete mít stejné možnosti pro **Přidání nové položky** .

1. V nabídce přejděte do **projektu** > **Přidat novou položku**.

1. Vyberte složku **vizuálu C++**  a v pravém podokně zvolte položku **soubor prostředků (. RC)** .

1. Do textového pole **název** zadejte název souboru skriptu prostředků a vyberte **otevřít**.

### <a name="to-open-a-resource-script-file"></a>Otevření souboru skriptu prostředků

Prostředky můžete zobrazit v souboru skriptu prostředků, aniž by byl otevřen projekt. Soubor skriptu se otevře v okně dokumentu na rozdíl od **prostředky**.

> [!NOTE]
> Některé příkazy jsou k dispozici pouze v případě, že je soubor otevřen samostatně, tzn. mimo projekt, aniž by bylo nutné nejprve načíst projekt. Chcete-li například použít příkaz **Uložit jako** a uložit soubor s jiným formátem nebo názvem souboru, je nutné soubor otevřít samostatně.

- Chcete-li otevřít soubor skriptu prostředků mimo projekt, přejděte v nabídce do **souboru** > **otevřít**a vyberte možnost **soubor**. Přejděte do souboru skriptu prostředků, zvýrazněte soubor a klikněte na **otevřít**.

    > [!NOTE]
    > Může nastat situace, kdy budete chtít zobrazit obsah souboru skriptu prostředků projektu bez použití editorů prostředků k otevření prostředku. Například můžete chtít vyhledat řetězec ve všech dialogových oknech v souboru prostředků, aniž byste je museli otevírat samostatně. Soubor prostředků v textovém formátu můžete snadno otevřít, chcete-li zobrazit všechny prostředky, které obsahuje, a dokončit globální operace podporované v textovém editoru.
    >
    > Chcete-li otevřít soubor skriptu prostředků v textovém formátu, použijte šipku rozevíracího seznamu na pravé straně tlačítka **otevřít** ve výše uvedeném kroku a vyberte možnost **otevřít v programu**. Vyberte položku **Editor zdrojového kódu (text)** a z rozevíracího seznamu **Otevřít jako** vyberte **text** a prostředek se otevře v editoru **zdrojového kódu** .

- Chcete-li otevřít více skriptů prostředků, postupujte podle výše uvedeného kroku pro každý soubor, který chcete otevřít, například *source1. RC* a *SOURCE2. RC*. Poté, když jsou oba soubory. RC otevřeny v samostatných oknech dokumentů, buď použijte nabídku **okna** , nebo klikněte pravým tlačítkem myši na jeden ze souborů a zvolte možnost **Nová vodorovná skupina karet** nebo **Nová svislá skupina karet**. Okna jsou nyní rozložená tak, abyste je mohli zobrazit současně.

> [!TIP]
> Soubory skriptu prostředků můžete otevřít tak, že kliknete pravým tlačítkem na soubor. rc v **Průzkumník řešení**, vyberete **otevřít v programu** a zvolíte **Editor zdrojového kódu (text)** .

Při sestavování aplikace MFC (Microsoft Foundation Class) pro systém Windows pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md)vygeneruje průvodce základní sadu souborů, včetně souboru skriptu prostředků (. RC), který obsahuje základní funkce knihovny MFC. Tyto funkce specifické pro knihovnu MFC však nejsou k dispozici při úpravách souboru. RC pro aplikace systému Windows, které nejsou založené na knihovně MFC. Patří sem průvodce kódem, řetězce v nabídce, seznam obsahu pro ovládací prvky pole se seznamem a hostování ovládacího prvku ActiveX.

- Chcete-li přidat podporu knihovny MFC se souborem skriptu prostředků otevřený, v **prostředky**zvýrazněte složku Resources (například *MFC. RC*). Poté v [okno Vlastnosti](/visualstudio/ide/reference/properties-window)nastavte **režim MFC** na **hodnotu true**.

  > [!NOTE]
  > Kromě nastavení **režimu MFC**musí být soubor. RC součástí projektu knihovny MFC. Pouze nastavení **režimu MFC** na **hodnotu true** v souboru. rc v projektu Win32 neposkytne funkce MFC.

## <a name="create-resources"></a>Vytváření prostředků

Prostředek můžete vytvořit jako nový výchozí prostředek, což znamená prostředek, který není založen na šabloně, nebo jako prostředek vytvořený za šablonou.

Použijte okno **prostředky** k zobrazení souborů prostředků obsažených ve vašich projektech. Rozbalením horní složky, například *Project1. RC*, se zobrazí typy prostředků v tomto souboru. Rozbalením jednotlivých typů prostředků zobrazíte jednotlivé prostředky daného typu.

> [!TIP]
> Chcete-li otevřít okno **prostředky** , přejděte do nabídky **zobrazení** > **Další Windows** > **prostředky** nebo stiskněte klávesu **CTRL**+**SHIFT**+**E**.

Můžete také kliknout pravým tlačítkem myši na okno **prostředky** a spustit místní nabídku příkazů nebo dvakrát kliknout na záhlaví a uvolnit okno. Klikněte pravým tlačítkem myši na záhlaví příkazů pro příkazy, které řídí chování okna. Další informace najdete v tématu [Správa systému Windows](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

**Prostředky** Windows obsahuje dialogové okno **Přidat prostředek** s následujícími vlastnostmi pro přidání prostředků do projektu desktopové aplikace C++ Windows:

| Vlastnost | Popis |
|---|---|
| **Typ prostředku** | Zadejte druh prostředku, který chcete vytvořit.<br/><br/>Můžete rozbalit kategorie prostředků kurzoru a dialogového okna a odhalit další prostředky, které jsou umístěny v *. \Microsoft Visual Studio \<verze\>\VC\VCResourceTemplates\\< LCID\>\mfc.RCT*. Pokud potřebujete přidat soubory. RCT, umístěte je sem nebo zadejte jinou [cestu zahrnutí](../windows/how-to-specify-include-directories-for-resources.md). Zdroje zobrazené na nejvyšší úrovni v ovládacím prvku strom jsou výchozí prostředky, které nabízí Visual Studio. Prostředky v souborech. RCT se zobrazí na druhé úrovni v příslušné kategorii. Není k dispozici žádný přednastavený limit počtu souborů. RCT, které můžete přidat.<br/><br/> |
| **New** | Vytvořte prostředek na základě typu vybraného v poli **typ prostředku** a otevřete prostředek v příslušném editoru.<br/><br/>Například pokud vytvoříte prostředek dialogového okna, otevře se prostředek v [editoru dialogových oken](../windows/dialog-editor.md). |
| **Import** | Otevřete dialogové okno **importovat** a přejděte k prostředku, který chcete importovat do aktuálního projektu.<br/><br/>Můžete importovat rastrový obrázek, ikonu, kurzor, HTML, zvuk (. WAV) nebo vlastní soubor prostředků. |
| **Uživatelská** | Otevřete dialogové okno **Nový vlastní prostředek** a vytvořte vlastní prostředek.<br/><br/>Obsahuje také vlastnost **typ prostředku** , která poskytuje textové pole pro zadání názvu vlastního typu prostředku. Při C++ ukončení se vizuál automaticky převede na velká písmena. Vlastní prostředky se upravují jenom v [binárním editoru](../windows/binary-editor.md). |

Když vytvoříte nový prostředek, přiřadí vám C++ vizuál jedinečný název, například `IDD_Dialog1`. Toto ID prostředku můžete upravit úpravou vlastností prostředku, a to buď v přidruženém editoru prostředků, nebo v [okno Vlastnosti](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> Nezadávejte název prostředku nebo ID, které jsou rezervované v rámci sady Visual Studio. Rezervované názvy jsou `DESIGNINFO`, `HWB`a `TEXTINCLUDE`a rezervované ID `255`.

### <a name="to-create-a-resource"></a>Vytvoření prostředku

- V **prostředky**vyberte soubor. RC a pak použijte **Upravit** > **Přidat prostředek** a zvolte typ prostředku, který chcete přidat do projektu.

   > [!TIP]
   > Můžete také kliknout pravým tlačítkem na soubor. rc v **prostředky** a zvolit **Přidat prostředek** z místní nabídky.

- V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku projektu, vyberte **Přidat** > **Přidat prostředek** a zvolte typ prostředku, který chcete přidat do projektu.

   > [!NOTE]
   > Pokud v projektu ještě nemáte soubor. RC, tento krok ho vytvoří. Pak můžete tento krok opakovat a přidat do nového souboru. RC konkrétní typy prostředků.

- V [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code)klikněte pravým tlačítkem myši na třídu, vyberte **Přidat** > **Přidat prostředek** a zvolte typ prostředku, který chcete přidat do projektu.

- Použijte **projekt** nabídky > **Přidat prostředek**.

## <a name="use-resource-templates"></a>Použití šablon prostředků

Šablona prostředku je přizpůsobený prostředek, který jste uložili jako soubor. RCT. Šablona prostředků pak slouží jako výchozí bod pro vytváření prostředků. Šablony prostředků šetří čas při vývoji dalších prostředků nebo skupin prostředků, které sdílejí funkce, jako jsou standardní ovládací prvky nebo opakující se prvky. Například pokud chcete v několika dialogových oknech zahrnout tlačítko Help s ikonou loga společnosti, vytvořte novou šablonu dialogového okna a upravte ji pomocí tlačítka Help a loga.

Po přizpůsobení šablony prostředku uložte změny do složky šablony nebo do umístění uvedeného v cestě include, aby se nová šablona prostředku zobrazila pod jejím typem prostředku v dialogovém okně **Přidat prostředek** . Nyní můžete novou šablonu prostředků použít jak často potřebujete.

> [!NOTE]
> Editor prostředků automaticky poskytuje jedinečné ID prostředku. Podle potřeby můžete upravit [vlastnosti prostředku](../windows/changing-the-properties-of-a-resource.md) .

> [!NOTE]
> Soubory šablon konkrétního jazyka umístěte do podadresářů hlavního adresáře šablon. Například soubory šablon jenom v angličtině jdou do *složky..\\< adresář šablon prostředků\>\ 1033*.
>
> Visual Studio vyhledá nové soubory. RCT ve složce *\Program Files\Microsoft Visual Studio \<verze\>\VC\VCResourceTemplates*, *\Program Files\Microsoft Visual Studio \<verze > \VC\VCRESOURCETEMPLATES\\< LCID\>* (například LCID 1033 pro angličtinu) nebo kdekoli v [cestě include](../windows/how-to-specify-include-directories-for-resources.md). Pokud upřednostňujete ukládání souborů. RCT do jiného umístění, musíte do cesty include přidat umístění.

### <a name="to-create-and-use-a-resource-template"></a>Vytvoření a použití šablony prostředků

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na projekt a vyberte **Přidat** > **Přidat novou položku**.

1. V podokně **šablony:** vyberte **soubor šablony prostředků (. RCT)** .

1. Zadejte název a umístění nového souboru *. RCT* a klikněte na tlačítko **otevřít**.

   Nový soubor *. RCT* se přidá do projektu a zobrazí se v **Průzkumník řešení** ve složce **Resources (prostředky** ).

1. Poklikejte na soubor *. RCT* a otevře se v okně dokumentu. Prostředky přidáte tak, že kliknete pravým tlačítkem na soubor v okně dokumentu a zvolíte **Přidat prostředek**.

   Můžete přizpůsobit přidané prostředky a uložit soubor *. RCT* .

1. V podokně **prostředky** klikněte pravým tlačítkem na soubor *. RC* a vyberte **Přidat prostředek**.

1. Vyberte znaménko plus ( **+** ) vedle prostředku a rozbalte tak uzel prostředku a zobrazte šablony, které jsou pro daný prostředek k dispozici.

1. Dvakrát klikněte na šablonu, kterou chcete použít.

   Přidaný prostředek můžete podle potřeby upravit v editoru prostředků.

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>Převod existujícího souboru prostředků na šablonu

V otevřeném souboru skriptu prostředků přejděte v nabídce na **soubor** > **uložit \<*filename*> jako**. Zadejte umístění a zvolte **OK**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Postupy: Správa prostředků](../windows/how-to-copy-resources.md)<br/>
[Postupy: Zahrnutí prostředků v čase kompilace](../windows/how-to-include-resources-at-compile-time.md)<br/>