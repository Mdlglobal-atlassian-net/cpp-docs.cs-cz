---
title: Výběr oblasti obrázku (editor obrázků pro ikony)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.image.editing
helpviewer_keywords:
- Image editor [C++], image selection
- Image editor [C++], selecting images
- images [C++], selecting
- cursors [C++], selecting areas of
ms.assetid: 8b6ce4ad-eba1-4ece-86ba-cea92c3edff2
ms.openlocfilehash: 5e2522d23b30a91639e887a8761871e3df8139f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565110"
---
# <a name="selecting-an-area-of-an-image-image-editor-for-icons"></a>Výběr oblasti obrázku (editor obrázků pro ikony)

Nástroje pro výběr můžete použít k definování oblast bitovou kopii, kterou chcete vyjmout, kopírovat, zrušte, změna velikosti, Invertovat nebo přesunout. S **obdélníku výběru** nástroje můžete definovat a vyberte obdélníkovou oblast obrázku. S **Volný výběr** nástroj od ruky obrys oblasti, kterou chcete vybrat pro vyjmutí, kopírování nebo jiné operace můžete nakreslit.

> [!NOTE]
> Najdete v článku **obdélníku výběru** a **Volný výběr** nástroje na obrázku [panelu nástrojů editoru obrázků](../windows/toolbar-image-editor-for-icons.md) nebo zobrazení popisů tlačítek spojených s každé tlačítko na **Editor obrázků** nástrojů.

Můžete také vytvořit vlastní štětec z výběru. Další informace najdete v tématu [vytvoření vlastního štětce](../windows/creating-a-custom-brush-image-editor-for-icons.md).

### <a name="to-select-an-area-of-an-image"></a>Vyberte oblast obrázku

1. Na **Editor obrázků** nástrojů (nebo z **Image** nabídce **nástroje** příkaz), klikněte na nástroj pro výběr chcete.

2. Přesuňte bod vložen do jednoho rohu oblast obrázku, který chcete vybrat. Mezi vlasy se zobrazí po kurzoru nad bitovou kopii.

3. Přetáhněte kurzor protilehlého rohu oblasti, kterou chcete vybrat. Obdélník ukazuje, jaké pixelů bude vybrána. Všechny obrazové body v obdélníku, včetně těch v obdélníku, jsou zahrnuté ve výběru.

4. Uvolněte tlačítko myši. Ohraničení výběru obklopuje vybrané oblasti.

### <a name="to-select-an-entire-image"></a>K výběru celého obrázku

1. Kliknutím na obrázek mimo aktuální výběr. Ohraničení výběru změní fokus a zahrnuje celou image ještě jednou.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)