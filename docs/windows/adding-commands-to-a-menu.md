---
title: Přidání příkazů do nabídky | Dokumentace Microsoftu
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
ms.openlocfilehash: c0c744e920c71b74d9296e6961add704435658fe
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644726"
---
# <a name="adding-commands-to-a-menu"></a>Přidání komentářů k nabídce
### <a name="to-add-commands-to-a-menu"></a>Chcete-li přidat do nabídky příkazů  
  
1.  [Vytvořit nabídku](../windows/creating-a-menu.md).  
  
2.  Klikněte na název nabídky, například **souboru**.  
  
     Každá nabídka bude rozbalte a vystavovat nové položky pole pro příkazy. Například můžete přidat příkazy **nový**, **otevřít**, a **Zavřít** k **souboru** nabídky.  
  
3.  Do pole nové položky zadejte název pro nový příkaz nabídky.  
  
    > [!NOTE]
    >  Text, který zadáte, se zobrazí v **nabídky** editoru a **titulek** pole [okno vlastností](/visualstudio/ide/reference/properties-window). Upravit vlastnosti pro vaše nové nabídce v některém umístění.  
  
    > [!TIP]
    >  Můžete definovat přístupové klávesy (Klávesová zkratka), který umožňuje uživateli vybrat příkaz nabídky. Zadejte znak ampersand (`&`) před písmenem určit jako symbol. Uživatel může vybrat příkaz nabídky tak, že zadáte písmeno.  
  
4.  V **vlastnosti** okna, vyberte příkaz Vlastnosti, které se vztahují na nabídku. Podrobnosti najdete v tématu [vlastnosti příkazu nabídky](../windows/menu-command-properties.md).  
  
5.  V **řádku** pole **vlastnosti** okno, zadejte řetězec výzvy, které se mají zobrazit ve stavovém řádku vaší aplikace.  
  
     Tím se vytvoří záznam v tabulce řetězců se stejným identifikátorem prostředku jako příkaz, který jste vytvořili.  
  
    > [!NOTE]
    >  Výzvy lze použít pouze pro položky nabídky **automaticky otevírané okno** vlastnost **True**. Například položky nabídek nejvyšší úrovně může mít výzvy, pokud mají položky dílčí nabídky. Účel **výzvy** je určit, co se stane, pokud uživatel klikne na položku nabídky.  
  
6.  Stisknutím klávesy **Enter** na dokončení příkazu nabídky.  
  
     Nové položky políčko je zaškrtnuto, takže si můžete vytvořit další příkazy.  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor nabídek](../windows/menu-editor.md)   