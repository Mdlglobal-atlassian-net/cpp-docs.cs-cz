---
title: Přidání příkazů na nabídky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.menu
dev_langs:
- C++
helpviewer_keywords:
- menu items, adding to menus
- menus, adding items
- commands, adding to menus
- commands
- menu items
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3564a808d39aa81ed3b45a1bc5812b285199e04
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856316"
---
# <a name="adding-commands-to-a-menu"></a>Přidání komentářů k nabídce
### <a name="to-add-commands-to-a-menu"></a>Chcete-li přidat příkazy k nabídce  
  
1.  [Vytvořit nabídku](../windows/creating-a-menu.md).  
  
2.  Klikněte na název nabídky, například souboru.  
  
     Jednotlivé nabídky bude rozbalte a vystavit nové pole položky pro příkazy. Například můžete přidat nové příkazy, otevřete a zavřete soubor nabídky.  
  
3.  Do pole nové položky zadejte název pro nový příkaz nabídky.  
  
    > [!NOTE]
    >  Zadáte text se zobrazí v editoru nabídky a v **popisek** pole [vlastnosti – okno](/visualstudio/ide/reference/properties-window). Můžete upravit vlastnosti pro vaše nové nabídky v některém umístění.  
  
    > [!TIP]
    >  Můžete definovat klávesovými klíč (přístupové klávesy), který umožňuje uživateli vybrat příkaz nabídky. Zadejte znak ampersand (&) před písmenem, zadejte je jako symbol. Uživatele můžete vybrat příkaz nabídky zadáním jím písmeno.  
  
4.  V okně Vlastnosti vyberte vlastnosti příkazu nabídky, které se vztahují. Podrobnosti najdete v tématu [vlastnosti příkazu nabídky](../windows/menu-command-properties.md).  
  
5.  V **řádku** pole v okně vlastností, zadejte výzvy řetězec, který se má zobrazit ve stavovém vaší aplikace.  
  
     Tím se vytvoří záznam v tabulce řetězců se stejným identifikátorem prostředků jako příkaz, který jste vytvořili.  
  
    > [!NOTE]
    >  Výzvy lze použít pouze pro položky, které nabídky **místní** vlastnost **True**. Například položek nabídek nejvyšší úrovně může mít výzvy, pokud mají položky dílčí nabídky. Účelem výzva je označuje, co se stane Pokud uživatel klikne na položku nabídky.  
  
6.  Stiskněte klávesu **ENTER** na dokončení příkazu nabídky.  
  
     Pole nové položky je vybrána, takže si můžete vytvořit další příkazy.  
  

  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor nabídek](../windows/menu-editor.md)   
