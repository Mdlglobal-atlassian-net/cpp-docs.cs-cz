---
title: "Vlastní ovládací prvky v editoru dialogového okna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Custom Control
dev_langs: C++
helpviewer_keywords:
- controls [C++], templates
- custom controls [Visual Studio], dialog boxes
- custom controls [Visual Studio]
- dialog box controls, custom (user) controls
- Dialog editor, custom controls
ms.assetid: f494b314-4000-4bbe-bbd0-4b18fb71ede1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1ae2293cfdc20e662a72a2ef18c8e089c945fa35
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="custom-controls-in-the-dialog-editor"></a>Vlastní ovládací prvky v editoru dialogových oken
Editor dialogových oken umožňuje použít existující "vlastní" nebo "user" ovládacích prvků v poli šablony dialogového okna.  
  
> [!NOTE]
>  Vlastní ovládací prvky v tomto smyslu jsou Nezaměňovat s ovládacími prvky ActiveX. ActiveX – ovládací prvky se někdy označuje jako vlastní ovládací prvky OLE. Nepleťte si také tyto ovládací prvky s ovládacími prvky vykreslované uživatelem v systému Windows.  
  
 Tato funkce slouží ke vám umožňují používat ovládací prvky kromě těch, zadaný v systému Windows. V době běhu ovládacího prvku s třídou není spojen okno (není stejný jako třída C++). Častější způsob, jak provést stejný úkol je instalace libovolný ovládací prvek, například statické ovládací prvek, ve vašem dialogovém okně. Potom v době spuštění v [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) funkce, odeberte tuto kontrolu a nahraďte ji metodou vlastního ovládacího prvku.  
  
 Toto je starý techniku. Dnes doporučuje ve většině případů k zápisu ovládací prvek ActiveX nebo podtřídou běžného ovládacího prvku systému Windows.  
  
 U těchto vlastních ovládacích prvků jste omezeni na:  
  
-   V dialogovém okně Nastavení umístění.  
  
-   Zadejte popisek.  
  
-   Identifikace název třídy ovládacího prvku systému Windows (kód aplikace musíte zaregistrovat ovládací prvek s tímto názvem).  
  
-   Zadáním 32bitové šestnáctkové hodnotu, která nastaví styl ovládacího prvku.  
  
-   Nastavení rozšířených stylu.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

