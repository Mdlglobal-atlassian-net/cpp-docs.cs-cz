---
title: Přiřazení přístupových kláves příkazům nabídky | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- access keys [C++], checking
- menus, shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics, adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics, uniqueness checking
- Check Mnemonics command
ms.assetid: fbcf1a00-af6a-4171-805a-0ac01d4e8b0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 44a21e5930d0d8f2fcaad79cc5cef5bc984ad8b5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="assigning-access-keys-to-menu-commands"></a>Přiřazení přístupových kláves příkazům nabídky
Přístupový klíč (symbol, který umožňuje uživateli vybrat v nabídce pomocí klávesnice) můžete přiřadit nabídek a příkazů nabídky.  
  
### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Přiřazení (místní) přístupový klíč k příkazu nabídky  
  
1.  Zadejte znak ampersand (**&**) před písmenem v nabídce název nebo název příkazu k určení jím písmeno jako odpovídající přístupový klíč. Například "& souboru" sady ALT + F jako klávesovou zkratku v aplikace napsané pro Microsoft Windows v nabídce Soubor.  
  
     Položky nabídky poskytne viditelné signálem, že jedno z písmen obsahuje klávesovou zkratku přiřazen. Následující písmeno, které se zobrazí ampersand podtrhnou (contingent na operačním systému).  
  
    > [!NOTE]
    >  Zkontrolujte, zda všechny přístupové klíče v nabídce jsou jedinečné pravým tlačítkem myši na vaší nabídky a zvolením **zkontrolovat klávesové zkratky** z místní nabídky.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor nabídek](../windows/menu-editor.md)