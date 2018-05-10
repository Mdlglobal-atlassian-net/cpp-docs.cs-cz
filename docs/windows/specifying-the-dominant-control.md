---
title: Určení dominantního ovládacího prvku | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dominant controls
- Dialog editor, dominant control
- controls [C++], dominant
ms.assetid: 42b523a7-192a-417b-9512-d4af795e002f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 07bf73fdcd69866a811cd37af6ef59aef062c01c
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="specifying-the-dominant-control"></a>Určení dominantního ovládacího prvku
Ovládací prvek je nejdřív dominantního ovládacího prvku.  
  
### <a name="to-specify-the-dominant-control"></a>K určení dominantního ovládacího prvku  
  
1.  Podržte stisknutou **CTRL** klíče a klikněte na ovládací prvek, který chcete použít k ovlivnění velikosti či umístění jiných ovládacích prvků *první*.  
  
     **Poznámka:** za úchyty dominantního ovládacího prvku je plná, zatímco obslužné rutiny podřízených ovládacích prvků dutý. Všechny další změně velikosti nebo zarovnání je založen na dominantního ovládacího prvku.  
  
### <a name="to-change-the-dominant-control"></a>Chcete-li změnit dominantního ovládacího prvku  
  
1.  Zrušte aktuální výběr kliknutím mimo všechny aktuálně vybrané ovládací prvky.  
  
2.  Opakujte předchozí postup, nejprve výběru ovládacího prvku jiný.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Požadavky**  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Výběr více ovládacích prvků](../windows/selecting-multiple-controls.md)   
 [Výběr ovládacích prvků](../windows/selecting-controls.md)   
 [Ovládací prvky v dialogových oknech](../windows/controls-in-dialog-boxes.md)

