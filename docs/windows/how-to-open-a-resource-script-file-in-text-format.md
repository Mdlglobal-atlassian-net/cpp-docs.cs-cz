---
title: "Postupy: otevření souboru skriptu prostředků v textovém formátu | Microsoft Docs"
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
- resource script files, opening in text format
- .rc files, opening in text format
- rc files, opening in text format
ms.assetid: 0bc57527-f53b-40c9-99a9-4dcbc5c9af57
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 19f6a105b255fd5ab4ecb777cc52cccf7a978b7f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-open-a-resource-script-file-in-text-format"></a>Postupy: Otevření souboru skriptu prostředků v textovém formátu
Může nastat situace, kdy budete chtít zobrazit obsah souboru skriptu (.rc) vašeho projektu prostředků bez otevření prostředku, například dialogové okno, v editoru jeho konkrétní prostředků. Můžete například hledat řetězec napříč všechna dialogová okna v souboru prostředků bez nutnosti otevírání každé z nich samostatně.  
  
> [!NOTE]
>  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
 Můžete snadno otevřít soubor prostředků v textovém formátu zobrazovat všechny prostředky, které obsahuje a provádět globální operací podporované [textového editoru](http://msdn.microsoft.com/en-us/508e1f18-99d5-48ad-b5ad-d011b21c6ab1).  
  
> [!NOTE]
>  Editory prostředků nečtou soubory .rc nebo resource.h přímo. Kompilátor prostředků je zkompiluje do .aps soubory, které se spotřebovávají editory prostředků. Tento soubor je krok kompilace a ukládá jenom symbolický data. Jako normální kompilaci proces, informace, které není symbolický (například komentáře) se zahodí během kompilace. Vždy, když soubor .aps získá synchronizována se soubor, znovu vygeneruje soubor (například když uložíte, editor prostředků přepíše .rc soubor a soubor resource.h). Všechny změny prostředků sami zůstanou zahrnuté v souboru .rc, ale komentáře vždy budou ztraceny po .rc soubor se přepíše. Informace o tom, jak zachovat komentáře najdete v tématu [včetně prostředků v době kompilace](../windows/how-to-include-resources-at-compile-time.md).  
  
### <a name="to-open-a-resource-script-file-as-text"></a>Otevření souboru skriptu prostředků jako text  
  
1.  Z **soubor** nabídce zvolte **otevřete**, pak klikněte na tlačítko **souboru.**  
  
2.  V **otevření souboru** dialogové okno pole, přejděte do souboru skriptu prostředků, které chcete zobrazit v textovém formátu.  
  
3.  Zvýrazněte soubor a pak klikněte na šipku rozevíracího seznamu na **otevřete** tlačítko (nachází se na pravé straně tlačítko).  
  
4.  Zvolte **otevřít v** z rozevírací nabídky.  
  
5.  V **otevřít v** dialogové okno, klikněte na tlačítko **zdrojový kód (Text) Editor**.  
  
6.  Z **otevřít jako** rozevíracího seznamu vyberte **Text**.  
  
     Prostředek se otevře v editoru zdrojového kódu.  
  
 \-nebo –  
  
1.  V **Průzkumníku**, klikněte pravým tlačítkem na soubor.  
  
2.  V místní nabídce vyberte příkaz **otevřít v programu...** , pak vyberte **zdrojový kód (Text) Editor**.  
  

  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Soubory prostředků](../windows/resource-files-visual-studio.md)   
 [Editory prostředků](../windows/resource-editors.md)