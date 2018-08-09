---
title: Nastavení vlastností akcelerátoru | Dokumentace Microsoftu
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
ms.openlocfilehash: 5337378b54c2109d05e28cb9d1bfed82f81913f3
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652695"
---
# <a name="setting-accelerator-properties"></a>Nastavení vlastností akcelerátoru
Můžete nastavit vlastnosti akcelerátoru [okno vlastností](/visualstudio/ide/reference/properties-window) kdykoli. Editor akcelerátorů můžete také použít k úpravě vlastností akcelerátoru v tabulce akcelerátorů. Změny provedené pomocí okna vlastnosti nebo editor akcelerátorů mít stejný výsledek: úpravy se okamžitě projeví v tabulce akcelerátorů.  
  
 Existují tři vlastnosti pro každý akcelerátor [ID](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160/locales/en-US):  
  
-   [Vlastnost modifikátoru](../windows/accelerator-modifier-property.md) nastaví prvek kombinace kláves pro akcelerátor.  
  
    > [!NOTE]
    >  V okně Vlastnosti, tato vlastnost se zobrazí jako tři samostatné logické vlastnosti, které je možné řídit nezávisle na sobě: **Alt**, **Ctrl**, a **Shift**.  
  
-   [Klíčové vlastnosti](../windows/accelerator-key-property.md) nastaví skutečné klíč pro použití jako akcelerátor.  
  
-   [Zadejte vlastnost](../windows/accelerator-type-property.md) Určuje, zda klíč je interpretován jako virtuální (VIRTKEY) nebo ASCII a ANSI.  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Předdefinované klávesy akcelerátoru](../windows/predefined-accelerator-keys.md)   
 [Editory prostředků](../windows/resource-editors.md)   
 [Editor akcelerátorů](../windows/accelerator-editor.md)