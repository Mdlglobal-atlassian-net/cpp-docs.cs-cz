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
ms.openlocfilehash: dbb1d1d4b865380abde189ae6a72a1bfc3755840
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320845"
---
# <a name="how-to-create-resources-c"></a>Postupy: Vytvoření prostředků (C++)

**Zobrazení prostředků** okno zobrazuje soubory prostředků zahrnuté ve vašich projektech. Rozbalením složky nejvyšší úrovně (například *Project1.rc*) ukazuje typy prostředků v rámci, že soubor a rozbalením každého typu prostředku lze zobrazit jednotlivé prostředky daného typu.

> [!TIP]
> Otevření okna zobrazení prostředků, vyberte **zobrazení prostředků** na **zobrazení** nabídce (nebo použijte **Ctrl** + **Shift**  +  **E**).
>
> Klikněte pravým tlačítkem můžete použít také u **zobrazení prostředků** okno místní nabídku příkazů nebo dvakrát klikněte na záhlaví okna ukotvit nebo uvolnit okna. Pravým tlačítkem myši záhlaví poskytuje další příkazy, kterými lze ovládat chování okna. Další informace najdete v tématu [Windows Management](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

**Zobrazení prostředků** zahrnuje windows **přidat prostředek** dialogové okno s následující vlastnosti, které chcete přidat prostředky do projektu aplikace klasické pracovní plochy Windows C++:

|Vlastnost|Popis|
|--|----|
|**Typ prostředku**|Určuje typ prostředku, který chcete vytvořit.<br/><br/>Lze rozbalit kategorie prostředků kurzoru a dialogového okna, čímž odhalíte další prostředky. Tyto prostředky jsou umístěny v ...\Microsoft Visual Studio \<verze\>\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Pokud přidáte soubory .rct, je umístit do tohoto adresáře nebo zadejte jiný [zahrnout cestu](../windows/how-to-specify-include-directories-for-resources.md). Prostředky v těchto souborech se potom objeví na druhé úrovni pod příslušnou kategorií. Není nijak omezený počet souborů .rct, můžete přidat.<br/><br/>Prostředky zobrazené na nejvyšší úrovni stromové struktury jsou výchozí prostředky, které jsou k dispozici v systému Visual Studio.|
|**Nové**|Vytvoří prostředek v závislosti na typu vybraného v **typ prostředku** pole a prostředek se otevře ve vhodném editoru. Například pokud vytvoříte prostředek dialogového okna, otevře se v [editoru dialogového okna](../windows/dialog-editor.md).|
|**Import**|Otevře **importovat** dialogovému oknu, kde můžete přejít k prostředku je chcete importovat do aktuálního projektu. Můžete importovat bitmapy, ikony, kurzor, HTML, zvuku (. WAV), nebo soubory vlastních prostředků.|
|**Vlastní**|Otevře **nový vlastní prostředek** dialogovému oknu, kde můžete vytvořit vlastní prostředek. Vlastní prostředky jsou upravit jen v binárním editoru.|

**Přidat prostředek** dialogové okno obsahuje **nový vlastní prostředek** dialogové okno s následující vlastností, chcete-li vytvořit nový vlastní prostředek v projektu jazyka C++:

|Vlastnost|Popis|
|--|----|
|**Typ prostředku**|Poskytuje textového pole zadejte název vlastní typ prostředku. Visual C++ automaticky změní na velké název při ukončení **nový vlastní prostředek** dialogové okno.|

> [!NOTE]
> **Editor prostředků** nebo **zobrazení prostředků** není k dispozici ve verzích Express.

## <a name="resource-scripts"></a>Skripty prostředků

Předtím, než vytvoříte a přidáte nové prostředky do projektu, musíte nejprve vytvořit skript prostředků (soubor .rc).

> [!NOTE]
> Skript prostředků (soubor .rc) lze přidat pouze do existujícího projektu, který je načten do vývojového prostředí (IDE) pro Visual Studio. Nelze vytvořit samostatný skript prostředků (mimo projekt). Šablony prostředků (soubory .rct) lze vytvořit kdykoli.

### <a name="to-create-a-resource-script"></a>Postup vytvoření skriptu prostředků

1. Přesuňte fokus na složku existujícího projektu v **Průzkumníka řešení**, například *MyProject*.

   > [!NOTE]
   > Nepleťte si složku projektu se složkou řešení v **Průzkumníka řešení**. Pokud přesunete fokus na **řešení** složka, budou možnosti v **přidat novou položku** dialogové okno se bude lišit.

1. Na **projektu** nabídce vyberte možnost **přidat novou položku**.

1. Vyberte **Visual C++** složky, klikněte na tlačítko **soubor prostředků (.rc)** v pravém podokně.

1. Zadejte název vašeho skriptu prostředků v **název** textového pole a vyberte **otevřít**.

### <a name="to-open-a-resource-script"></a>Chcete-li spustit skript prostředků

Prostředky můžete zobrazit ve skriptu prostředků bez nutnosti otevřít projekt. Soubor skriptu se otevře v okně dokumentu, nikoli **zobrazení prostředků** okna.

> [!NOTE]
> Některé příkazy jsou dostupné, jenom když je soubor otevřen samostatné (mimo projekt). Otevření souboru samostatné znamená, že otevírání bez první načtení projektu.
>
> Například pro uložení souboru do jiného formátu nebo jako jiný název souboru (jako **uložit jako** příkazu není k dispozici pro soubor v projektu). Pokud otevřete projekt první pomocí **souboru** > **otevřete** > **projektu**, tyto příkazy nejsou k dispozici.

#### <a name="to-open-a-resource-script-outside-of-a-project"></a>Chcete-li otevřít skriptu prostředků mimo projekt

1. Z **souboru** nabídce vyberte možnost **otevřít**, klikněte na tlačítko **souboru**.

1. Přejděte do souboru skriptu prostředků, zvýrazněte soubor a zvolte **otevřít**.

#### <a name="to-open-multiple-resource-scripts-outside-of-a-project"></a>Chcete-li spustit více skripty prostředků mimo projekt

1. Otevřete oba samostatné soubory prostředků. Například otevřete *Source1.rc* a *Source2.rc*.

1. Z **souboru** nabídce zvolte **otevřít**a pak vyberte **souboru**.

1. Přejděte do první souboru skriptu prostředků, kterou chcete otevřít (*Source1.rc*), vyberte ho a zvolte možnost **otevřete**.

1. Opakujte předchozí krok pro druhý .rc soubor otevřít (*Source2.rc*).

   Oba soubory .rc jsou nyní otevřené v samostatných dokumentech systému windows.

1. Použití **okno** nabídce (nebo klikněte pravým tlačítkem na jeden ze souborů .rc) a zvolte **Nová vodorovná skupina karet** nebo **Nová svislá skupina karet**.

   Systému windows jsou teď vedle sebe, je možné současně zobrazit.

Může nastat situace, kdy budete chtít zobrazit obsah souboru projektu prostředků skriptů (.rc) bez nutnosti otevřít prostředek, jako je například dialogové okno, v jeho editoru konkrétní prostředek. Můžete například hledání řetězce napříč všechna dialogová okna v souboru prostředků, aniž byste museli otevřít každý z nich samostatně.

Snadno můžete otevřít soubor prostředků v textovém formátu zobrazit všechny prostředky, které obsahuje a dokončete globální operací podporované textového editoru.

> [!NOTE]
> Editory prostředků nečtou přímo .rc nebo `resource.h` soubory. Nástroj resource compiler jejich kompiluje do soubory .aps, které se spotřebovávají editory prostředků. Tento soubor je kompilační krok a ukládá pouze datový symbolické. Jako normální zkompilovat procesu, se zahodí informace, které nejsou symbolické (například komentáře) v průběhu kompilace. Pokaždé, když se soubor .aps získá synchronizována se soubor .rc, se znovu vygeneroval soubor .rc (například když uložíte, editor prostředků přepíše soubor .rc a `resource.h` souboru). Všechny změny samotné prostředky zůstanou zahrnuté v souboru .rc, ale komentáře jsou ztraceny, jakmile dojde k přepsání souboru .rc. Informace o tom, jak zachovat komentáře, naleznete v tématu [zahrnutí prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).

### <a name="to-open-a-resource-script-file-in-text-format"></a>K otevření souboru skriptu prostředků v textovém formátu

1. Z **souboru** nabídky vyberte možnost **otevřít**, klikněte na tlačítko **souboru**.

1. V **otevřít soubor** dialogové okno, přejděte do souboru skriptu prostředků, které chcete zobrazit v textovém formátu.

1. Zvýrazněte soubor a pak vyberte šipku rozevíracího seznamu na **otevřít** (na pravé straně tlačítka).

1. Zvolte **otevřít v** z rozevírací nabídky a vybereme **Editor zdrojového kódu (textu)**.

1. Z **otevřít jako** rozevíracího seznamu vyberte **Text**.

   Prostředek se otevře v **zdrojový kód** editoru.

> [!TIP]
> Je zde zástupce pravým tlačítkem myši na soubor .rc v **Průzkumníka řešení**, zvolte **otevřít v programu...**  a vyberte **Editor zdrojového kódu (textu)**.

## <a name="resources"></a>Prostředky

Prostředek můžete vytvořit jako nové výchozí prostředek (prostředek, který není založen na šabloně) nebo jako prostředek vzorované po šablony.

Při vytváření nového prostředku jazyka Visual C++ přiřadí jedinečný název, například `IDD_Dialog1`. Toto ID prostředku lze přizpůsobit úpravou vlastností pro prostředek v editoru přidružený prostředek nebo v [okno vlastností](/visualstudio/ide/reference/properties-window).

> [!NOTE]
> Nezadávejte název prostředku nebo ID, který je vyhrazený pro Visual Studio. Vyhrazené názvy jsou DESIGNINFO, HWB a TEXTINCLUDE a vyhrazené ID je 255.

### <a name="to-create-a-resource"></a>Vytvoření prostředku

Můžete vytvořit nový prostředek pomocí jedné z následujících akcí:

- V **zobrazení prostředků**, vyberte soubor .rc, pak použijte **upravit** > **přidat prostředek** a vyberte typ prostředku, které chcete přidat do projektu.

   > [!TIP]
   > Můžete také kliknout pravým tlačítkem soubor .rc v **zobrazení prostředků** a zvolte **přidat prostředek** z místní nabídky.

- V **Průzkumníka řešení**, klikněte pravým tlačítkem na složku projektu, vyberte **přidat** > **přidat prostředek** a vyberte typ prostředku, které chcete přidat do projektu.

   > [!NOTE]
   > Pokud ještě nemáte souboru .rc v projektu, tento krok ho vytvoří. Opakujte tento krok a přidejte konkrétní typy prostředků do nového souboru .rc.

- V [zobrazení tříd](/visualstudio/ide/viewing-the-structure-of-code), klikněte pravým tlačítkem na třídu, vyberte **přidat** > **přidat prostředek** a vyberte typ prostředku, které chcete přidat do projektu.

- V **projektu** nabídce vyberte možnost **přidat prostředek**.

### <a name="support-for-mfc"></a>Podpora knihovny MFC

Obvykle Pokud vytvoříte aplikaci Microsoft Foundation Class (MFC) pro Windows pomocí [Průvodce aplikací knihovny MFC](../mfc/reference/mfc-application-wizard.md), průvodce vygeneruje základní sadu souborů (včetně souboru prostředků skriptů (.rc)), které obsahuje základní funkce KNIHOVNY MFC. Nicméně pokud upravujete soubor .rc pro aplikaci Windows není založena na knihovně MFC, následující funkce specifické pro knihovny MFC nejsou k dispozici: Průvodci kódem knihovny MFC, řetězce výzev nabídky zobrazí obsah pole se seznamem a hostování ovládacího prvku ActiveX.

#### <a name="to-add-mfc-support-to-a-resource-script-file"></a>Přidání podpory MFC do souboru skriptu prostředků

1. Otevření souboru skriptu prostředků.

1. V **zobrazení prostředků**, zvýrazněte složku prostředků (například *MFC.rc*).

1. V [okno vlastností](/visualstudio/ide/reference/properties-window), nastavte **MFC režimu** vlastnost **True**.

   > [!NOTE]
   > Kromě nastavení této vlastnosti musí být soubor .rc součástí projektu knihovny MFC. Například pouhé nastavení **MFC režimu** k **True** na který #zahrnuje soubor v projektu Win32 vám neposkytne funkcí knihovny MFC.

## <a name="resource-templates"></a>Šablony prostředků

Prostředek šablony je vlastní prostředek, který jste uložili jako soubor .rct. Šablony prostředků pak slouží jako výchozí bod pro vytváření prostředků. Šablony prostředků ušetřit čas při vývoji další prostředky nebo skupiny prostředků, které sdílejí funkce, jako je například standardní ovládací prvky nebo opakované prvků. Pokud chcete zahrnout tlačítko nápovědy s ikonou logo společnosti v několika dialogových oknech, vytvořte novou šablonu pole dialogové okno a přizpůsobit pomocí tlačítka nápovědy a logo.

Po přizpůsobení šablony prostředků, uložte změny do složky šablony (nebo umístění zadaná v cestě k zahrnutí) tak, aby nového prostředku šablony se zobrazí v části jeho typ prostředku v **přidat prostředek** dialogové okno. Nyní můžete nového prostředku šablony tak často, podle potřeby.

> [!NOTE]
> Editor prostředků automaticky poskytuje jedinečné prostředku. Můžete zkontrolovat, jestli [vlastnosti prostředku](../windows/changing-the-properties-of-a-resource.md) podle potřeby.

> [!NOTE]
> Umístěte soubory šablon specifické pro jazyk v podadresářích adresáře hlavní šablony. Například umístíte soubory šablon anglické v... \\< adresář prostředků šablony\>\1033. Visual Studio vyhledá nové RCT – soubory v sadě Visual Studio \Program Files\Microsoft \<verze\>\VC\VCResourceTemplates v sadě Visual Studio \Program Files\Microsoft \<verze > \VC\VCResourceTemplates\\< LCID\> (např. 1033 pro angličtinu) *nebo* kdekoli [zahrnout cestu](../windows/how-to-specify-include-directories-for-resources.md). Pokud chcete ukládat soubory RCT v jiném umístění, například dokumenty, musíte tuto složku, sada Visual Studio můžete najít soubor RCT přidat do cesty zahrnutí.

### <a name="to-create-a-resource-template"></a>Vytvoření šablony prostředků

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na projekt.

1. V místní nabídce vyberte **přidat** > **přidat novou položku**.

1. V **šablony:** vyberte **soubor šablony zdrojů (.rct)**.

1. Zadejte název a umístění souboru nového .rct a zvolte **otevřít**.

   Nový soubor .rct se přidá do vašeho projektu a zobrazí se v **Průzkumníka řešení** pod **prostředky** složky.

1. Poklikejte na soubor .rct, otevřete ho v okně dokumentu. Pokud chcete přidat prostředky, klikněte pravým tlačítkem na soubor v okně dokumentu a zvolte **přidat prostředek**.

   Můžete přizpůsobit tyto prostředky a uložte soubor .rct.

### <a name="to-create-a-new-resource-from-a-template"></a>Chcete-li vytvořit nový prostředek ze šablony

1. V **zobrazení prostředků** podokně klikněte pravým tlačítkem na soubor .rc a zvolte **přidat prostředek** z místní nabídky.

1. Vyberte znaménko plus (**+**) u prostředků, rozbalte uzel zdroje a zobrazí se všechny šablony, které jsou k dispozici pro daný prostředek.

1. Dvakrát klikněte na šablonu, kterou chcete použít.

1. Přidání prostředku upravte podle potřeby v jeho editor prostředků.

### <a name="to-convert-an-existing-resource-file-to-a-template"></a>Chcete-li převést existující soubor prostředků do šablony

1. Otevřete soubor .rc jako samostatný soubor.

1. Na **souboru** nabídce vyberte možnost **Uložit \< *filename*> jako**.

1. Zadejte umístění a zvolte **OK**.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Soubory prostředků](../windows/resource-files-visual-studio.md)<br/>
[Správa prostředků](../windows/how-to-copy-resources.md)<br/>
[Zahrnutí prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md)<br/>