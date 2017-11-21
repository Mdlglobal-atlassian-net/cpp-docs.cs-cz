---
title: "Nastavení vlastností akcelerátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- accelerator properties
- properties [C++], accelerator properties
- Type property
- Key property
- Modifier property
ms.assetid: 0fce9156-3025-4e18-b034-e219a4c65812
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8a83b155b5e0a350d5c578a8dccfb9040cec3df
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2017
---
# <a name="setting-accelerator-properties"></a>Nastavení vlastností akcelerátoru
Vlastnosti akcelerátoru můžete nastavit v [vlastnosti – okno](/visualstudio/ide/reference/properties-window) kdykoli. Editor akcelerátorů můžete také použít k úpravě vlastností akcelerátoru v tabulce akcelerátorů. Změny provedené pomocí okna vlastnosti nebo editor akcelerátorů mít stejný výsledek: úpravy se okamžitě projeví v tabulce akcelerátorů.  
  
 Nejsou k dispozici tři vlastnosti pro každý akcelerátoru [ID](https://www.microsoftonedoc.com/#/organizations/e6f6a65cf14f462597b64ac058dbe1d0/projects/3fedad16-eaf1-41a6-8f96-0c1949c68f32/containers/a3daf831-1c5f-4bbe-964d-503870caf874/tocpaths/3487f185-de96-4b1d-87db-034a52223160/locales/en-US):  
  
-   [Modifikátor – vlastnost](../windows/accelerator-modifier-property.md) nastaví kombinace kláves pro akcelerátor ovládacího prvku.  
  
    > [!NOTE]
    >  V okně vlastností tato vlastnost se zobrazí jako tři samostatné logická hodnota vlastnosti, které lze kontrolovat nezávisle: Alt, Ctrl a Shift.  
  
-   [Klíče vlastnost](../windows/accelerator-key-property.md) nastaví skutečný klíč pro použití jako zkratku.  
  
-   [Zadejte vlastnost](../windows/accelerator-type-property.md) Určuje, zda je klíč interpretována jako virtuální (VIRTKEY) nebo ASCII nebo ANSI.  
  

  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Předdefinované klávesy akcelerátoru](../windows/predefined-accelerator-keys.md)   
 [Editory prostředků](../windows/resource-editors.md)   
 [Editor akcelerátorů](../windows/accelerator-editor.md)