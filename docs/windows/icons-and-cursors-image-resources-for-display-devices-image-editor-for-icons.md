---
title: 'Ikony a kurzory: prostředky obrázků pro zobrazovací zařízení (C++ Editor obrázků pro ikony)'
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
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
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
ms.openlocfilehash: 91de1351b3e41701d302d290533b60d4fe791b80
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693006"
---
# <a name="icons-and-cursors-image-resources-for-display-devices-c-image-editor-for-icons"></a>Ikony a kurzory: prostředky obrázků pro zobrazovací zařízení (C++ Editor obrázků pro ikony)

Ikony a kurzory jsou grafických prostředků, které může obsahovat více bitových kopií v různých velikostech a barevná schémata pro různé typy zařízení s displejem. Kromě toho kurzor má "aktivního bodu," požadované místo Windows používá ke sledování jeho pozice. Ikony a kurzory jsou vytvořeny a upravovat pomocí **Image** editoru, jako jsou rastrové obrázky a další Image.

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

- [Vytvoření nového obrázku zařízení (ikony nebo kurzoru)](../windows/creating-a-device-image-image-editor-for-icons.md)

- [Přidání obrázku pro zařízení s jiným zobrazením](../windows/adding-an-image-for-a-different-display-device-image-editor-for-icons.md)

- [Kopírování obrázku zařízení](../windows/copying-a-device-image-image-editor-for-icons.md)

- [Odstranění obrázku zařízení](../windows/deleting-a-device-image-image-editor-for-icons.md)

- [Vytvoření průhledných nebo obrácených oblastí v obrázcích zařízení](../windows/creating-transparent-or-inverse-regions-in-device-images.md)

- [Vytvoření 256barevných ikony nebo kurzoru](creating-a-256-color-icon-or-cursor-image-editor-for-icons.md)

- [Nastavení aktivního bodu kurzoru](../windows/setting-a-cursor-s-hot-spot-image-editor-for-icons.md)

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
[Ikony](/windows/desktop/menurc/icons)<br/>
[Kurzory](/windows/desktop/menurc/cursors)