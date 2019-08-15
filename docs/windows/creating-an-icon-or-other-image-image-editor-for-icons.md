---
title: 'Postupy: Vytvoření ikony nebo jiného obrázku'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
- vc.editors.image.editing
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
- cursors [C++], creating
- image resources [C++], display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices [C++], creating icons for
- cursors [C++], hot spots
- icons [C++], types
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
- New Device Image command
- display devices [C++], adding images
- cursors [C++], adding
- icons, adding
- display devices [C++], copying images
- cursors [C++], copying
- icons, copying
- cursors [C++], deleting
- display devices [C++], deleting device image
- icons, erasing
- icons, deleting
- cursors [C++], undoing changes
- icons, undoing changes
- cursors [C++], screen regions
- inverse colors [C++], device images
- transparent regions, device images
- transparency, device images
- Image editor [C++], device images
- inverse regions, device images
- cursors [C++], transparent regions
- screen colors
- regions, transparent
- icons [C++], transparent regions
- display devices [C++], transparent and screen regions
- transparent regions in devices
- regions, inverse
- colors [C++], Image editor
- device projects [C++], transparent images
- icons [C++], screen regions
- 256-color palette
- cursors [C++], color
- colors [C++], icons
- colors [C++], cursors
- icons, color
- colors [C++], icons and cursors
- color palettes, 256-color
- palettes, 256-color
- cursors [C++], hot spots
- hot spots
- .gif files [C++], saving bitmaps as
- jpg files [C++], saving bitmaps as
- jpeg files [C++], saving bitmaps as
- .jpg files [C++], saving bitmaps as
- Image editor [C++], converting image formats
- gif files [C++], saving bitmaps as
- bitmaps [C++], converting formats
- .jpeg files [C++], saving bitmaps as
- graphics [C++], converting formats
- images [C++], converting formats
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
ms.openlocfilehash: 2605644533d55527a07904ac89fa937db1b2eec5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513745"
---
# <a name="how-to-create-an-icon-or-other-image"></a>Postupy: Vytvoření ikony nebo jiného obrázku

Můžete vytvořit nový obrázek, rastrový obrázek, ikonu, kurzor nebo panel nástrojů a potom použít **Editor obrázků** k přizpůsobení jeho vzhledu. Po vytvoření [šablony prostředku](../windows/how-to-use-resource-templates.md)můžete také vytvořit nový rastrový obrázek.

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>Ikony a kurzory: Prostředky obrázků pro zobrazovací zařízení

Ikony a kurzory jsou grafické prostředky, které mohou obsahovat více obrázků v různých velikostech a barevná schémata pro různé typy zobrazovacích zařízení. Kurzor má také aktivní bod, umístění, ve kterém systém Windows používá ke sledování jeho pozice. Ikony a kurzory jsou vytvářeny a upravovány pomocí **editoru obrázků**, stejně jako rastrové obrázky a další obrázky.

Když vytvoříte novou ikonu nebo kurzor, **Editor obrázků** nejprve vytvoří obrázek standardního typu. Obrázek je původně vyplněn barvou obrazovky (průhledná). Pokud je obrázek kurzorem, je aktivním bodem zpočátku levý horní roh s souřadnicemi `0,0`.

**Editor obrázků** standardně podporuje vytváření dalších imagí pro zařízení uvedená v následující tabulce. Můžete vytvořit obrázky pro jiná zařízení zadáním parametrů šířka, Výška a počet barev do dialogového okna **vlastní obrázek** .

|Barva|Šířka (pixely)|Výška (v pixelech)|
|-----------|----------------------|-----------------------|
|Jednobarevné|16|16|
|Jednobarevné|32|32|
|Jednobarevné|48|48|
|Jednobarevné|64|64|
|Jednobarevné|96|96|
|16|16|16|
|16|32|32|
|16|64|64|
|16|48|48|
|16|96|96|
|256|16|16|
|256|32|32|
|256|48|48|
|256|64|64|
|256|96|96|

### <a name="create-a-device-image-icon-or-cursor"></a>Vytvoření obrázku zařízení (ikona nebo kurzor)

Když vytvoříte novou ikonu nebo prostředek kurzoru, **Editor obrázků** nejprve vytvoří obrázek v konkrétním stylu (32 × 32, 16 barev pro ikony a 32 × 32, monochromaticke pro kurzory). Pak můžete přidat obrázky v různých velikostech a stylech na počáteční ikonu nebo kurzor a podle potřeby upravit každou další bitovou kopii pro různá zobrazovací zařízení. Můžete také upravit obrázek pomocí operace vyjmutí a vložení z existujícího typu obrázku nebo z rastrového obrázku vytvořeného v grafickém programu.

Když v [editoru obrázků](../windows/image-editor-for-icons.md)otevřete ikonu nebo prostředek kurzoru, otevře se ve výchozím nastavení obrázek přesně vyhovující aktuálnímu zobrazovacímu zařízení.

> [!NOTE]
> Pokud projekt ještě neobsahuje soubor. RC, přečtěte si téma [Vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

Dialogové **okno &lt;nový&gt; typ obrázku zařízení** umožňuje vytvořit novou image zařízení zadaného typu. Chcete-li otevřít dialogové okno **nový \<obrázek > zařízení** , přejděte na příkaz **Obrázek** > nabídky**nový typ obrázku**. K dispozici jsou následující vlastnosti **cílového typu obrázku** a **vlastní**.

Vlastnost **typ cílové image** obsahuje seznam dostupných typů imagí, kde můžete vybrat typ obrázku, který chcete otevřít:

||||
|-|-|-|
|– 16 × 16, 16 barev|-48 x 48, 16 barev|-96 x 96, 16 barev|
|– 16 × 16, 256 barev|-48 x 48, 256 barev|-96 x 96, 256 barev|
|– 16 × 16, monochromatické|-48 × 48, monochromatický|-96 × 96, monochromatický|
|-32 x 32, 16 barev|-64 x 64, 16 barev||
|-32 x 32, 256 barev|-64 x 64, 256 barev||
|-32 × 32, monochromatický|-64 × 64, monochromatický||

> [!NOTE]
> V tomto seznamu se nezobrazí žádné existující image.

**Vlastní** vlastnost otevře dialogové okno **vlastní obrázek** , ve kterém můžete vytvořit novou image s vlastní velikostí a počtem barev.

Dialogové okno **vlastní obrázek** umožňuje vytvořit novou image s vlastní velikostí a počtem barev. K dispozici jsou následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Délk**|Poskytuje prostor pro zadání šířky vlastní image v pixelech (1-512, limit 2048).|
|**Výška**|Poskytuje prostor pro zadání výšky vlastní image v pixelech (1-512, limit 2048).|
|**Barvy**|Poskytuje prostor pro výběr počtu barev pro vlastní image: 2, 16 nebo 256.|

Pomocí dialogového **okna &lt;otevřít&gt; obrázek zařízení** otevřete obrázky zařízení v C++ projektech. Zobrazuje seznam existujících imagí zařízení v aktuálním prostředku (obrázky, které jsou součástí aktuálního prostředku). K dispozici je následující vlastnost:

|Vlastnost|Popis|
|---|---|
|**Aktuální obrázky**|Zobrazuje seznam imagí obsažených v prostředku. Vyberte typ obrázku, který chcete otevřít.|

#### <a name="to-create-a-new-icon-or-cursor"></a>Vytvoření nové ikony nebo kurzoru

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)klikněte pravým tlačítkem na soubor *. RC* a pak zvolte **Vložit prostředek**. Pokud již máte existující prostředek image v souboru *. RC* , jako je například kurzor, můžete kliknout pravým tlačítkem myši na složku **kurzor** a vybrat možnost **Vložit kurzor**.

1. V [dialogovém okně Vložit prostředek](../windows/add-resource-dialog-box.md)vyberte **ikonu** nebo **kurzor** a klikněte na tlačítko **Nový**. V případě ikon Tato akce vytvoří prostředek ikony s ikonou 32 × 32, 16 Barva. Pro kurzory se vytvoří obrázek 32 × 32, monochromatický (2D barevný) obraz.

   Pokud se vedle položky typ **+** prostředku obrázku v dialogovém okně **Vložit prostředek** objeví znaménko plus (), znamená to, že jsou k dispozici šablony panelu nástrojů. Vyberte znaménko plus a rozbalte seznam šablon, vyberte šablonu a zvolte **Nový**.

### <a name="to-add-an-image-for-a-different-display-device"></a>Přidání obrázku pro jiné zobrazovací zařízení

1. Přejděte na **Obrázek** > nabídky**Nová Image zařízení**nebo klikněte pravým tlačítkem v podokně **Editor obrázků** a vyberte **Nový obrázek zařízení**.

1. Vyberte typ obrázku, který chcete přidat. Můžete také vybrat možnost **vlastní** a vytvořit ikonu, jejíž velikost není k dispozici ve výchozím seznamu.

### <a name="to-copy-a-device-image"></a>Kopírování obrázku zařízení

1. Přejděte na **Obrázek** > nabídky**otevřít obrázek zařízení** a vyberte obrázek ze seznamu aktuální obrázky. Například vyberte verzi ikony 32 × 32, 16 barev.

1. Zkopíruje aktuálně zobrazený obrázek ikony (**CTRL**+**C**).

1. Otevřete jiný obrázek ikony v jiném okně **editoru obrázků** . Otevřete například ikonu 16 × 16, 16 barev.

1. Vložte obrázek ikony (**CTRL**+**V**) z jednoho okna **editoru obrázků** do druhé. Pokud vkládáte větší velikost do menší velikosti, můžete použít táhla ikon pro změnu velikosti obrázku.

### <a name="to-delete-a-device-image"></a>Postup odstranění obrázku zařízení

I když se obrázek ikony zobrazuje v **editoru obrázků**, přejděte do nabídky **Obrázek** > **Odstranit obrázek zařízení**. Když odstraníte poslední obrázek ikony v prostředku, odstraní se i prostředek.

> [!NOTE]
> Když stisknete klávesu **del** , odstraní se obrázky a barvy, které jste vykreslili na ikonu, ale ikona zůstane a Vy ji teď můžete změnit. Kliknete-li na tlačítko **del** omylem, vraťte akci stisknutím **kombinace kláves CTRL**+**Z** .

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>Vytvoření průhledných nebo inverzních oblastí v obrázcích zařízení

V [editoru obrázků](../windows/image-editor-for-icons.md)má počáteční ikona nebo obrázek kurzoru transparentní atribut. I když jsou obrázky ikon a kurzorů pravoúhlé, mnoho se nezobrazuje, protože části obrázku jsou transparentní a podkladový obrázek na obrazovce se zobrazuje přes ikonu nebo kurzor. Když přetáhnete ikonu, části obrázku se mohou zobrazit v obrácené barvě. Tento efekt můžete vytvořit nastavením barvy obrazovky a inverzní barvy v [okně barvy](../windows/colors-window-image-editor-for-icons.md).

Obrazovka a informující barvy, které použijete pro ikony a kurzory, buď tvarování a barva odvozeného obrázku, nebo přiřazení inverzních oblastí. Barvy označují části obrázku, které mají tyto atributy. Můžete změnit barvy, které reprezentují atributy barvy obrazovky a inverzní barvy v úpravách. Tyto změny neovlivní vzhled ikony nebo kurzoru v aplikaci.

> [!NOTE]
> Dialogová okna a příkazy nabídek, zobrazí se mohou lišit od těch popsaných v **pomáhají** v závislosti na aktivních nastaveních nebo edici. Pokud chcete změnit nastavení, přejděte na **nástroje** > nabídky**Import a export nastavení**. Další informace najdete v tématu [Přizpůsobení integrovaného vývojového prostředí (IDE) sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

#### <a name="to-create-transparent-or-inverse-regions"></a>Vytvoření průhledných nebo inverzních oblastí

1. V okně **barvy** klikněte na možnost selektor **obrazovky-barva** nebo **inverzní barva**.

1. Aplikujte na obrázek obrazovku nebo inverzní barvu pomocí nástroje pro kreslení. Další informace o nástrojích pro kreslení najdete v tématu [použití nástroje pro kreslení](using-a-drawing-tool-image-editor-for-icons.md).

#### <a name="to-change-the-screen-or-inverse-color"></a>Změna obrazovky nebo inverzní barvy

1. Vyberte buď výběr **barvy obrazovky** , nebo rozevírací selektor pro invertování **barev** .

1. Vyberte barvu z palety **barev** v okně **barvy** .

   Doplňková barva je automaticky přiřazena pro druhý selektor.

   > [!TIP]
   > Pokud dvakrát kliknete na výběr **barvy obrazovky** nebo **inverzní barvy** , zobrazí se [dialogové okno pro výběr vlastní barvy](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) .

### <a name="use-the-256-color-palette"></a>Použití palety barev 256

Pomocí **editoru obrázků**může být velikost ikon a kurzorů velká (64 × 64) s paletou 256-Color pro výběr. Po vytvoření prostředku se vybere styl obrázku zařízení.

#### <a name="to-create-a-256-color-icon-or-cursor"></a>Vytvoření ikony nebo kurzoru barvy 256

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)klikněte pravým tlačítkem na soubor *. RC* a pak zvolte **Vložit prostředek**. Pokud již máte existující prostředek image v souboru *. RC* , jako je například kurzor, můžete kliknout pravým tlačítkem myši na složku **kurzor** a vybrat možnost **Vložit kurzor**.

1. V [dialogovém okně Vložit prostředek](../windows/add-resource-dialog-box.md)vyberte **ikonu** nebo **kurzor** a klikněte na tlačítko **Nový**.

1. Přejít na **Obrázek** > nabídky**nové obrázek zařízení** a vybrat styl obrázku 256, který chcete.

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Výběr barvy z palety barev 256 pro velké ikony

Chcete-li kreslit s výběrem z palety barev 256, je nutné vybrat barvy z palety **barev** v [okně barvy](../windows/colors-window-image-editor-for-icons.md).

1. Vyberte velkou ikonu nebo kurzor nebo vytvořte novou velkou ikonu nebo kurzor.

1. Vyberte barvu ze barvy 256 zobrazené v paletě **barvy** v okně **barvy** .

   Vybraná barva se stane aktuální barvou v paletě **barvy** v okně **barvy** .

   > [!NOTE]
   > Počáteční paleta použitá pro barevné obrázky 256 se shoduje s paletou vrácenou `CreateHalftonePalette` rozhraním API systému Windows. Všechny ikony určené pro prostředí Windows by měly tuto paletu používat k tomu, aby se zabránilo blikání během realizace palety.

### <a name="to-set-a-cursors-hot-spot"></a>Nastavení aktivního bodu kurzoru

Aktivním bodem kurzoru je bod, na který Windows odkazuje při sledování pozice kurzoru. Ve výchozím nastavení je aktivní bod nastaven na levý horní roh kurzoru pomocí souřadnic `0,0`. Vlastnost **hotspot** v [okno Vlastnosti](/visualstudio/ide/reference/properties-window) zobrazuje souřadnice aktivního bodu.

1. Na [panelu nástrojů Editor obrázků](../windows/toolbar-image-editor-for-icons.md)vyberte nástroj **nastavit hotspot** .

1. Vyberte pixel, který chcete přiřadit jako aktivní bod kurzoru.

   Vlastnost **hotspot** v okně **vlastnosti** zobrazuje nové souřadnice.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Vytvoření a uložení rastrového obrázku jako souboru. gif nebo. jpeg

Při vytváření rastrového obrázku bude obrázek vytvořen ve formátu rastrového obrázku (. bmp). Obrázek ale můžete uložit jako GIF nebo JPEG nebo v jiných grafických formátech.

> [!NOTE]
> Tento proces se nevztahuje na ikony a kurzory.

1. Přejděte na **soubor** > nabídky**otevřít**a pak vyberte **soubor**.

1. V **dialogovém okně Nový soubor**zvolte složku **vizuál C++**  , pak v poli **šablony** vyberte **rastrový soubor (. bmp)** a vyberte **otevřít**.

   Rastrový obrázek se otevře v **editoru obrázků**.

1. Podle potřeby proveďte změny v novém bitmapě.

1. Když je bitmapa pořád otevřená v **editoru obrázků**, přejděte na **soubor** > nabídky**Uložit *filename*. bmp jako**.

1. V dialogovém okně **Uložit soubor jako** zadejte název, který chcete souboru, a příponu, která označuje požadovaný formát souboru v poli **název souboru** . Například *MyFile. gif*.

   > [!NOTE]
   > Je nutné vytvořit nebo otevřít rastrový obrázek mimo váš projekt, aby byl uložen jako jiný formát souboru. Pokud vytvoříte nebo otevřete v rámci projektu, příkaz **Uložit jako** nebude k dispozici. Další informace naleznete v tématu [zobrazení prostředků v souboru skriptu prostředků mimo projekt (samostatný)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

1. Vyberte **Uložit**.

### <a name="to-convert-an-image-from-one-format-to-another"></a>Převod obrázku z jednoho formátu na jiný

Obrázky GIF a JPEG můžete otevřít v **editoru obrázků** a uložit je jako rastrové obrázky. Můžete také otevřít rastrový soubor a uložit ho jako GIF nebo JPEG. Obrázky, se kterými pracujete, nemusí být součástí projektu pro úpravy ve vývojovém prostředí (viz [Úprava samostatného obrázku](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)).

1. Otevřete obrázek v **editoru obrázků**.

1. Do nabídky název **souboru** > **uložte jako**.

1. V dialogovém okně **Uložit soubor jako** v poli **název souboru** zadejte název souboru a příponu, které označují požadovaný formát.

1. Vyberte **Uložit**.

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Přidání nového prostředku obrázku do nespravovaného C++ projektu

1. V [prostředky](how-to-create-a-resource-script-file.md#create-resources)klikněte pravým tlačítkem na soubor *. RC* a pak zvolte **Vložit prostředek**. Pokud již máte existující prostředek image v souboru *. RC* , například kurzor, stačí kliknout pravým tlačítkem myši na složku **kurzor** a vybrat možnost **Vložit kurzor**.

1. V [dialogovém okně Vložit prostředek](../windows/add-resource-dialog-box.md)vyberte typ prostředku obrázku, který chcete vytvořit (například rastrový obrázek), a pak zvolte **Nový**.

   Pokud se vedle položky typ **+** prostředku obrázku v dialogovém okně **Vložit prostředek** objeví znaménko plus (), znamená to, že jsou k dispozici šablony panelu nástrojů. Vyberte znaménko plus a rozbalte seznam šablon, vyberte šablonu a zvolte **Nový**.

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Přidání nového prostředku obrázku do projektu v programovacím jazyce .NET

1. V **Průzkumník řešení**klikněte pravým tlačítkem myši na složku projektu (například *WindowsApplication1*).

1. V místní nabídce vyberte **Přidat**a pak zvolte **Přidat novou položku**.

1. V podokně **kategorie** rozbalte složku **místní položky projektu** a pak zvolte **prostředky**.

1. V podokně **šablony** vyberte typ prostředku, který chcete přidat do projektu.

   Prostředek se přidá do projektu v **Průzkumník řešení** a prostředek se otevře v [editoru obrázků](../windows/image-editor-for-icons.md). K úpravě image teď můžete použít všechny nástroje dostupné v **editoru imagí** . Další informace o přidání obrázků do spravovaného projektu naleznete v tématu [nasazování obrázku v době návrhu](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také:

[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
[Postupy: Úprava obrázku](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md)<br/>
[Postupy: Použití nástroje pro kreslení](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Postupy: Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
<!--
[Converting Bitmaps to Toolbars](../windows/converting-bitmaps-to-toolbars.md)<br/>
[Creating New Toolbars](../windows/creating-new-toolbars.md)<br/>
[Icons](/windows/win32/menurc/icons)<br/>
[Cursors](/windows/win32/menurc/cursors)<br/>-->