---
title: Ukládání a načítání různých barevných palet (Editor obrázků pro ikony) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.image.color
dev_langs:
- C++
helpviewer_keywords:
- color palettes [C++]
- palettes
- palettes, Image editor
- colors [C++], Image editor
- Image editor [C++], palettes
ms.assetid: 694b6346-e606-4f19-aa01-9b4ceb47f423
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8b96411341baeb6abb75c44063072b94fae3ac6a
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Ukládání a načítání různých barevných palet (editor obrázků pro ikony)
Můžete uložit a načíst barvy palety, který obsahuje [přizpůsobit barvy](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (Ve výchozím nastavení, barevná paleta naposledy použité je načtou automaticky při spuštění sady Visual Studio.)  
  
> [!TIP]
>  Vzhledem k tomu, že editor obrázků nemá žádný způsob, jak obnovit výchozí barvy palety, byste měli uložit výchozí barevná paleta pod názvem například standard.pal nebo default.pal tak, aby můžete snadno obnovit výchozí nastavení.  
  
### <a name="to-save-a-custom-colors-palette"></a>Uložte vlastní barevná paleta  
  
1.  Z **Image** nabídce zvolte **uložit palety**.  
  
2.  Přejděte do adresáře, kam chcete uložit paletu a zadejte název paletě.  
  
3.  Klikněte na tlačítko **Uložit**.  
  
### <a name="to-load-a-custom-colors-palette"></a>Načíst vlastní barevná paleta  
  
1.  Z **Image** nabídce zvolte **zatížení palety**.  
  
2.  V [dialogové okno Načíst barvy palety](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), přejděte do adresáře, správné a vyberte palety chcete načíst. Palety barev se uloží s příponou souboru PAL.  
  

  
 Požadavky  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)