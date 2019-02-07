---
title: 'Ikony a kurzory: Prostředky obrázků pro zobrazovací zařízení (C++ Editor obrázků pro ikony)'
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
- vc.editors.image.editing
helpviewer_keywords:
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
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
ms.openlocfilehash: 027c3c0380a73c624432bbe45758b3296732949a
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55849942"
---
# <a name="icons-and-cursors-image-resources-for-display-devices-c-image-editor-for-icons"></a>Ikony a kurzory: Prostředky obrázků pro zobrazovací zařízení (C++ Editor obrázků pro ikony)

Ikony a kurzory jsou grafických prostředků, které může obsahovat více bitových kopií v různých velikostech a barevná schémata pro různé typy zařízení s displejem. Kurzor má také "aktivního bodu," požadované místo Windows používá ke sledování jeho pozice. Ikony a kurzory jsou vytvořeny a upravovat pomocí **Image** editoru, jako jsou rastrové obrázky a další Image.

Při vytváření nové ikony nebo kurzoru, **Image** editoru nejprve vytvoří bitovou kopii standardních typů. Na obrázku je zpočátku vyplněn barvou obrazovky (transparentní). Pokud se image nachází kurzor, aktivního bodu je zpočátku levý horní roh (souřadnice 0; 0).

Ve výchozím nastavení **Image** editor podporuje vytváření dalších bitových kopií pro zařízení uvedené v následující tabulce. Můžete vytvářet Image pro jiná zařízení tak, že zadáte parametry šířku, výšku a počet barev do [dialogové okno vlastní obrázek](custom-image-dialog-box-image-editor-for-icons.md).

> [!NOTE]
> Použití **Editor obrázků**, můžete zobrazit obrázky 32-bit, ale nemůžete je upravovat.

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

## <a name="create-a-device-image-icon-or-cursor"></a>Vytvoření obrázku zařízení (ikony nebo kurzoru)

Když vytvoříte nové ikony nebo kurzoru prostředků **Image** editoru nejprve vytvoří bitovou kopii v konkrétním stylu (32 × 32, 16 barvy ikony a 32 × 32, monochromatický pro ukazatele). Můžete přidat obrázky v různých velikostech a styly do počáteční ikony nebo kurzoru a upravit každé další image, podle potřeby pro jiné zobrazovací zařízení. Můžete také upravit obrázek pomocí operace vyjmutí a vložení z existujícího typu obrázku nebo z bitmapy vytvořené v programu grafiky.

Při otevření prostředku ikony nebo kurzoru v [editor obrázků](../windows/image-editor-for-icons.md), image, většina úzce odpovídající aktuální zobrazovací zařízení se otevře ve výchozím nastavení.

### <a name="new-ltdevicegt-image-type-dialog-box"></a>Nové &lt;zařízení&gt; dialogové okno typ obrázku

**Nový &lt;zařízení&gt; typ obrázku** dialogové okno umožňuje vytvořit nový obrázek zařízení zadaného typu. Otevřete **nový \<zařízení > obrázku** dialogu **nový typ obrázku** na **Image** nabídky. Jsou zahrnuty následující vlastnosti **cílový typ obrázku** a **vlastní**.

#### <a name="target-image-type"></a>Cílový typ obrázku

Seznam typů dostupné image. Vyberte typ obrázku, který chcete otevřít:

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

#### <a name="custom"></a>Vlastní

Otevře **vlastní Image** dialogovému oknu, ve kterém můžete vytvořit novou bitovou kopii s vlastní velikost a počet barev.

**Vlastní Image** dialogové okno umožňuje vytvořit novou bitovou kopii s vlastní velikost a počet barev. Jsou zahrnuty následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Šířka**|Poskytuje prostor pro zadání šířku vlastního obrázku v pixelech (1-512, limit 2048).|
|**Výška**|Poskytuje prostor pro zadání výška vlastního obrázku v pixelech (1-512, limit 2048).|
|**Barvy**|Poskytuje prostor můžete zvolit počet barev pro vlastní image: 2, 16 nebo 256.|

### <a name="open-ltdevicegt-image-dialog-box"></a>Otevřít &lt;zařízení&gt; dialogové okno Obrázek

Použití **otevřete &lt;zařízení&gt; Image** dialogové okno otevřete obrázcích zařízení v projektech C++. Zobrazí seznam stávajících zařízení imagí v aktuální prostředek (bitové kopie, které jsou součástí aktuální prostředek). Je zahrnut následující vlastnost:

|Vlastnost|Popis|
|---|---|
|**Aktuálních Imagí**|Obsahuje seznam imagí, které jsou zahrnuté v prostředku. Výběr typu image, kterou chcete otevřít.|

### <a name="to-create-a-new-icon-or-cursor"></a>Chcete-li vytvořit nové ikony nebo kurzoru

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a pak zvolte **vložit prostředků** z místní nabídky. (Pokud už máte existující prostředek obrázku v souboru .rc, jako je například kurzoru, kliknete pravým tlačítkem **kurzor** a pak zvolte položku **vložení kurzoru** z místní nabídky.)

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, přečtěte si téma [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. V [vložit prostředek – dialogové okno](../windows/add-resource-dialog-box.md)vyberte **ikonu** nebo **kurzor** a zvolte **nový**. U ikon tato akce vytvoří prostředek s ikonou s 32 × 32, ikona 16 barev. Pro ukazatele, 32 × 32, bude vytvořena monochromatický obrázek (barvami. 2).

   Pokud symbol plus (**+**) se zobrazí u typu prostředku bitové kopie v **vložit prostředků** dialogové okno, znamená to, že šablony nástrojů jsou k dispozici. Vyberte znaménko plus rozbalit seznam šablon, vyberte šablonu a zvolte **nový**.

## <a name="add-an-image-for-a-different-display-device"></a>Přidání obrázku pro zařízení s jiným zobrazením

1. Na **Image** nabídce vyberte možnost **nový obrázek zařízení** (nebo klikněte pravým tlačítkem **Editor obrázků** podokně a zvolte **nový obrázek zařízení** z místní nabídka).

1. Vyberte typ image, kterou chcete přidat. Můžete také vybrat **vlastní** vytváření ikony jejíž velikost není k dispozici ve výchozím seznamu.

## <a name="copy-a-device-image"></a>Kopírování obrázku zařízení

1. Na **Image** nabídce vyberte možnost **otevřít obraz zařízení** a pak vyberte bitovou kopii z aktuálního seznamu imagí. Například zvolte 32 × 32, 16 barev verzi ikonu.

1. Zkopírujte aktuálně zobrazené obraz bitové kopie (**Ctrl**+**C**).

1. Otevřete jiný obrázek ikony v jiném **Editor obrázků** okna. Například otevřete 16 × 16, ikona verzi 16 barev.

1. Vložit obrázek ikony (**Ctrl**+**V**) z jednoho **Editor obrázků** okně do jiné. Pokud vkládáte větší velikost do menší velikost, můžete změnit velikost obrázku obslužné rutiny ikonu.

## <a name="delete-a-device-image"></a>Odstranění obrázku zařízení

Zatímco obrázek ikony se zobrazí v **Image** editoru, vyberte **odstranění obrázku zařízení** z **Image** nabídky. Když odstraníte poslední obrázek ikony v prostředku, prostředek se také odstraní.

   > [!NOTE]
   > Po stisknutí klávesy **Del** klíče, obrázky a barvy nakreslen na ikonu se odstraní, ale zůstane ikona; nyní ji můžete upravit. Pokud stisknete **Del** omylem, můžete stisknout **Ctrl**+**Z** vrátit zpět akce.

## <a name="create-transparent-or-inverse-regions-in-device-images"></a>Vytvoření průhledných nebo obrácených oblastí v obrázcích zařízení

V [editor obrázků](../windows/image-editor-for-icons.md), počáteční ikony nebo kurzoru bitová kopie má atribut transparentní. I když jsou obdélníkové obrázky ikon a kurzorů, mnoho nezobrazí, protože části obrázku jsou transparentní; základní image na obrazovce zobrazí prostřednictvím ikony nebo kurzoru. Při přetažení ikonu, části obrázku se může vyskytovat obrácenou barvu. Vytvoření tohoto efektu tak, že nastavíte barvu obrazovky a inverzní barvy v [okno barvy](../windows/colors-window-image-editor-for-icons.md).

Obrazovky a inverzní barvy použijete s ikonami a kurzory tvar a barva odvozené image nebo přiřadit inverzní oblasti. Barvy označují částí bitové kopie, které mají tyto atributy. Můžete změnit barvy, které představují vlastnosti obrazovky a inverzní barev v úpravách. Tyto změny nemají vliv na vzhled ikony nebo kurzoru v aplikaci.

> [!NOTE]
> Dialogová okna a příkazy nabídek, zobrazí se mohou lišit od těch popsaných v **pomáhají** v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-create-transparent-or-inverse-regions"></a>Vytvoření průhledných nebo obrácených oblastí

1. V **barvy** okna, vyberte **barvy obrazovky** selektor nebo **inverzní barvy** selektor.

1. Použijte na obrazovce nebo inverzní barvy na používání nástroje kreslení obrázku. Další informace o kreslicích nástrojů najdete v tématu [používání nástroje kreslení](using-a-drawing-tool-image-editor-for-icons.md).

### <a name="to-change-the-screen-or-inverse-color"></a>Chcete-li změnit barvu obrazovky nebo inverzní

1. Vyberte buď **barvy obrazovky** selektor nebo **inverzní barvy** selektor.

1. Zvolte barvu z **barvy** paletu **barvy** okna.

   Pro další selektor se automaticky přiřadí doplňkovou barvu.

   > [!TIP]
   > Pokud dvakrát kliknete **barvy obrazovky** nebo **inverzní barvy** pro výběr [dialogové okno Výběr vlastních barev](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md) se zobrazí.

## <a name="use-the-256-color-palette"></a>Použití 256 barev

Použití **Image** editoru, ikony a kurzory může být velikosti velké (64 × 64) s 256 barev palety lze vybírat. Po vytvoření prostředku, je vybrat styl obrázku zařízení.

### <a name="to-create-a-256-color-icon-or-cursor"></a>Chcete-li vytvořit 256barevných ikony nebo kurzoru

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a pak zvolte **vložit prostředků** z místní nabídky. (Pokud už máte existující prostředek obrázku v souboru .rc, jako je například kurzoru, kliknete pravým tlačítkem **kurzor** a pak zvolte položku **vložení kurzoru** z místní nabídky.)

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. V [vložit prostředek – dialogové okno](../windows/add-resource-dialog-box.md)vyberte **ikonu** nebo **kurzor** a zvolte **nový**.

1. Na **Image** nabídce vyberte možnost **nový obrázek zařízení**.

1. Vyberte požadovaný styl 256 barev obrázku.

### <a name="to-choose-a-color-from-the-256-color-palette-for-large-icons"></a>Vybrat barvu z palety barev 256 pro velké ikony

Pro kreslení pomocí výběru z palety barev 256, je nutné vybrat barvy z **barvy** paletu [okno barvy](../windows/colors-window-image-editor-for-icons.md).

1. Vyberte velké ikony nebo kurzoru nebo vytvořte novou velké ikony nebo kurzoru.

1. Výběr barvy z 256 barev zobrazených v **barvy** paletu **barvy** okna.

   Barva vybraná se stane aktuální barvu v **barvy** paletu **barvy** okna.

   > [!NOTE]
   > Počáteční paletu 256barevných imagí odpovídá na paletě vrácené `CreateHalftonePalette` rozhraní Windows API. Všechny ikony určený pro prostředí Windows by měl palety můžete zabránit blikání během palety realizace.

## <a name="set-a-cursor39s-hot-spot"></a>Nastavit kurzor&#39;s aktivního bodu

Aktivního bodu kurzoru je bod, na které odkazuje Windows ve sledování pozice kurzoru. Ve výchozím nastavení je nastavení aktivního bodu do levého horního rohu kurzor (souřadnice 0; 0). **Aktivního bodu** vlastnost [okno vlastností](/visualstudio/ide/reference/properties-window) ukazuje souřadnice aktivního bodu.

### <a name="to-set-a-cursors-hot-spot"></a>Nastavení aktivního bodu kurzoru

1. Na [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md), zvolte **nastavte aktivní bod** nástroj.

1. Vyberte pixel, kterou chcete přiřadit jako aktivního bodu kurzoru.

   **Hotspot** vlastnost **vlastnosti** v okně se zobrazí nové souřadnice.

   > [!TIP]
   > Popisy tlačítek se zobrazí při přejeďte kurzorem přes tlačítko panelu nástrojů. Tyto tipy mohou pomoci identifikovat funkce každé tlačítko.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také:

[Nabídka obrázku](../windows/image-menu-image-editor-for-icons.md)<br/>
[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
[Ikony](/windows/desktop/menurc/icons)<br/>
[Kurzory](/windows/desktop/menurc/cursors)<br/>
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
