---
title: Vytvoření obrázku zařízení (editor obrázků pro ikony)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
- vc.editors.newimagetype
- vc.editors.customimage
- vc.editors.opendeviceimage
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
- New <Device> Image Type dialog box [C++]
- Custom Image dialog box [C++]
- Open <Device> Image dialog box [C++]
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
ms.openlocfilehash: ce1069f6f410d7a60d631461086ca8870ef679c0
ms.sourcegitcommit: efcc8c97570ddf7631570226c700e8f6ebb6c7be
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2019
ms.locfileid: "55560293"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>Vytvoření obrázku zařízení (editor obrázků pro ikony)

Když vytvoříte nové ikony nebo kurzoru prostředků **Image** editoru nejprve vytvoří bitovou kopii v konkrétním stylu (32 × 32, 16 barvy ikony a 32 × 32, monochromatický pro ukazatele). Můžete přidat obrázky v různých velikostech a styly do počáteční ikony nebo kurzoru a upravit každé další image, podle potřeby pro jiné zobrazovací zařízení. Můžete také upravit obrázek pomocí operace vyjmutí a vložení z existujícího typu obrázku nebo z bitmapy vytvořené v programu grafiky.

Při otevření prostředku ikony nebo kurzoru v [editor obrázků](../windows/image-editor-for-icons.md), image, většina úzce odpovídající aktuální zobrazovací zařízení se otevře ve výchozím nastavení.

Informace o přidávání prostředků do spravovaných projektů naleznete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="new-ltdevicegt-image-type-dialog-box"></a>Nové &lt;zařízení&gt; dialogové okno typ obrázku

**Nový &lt;zařízení&gt; typ obrázku** dialogové okno umožňuje vytvořit nový obrázek zařízení zadaného typu. Otevřete **nový \<zařízení > obrázku** dialogu **nový typ obrázku** na **Image** nabídky. Jsou zahrnuty následující vlastnosti **cílový typ obrázku** a **vlastní**.

### <a name="target-image-type"></a>Cílový typ obrázku

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

### <a name="custom"></a>Vlastní

Otevře **vlastní Image** dialogovému oknu, ve kterém můžete vytvořit novou bitovou kopii s vlastní velikost a počet barev.

**Vlastní Image** dialogové okno umožňuje vytvořit novou bitovou kopii s vlastní velikost a počet barev. Jsou zahrnuty následující vlastnosti:

|Vlastnost|Popis|
|---|---|
|**Šířka**|Poskytuje prostor pro zadání šířku vlastního obrázku v pixelech (1-512, limit 2048).|
|**Výška**|Poskytuje prostor pro zadání výška vlastního obrázku v pixelech (1-512, limit 2048).|
|**Barvy**|Poskytuje prostor můžete zvolit počet barev pro vlastní image: 2, 16 nebo 256.|

## <a name="open-ltdevicegt-image-dialog-box"></a>Otevřít &lt;zařízení&gt; dialogové okno Obrázek

Použití **otevřete &lt;zařízení&gt; Image** dialogové okno otevřete obrázcích zařízení v projektech C++. Zobrazí seznam stávajících zařízení imagí v aktuální prostředek (bitové kopie, které jsou součástí aktuální prostředek). Je zahrnut následující vlastnost:

|Vlastnost|Popis|
|---|---|
|**Aktuálních Imagí**|Obsahuje seznam imagí, které jsou zahrnuté v prostředku. Výběr typu image, kterou chcete otevřít.|

## <a name="to-create-a-new-icon-or-cursor"></a>Chcete-li vytvořit nové ikony nebo kurzoru

1. V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na soubor .rc a pak zvolte **vložit prostředků** z místní nabídky. (Pokud už máte existující prostředek obrázku v souboru .rc, jako je například kurzoru, kliknete pravým tlačítkem **kurzor** a pak zvolte položku **vložení kurzoru** z místní nabídky.)

   > [!NOTE]
   > Pokud váš projekt již neobsahuje soubor .rc, najdete [vytváření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).

1. V [vložit prostředek – dialogové okno](../windows/add-resource-dialog-box.md)vyberte **ikonu** nebo **kurzor** a zvolte **nový**. U ikon tato akce vytvoří prostředek s ikonou s 32 × 32, ikona 16 barev. Pro ukazatele, 32 × 32, bude vytvořena monochromatický obrázek (barvami. 2).

   Pokud symbol plus (**+**) se zobrazí u typu prostředku bitové kopie v **vložit prostředků** dialogové okno, znamená to, že šablony nástrojů jsou k dispozici. Vyberte znaménko plus rozbalit seznam šablon, vyberte šablonu a zvolte **nový**.

## <a name="requirements"></a>Požadavky

Žádná

## <a name="see-also"></a>Viz také

[Ikony a kurzory: Prostředky obrázků pro zobrazovací zařízení](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Ikony a kurzory: Prostředky obrázků pro zobrazovací zařízení](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[Nabídka obrázku](../windows/image-menu-image-editor-for-icons.md)<br/>
[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)<br/>
