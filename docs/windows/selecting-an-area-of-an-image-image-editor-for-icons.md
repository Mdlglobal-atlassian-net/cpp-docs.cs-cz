---
title: 'Postupy: Úprava obrázku'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
- Image editor [C++], editing images
- Clipboard [C++], pasting
- images [C++], editing
- images [C++], deleting selected parts
- images [C++], copying selected parts
- images [C++], moving selected parts
- images [C++], dragging and replicating selected parts
- images [C++], pasting into
- graphics [C++], editing
- Image editor [C++], flipping and rotating images
- images [C++], flipping
- images [C++], rotating
- Image editor [C++], resizing images
- graphics [C++], resizing
- images [C++], resizing
- resizing images
- size [C++], images
- images [C++], cropping
- images [C++], extending
- Image editor [C++], cropping or extending images
- Image editor [C++], shrinking and stretching images
- images [C++], stretching
- images [C++], shrinking
- bitmaps [C++], shrinking
- bitmaps [C++], stretching
- Image editor [C++], editing images
- images [C++], editing
- images [C++], properties
- Image editor [C++], Properties window
- Properties window, image editor
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: 6d973ad444f719b905af5a33e47ef28f4895111f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447301"
---
# <a name="how-to-edit-an-image"></a>Postupy: Úprava obrázku

Pomocí nástrojů pro výběr můžete definovat oblast obrázku, který chcete vyjmout, kopírovat, vymazat, změnit velikost, Invertovat nebo přesunout. Pomocí nástroje **Výběr obdélníku** můžete definovat a vybrat obdélníkovou oblast obrázku. Pomocí nástroje pro **Výběr nepravidelného výběru** můžete nakreslit obrys od oblasti, kterou chcete vybrat pro operaci vyjmutí, kopírování nebo jiné.

> [!NOTE]
> Podívejte se na **Výběr obdélníku** a nástroje pro **Výběr nestandardního výběru** na [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) nebo si prohlédněte tipy nástrojů přidružené k jednotlivým tlačítkům na panelu nástrojů **editoru obrázků** .

Můžete také vytvořit vlastní štětce z výběru. Další informace najdete v tématu [Vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).

## <a name="how-to"></a>Postup

Chcete-li upravit obrázek, přečtěte si téma Jak:

### <a name="to-select-an-image"></a>Výběr obrázku

1. Použijte panel nástrojů **Editor obrázků** nebo přejděte na **Image** nabídky > **nástroje** a vyberte nástroj pro výběr, který chcete.

1. Přesuňte bod vložení do jednoho rohu oblasti obrázku, kterou chcete vybrat. Křížové vlasy se zobrazí, když se kurzor nachází na obrázku.

1. Přetáhněte bod vložení do opačného rohu oblasti, kterou chcete vybrat. Obdélník ukazuje, které pixely budou vybrány. Do výběru jsou zahrnuty všechny pixely v obdélníku, včetně těch, které jsou v obdélníku.

1. Uvolněte tlačítko myši. Vybraná oblast je ohraničena ohraničením výběru.

#### <a name="to-select-an-entire-image"></a>Výběr celého obrázku

Vyberte obrázek mimo aktuální výběr. Ohraničení výběru se změní na vybraný a celý obraz se pak znovu zazahrnuje.

### <a name="to-edit-parts-of-an-image"></a>Úprava částí obrázku

Můžete provádět standardní operace úprav – výběr, kopírování, mazání a přesouvání – u [výběru](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), zda je výběr celý nebo pouze jeho část. Vzhledem k tomu, že **Editor obrázků** používá **schránku systému Windows**, můžete přenášet obrázky mezi **editorem obrázků** a dalšími aplikacemi pro systém Windows.

Kromě toho můžete změnit velikost výběru bez ohledu na to, zda obsahuje celý obrázek nebo pouze část.

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Chcete-li vyjmout aktuální výběr a přesunout ho do schránky

Přejděte do nabídky **upravit** > **Vyjmout**.

#### <a name="to-copy-the-selection"></a>Kopírování výběru

1. Umístit ukazatel dovnitř ohraničení výběru nebo kdekoli na něj s výjimkou úchytů pro změnu velikosti.

1. Podržte stisknutou **klávesu CTRL** při přetahování výběru na nové umístění. Oblast původního výběru je beze změny.

1. Chcete-li kopírovat výběr do obrázku v jeho aktuálním umístění, vyberte mimo kurzor výběru.

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Vložení obsahu schránky do obrázku

1. Přejděte do nabídky **upravit** > **Vložit**.

   Obsah schránky ohraničený ohraničením výběru se zobrazí v levém horním rohu podokna.

1. Umístěte ukazatel myši do ohraničení výběru a přetáhněte obrázek do požadovaného umístění na obrázku.

1. Chcete-li obrázek ukotvit v novém umístění, vyberte mimo hranice výběru.

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Odstranění aktuálního výběru bez jeho přesunutí do schránky

Přejděte na nabídku **upravit** > **Odstranit**.

   Původní oblast výběru je vyplněna aktuální barvou pozadí.

> [!NOTE]
> Příkazy **Vyjmout**, **Kopírovat**, **Vložit**a **Odstranit** můžete získat tak, že kliknete pravým tlačítkem myši na **prostředky** okno.

#### <a name="to-move-the-selection"></a>Přesun výběru

1. Umístit ukazatel dovnitř ohraničení výběru nebo kdekoli na něj s výjimkou úchytů pro změnu velikosti.

1. Přetáhněte výběr do nového umístění.

1. Chcete-li ukotvit výběr v obrázku v jeho novém umístění, vyberte mimo hranice výběru.

Další informace o vykreslování s výběrem najdete v tématu [Vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).

### <a name="to-flip-an-image"></a>Překlopení obrázku

Obrázek můžete překlopit nebo otočit buď tak, že vytvoříte zrcadlový obraz originálu, zapnete obrázek v dolní části nebo otočíte obrázek vpravo 90 stupňů v čase.

- Pokud chcete obrázek Překlopit vodorovně (zrcadlový obrázek), přejděte na **Obrázek** nabídky > **Překlopit vodorovně**.

- Pokud chcete obrázek Překlopit svisle (zapíná dolů), přejděte na **Obrázek** nabídky > **Překlopit svisle**.

- Pokud chcete otočit obrázek 90 stupňů, přejděte na **Obrázek** nabídky > **Otočit 90 stupňů**.

   > [!NOTE]
   > K těmto příkazům můžete také použít klávesové zkratky [(zkratky)](../windows/accelerator-keys-image-editor-for-icons.md) nebo získat přístup k příkazům z místní nabídky (vyberte mimo obrázek v **editoru obrázků**).

### <a name="to-resize-an-image"></a>Změna velikosti obrázku

Chování **editoru obrázků** při změně velikosti obrázku závisí na tom, zda jste [vybrali](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) celý obrázek nebo pouze jeho část.

Když výběr zahrnuje pouze část obrázku, **Editor obrázků** zmenší výběr odstraněním řádků nebo sloupců pixelů a vyplněním oblastí uvolněné aktuální barvou pozadí. Výběr můžete také roztáhnout tak, že duplikujete řádky nebo sloupce v pixelech.

Když výběr zahrnuje celý obrázek, **Editor obrázků** buď zmenší a roztáhne obrázek, nebo ho ořízne a rozšíří.

Existují dva mechanismy pro změnu velikosti obrázku: úchyty pro změnu velikosti a [okno Vlastnosti](/visualstudio/ide/reference/properties-window). Přetažením úchytů pro změnu velikosti můžete změnit velikost celého obrázku nebo jeho části. Úchyty pro změnu velikosti, které lze přetáhnout, jsou plné. Nemůžete přetahovat úchyty, které jsou prázdné. V okně **vlastnosti** můžete změnit velikost celého obrázku, nikoli vybrané části.

![Úchyty pro změnu velikosti rastrového obrázku](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Úchyty pro změnu velikosti

> [!NOTE]
> Pokud máte v [dialogovém okně nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md)vybranou možnost **Mřížka dlaždice** , pak se změna velikosti přitahuje na čáru mřížky další dlaždice. Pokud je vybraná jenom možnost **Mřížka pixelů** (výchozí nastavení), změna velikosti se přitahuje na další dostupný pixel.

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>Změna velikosti celého obrázku pomocí okna vlastnosti

1. Otevřete obrázek, jehož vlastnosti chcete změnit.

1. Do polí **Šířka** a **Výška** v [okno Vlastnosti](/visualstudio/ide/reference/properties-window)zadejte požadované rozměry.

   Pokud zvětšíte velikost obrázku, **Editor obrázků** rozšiřuje obrázek doprava, dolů nebo obou a vyplní novou oblast aktuální barvou pozadí. Obrázek není roztažen.

   Pokud zkrátíte velikost obrázku, **Editor obrázků** ořízne obrázek na pravém nebo spodním okraji, případně obojí.

   > [!NOTE]
   > Vlastnosti **Width** a **Height** můžete použít k změně velikosti pouze celého obrázku, nikoli k částečnému výběru.

#### <a name="to-crop-or-extend-an-entire-image"></a>Oříznutí nebo roztažení celého obrázku

1. Vyberte celý obrázek.

   Pokud je aktuálně vybraná část image a chcete vybrat celý obrázek, vyberte kdekoliv na obrázku mimo aktuální hranici výběru.

1. Přetáhněte úchyt pro změnu velikosti, dokud obrázek nemá správnou velikost.

**Editor obrázků** obvykle ořízne nebo zvětšuje obrázek při změně jeho velikosti přesunutím úchytu pro změnu velikosti. Pokud při přesunu úchytu podržíte klávesu **SHIFT** , **Editor obrázků** zmenší nebo roztáhne obrázek.

#### <a name="to-shrink-or-stretch-an-entire-image"></a>Zmenšení nebo roztažení celého obrázku

1. Vyberte celý obrázek.

   Pokud je aktuálně vybraná část obrázku a chcete vybrat celý obrázek, vyberte kdekoliv na obrázku mimo aktuální hranici výběru.

1. Podržte stisknutou klávesu **SHIFT** a přetáhněte úchyt pro změnu velikosti, dokud obrázek nemá správnou velikost.

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>Zmenšení nebo roztažení části obrázku

1. Vyberte část obrázku, u kterého chcete změnit velikost. Další informace najdete v tématu [Výběr oblasti obrázku](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Přetáhněte jeden z úchytů pro změnu velikosti, dokud není výběr správné velikosti.

### <a name="to-edit-an-image-outside-of-a-project"></a>Úprava obrázku mimo projekt

Obrázky ve vývojovém prostředí můžete otevřít a upravit stejným způsobem jako v libovolné aplikaci grafiky, například když otevřete rastrový obrázek pro samostatné úpravy. Obrázky, se kterými pracujete, nemusí být součástí projektu sady Visual Studio.

1. Přejděte na **soubor** nabídky > **otevřít**.

1. V poli **soubory typu** vyberte možnost **všechny soubory**.

1. Vyhledejte a otevřete obrázek, který chcete upravit.

### <a name="to-change-image-properties"></a>Změna vlastností obrázku

Můžete nastavit nebo upravit vlastnosti obrázku pomocí [okno Vlastnosti](/visualstudio/ide/reference/properties-window).

1. Otevřete obrázek v **editoru obrázků**.

1. V okně **vlastnosti** změňte všechny vlastnosti obrázku.

   |Vlastnost|Popis|
   |--------------|-----------------|
   |**Barvy**|Určuje barevné schéma pro obrázek. Vyberte možnost **monochromatické**, **16**nebo **256**nebo **True Color**.<br/><br/>Pokud jste již obrázek vykreslili pomocí palety s 16 barvami, výběr možnosti **monochromaticke** způsobí nahrazení černé a bílé barvy v obrázku. Kontrast není vždy udržován: například sousední oblasti červené a zelené jsou převedeny na černou.|
   |**Bitmap**|Určuje název souboru obrázku.<br/><br/>Ve výchozím nastavení Visual Studio přiřadí základní název souboru vytvořený odebráním prvních čtyř znaků ("IDB_") z výchozího identifikátoru prostředku (IDB_BITMAP1) a přidáním příslušné přípony. Název souboru pro obrázek v tomto příkladu by byl *Bitmap1. bmp*. Mohli byste ho přejmenovat *MYBITMAP1. bmp*.|
   |**Výška**|Nastaví výšku obrázku (v pixelech). Výchozí hodnota je 48.<br/><br/>Obrázek se ořízne nebo se pod existující imagí přidá prázdné místo.|
   |**ID**|Nastaví identifikátor prostředku.<br/><br/>U obrázku Microsoft Visual Studio standardně přiřadí další dostupný identifikátor v řadě: IDB_BITMAP1, IDB_BITMAP2 a tak dále. Podobné názvy se používají pro ikony a kurzory.|
   |**Zadání**|Změní vlastnosti barvy.<br/><br/>Dvojitým kliknutím vyberte barvu a zobrazí se [dialogové okno pro výběr vlastních barev](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Definujte barvu zadáním hodnot RGB nebo HSL do příslušných textových polí.|
   |**SaveCompressed**|Označuje, zda je obrázek v komprimovaném formátu. Tato vlastnost je jen ke čtení.<br/><br/>Visual Studio neumožňuje ukládat obrázky v komprimovaném formátu, takže pro všechny image vytvořené v aplikaci Visual Studio bude tato vlastnost **false**. Pokud otevřete komprimovanou bitovou kopii (vytvořenou v jiném programu) v aplikaci Visual Studio, bude tato vlastnost **pravdivá**. Pokud uložíte komprimovanou bitovou kopii pomocí sady Visual Studio, bude nekomprimovaná a tato vlastnost se vrátí zpět na **false**.|
   |**Délk**|Nastaví šířku obrázku (v pixelech). Výchozí hodnota pro rastrové obrázky je 48.<br/><br/>Obrázek se ořízne nebo se na pravé straně existující image přidá prázdné místo.|

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také

[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
[Postupy: vytvoření ikony nebo jiného obrázku](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Postupy: použití nástroje pro kreslení](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Postupy: práce s barvou](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>