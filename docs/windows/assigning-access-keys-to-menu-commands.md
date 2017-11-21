---
title: "Přiřazení přístupových kláves příkazům nabídky | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 27291689e3fbfb9418d783917f59ffeee7a54235
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="assigning-access-keys-to-menu-commands"></a>Přiřazení přístupových kláves příkazům nabídky
Přístupový klíč (symbol, který umožňuje uživateli vybrat v nabídce pomocí klávesnice) můžete přiřadit nabídek a příkazů nabídky.  
  
### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Přiřazení (místní) přístupový klíč k příkazu nabídky  
  
1.  Zadejte znak ampersand (**&**) před písmenem v nabídce název nebo název příkazu k určení jím písmeno jako odpovídající přístupový klíč. Například "& souboru" sady ALT + F jako klávesovou zkratku v aplikace napsané pro Microsoft Windows v nabídce Soubor.  
  
     Položky nabídky poskytne viditelné signálem, že jedno z písmen obsahuje klávesovou zkratku přiřazen. Následující písmeno, které se zobrazí ampersand podtrhnou (contingent na operačním systému).  
  
    > [!NOTE]
    >  Zkontrolujte, zda všechny přístupové klíče v nabídce jsou jedinečné pravým tlačítkem myši na vaší nabídky a zvolením **zkontrolovat klávesové zkratky** z místní nabídky.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor nabídek](../windows/menu-editor.md)