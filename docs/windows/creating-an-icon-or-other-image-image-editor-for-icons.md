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
ms.openlocfilehash: d10593ffbae7aef55adc3334057402b6952d8ba7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59027594"
---
# <a name="how-to-create-an-icon-or-other-image"></a>Postupy: Vytvoření ikony nebo jiného obrázku

Můžete vytvořit novou bitovou kopii, rastrový obrázek, ikona, kurzoru nebo panelu nástrojů a pak použít **Editor obrázků** přizpůsobit její vzhled. Můžete také vytvořit nový rastrový obrázek vzorované po [šablony resource](../windows/how-to-use-resource-templates.md).

## <a name="icons-and-cursors-image-resources-for-display-devices"></a>Ikony a kurzory: Prostředky obrázků pro zobrazovací zařízení

Ikony a kurzory jsou grafických prostředků, které může obsahovat více bitových kopií v různých velikostech a barevná schémata pro různé typy zařízení s displejem. Také obsahuje aktivního bodu kurzoru, místo Windows používá ke sledování jeho pozice. Ikony a kurzory jsou vytvořeny a upravovat pomocí **Editor obrázků**, protože jsou rastrové obrázky a další Image.

Při vytváření nové ikony nebo kurzoru, **Editor obrázků** nejprve vytvoří bitovou kopii standardních typů. Na obrázku je zpočátku vyplněn barvou obrazovky (transparentní). Pokud se image nachází kurzor, aktivního bodu je zpočátku levém horním rohu se souřadnicemi `0,0`.

Ve výchozím nastavení **Editor obrázků** podporuje vytváření dalších bitových kopií pro zařízení uvedené v následující tabulce. Můžete vytvářet Image pro jiná zařízení tak, že zadáte parametry šířku, výšku a počet barev do **vlastní Image** dialogové okno.

|Barva|Šířka (v pixelech)|Výška (v pixelech)|
|-----------|----------------------|-----------------------|
|Monochromatický|16|16|
|Monochromatický|32|32|
|Monochromatický|48|48|
|Monochromatický|64|64|
|Monochromatický|96|96|
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

### <a name="create-a-device-image-icon-or-cursor"></a>Vytvoření obrázku zařízení (ikony nebo kurzoru)

Když vytvoříte nové ikony nebo kurzoru prostředků **Editor obrázků** nejprve vytvoří bitovou kopii v konkrétním stylu (32 × 32, 16 barvy ikony a 32 × 32, monochromatický pro ukazatele). Můžete přidat obrázky v různých velikostech a styly do počáteční ikony nebo kurzoru a upravit každé další image, podle potřeby pro jiné zobrazovací zařízení. Můžete také upravit obrázek pomocí operace vyjmutí a vložení z existujícího typu obrázku nebo z bitmapy vytvořené v programu grafiky.

Při otevření prostředku ikony nebo kurzoru v [Editor obrázků](../windows/image-editor-for-icons.md), image, většina úzce odpovídající aktuální zobrazovací zařízení se otevře ve výchozím nastavení.

> [!NOTE]
> Pokud váš projekt již neobsahuje soubor .rc, přečtěte si téma [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

**Nový &lt;zařízení&gt; typ obrázku** dialogové okno umožňuje vytvořit nový obrázek zařízení zadaného typu. Chcete-li otevřít **nový \<zařízení > obrázku** dialogové okno, přejděte do nabídky **Image** > **nový typ obrázku**. Jsou zahrnuty následující vlastnosti **cílový typ obrázku** a **vlastní**.

**Cílový typ obrázku** dostupné image typy, kde můžete vybrat image seznamů vlastností typu, který chcete spustit:

||||
|-|-|-|
|-16 x 16, 16 barev|-48 x 48, 16 barev|-96 x 96, 16 barev|
|-16 x 16, 256 barev|-48 x 48, 256 barev|-96 x 96, 256 barev|
|-16 x 16, monochromatický|- 48 x 48, Monochrome|- 96 x 96, Monochrome|
|-32 x 32, 16 barev|-64 x 64, 16 barev||
|-32 x 32, 256 barev|-64 x 64, 256 barev||
|- 32 x 32, Monochrome|- 64 x 64, Monochrome||

> [!NOTE]
> V tomto seznamu se nezobrazí žádné existující Image.

**Vlastní** vlastnost otevře **vlastní Image** dialogovému oknu, ve kterém můžete vytvořit novou bitovou kopii s vlastní velikost a počet barev.

**Vlastní Image** dialogové okno umožňuje vytvořit novou bitovou kopii s vlastní velikost a počet barev. Jsou zahrnuty následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Šířka**|Poskytuje prostor pro zadání šířku vlastního obrázku v pixelech (1-512, limit 2048).|
|**Výška**|Poskytuje prostor pro zadání výška vlastního obrázku v pixelech (1-512, limit 2048).|
|**Barvy**|Poskytuje prostor můžete zvolit počet barev pro vlastní image: 2, 16 nebo 256.|

Použití **otevřete &lt;zařízení&gt; Image** dialogové okno otevřete obrázcích zařízení v projektech C++. Zobrazí seznam stávajících zařízení imagí v aktuální prostředek (bitové kopie, které jsou součástí aktuální prostředek). Je zahrnut následující vlastnost:

|Vlastnost|Popis|
|---|---|
|**Aktuálních Imagí**|Obsahuje seznam imagí, které jsou zahrnuté v prostředku. Výběr typu image, kterou chcete otevřít.|

#### <a name="to-create-a-new-icon-or-cursor"></a>Chcete-li vytvořit nové ikony nebo kurzoru

1. V [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources), klikněte pravým tlačítkem na váš *.rc* souboru a pak zvolte **vložit prostředků**. Pokud už máte existující prostředek obrázku vaše *.rc* souboru, jako je například kurzor, můžete kliknout pravým tlačítkem **kurzor** a pak zvolte položku **vložení kurzoru**.

1. V [vložit prostředek – dialogové okno](../windows/add-resource-dialog-box.md)vyberte **ikonu** nebo **kurzor** a zvolte **nový**. U ikon tato akce vytvoří prostředek s ikonou s 32 × 32, ikona 16 barev. Pro ukazatele, 32 × 32, bude vytvořena monochromatický obrázek (barvami. 2).

   Pokud symbol plus (**+**) se zobrazí u typu prostředku bitové kopie v **vložit prostředků** dialogové okno, znamená to, že šablony nástrojů jsou k dispozici. Vyberte znaménko plus rozbalit seznam šablon, vyberte šablonu a zvolte **nový**.

### <a name="to-add-an-image-for-a-different-display-device"></a>Přidání obrázku pro zařízení s jiným zobrazením

1. Přejděte do nabídky **Image** > **nový obrázek zařízení**, nebo klikněte pravým tlačítkem **Editor obrázků** podokně a zvolte **nový obrázek zařízení**.

1. Vyberte typ image, kterou chcete přidat. Můžete také vybrat **vlastní** vytváření ikony jejíž velikost není k dispozici ve výchozím seznamu.

### <a name="to-copy-a-device-image"></a>Kopírování obrázku zařízení

1. Přejděte do nabídky **Image** > **otevřít obraz zařízení** a pak vyberte bitovou kopii z aktuálního seznamu imagí. Například zvolte 32 × 32, 16 barev verzi ikonu.

1. Zkopírujte aktuálně zobrazené obraz bitové kopie (**Ctrl**+**C**).

1. Otevřete jiný obrázek ikony v jiném **Editor obrázků** okna. Například otevřete 16 × 16, ikona verzi 16 barev.

1. Vložit obrázek ikony (**Ctrl**+**V**) z jednoho **Editor obrázků** okně do jiné. Pokud vkládáte větší velikost do menší velikost, můžete změnit velikost obrázku obslužné rutiny ikonu.

### <a name="to-delete-a-device-image"></a>Odstranění obrázku zařízení

Zatímco obrázek ikony se zobrazí v **Editor obrázků**, přejděte do nabídky **Image** > **odstranění obrázku zařízení**. Když odstraníte poslední obrázek ikony v prostředku, prostředek se také odstraní.

> [!NOTE]
> Po stisknutí klávesy **Del** klíče, obrázky a barvy nakreslen na ikonu se odstraní, ale zůstává na ikonu a teď ji můžete upravit. Pokud stisknete **Del** omylem, stiskněte klávesu **Ctrl**+**Z** vrátit zpět akce.

### <a name="to-create-transparent-or-inverse-regions-in-device-images"></a>Vytvoření průhledných nebo obrácených oblastí v obrázcích zařízení

V [Editor obrázků](../windows/image-editor-for-icons.md), počáteční ikony nebo kurzoru bitová kopie má atribut transparentní. I když jsou obdélníkové obrázky ikon a kurzorů, nejsou mnoho tak zobrazeny, protože jsou transparentní části obrázku a základní image na obrazovce zobrazí prostřednictvím ikony nebo kurzoru. Při přetažení ikonu, části obrázku se může vyskytovat obrácenou barvu. Vytvoření tohoto efektu tak, že nastavíte barvu obrazovky a inverzní barvy v [okno barvy](../windows/colors-window-image-editor-for-icons.md).

Obrazovky a inverzní barvy použijete s ikonami a kurzory tvar a barva odvozené image nebo přiřadit inverzní oblasti. Barvy označují částí bitové kopie, které mají tyto atributy. Můžete změnit barvy, které představují vlastnosti obrazovky a inverzní barev v úpravách. Tyto změny nemají vliv na vzhled ikony nebo kurzoru v aplikaci.

> [!NOTE]
> Dialogová okna a příkazy nabídek, zobrazí se mohou lišit od těch popsaných v **pomáhají** v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, přejděte do nabídky **nástroje** > **nastavení importu a exportu**. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

#### <a name="to-create-transparent-or-inverse-regions"></a>Vytvoření průhledných nebo obrácených oblastí

1. V **barvy** okně zvolte volič **barvy obrazovky** nebo **inverzní barvy**.

1. Použijte na obrazovce nebo inverzní barvy na používání nástroje kreslení obrázku. Další informace o kreslicích nástrojů najdete v tématu [používání nástroje kreslení](using-a-drawing-tool-image-editor-for-icons.md).

#### <a name="to-change-the-screen-or-inverse-color"></a>Chcete-li změnit barvu obrazovky nebo inverzní

1. Vyberte buď **barvy obrazovky** selektor nebo **inverzní barvy** selektor.

1. Zvolte barvu z **barvy** paletu **barvy** okna.

   Pro další selektor se automaticky přiřadí doplňkovou barvu.

   > [!TIP]
   > Pokud dvakrát kliknete **barvy obrazovky** nebo **inverzní barvy** pro výběr [dialogové okno Výběr vlastních barev](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) se zobrazí.

### <a name="use-the-256-color-palette"></a>Použití 256 barev

Použití **Editor obrázků**, ikony a kurzory mohou být velikosti velké (64 × 64) s 256 barev palety zvolit z. Po vytvoření prostředku, je vybrat styl obrázku zařízení.

#### <a name="to-create-a-256-color-icon-or-cursor"></a>Chcete-li vytvořit 256barevných ikony nebo kurzoru

1. V [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources), klikněte pravým tlačítkem na váš *.rc* souboru a pak zvolte **vložit prostředků**. Pokud už máte existující prostředek obrázku vaše *.rc* souboru, jako je například kurzor, můžete kliknout pravým tlačítkem **kurzor** a pak zvolte položku **vložení kurzoru**.

1. V [vložit prostředek – dialogové okno](../windows/add-resource-dialog-box.md)vyberte **ikonu** nebo **kurzor** a zvolte **nový**.

1. Přejděte do nabídky **Image** > **nový obrázek zařízení** a vyberte požadovaný styl 256 barev obrázku.

#### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Vybrat barvu z palety barev 256 pro velké ikony

Pro kreslení pomocí výběru z palety barev 256, je nutné vybrat barvy z **barvy** paletu [okno barvy](../windows/colors-window-image-editor-for-icons.md).

1. Vyberte velké ikony nebo kurzoru nebo vytvořte novou velké ikony nebo kurzoru.

1. Výběr barvy z 256 barev zobrazených v **barvy** paletu **barvy** okna.

   Barva vybraná se stane aktuální barvu v **barvy** paletu **barvy** okna.

   > [!NOTE]
   > Počáteční paletu 256barevných imagí odpovídá na paletě vrácené `CreateHalftonePalette` rozhraní Windows API. Všechny ikony určený pro prostředí Windows by měl palety můžete zabránit blikání během palety realizace.

### <a name="to-set-a-cursors-hot-spot"></a>Nastavení aktivního bodu kurzoru

Aktivního bodu kurzoru je bod, na které odkazuje Windows ve sledování pozice kurzoru. Ve výchozím nastavení, je nastavení aktivního bodu do levého horního rohu kurzor se souřadnicemi `0,0`. **Aktivního bodu** vlastnost [okno vlastností](/visualstudio/ide/reference/properties-window) ukazuje souřadnice aktivního bodu.

1. Na [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md), zvolte **nastavte aktivní bod** nástroj.

1. Vyberte pixel, kterou chcete přiřadit jako aktivního bodu kurzoru.

   **Hotspot** vlastnost **vlastnosti** v okně se zobrazí nové souřadnice.

### <a name="to-create-and-save-a-bitmap-as-a-gif-or-jpeg"></a>Vytvoříte a uložíte rastrový obrázek GIF nebo JPEG

Když vytvoříte rastrový obrázek, vytvoření image ve formátu rastrový obrázek (BMP). Image můžete, ale uložit jako ve formátu GIF nebo JPEG nebo v jiné formáty.

> [!NOTE]
> Tento proces se nevztahuje na ikony a kurzory.

1. Přejděte do nabídky **souboru** > **otevřít**a pak vyberte **souboru**.

1. V **dialogové okno Nový soubor**, zvolte **Visual C++** složku, pak vyberte **rastrového obrázku (BMP)** v **šablony** a vyberte  **Otevřít**.

   Rastrový obrázek se otevře v **Editor obrázků**.

1. Podle potřeby proveďte změny na nový rastrový obrázek.

1. Se stále otevřen v rastrového obrázku **Editor obrázků**, přejděte do nabídky **souboru** > **Uložit *filename*.bmp jako**.

1. V **uložit soubor jako** dialogového okna zadejte název, kterému chcete udělit soubor a rozšíření, která označuje formát souboru, které chcete v **název_souboru** pole. Například *myfile.gif*.

   > [!NOTE]
   > Musíte vytvořit nebo otevřít rastrového obrázku mimo projekt Pokud chcete uložit v jiném formátu. Pokud vytvoříte nebo jej otevřete v projektu **uložit jako** příkaz nebude k dispozici. Další informace najdete v tématu [zobrazování prostředků v prostředků skriptu souboru mimo of projekt (samostatný)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

1. Vyberte **Uložit**.

### <a name="to-convert-an-image-from-one-format-to-another"></a>K převedení obrázku z jednoho formátu do druhého

Můžete otevřít ve formátu GIF nebo JPEG imagí v **Editor obrázků** a uložit je jako rastrové obrázky. Můžete také otevřít soubor rastrového obrázku a uložit jako ve formátu GIF nebo JPEG. Při práci s obrázky nemusí být součástí projektu pro úpravy ve vývojovém prostředí (naleznete v tématu [samostatný obrázek úpravy](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)).

1. Otevřít obrázek v **Editor obrázků**.

1. Přejděte do nabídky **souboru** > **Uložit *filename* jako**.

1. V **uložit soubor jako** v dialogu **název_souboru** zadejte název souboru a rozšíření, která označuje požadovaný formát.

1. Vyberte **Uložit**.

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>Chcete-li přidat nový prostředek obrázku do nespravované projektu C++

1. V [zobrazení prostředků](how-to-create-a-resource-script-file.md#create-resources), klikněte pravým tlačítkem na váš *.rc* souboru a pak zvolte **vložit prostředků**. Pokud už máte existující prostředek obrázku vaše *.rc* souboru, jako je například kurzor, můžete jednoduše klikněte pravým tlačítkem **kurzor** a pak zvolte položku **vložení kurzoru**.

1. V [vložit prostředek – dialogové okno](../windows/add-resource-dialog-box.md), vyberte typ, který chcete vytvořit prostředek obrázku (**rastrový obrázek**, například) klikněte na tlačítko **nový**.

   Pokud symbol plus (**+**) se zobrazí u typu prostředku bitové kopie v **vložit prostředků** dialogové okno, znamená to, že šablony nástrojů jsou k dispozici. Vyberte znaménko plus rozbalit seznam šablon, vyberte šablonu a zvolte **nový**.

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>Chcete-li přidat nový prostředek obrázku do projektu v .NET programovací jazyk

1. V **Průzkumníka řešení**, klikněte pravým tlačítkem na složku projektu (například *WindowsApplication1*).

1. V místní nabídce vyberte **přidat**, klikněte na tlačítko **přidat novou položku**.

1. V **kategorie** podokně rozbalte **místní položky projektu** složky, klikněte na tlačítko **prostředky**.

1. V **šablony** podokně, vyberte typ prostředku, který chcete přidat do projektu.

   Prostředek se přidá do vašeho projektu v **Průzkumníka řešení** a prostředek se otevře [Editor obrázků](../windows/image-editor-for-icons.md). Teď můžete použít všechny nástroje, které jsou k dispozici v **Editor obrázků** úprava vaší bitové kopie. Další informace o přidávání bitové kopie do spravovaných projektů naleznete v tématu [načítání obrázku v době návrhu](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms).

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
[Icons](/windows/desktop/menurc/icons)<br/>
[Cursors](/windows/desktop/menurc/cursors)<br/>-->