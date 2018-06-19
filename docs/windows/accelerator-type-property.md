---
title: Vlastnost typu akcelerátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Type property
- VIRTKEY
ms.assetid: 8c349bc4-e6ad-43fa-959e-f29168af35b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cb1ba8f117fadab7cccb835ba8889d57bcc9f184
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856498"
---
# <a name="accelerator-type-property"></a>Vlastnost typu akcelerátoru
Akcelerátor **typ** vlastnost určuje, zda je klávesová zkratka přidružené k ID akcelerátoru virtuální kombinace klíče nebo klíče hodnotu ASCII nebo ANSI:  
  
-   Pokud **typ** vlastnost je **ASCII**, [modifikátor](../windows/accelerator-modifier-property.md) může být pouze None nebo Alt, nebo může mít akcelerátor, který používá klávesu CTRL (zadat tak, že před klíč s ^).  
  
-   Pokud **typ** vlastnost je **VIRTKEY**, libovolné kombinace hodnot modifikátor a klíč je platný.  
  
    > [!NOTE]
    >  Pokud chcete zadat hodnotu do tabulky akcelerátorů a mají hodnotu zacházet jako ASCII nebo ANSI, jednoduše klikněte na typ pro záznam v tabulce a z rozevíracího seznamu vyberte ASCII. Ale pokud používáte **další zadali klíč** příkazu (**upravit** nabídky) k určení klíče, je nutné změnit **typ** vlastnost z VIRTKEY ASCII *před* zadávání kódu klíč.  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Nastavení vlastností akcelerátoru](../windows/setting-accelerator-properties.md)   
 [Editor akcelerátorů](../windows/accelerator-editor.md)