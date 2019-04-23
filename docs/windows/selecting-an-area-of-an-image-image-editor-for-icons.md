---
title: 'Postupy: Upravit obrázek'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.image.editing
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
ms.openlocfilehash: 849da0d14987a057d39d5f9531e97545b3d4b8cf
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033284"
---
# <a name="how-to-edit-an-image"></a>Postupy: Upravit obrázek

Nástroje pro výběr můžete použít k definování oblast bitovou kopii, kterou chcete vyjmout, kopírovat, zrušte, změna velikosti, Invertovat nebo přesunout. S **obdélníku výběru** nástroje můžete definovat a vyberte obdélníkovou oblast obrázku. S **Volný výběr** nástroj od ruky obrys oblasti, kterou chcete vybrat pro vyjmutí, kopírování nebo jiné operace můžete nakreslit.

> [!NOTE]
> Najdete v článku **obdélníku výběru** a **Volný výběr** nástroje na obrázku [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) nebo zobrazení popisů tlačítek spojených s každé tlačítko na **Editor obrázků** nástrojů.

Můžete také vytvořit vlastní štětec z výběru. Další informace najdete v tématu [vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).

## <a name="how-to"></a>Postupy

Chcete-li upravit obrázek, naleznete v tématu Jak:

### <a name="to-select-an-image"></a>Chcete-li vybrat bitovou kopii

1. Použití **Editor obrázků** nástrojů nebo přejděte do nabídky **Image** > **nástroje** a zvolte nástroj pro výběr chcete.

1. Přesuňte bod vložen do jednoho rohu oblast obrázku, který chcete vybrat. Mezi vlasy se zobrazí po kurzoru nad bitovou kopii.

1. Přetáhněte kurzor protilehlého rohu oblasti, kterou chcete vybrat. Obdélník ukazuje, jaké pixelů bude vybrána. Všechny obrazové body v obdélníku, včetně těch v obdélníku, jsou zahrnuté ve výběru.

1. Uvolněte tlačítko myši. Ohraničení výběru obklopuje vybrané oblasti.

#### <a name="to-select-an-entire-image"></a>K výběru celého obrázku

Vyberte bitovou kopii mimo aktuální výběr. Ohraničení výběru změní fokus a zahrnuje celou image ještě jednou.

### <a name="to-edit-parts-of-an-image"></a>Úprava částí obrázku

Můžete provádět standardní operace úprav – vyjmutí, kopírování, vymazání a přesouvání – na [výběr](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md), zda je výběr celého obrázku nebo jen jeho části. Protože **Editor obrázků** používá **schránky Windows**, můžou přenášet imagí mezi **Editor obrázků** a dalšími aplikacemi pro Windows.

Kromě toho můžete změnit velikost výběru, zda obsahuje celého obrázku nebo jen část.

#### <a name="to-cut-the-current-selection-and-move-it-to-the-clipboard"></a>Vyjmout aktuálního výběru a přesunout ho do schránky.

Přejděte do nabídky **upravit** > **Vyjmout**.

#### <a name="to-copy-the-selection"></a>Kopírovat výběr

1. Umístěte ukazatel uvnitř ohraničení výběru nebo kdekoli na něm s výjimkou úchyty pro změnu velikosti.

1. Podržte stisknutou klávesu **Ctrl** klíče při přetahování výběr do nového umístění. Obsah původního výběru je beze změny.

1. Zkopíruje výběr do bitové kopie v daném umístění, vyberte vně výběr kurzoru.

#### <a name="to-paste-the-clipboard-contents-into-an-image"></a>Chcete-li vložit obsah schránky do bitové kopie

1. Přejděte do nabídky **upravit** > **vložit**.

   Obsah schránky obklopený ohraničení výběru se zobrazí v levém horním rohu podokna.

1. Umístěte ukazatel myši v rámci ohraničení výběru a přetáhněte ji na obrázku do požadovaného umístění na obrázku.

1. Ukotvit bitové kopie v jeho novém umístění, vyberte mimo hranice výběru.

#### <a name="to-delete-the-current-selection-without-moving-it-to-the-clipboard"></a>Chcete-li odstranit aktuální výběr bez přesouvání do schránky.

Přejděte do nabídky **upravit** > **odstranit**.

   Původní oblast výběru se vyplní aktuální barvou pozadí.

> [!NOTE]
> Můžete přistupovat **Vyjmout**, **kopírování**, **vložit**, a **odstranit** příkazy kliknutím pravým tlačítkem myši v **zobrazení prostředků** okna.

#### <a name="to-move-the-selection"></a>Chcete-li přesunout výběr

1. Umístěte ukazatel uvnitř ohraničení výběru nebo kdekoli na něm s výjimkou úchyty pro změnu velikosti.

1. Přetáhněte do nového umístění.

1. Chcete-li ukotvit výběr obrázku v jeho novém umístění, vyberte mimo hranice výběru.

Další informace o vykreslování s výběrem, naleznete v tématu [vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).

### <a name="to-flip-an-image"></a>Chcete-li Převrátit obrázek

Můžete překlopit nebo otočení obrázku vytvořit zrcadlový obraz původní, zapněte image vzhůru nohama, nebo otočit o 90 stupňů na obrázku vpravo v čase.

- Chcete-li Převrátit obrázek vodorovně (zrcadlový obraz), přejděte do nabídky **Image** > **Převrátit vodorovně**.

- Chcete-li Převrátit obrázek svisle (zapnout vzhůru nohama), přejděte do nabídky **Image** > **Převrátit svisle**.

- Otočit o 90 stupňů image, přejděte do nabídky **Image** > **otočit o 90 stupňů**.

   > [!NOTE]
   > Můžete také použít [klávesy akcelerátoru (místní)](../windows/accelerator-keys-image-editor-for-icons.md) pro tyto příkazy nebo přístupu k příkazům v místní nabídce (vyberte mimo image při **Editor obrázků**).

### <a name="to-resize-an-image"></a>Změna velikosti obrázku

Chování **Editor obrázků** zatímco Změna velikosti obrázku závisí na tom, jestli jste [vybrané](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) celého obrázku nebo jenom její část.

Pokud výběr obsahuje pouze část obrázku, **Editor obrázků** zmenšuje výběr odstraněním řádků nebo sloupců v pixelech a vyplnění uvolněných oblastech aktuální barvou pozadí. Výběr se také můžete roztáhnout tak, že duplikujete řádky nebo sloupce v pixelech.

Pokud výběr zahrnuje celého obrázku **Editor obrázků** buď zmenšuje a roztáhne na obrázku nebo ořízne tak a rozšiřuje ji.

Pro změnu velikosti obrázku dvěma způsoby: úchyty pro změnu velikosti a [okno vlastností](/visualstudio/ide/reference/properties-window). Můžete přetažením úchytů změňte velikost všech nebo části obrázku. Jsou plné úchyty pro změnu velikosti, které můžete přetáhnout. Nelze přetáhnout popisovačů, které jsou prázdné. Použití **vlastnosti** okna pro změnu velikosti celého obrázku pouze vybrané části.

![Úchyty na rastrový obrázek](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Úchyty pro změnu velikosti

> [!NOTE]
> Pokud máte **dlaždici mřížky** možnosti vybrané v [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md), pak změnu velikosti při kolika rozehrávkách byli na další řádek mřížky dlaždice. Pokud pouze **mřížku obrazových bodů** možnost je vybrána (výchozí nastavení), změnu velikosti při kolika rozehrávkách byli na další bod k dispozici.

#### <a name="to-resize-an-entire-image-using-the-properties-window"></a>Změna velikosti celého obrázku pomocí okna Vlastnosti

1. Otevřete obrázek, jehož vlastnosti chcete změnit.

1. V **šířka** a **výška** polích v [okno vlastností](/visualstudio/ide/reference/properties-window), zadejte dimenze, které chcete.

   Pokud jste zvýšit velikost bitové kopie, **Editor obrázků** rozšiřuje na obrázku vpravo směrem dolů, nebo obojí a vyplní nové oblasti aktuální barvou pozadí. Obrázek není roztažená.

   Pokud dobu velikost bitové kopie, **Editor obrázků** obrázek ořízne tak, na pravé nebo dolní okraj nebo obojí.

   > [!NOTE]
   > Můžete použít **šířka** a **výška** vlastnosti, které chcete změnit velikost pouze celého obrázku, ne pro změnu velikosti částečného výběru.

#### <a name="to-crop-or-extend-an-entire-image"></a>Oříznutí nebo rozšíření celého obrázku

1. Vyberte celého obrázku.

   Pokud aktuálně vybrané části obrázku, a chcete vybrat celého obrázku, klikněte kamkoli v imagi mimo aktuální ohraničení výběru.

1. Přetáhněte úchyt pro změnu velikosti obrázku se správnou velikost.

Za normálních okolností **Editor obrázků** ořízne nebo zvětší bitovou kopii, když změníte velikost přesunutím úchyt pro změnu velikosti. Při podržení **Shift** klíče při přesunu na úchyt **Editor obrázků** zmenšuje nebo Roztáhne obrázek.

#### <a name="to-shrink-or-stretch-an-entire-image"></a>Zmenšení nebo roztažení celého obrázku

1. Vyberte celého obrázku.

   Pokud chcete vybrat celého obrázku část obrázku je aktuálně vybrána, klikněte kamkoli v imagi mimo aktuální ohraničení výběru.

1. Podržte stisknutou klávesu **Shift** klíče a přetáhněte úchyt pro změnu velikosti obrázku se správnou velikost.

#### <a name="to-shrink-or-stretch-part-of-an-image"></a>Zmenšení nebo roztažení části obrázku

1. Vyberte část image, kterou chcete změnit velikost. Další informace najdete v tématu [výběr oblasti obrázku](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Přetáhněte jednu z úchytů, dokud nebude výběr správné velikosti.

### <a name="to-edit-an-image-outside-of-a-project"></a>Úprava obrázku mimo projekt

Můžete otevřít a upravit obrázky ve vývojovém prostředí, stejně jako v jakékoli grafické aplikace, například otevírání rastrový obrázek pro samostatné úpravy. Obrázky, které při práci s nemusí být součástí projektu sady Visual Studio.

1. Přejděte do nabídky **souboru** > **otevřít**.

1. V **soubory typu** vyberte **všechny soubory**.

1. Najděte a otevřete image, kterou chcete upravit.

### <a name="to-change-image-properties"></a>Chcete-li změnit vlastnosti bitové kopie

Můžete nastavit nebo upravit vlastnosti image pomocí [okno vlastností](/visualstudio/ide/reference/properties-window).

1. Otevřít obrázek v **Editor obrázků**.

1. V **vlastnosti** okně změnit některé nebo všechny vlastnosti pro vaši image.

   |Vlastnost|Popis|
   |--------------|-----------------|
   |**Barvy**|Určuje barevné schéma pro bitovou kopii. Vyberte **monochromatický**, **16**, nebo **256**, nebo **True Color**.<br/><br/>Pokud jste už k těm nejrozsáhlejším obrázek s barevnou paletu na 16 barev, výběru **monochromatický** způsobí, že nahrazení černá a bílá pro barvy v bitové kopii. Není vždy udržují kontrast: například sousední oblasti červenou a zelenou obě převedou na černou.|
   |**Název souboru**|Určuje název souboru obrázku.<br/><br/>Ve výchozím nastavení přiřadí sady Visual Studio z výchozího identifikátoru prostředku (IDB_BITMAP1) a přidání příslušné rozšíření základní název souboru vytvořené tak, že odeberete první čtyři znaky ("IDB_"). Název souboru bitové kopie v tomto příkladu by měl být *BITMAP1.bmp*. Můžete ho přejmenovat *MYBITMAP1.bmp*.|
   |**Výška**|Nastaví výšku obrázku (v pixelech). Výchozí hodnota je 48.<br/><br/>Oříznutí obrázku nebo je prázdné místo přidání následujících stávající bitovou kopii.|
   |**ID**|Nastaví identifikátor prostředku.<br/><br/>Pro bitovou kopii Microsoft Visual Studio ve výchozím nastavení, přiřadí identifikátor další dostupné v řadě: IDB_BITMAP1 IDB_BITMAP2 a tak dále. Podobně jako názvy jsou použity pro ikony a kurzory.|
   |**Paleta**|Změny barev vlastnosti.<br/><br/>Dvakrát klikněte na Zobrazit a vybrat barvu [dialogové okno Výběr vlastních barev](../windows/custom-color-selector-dialog-box-image-editor-for-icons.md). Definujte barvu tak, že zadáte hodnoty vyjadřující příslušná textová pole.|
   |**SaveCompressed**|Označuje, zda je na obrázku ve formátu komprimované. Tato vlastnost je pouze pro čtení.<br/><br/>Visual Studio neumožňuje uložit obrázky v komprimovaném formátu, takže pro všechny obrázky vytvořené v sadě Visual Studio, tato vlastnost bude **False**. Pokud v sadě Visual Studio otevřete komprimovanou bitovou kopii (vytvořený v jiném programu), bude mít tato vlastnost **True**. Pokud jste uložili komprimované bitové kopie pomocí sady Visual Studio, nekomprimovaný a tato vlastnost se vrátí zpět k **False**.|
   |**Šířka**|Nastaví šířku obrázku (v pixelech). Výchozí hodnota pro rastrových obrázků je 48.<br/><br/>Oříznutý obrázek nebo napravo od existující bitová kopie se přidá mezeru.|

## <a name="requirements"></a>Požadavky

Žádný

## <a name="see-also"></a>Viz také:

[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
[Postupy: Vytvoření ikony nebo jiného obrázku](../windows/creating-an-icon-or-other-image-image-editor-for-icons.md)<br/>
[Postupy: Použití nástroje pro kreslení](../windows/using-a-drawing-tool-image-editor-for-icons.md)<br/>
[Postupy: Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)<br/>
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>