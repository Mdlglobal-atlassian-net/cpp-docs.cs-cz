---
title: "Postupy: otevření souboru skriptu prostředků mimo projekt (samostatný) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.resource
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- .rc files, viewing resources
- resource script files, viewing resources
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cfe2df286960ca332a6c3d9ef33d53e0a5edb3bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-open-a-resource-script-file-outside-of-a-project-standalone"></a>Postupy: Otevření souboru skriptu prostředků mimo projekt (samostatný)
Prostředky můžete zobrazit v souboru .rc bez nutnosti otevřít projekt. Soubor se otevře v okně dokumentu a otevírání v [zobrazení prostředků](../windows/resource-view-window.md) okno (stejně jako když je soubor otevřete v projektu).  
  
> [!NOTE]
>  To je zásadní rozdíl, protože některé příkazy nejsou k dispozici, pouze když je soubor otevřenou samostatné (mimo projekt). Například můžete pouze uložit soubor do jiného formátu nebo jako jiný název souboru při otevření souboru mimo projekt ( **uložit jako** příkaz není k dispozici po otevření souboru v projektu).  
  
### <a name="to-open-an-rc-file-outside-a-project"></a>Otevřete soubor .rc mimo projekt  
  
1.  Z **soubor** nabídce zvolte **otevřete**, pak klikněte na tlačítko **soubor**.  
  
2.  V **otevření souboru** dialogové okno pole, přejděte do souboru skriptu prostředků, které chcete zobrazit, zvýrazněte soubor a klikněte na tlačítko **otevřete**.  
  
    > [!NOTE]
    >  Pokud nejprve otevřete projekt (**soubor**, **otevřete**, **projektu**), některé příkazy nebudou k dispozici. Otevření souboru "samostatnou" znamená otevření bez prvního načítání projektu.  
  
 Otevřít a zobrazit souboru prostředků v textovém formátu, najdete v části [úpravy skriptu prostředků (.rc) soubor](../windows/how-to-open-a-resource-script-file-in-text-format.md).  
  
#### <a name="to-open-multiple-rc-files-outside-a-project"></a>Chcete-li spustit více soubory .rc mimo projekt  
  
1.  Otevřete i samostatné soubory prostředků. Například otevřete Source1.rc a Source2.rc.  
  
    1.  Z **soubor** nabídce zvolte **otevřete**, pak klikněte na tlačítko **soubor**.  
  
    2.  V **otevřít soubor** dialogové okno pole, přejděte na první souboru skriptu prostředků, které chcete otevřít (Source1.rc), zvýrazněte soubor a klikněte na tlačítko **otevřete**.  
  
    3.  Opakujte předchozí krok Otevřete druhý soubor .rc (Source2.rc).  
  
         Soubory .rc jsou nyní otevřené v samostatné dokumenty systému windows.  
  
2.  Když jsou oba soubory .rc otevřené, dlaždici windows, aby se dala zobrazit současně:  
  
    -   Z **okno** nabídce zvolte **nové skupiny vodorovné karta** nebo **nové skupiny svislé karta**.  
  
         \-nebo –  
  
    -   Pravým tlačítkem na jednu soubory .rc a zvolte **nové skupiny vodorovné karta** nebo **nové skupiny svislé karta** z místní nabídky.  
  
> [!NOTE]
>  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  

  
### <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)