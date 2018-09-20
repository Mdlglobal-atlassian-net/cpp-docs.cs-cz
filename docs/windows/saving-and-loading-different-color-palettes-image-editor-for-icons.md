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
ms.openlocfilehash: 50e74c65e080b11583e6ff1e591ef612b17e9533
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438883"
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

[Klávesy akcelerátoru](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[Práce s barvou](../windows/working-with-color-image-editor-for-icons.md)