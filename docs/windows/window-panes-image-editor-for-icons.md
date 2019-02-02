---
title: Podokna (editor obrázků pro ikony)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.bitmap
- vc.editors.icon
helpviewer_keywords:
- graphics editor [C++]
- Image editor [C++], panes
- Image editor [C++], magnification
- grids, pixel
- pixel grid, Image editor
- Image editor [C++], pixel grid
- Image editor [C++], grid settings
- grid settings, Image editor
ms.assetid: d66ea5b3-e2e2-4fc4-aa99-f50022cc690e
ms.openlocfilehash: 72b7cf056147cdbd216d861f0e710da423951c5a
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560306"
---
# <a name="window-panes-image-editor-for-icons"></a>Podokna (editor obrázků pro ikony)

**Editor obrázků** okno obvykle zobrazí obrázek do dvou podoken oddělené rozdělovač. Jedno zobrazení je skutečná velikost a druhý se zvětší (výchozí rozšíření faktor je 6). Zobrazení v těchto dvou podoken se automaticky aktualizují: změny, které provedete v jedno podokno se okamžitě zobrazí v jiném. Velikost podoken usnadňují práci na zvětšeným zobrazením bitové kopie, ve kterém můžete rozlišení jednotlivých pixelech a, ve stejnou dobu, můžete sledovat účinek práce na zobrazení skutečné velikosti obrázku.

V levém podokně používá tolik místa je potřeba (až polovinu **Image** okno) Chcete-li zobrazit zobrazení zvětšením 1:1 (výchozí) z image. Pravý panel zobrazuje přiblíženou bitové kopie (6:1 zvětšení ve výchozím nastavení). Můžete změnit zvětšení v každé pomocí podokna **Magnify** nástroj [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) nebo pomocí klávesové zkratky.

Můžete zvětšit menší podokně **Editor obrázků** okno a použijte dvě podokna pro zobrazení různých oblastech velký obrázek. Vyberte v podokně zvolte jej.

Můžete změnit tak relativní velikosti podoken umístěním ukazatele na panelu rozdělení a přesunutí příčku směrem doprava nebo doleva. Pokud budete chtít pracovat na pouze jedno podokno, můžete příčku přesunout až po obou stranách.

Pokud **Editor obrázků** podokno se zvětšeným faktorem 4 nebo vyšší, můžete zobrazit mřížku obrazových bodů, který vymezuje jednotlivých pixelech na obrázku.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-change-the-magnification-factor"></a>Chcete-li změnit faktor zvětšení

Ve výchozím nastavení **Image** editoru se zobrazí v levém podokně ve skutečné velikosti zobrazení a zobrazení v pravém podokně na 6 časů skutečnou velikost. Faktoru zvětšení (prohlédnout ve stavovém řádku v dolní části pracovní prostor) je poměr mezi skutečná velikost bitové kopie a velikost. Výchozí faktor je 6 a rozsah je od 1 do 10.

1. Vyberte **Editor obrázků** podokně jehož faktor zvětšení, které chcete změnit.

1. Na [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md), vyberte šipku vpravo od [nebo vypne nástroj zvětšení](../windows/toolbar-image-editor-for-icons.md) a vyberte faktor zvětšení z podnabídky: **1 X**, **2 X**, **6 X**, nebo **8 X**.

   > [!NOTE]
   > Vybrat faktor zvětšení kromě oprávnění uvedených v seznamu **Magnify** nástroj, použijte klávesy akcelerátoru.

## <a name="to-display-or-hide-the-pixel-grid"></a>K zobrazení nebo skrytí mřížky pixelů

Pro všechny **Editor obrázků** podoken s faktor zvětšení 4 nebo vyšší, můžete zobrazit mřížku oddělující jednotlivé pixelů na obrázku.

1. Na **Image** nabídce vyberte možnost **nastavení mřížky**.

1. Vyberte **mřížku obrazových bodů** zaškrtávací políčko pro zobrazení mřížky, nebo zrušte zaškrtnutí políčka Skrýt mřížku.

> [!TIP]
> Popisy tlačítek se zobrazí při přejeďte kurzorem přes tlačítko panelu nástrojů. Tyto tipy mohou pomoci identifikovat funkce každé tlačítko.

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)