---
title: Vytvoření vlastního štětce (Editor obrázků pro ikony) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- colors [C++], brush
- brushes, colors
- brushes, creating custom
- images [C++], creating custom brushes
- graphics [C++], custom brushes
- custom brushes
ms.assetid: 750881aa-6f47-4de9-8ca6-a7a12afc6383
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 62e4cb9d6eebee4235db2bc38b2cd20935493b02
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42607977"
---
# <a name="creating-a-custom-brush-image-editor-for-icons"></a>Vytvoření vlastního štětce (editor obrázků pro ikony)

Vlastní štětce je obdélníkovou část bitovou kopii, která sbírání a používat jako jeden z **Image** předem připravená štětce editoru. Všechny operace, které můžete provádět na výběr, můžete provádět na vlastní štětce.

### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Vytvoření vlastního štětce z část obrázku

1. [Vyberte část obrázku](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) , kterou chcete použít pro štětce.

2. Podržení **Shift** klíče dolů, klikněte na tlačítko ve výběru a proveďte operaci přetažení přes obrázek.

   \- nebo –

3. Z **Image** nabídce zvolte **použít výběr jako štětce**.

   Váš výběr se změní vlastní štětec, který distribuuje barev ve výběru mezi bitovou kopii. Zkopíruje výběr jsou ponechána na cestě přetahování. Tím pomaleji se při přetahování, jsou provedeny další kopie.

   > [!NOTE]
   > Kliknutím **použít výběr jako štětce** bez nejprve vyberete část obrázku použije celého obrázku jako štětce. Výsledek použití vlastního štětce také závisí na tom, zda jste vybrali [neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

Pixelů vlastního štětce, které odpovídají barvě pozadí jsou obvykle transparentní: není vykreslení přes stávající bitovou kopii. Toto chování můžete změnit tak, aby barvu pozadí pixelů vykreslení přes stávající bitovou kopii.

Vlastní štětce jako razítko nebo vzorníku slouží k vytvoření širokou škálu speciální efekty.

### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Pro kreslení tvarů vlastní štětec pozadí barvou

1. [Vyberte neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).

2. [Nastavit barvu pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) barvu, ve kterém chcete kreslit.

3. Pozice vlastního štětce, ve které chcete kreslit.

4. Klikněte pravým tlačítkem myši. Jakékoli neprůhledné oblastech vlastního štětce vykresleny barvou pozadí.

### <a name="to-double-or-halve-the-custom-brush-size"></a>Dvakrát nebo polovinu velikost vlastního štětce

1. Stisknutím klávesy **znaménko Plus** (**+**) klíč na dvojnásobek velikosti štětce nebo **znaménko Minus** (**-**) klíč na polovinu ho .

### <a name="to-cancel-the-custom-brush"></a>Chcete-li zrušit vlastního štětce

1. Stisknutím klávesy **Esc** nebo zvolte jiný nástroj pro vykreslování.

Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)  
[Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[Editor obrázků pro ikony](../windows/image-editor-for-icons.md)