---
title: Ukládání a načítání různých barevných palet (Editor obrázků pro ikony) | Dokumentace Microsoftu
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
ms.openlocfilehash: 14cad19c53e8cd741bf16bab49420169e93f6af6
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2018
ms.locfileid: "39606969"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Ukládání a načítání různých barevných palet (editor obrázků pro ikony)
Můžete uložit a načíst paletu barev, která obsahuje [přizpůsobit barvy](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (Ve výchozím nastavení, barevná paleta naposledy použité se vyplní automaticky, když spustíte Visual Studio.)  
  
> [!TIP]
>  Protože editoru obrázků nemá žádný způsob, jak obnovit výchozí barvy palety, měli byste uložit výchozí palety barev pod názvem, jako je například standard.pal nebo default.pal tak, aby je snadno obnovit výchozí nastavení.  
  
### <a name="to-save-a-custom-colors-palette"></a>Chcete-li uložit vlastní barvy palety  
  
1.  Z **Image** nabídce zvolte **Uložit paletu**.  
  
2.  Přejděte do adresáře, kam chcete uložit paletu a zadejte název pro paletě.  
  
3.  Klikněte na tlačítko **Uložit**.  
  
### <a name="to-load-a-custom-colors-palette"></a>Načíst vlastní barvy palety  
  
1.  Z **Image** nabídce zvolte **načíst paletu**.  
  
2.  V [dialogové okno Načíst barvy palety](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), přejděte do správného adresáře a vybrat paletu, který chcete načíst. Palety barev, které se uloží s příponou souboru .pal.  
  
## <a name="requirements"></a>Požadavky  
  
 Žádné  
  
## <a name="see-also"></a>Viz také  
 [Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)   
 [Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)