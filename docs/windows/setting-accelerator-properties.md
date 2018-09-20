---
title: Nastavení vlastností akcelerátoru (C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 85d32a3dc01f5c0a496e6471472dab1cfafa0ca0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46437466"
---
# <a name="setting-accelerator-properties"></a>Nastavení vlastností akcelerátoru

Můžete nastavit vlastnosti akcelerátoru [okno vlastností](/visualstudio/ide/reference/properties-window) kdykoli. Můžete také použít **akcelerátoru** editor k úpravě vlastností akcelerátoru v tabulce akcelerátorů. Změny provedené pomocí **vlastnosti** okno nebo **akcelerátoru** editor mít stejný výsledek: úpravy se okamžitě projeví v tabulce akcelerátorů.

Existují tři vlastnosti každé ID akcelerátoru:

- [Vlastnost modifikátoru](../windows/accelerator-modifier-property.md) nastaví prvek kombinace kláves pro akcelerátor.

   > [!NOTE]
   > V **vlastnosti** okna, tato vlastnost se zobrazí jako tři samostatné logické vlastnosti, které je možné řídit nezávisle na sobě: **Alt**, **Ctrl**a **Shift**.

- [Klíčové vlastnosti](../windows/accelerator-key-property.md) nastaví skutečné klíč pro použití jako akcelerátor.

- [Zadejte vlastnost](../windows/accelerator-type-property.md) Určuje, zda klíč je interpretován jako virtuální (VIRTKEY) nebo ASCII a ANSI.

## <a name="requirements"></a>Požadavky

Win32

## <a name="see-also"></a>Viz také

[Předdefinované klávesy akcelerátoru](../windows/predefined-accelerator-keys.md)<br/>
[Editory prostředků](../windows/resource-editors.md)<br/>
[Editor akcelerátorů](../windows/accelerator-editor.md)