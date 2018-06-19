---
title: Vytvoření nabídky | Microsoft Docs
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
- mnemonics, associating menu items
- menus, associating commands with mnemonic keys
- menus, creating
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 95d9051e44216de9a64b68fc112fe8f17de112e3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882073"
---
# <a name="creating-a-menu"></a>Vytvoření nabídky
> [!NOTE]
>  Okno prostředek není k dispozici v edicích Express.  
  
### <a name="to-create-a-standard-menu"></a>Chcete-li vytvořit standardní nabídky  
  
1.  Z **zobrazení** nabídky, klikněte na **zobrazení prostředků** a potom klikněte pravým tlačítkem na **nabídky** záhlaví a zvolte **přidat prostředek**. Zvolte **nabídky**.  
  
2.  Vyberte **nová položka** pole (obdélníku, která obsahuje "Zde typu") na panelu nabídek.  
  
     ![Pole nové položky v nabídce editoru](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")  
Pole nové položky  
  
3.  Zadejte název vaší nové nabídky, například "Soubor".  
  
     Text, který zadáte, se zobrazí v **nabídky** editoru a v **popisek** pole [vlastnosti – okno](/visualstudio/ide/reference/properties-window). Můžete upravit vlastnosti pro vaše nové nabídky v některém umístění.  
  
     Jakmile jste udělili nové nabídky název v řádku nabídek, pole Nová položka posune vpravo (abyste mohli přidat jiné nabídky) a jiného pole nové položky otevře pod první nabídky proto do něj může přidat příkazy nabídky.  
  
     ![Rozšířená pole nové položky](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")  
Nové pole položky s fokusem Zapuštěno po zadejte název nabídky  
  
    > [!NOTE]
    >  K vytvoření jedné položky nabídky v řádku nabídek, nastavte vlastnost automaticky otevřeném okně na hodnotu False.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editor nabídek](../windows/menu-editor.md)