---
title: 'Ikony a kurzory: prostředky obrázků pro zobrazovací zařízení (Editor obrázků pro ikony) | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], creating
- image resources, display devices
- icons [C++], creating
- cursors [C++], types
- icons [C++]
- Image editor [C++], icons and cursors
- cursors [C++]
- display devices, creating icons for
- cursors [C++], hot spots
- icons [C++], types
ms.assetid: 8f0809a8-0cf0-4da9-b23d-51f28bf15f5b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a3e221c3546e0f9d02a9da7433ca2a353888a57a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42606200"
---
# <a name="icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons"></a>Ikony a kurzory: prostředky obrázků pro zařízení s displejem (editor obrázků pro ikony)

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

[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)  
[Ikony](http://msdn.microsoft.com/library/windows/desktop/ms646973)  
[Kurzory](http://msdn.microsoft.com/library/windows/desktop/ms646970)