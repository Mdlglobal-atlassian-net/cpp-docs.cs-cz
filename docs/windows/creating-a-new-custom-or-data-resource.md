---
title: "Vytvoření nového vlastního prostředku nebo prostředku dat | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.binary
dev_langs: C++
helpviewer_keywords:
- custom resources [C++]
- data resources [C++]
- resources [Visual Studio], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ff1beb01e08ea78f96b7f161e7f3ffc1110ff63b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="creating-a-new-custom-or-data-resource"></a>Vytvoření nového vlastního prostředku nebo prostředku dat
Můžete vytvořit nový prostředek vlastní nebo dat tím, že prostředek v samostatném souboru pomocí syntaxe souboru skriptu (.rc) normální prostředků a včetně tento soubor pravým tlačítkem myši na projekt v Průzkumníku řešení a kliknutím na **prostředek zahrnuje**  v místní nabídce.  
  
### <a name="to-create-a-new-custom-or-data-resource"></a>Chcete-li vytvořit nový prostředek vlastní nebo data  
  
1. [Vytvořte soubor .rc](../windows/how-to-create-a-resource-script-file.md) obsahující vlastní nebo data prostředků.  
  
     Můžete zadat vlastní data v souboru .rc jako uvozovkách řetězce ukončené hodnotou null, nebo jako celá čísla ve formátu decimal, šestnáctkové nebo osmičková.  
  
2.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na vaše projektového souboru a pak klikněte na tlačítko **prostředek zahrnuje** v místní nabídce.  
  
3.  V **kompilaci direktivy** zadejte **#include** příkaz, který poskytuje název souboru, který obsahuje vaše vlastní prostředek. Příklad:  
  
 ```  
    #include mydata.rc  
 ```  
  
     Zajistěte, aby se syntaxe a zda je typ jsou správné. Obsah **kompilaci direktivy** pole jsou vloženy do souboru skriptu prostředků přesně tak, jak byla zadána.  
  
4.  Klikněte na tlačítko **OK** k zaznamenání změny.  
  
 Jiný způsob, jak vytvořit vlastní prostředek se má importovat externí soubor jako vlastní prostředek. Další informace najdete v tématu [import a export prostředků](../windows/how-to-import-and-export-resources.md).  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](https://msdn.microsoft.com/library/f45fce5x.aspx) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](https://msdn.microsoft.com/library/xbx3z216.aspx). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](https://msdn.microsoft.com/library/h6270d0z.aspx).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Binární Editor](binary-editor.md)

