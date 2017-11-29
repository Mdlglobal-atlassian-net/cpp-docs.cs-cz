---
title: "Seskupování přepínačů v dialogovém okně | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.dialog.grouping
dev_langs: C++
helpviewer_keywords:
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls, grouping radio buttons
- grouping controls
- radio buttons, grouping on dialog boxes
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 40d1c75dfe70a5dcdf664f105f2872475219e294
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="grouping-radio-buttons-on-a-dialog-box"></a>Seskupení přepínačů v dialogovém okně
Když přidáte přepínače do dialogového okna, je považovat za skupinu nastavením vlastnosti skupiny v okně Vlastnosti pro první tlačítko ve skupině. ID ovládacího prvku pro tento přepínač se potom zobrazí v [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md), umožňuje přidání členské proměnné skupiny přepínačů.  
  
 Máte více než jedné skupině přepínacích tlačítek v dialogovém okně a každá skupina přidaly pomocí následujícího postupu.  
  
### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>K přidání skupiny přepínačů do dialogového okna  
  
1.  Vyberte ovládacího prvku tlačítko přepínač [okno sady nástrojů](/visualstudio/ide/reference/toolbox) a klikněte na umístění v dialogovém okně místo, kam chcete umístit ovládacího prvku.  
  
2.  Zopakujte krok 1 pro přidání tolika přepínačů, podle potřeby. Ujistěte se, že přepínače ve skupině jsou po sobě jdoucích v pořadí (Další informace najdete v tématu [Změna pořadí karet ovládacích prvků](../windows/changing-the-tab-order-of-controls.md)).  
  
3.  V [vlastnosti – okno](/visualstudio/ide/reference/properties-window), nastavte **skupiny** vlastnost *první* přepínač v pořadí pro **True**.  
  
     Změna **skupiny** vlastnost **True** styl ws_group – přidá do na tlačítko záznam v objektu dialogového okna skriptu prostředků a zajistí, že uživatel zvolit pouze jeden přepínač dobu tlačítko skupiny (po kliknutí na přepínač jeden, ostatní ve skupině jsou vymazány).  
  
    > [!NOTE]
    >  Pouze první přepínač ve skupině měli **skupiny** vlastnost nastavena na hodnotu **True**. Pokud máte další ovládací prvky, které nejsou součástí skupina tlačítek, nastavte **skupiny** vlastnost prvního ovládacího prvku *, je mimo skupinu* k **True** také. První prvek mimo skupinu můžete rychle identifikovat stisknutím kombinace kláves CTRL + D zobrazíte pořadí.  
  
### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Přidání členské proměnné pro skupině přepínacích tlačítek  
  
1.  Klikněte pravým tlačítkem první prvek přepínač v pořadí (dominantního ovládacího prvku a ten se **skupiny** vlastností nastavenou na hodnotu True).  
  
2.  Zvolte **přidat proměnnou** z místní nabídky.  
  
3.  V [Průvodce přidáním členské proměnné](../ide/add-member-variable-wizard.md), vyberte **řídicí proměnná** zaškrtněte políčko a potom vyberte **hodnotu** přepínač.  
  
4.  V **název proměnné** pole, zadejte název nové proměnné členů.  
  
5.  V **typ proměnné** pole se seznamem, vyberte **int** nebo typ **int**.  
  
6.  Nyní můžete upravit kód a zadejte, který přepínač by se měla objevit vybrané. Například m_radioBox1 = 0; Vybere první přepínač ve skupině.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Uspořádání ovládacích prvků v dialogových oknech](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)
