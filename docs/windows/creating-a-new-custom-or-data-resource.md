---
title: Vytvoření nového vlastního prostředku nebo prostředku dat | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- custom resources [C++]
- data resources [C++]
- resources [Visual Studio], creating
ms.assetid: 9918bf96-38fa-43a1-a384-572f95d84950
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c82e41544bde9cdd945e23f4ea5884e4e76ae22b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871829"
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
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Binární editor](binary-editor.md)

