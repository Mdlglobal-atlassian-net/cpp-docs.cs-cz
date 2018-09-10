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
ms.openlocfilehash: eb08a9dce4c90c9efddd10683bc4b7c2ac0b08b9
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314414"
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

[Předdefinované klávesy akcelerátoru](../windows/predefined-accelerator-keys.md)  
[Editory prostředků](../windows/resource-editors.md)  
[Editor akcelerátorů](../windows/accelerator-editor.md)