---
title: Přiřazení příkazu nabídky ke klávese akcelerátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts, menu association
- commands, associating menu commands with accelerator keys
- menu commands, associating with keyboard shortcuts
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c4f1aa4b80aec2e7c16485c08d2505695b21f4d5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858078"
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
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Přidání příkazů na nabídky](../windows/adding-commands-to-a-menu.md)   
 [Editor nabídek](../windows/menu-editor.md)