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
ms.openlocfilehash: 3ac4a7f23e6f37891851740ed65356d7d2bec3c0
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593620"
---
# <a name="saving-and-loading-different-color-palettes-image-editor-for-icons"></a>Ukládání a načítání různých barevných palet (editor obrázků pro ikony)

Můžete uložit a načíst **barvy** paletu, která obsahuje [přizpůsobit barvy](../windows/customizing-or-changing-colors-image-editor-for-icons.md). (Ve výchozím nastavení, **barvy** palety naposledy použité se vyplní automaticky, když spustíte Visual Studio.)

> [!TIP]
> Protože **Image** editor neobsahuje žádný způsob, jak obnovit výchozí **barvy** palety, měli byste uložit výchozí **barvy** palety pod názvem, jako  *Standard.PAL* nebo *default.pal* tak, aby je snadno obnovit výchozí nastavení.

### <a name="to-save-a-custom-colors-palette"></a>Chcete-li uložit vlastní barvy palety

1. Z **Image** nabídce zvolte **Uložit paletu**.

2. Přejděte do adresáře, kam chcete uložit paletu a zadejte název pro paletě.

3. Klikněte na tlačítko **Uložit**.

### <a name="to-load-a-custom-colors-palette"></a>Načíst vlastní barvy palety

1. Z **Image** nabídce zvolte **načíst paletu**.

2. V [dialogové okno Načíst barvy palety](../windows/load-palette-colors-dialog-box-image-editor-for-icons.md), přejděte do správného adresáře a vybrat paletu, který chcete načíst. **Barva** palety se uloží s příponou souboru .pal.

## <a name="requirements"></a>Požadavky

Žádné

## <a name="see-also"></a>Viz také

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)  
[Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)