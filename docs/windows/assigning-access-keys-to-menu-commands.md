---
title: Přiřazení přístupových kláves k příkazům nabídky | Dokumentace Microsoftu
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
ms.openlocfilehash: 4745bd188f42b5df976750f952a91ce0e30a9cd9
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39645796"
---
# <a name="assigning-access-keys-to-menu-commands"></a>Přiřazení přístupových kláves příkazům nabídky
Přístupový klíč (symbol, který umožňuje uživateli vybrat nabídku pomocí klávesnice) můžete přiřadit nabídek a příkazů nabídky.  
  
### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Přiřazení (místní) přístupový klíč k příkazu nabídky  
  
1.  Zadejte znak ampersand (`&`) před písmena v názvu nabídky nebo název příkazu zadat písmeno jako odpovídající přístupový klíč. Například "& soubor" sady **Alt**+**F** jako klávesovou zkratku **souboru** nabídky aplikace napsané pro Microsoft Windows.  
  
     Položka nabídky bude informovat viditelné s jedním z písmen klávesová zkratka přiřazena. Následující písmeno, znak ampersand se zobrazí podtržený (závislý na operační systém).  
  
    > [!NOTE]
    >  Ujistěte se, že přístupové klíče v nabídce jsou jedinečné pravým tlačítkem myši na vaše nabídky a zvolením **zkontrolujte klávesových zkratek** z místní nabídky.  
  
 Informace o přidávání prostředků do spravovaných projektů, najdete v tématu [prostředky v desktopových aplikací](/dotnet/framework/resources/index) v *rozhraní .NET Framework Developer's Guide*. Informace o ručním přidání souborů prostředků do spravovaných projektů, přístupu k prostředkům, zobrazení statických prostředků a přiřazení řetězců prostředků k vlastnostem, naleznete v tématu [Creating Resource Files pro desktopových aplikací](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor nabídek](../windows/menu-editor.md)