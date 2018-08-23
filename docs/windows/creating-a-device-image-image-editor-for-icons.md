---
title: Vytvoření obrázku zařízení (Editor obrázků pro ikony) | Dokumentace Microsoftu
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
- icons [C++], creating
- display devices
- display devices, creating image
- images [C++], creating for display devices
- icons [C++], inserting
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0a8af9b18b8fc1afb4ad7d0770a1b302e4e7a0e9
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597372"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>Vytvoření obrázku zařízení (editor obrázků pro ikony)

Když vytvoříte nové ikony nebo kurzoru prostředků **Image** editoru nejprve vytvoří bitovou kopii v konkrétním stylu (32 × 32, 16 barvy ikony a 32 × 32, monochromatický pro ukazatele). Můžete přidat obrázky v různých velikostech a styly do počáteční ikony nebo kurzoru a upravit každé další image, podle potřeby pro jiné zobrazovací zařízení. Můžete také upravit obrázek pomocí operace vyjmutí a vložení z existujícího typu obrázku nebo z bitmapy vytvořené v programu grafiky.

Při otevření prostředku ikony nebo kurzoru v [editor obrázků](../windows/image-editor-for-icons.md), image, většina úzce odpovídající aktuální zobrazovací zařízení se otevře ve výchozím nastavení.

### <a name="to-create-a-new-icon-or-cursor"></a>Chcete-li vytvořit nové ikony nebo kurzoru

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a pak zvolte **vložit prostředků** z místní nabídky. (Pokud už máte existující prostředek obrázku v souboru .rc, jako je například kurzor, můžete můžete jednoduše kliknout pravým tlačítkem **kurzor** a pak zvolte položku **vložení kurzoru** z místní nabídky.)

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

2. V [vložit prostředek – dialogové okno](../windows/add-resource-dialog-box.md)vyberte **ikonu** nebo **kurzor** a klikněte na tlačítko **nový**. U ikon tím se vytvoří prostředek s ikonou s 32 × 32, ikona 16 barev. Pro ukazatele, 32 × 32, bude vytvořena monochromatický obrázek (barvami. 2).

   Pokud symbol plus (**+**) se zobrazí u typu prostředku bitové kopie v **vložit prostředků** dialogové okno, znamená to, že šablony nástrojů jsou k dispozici. Klikněte na znaménko plus rozbalit seznam šablon, vyberte šablonu a klikněte na **nový**.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Ikony a kurzory: prostředky obrázků pro zobrazovací zařízení](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)  
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)  
[Ikony a kurzory: prostředky obrázků pro zobrazovací zařízení](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)