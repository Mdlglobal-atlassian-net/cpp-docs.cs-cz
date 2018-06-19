---
title: Vytvoření vlastního štětce (Editor obrázků pro ikony) | Microsoft Docs
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
ms.openlocfilehash: a879850c00957568065150b6c6fc1c801c049fa2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33873144"
---
# <a name="creating-a-custom-brush-image-editor-for-icons"></a>Vytvoření vlastního štětce (editor obrázků pro ikony)
Vlastní štětce je obdélníková část imagí, která se vyzvedávat a použít jako jeden z předdefinovaných štětce editor obrázků. Všechny operace, které můžete provádět na výběr, můžete u vlastního štětce.  
  
### <a name="to-create-a-custom-brush-from-a-portion-of-an-image"></a>Vytvoření vlastního štětce z část obrázku  
  
1.  [Vyberte část obrázku](../windows/selecting-an-area-of-an-image-image-editor-for-icons.md) , kterou chcete použít pro štětce.  
  
2.  Podržíte **SHIFT** klíče dolů, klikněte na tlačítko ve výběru a přetáhněte ji napříč bitovou kopii.  
  
     \- nebo –  
  
3.  Z **Image** nabídce zvolte **použít výběr jako štětce**.  
  
     Výběr stane vlastního štětce, která distribuuje barev ve výběru v bitovou kopii. Zkopíruje výběr jsou ponechána v přetahování cestě. Tím pomaleji přetažení, jsou provedeny další kopie.  
  
     **Poznámka:** kliknutím **použít výběr jako štětce** bez výběrem položky část obrázku použije bitovou kopii celou jako štětce. Výsledek pomocí vlastního štětce bude také záviset na tom, zda jste vybrali [neprůhledné nebo průhledná pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
 Pixelů vlastního štětce, které odpovídají aktuálním barvu pozadí jsou obvykle transparentní: není malovat přes existující bitová kopie. Toto chování můžete změnit tak, aby barva pozadí pixelů malovat přes existující bitová kopie.  
  
 Vlastní štětce jako razítko nebo vzorníku můžete vytvořit různé speciální efekty.  
  
#### <a name="to-draw-custom-brush-shapes-in-the-background-color"></a>Kreslení tvarů vlastního štětce v barvu pozadí  
  
1.  [Vyberte neprůhledné nebo průhledné pozadí](../windows/choosing-a-transparent-or-opaque-background-image-editor-for-icons.md).  
  
2.  [Nastavení barvy pozadí](../windows/selecting-foreground-or-background-colors-image-editor-for-icons.md) na barvu, ve kterém chcete kreslení.  
  
3.  Nastavte vlastního štětce, kam chcete k vykreslení.  
  
4.  Klikněte pravým tlačítkem myši. Všechny neprůhledné oblasti vlastního štětce jsou vykreslovány v barvu pozadí.  
  
#### <a name="to-double-or-halve-the-custom-brush-size"></a>Dvakrát nebo polovinu velikost vlastního štětce  
  
1.  Stiskněte **znaménko PLUS** (**+**) klíč dvojnásobku velikosti štětce nebo **ZNAMÉNKA MINUS** (**-**) klíče na polovinu ho .  
  
#### <a name="to-cancel-the-custom-brush"></a>Chcete-li zrušit vlastního štětce  
  
1.  Stiskněte klávesu **ESC** nebo zvolte jiný nástroj pro vykreslování.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Požadavky  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Úprava grafických prostředků](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [Editor obrázků pro ikony](../windows/image-editor-for-icons.md)

