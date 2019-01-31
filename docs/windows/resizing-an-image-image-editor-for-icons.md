---
title: Změna velikosti obrázku (editor obrázků pro ikony)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
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
ms.assetid: d83a02c4-4dfe-4586-a0df-51a50c2ba71d
ms.openlocfilehash: d88a4cccff5b9b7b6303329782b7367cb953b13d
ms.sourcegitcommit: 5270117dbecc4c49bca0cf10b927bae3c9930038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/31/2019
ms.locfileid: "55484965"
---
# <a name="resizing-an-image-image-editor-for-icons"></a>Změna velikosti obrázku (editor obrázků pro ikony)

Chování **Image** editoru při změně velikosti obrázku závisí na tom, jestli jste [vybrané](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) celého obrázku nebo jenom její část.

Pokud výběr obsahuje pouze část obrázku, **Image** editor zmenšuje výběr odstraněním řádků nebo sloupců v pixelech a vyplnění uvolněných oblastech aktuální barvou pozadí. Výběr se také můžete roztáhnout tak, že duplikujete řádky nebo sloupce v pixelech.

Pokud výběr zahrnuje celého obrázku **Image** editor buď zmenšuje a roztáhne na obrázku nebo ořízne a rozšiřuje jej.

Pro změnu velikosti obrázku dvěma způsoby: úchyty pro změnu velikosti a [okno vlastností](/visualstudio/ide/reference/properties-window). Můžete přetažením úchytů změňte velikost všech nebo části obrázku. Jsou plné úchyty pro změnu velikosti, které můžete přetáhnout. Nelze přetáhnout popisovačů, které jsou prázdné. Použití **vlastnosti** okna pro změnu velikosti celého obrázku pouze vybrané části.

![Úchyty na rastrový obrázek](../mfc/media/vcimageeditorsizinghandles.gif "vcImageEditorSizingHandles")<br/>
Úchyty pro změnu velikosti

> [!NOTE]
> Pokud máte **dlaždici mřížky** možnosti vybrané v [dialogové okno Nastavení mřížky](../windows/grid-settings-dialog-box-image-editor-for-icons.md), pak změnu velikosti při kolika rozehrávkách byli na další řádek mřížky dlaždice. Pokud pouze **mřížku obrazových bodů** možnost je vybrána (výchozí nastavení), změnu velikosti při kolika rozehrávkách byli na další bod k dispozici.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-resize-an-entire-image-using-the-properties-window"></a>Změna velikosti celého obrázku pomocí okna Vlastnosti

1. Otevřete obrázek, jehož vlastnosti chcete změnit.

1. V **šířka** a **výška** polích v [okno vlastností](/visualstudio/ide/reference/properties-window), zadejte dimenze, které chcete.

   Pokud jste zvýšit velikost bitové kopie, **Image** editor rozšiřuje na obrázku vpravo směrem dolů, nebo obojí a vyplní nové oblasti aktuální barvou pozadí. Obrázek není roztažená.

   Pokud dobu velikost bitové kopie, **Image** editor obrázek ořízne tak, na pravé nebo dolní okraj nebo obojí.

   > [!NOTE]
   > Můžete použít **šířka** a **výška** vlastnosti, které chcete změnit velikost pouze celého obrázku, ne pro změnu velikosti částečného výběru.

## <a name="to-crop-or-extend-an-entire-image"></a>Oříznutí nebo rozšíření celého obrázku

1. Vyberte celého obrázku.

   Pokud aktuálně vybrané části obrázku, a chcete vybrat celého obrázku, klikněte kamkoli v imagi mimo aktuální ohraničení výběru.

1. Přetáhněte úchyt pro změnu velikosti obrázku se správnou velikost.

Za normálních okolností **Image** editoru ořízne nebo (zvětšit) zvětší bitovou kopii, když změníte velikost přesunutím úchyt pro změnu velikosti. Při podržení **Shift** klíče při přesunu na úchyt **Image** editoru zmenší, nebo Roztáhne obrázek.

## <a name="to-shrink-or-stretch-an-entire-image"></a>Zmenšení nebo roztažení celého obrázku

1. Vyberte celého obrázku.

   Pokud chcete vybrat celého obrázku část obrázku je aktuálně vybrána, klikněte kamkoli v imagi mimo aktuální ohraničení výběru.

1. Podržte stisknutou klávesu **Shift** klíče a přetáhněte úchyt pro změnu velikosti obrázku se správnou velikost.

## <a name="to-shrink-or-stretch-part-of-an-image"></a>Zmenšení nebo roztažení části obrázku

1. Vyberte část image, kterou chcete změnit velikost. Další informace najdete v tématu [výběr oblasti obrázku](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md).

1. Přetáhněte jednu z úchytů, dokud nebude výběr správné velikosti.

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)