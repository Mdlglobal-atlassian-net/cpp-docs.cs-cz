---
title: "Přiřazení příkazu nabídky ke klávese akcelerátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- keyboard shortcuts, menu association
- commands, associating menu commands with accelerator keys
- menu commands, associating with keyboard shortcuts
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 26a44a8d1c2ddd32a63f86e0cba932da2437bad2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="associating-a-menu-command-with-an-accelerator-key"></a>Přiřazení příkazu nabídky ke klávese akcelerátoru
Jsou často časy, kdy má příkaz nabídky a kombinace kláves vydejte stejný příkaz programu. Můžete to provést pomocí editoru nabídky přiřadit stejný identifikátor prostředku, na příkaz nabídky a položce v tabulce akcelerátorů vaší aplikace. Potom upravte [popisek](../windows/menu-command-properties.md) příkazu v nabídce Zobrazit název klíče akcelerátoru.  
  
### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Chcete-li přidružit příkazu nabídky ke klávese akcelerátoru  
  
1.  V **nabídky** editor, vyberte požadovaný příkaz nabídky.  
  
2.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window), přidejte název klíče akcelerátoru k **popisek** vlastnost:  
  
    -   Následující titulek nabídky zadejte řídicí sekvence karta (\t), tak, aby všechny, které jsou ponechána v nabídce klávesy akcelerátoru zarovnána.  
  
    -   Zadejte název klíče – modifikátor (**CTRL**, **ALT**, nebo **SHIFT**) následovat znak plus (**+**) a název, písmeno, nebo symbol další klíče.  
  
         Například přiřadit **CTRL + O** k **otevřete** příkaz na **soubor** nabídce Upravit příkaz nabídky **popisek** tak, aby vypadal jako Toto:  
  
        ```  
        &Open...\tCtrl+O   
        ```  
  
         Příkaz nabídky v editoru nabídky je aktualizována tak, aby odrážely novou titulek při psaní ho.  
  
3.  [Vytvoření položky tabulky akcelerátorů](../windows/adding-an-entry-to-an-accelerator-table.md) v **akcelerátoru** editoru a přiřaďte ho stejný identifikátor jako příkaz nabídky. Pomocí kombinace kláves, který si myslíte, že se bude snadno pamatovat.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Přidání příkazů na nabídky](../windows/adding-commands-to-a-menu.md)   
 [Editor nabídek](../windows/menu-editor.md)