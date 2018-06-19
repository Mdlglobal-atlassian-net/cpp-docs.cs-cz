---
title: Vlastnost klávesy akcelerátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Key property
ms.assetid: d1570cd9-b414-4cd6-96bd-47c38281eaca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e4fc56384d666026f4cc7e21f9d8af9347046fd1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857204"
---
# <a name="accelerator-key-property"></a>Vlastnost klávesy akcelerátoru
Dále jsou právní položky pro vlastnost klíč v tabulce akcelerátorů:  
  
-   Celé číslo mezi 0 a 255 ve formátu desetinného čísla. Hodnota určuje, zda je hodnota považovány za ASCII nebo ANSI následujícím způsobem:  
  
    -   Jednociferné čísla jsou vždy vyhodnocena jako odpovídající klíč, nikoli jako hodnoty ASCII nebo ANSI.  
  
    -   Hodnoty od 1 do 26, je-li před nul, se interpretují jako ^ A prostřednictvím ^ Z, která představuje hodnotu ASCII písmena abecedy při stisknutí se stisknutou klávesou CTRL.  
  
    -   Hodnoty z 27-32 jsou vždy interpretovat jako desetinných míst třímístné 027 prostřednictvím 032.  
  
    -   Hodnoty z 033 do 255, ať už před sebou na 0 nebo nejsou vyhodnocena jako hodnoty ANSI.  
  
-   Klávesnice jeden znak. Velká písmena A - Z nebo číslice 0 – 9 může být ASCII nebo virtuální hodnoty klíče; Další znak je pouze v ASCII.  
  
-   Klávesnice jeden znak v rozsahu A – Z (velká písmena pouze), před sebou šipka nahoru (^) (například ^ C). To zadá hodnotu ASCII klíče při stisknutí se stisknutou klávesou CTRL.  
  
    > [!NOTE]
    >  Pokud zadáte hodnotu ASCII, možnosti vlastnost modifikátor budou omezeny. Jenom řízení klíč k dispozici pro použití je klávesu ALT.  
  
-   Všechny platné virtuální identifikátor klíče. Rozevírací seznam klíč v tabulce akcelerátorů obsahuje seznam identifikátorů standardní virtuální klíče.  
  
    > [!TIP]
    >  Jiný způsob, jak definovat klávese akcelerátoru je klikněte pravým tlačítkem na položku nebo více položek v tabulce akcelerátorů, zvolte **další zadali klíč** z místní nabídky a potom stiskněte klávesu klíče nebo kombinace kláves na klávesnici. **Další zadali klíč** je k dispozici z také **upravit** nabídky.  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Nastavení vlastností akcelerátoru](../windows/setting-accelerator-properties.md)   
 [Úprava v tabulce akcelerátorů](../windows/editing-in-an-accelerator-table.md)   
 [Editor akcelerátorů](../windows/accelerator-editor.md)