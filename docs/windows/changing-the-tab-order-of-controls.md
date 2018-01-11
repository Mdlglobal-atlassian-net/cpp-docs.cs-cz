---
title: "Změna pořadí karet ovládacích prvků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- controls [C++], tab order
- focus, tab order
- tab controls, tab order
- Tabstop property for controls
- controls [C++], focus
- dialog box controls, tab order
ms.assetid: e2cee764-4367-42d7-9563-65a68f76f5ff
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dca6b1bb894aa2219a0352ba9c359e6f3c5a4677
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="changing-the-tab-order-of-controls"></a>Změna pořadí karet ovládacích prvků
Pořadí je pořadí, ve kterém klávesy TAB přesune zaměření pro vstup z jeden ovládací prvek v rámci dialogového okna. Pořadí karet obvykle pokračuje zleva doprava a shora dolů v dialogovém okně. Má každý ovládací prvek **zarážek tabulátorů** vlastnost, která určuje, zda ovládacího prvku obdrží zaměření pro vstup.  
  
### <a name="to-set-input-focus-for-a-control"></a>Chcete-li nastavit zaměření pro vstup pro ovládací prvek  
  
1.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window), vyberte **True** nebo **False** v **zarážek tabulátorů** vlastnost.  
  
 I ovládací prvky, které nemají vlastnost zarážek tabulátorů nastavená na hodnotu True musí být součástí pořadí. To může být důležité, například, když jste [přístupové klávesy (klávesové zkratky) definovat](../windows/defining-mnemonics-access-keys.md) pro ovládací prvky, které nemají titulky. Statický text, který obsahuje přístupový klíč pro související ovládací prvek okamžitě musí předcházet související ovládací prvek v pořadí.  
  
> [!NOTE]
>  Pokud vaše dialogové okno obsahuje překrývající se ovládací prvky, změna pořadí karet může změnit způsob, jakým se zobrazí ovládací prvky. Ovládací prvky, které jsou dále v pořadí karet se zobrazují vždy nad překrývající se ovládací prvky, které je předcházet v pořadí.  
  
#### <a name="to-view-the-current-tab-order-for-all-controls-in-a-dialog-box"></a>Chcete-li zobrazit aktuální pořadí pro všechny ovládací prvky v dialogovém okně  
  
1.  Na **formátu** nabídky, klikněte na tlačítko **pořadí karet**.  
  
 \-nebo –  
  
-   Stiskněte kombinaci kláves CTRL + D.  
  
#### <a name="to-change-the-tab-order-for-all-controls-in-a-dialog-box"></a>Chcete-li změnit pořadí pro všechny ovládací prvky v dialogovém okně  
  
1.  Na **formátu** nabídky, klikněte na tlačítko **pořadí karet**.  
  
     Číslo v levém horním rohu každé řízení zobrazí jeho místo v aktuální pořadí.  
  
2.  Kliknutím na každý ovládací prvek v pořadí, ve které klávesy TAB můžete postupovat podle nastavení pořadí karet.  
  
3.  Stiskněte klávesu **ENTER** ukončíte **pořadí karet** režimu.  
  
    > [!TIP]
    >  Jakmile zadáte režim pořadí karet, stisknutím klávesy ESC nebo zadejte možnost, chcete-li změnit pořadí zakázat.  
  
#### <a name="to-change-the-tab-order-for-two-or-more-controls"></a>Chcete-li změnit pořadí pro dva nebo více ovládacích prvků  
  
1.  Z **formátu** nabídce zvolte **pořadí karet**.  
  
2.  Zadejte, kde bude zahájena změna v pořadí. Chcete-li to provést, podržte klávesu **CTRL** klíče a klikněte na ovládací prvek před ten, kde chcete změněné pořadí zahájíte.  
  
     Například pokud chcete změnit pořadí prvků 7 až 9, podržte klávesu CTRL a potom vyberte první prvek 6.  
  
    > [!NOTE]
    >  Nastavit určitý ovládací prvek na číslo 1 (první v pořadí), dvakrát klikněte na ovládací prvek.  
  
3.  Uvolněte klávesu CTRL a potom klikněte na ovládací prvky v pořadí, ve které klávesy TAB můžete postupovat podle od tohoto okamžiku.  
  
4.  Stiskněte klávesu **ENTER** ukončíte **pořadí karet** režimu.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Uspořádání ovládacích prvků v dialogových oknech](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

