---
title: "Změna symbolu & č. 39; s číselnou hodnotu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.changing.value
dev_langs: C++
helpviewer_keywords:
- numeric values
- symbols, numeric values
- numeric values, changing symbols
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce2c846d844b79a6ff054bb6c209d1f4653a26d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="changing-a-symbol39s-numeric-value"></a>Změna symbolu & č. 39; s číselnou hodnotu
Pro symboly přidružené jediný zdroj, můžete použít [vlastnosti – okno](/visualstudio/ide/reference/properties-window) ke změně hodnoty symbolu. Můžete použít [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md) ke změně hodnoty symbolů prostředek není aktuálně přiřazen. Další informace najdete v tématu [změna nepřiřazených symbolů](../windows/changing-unassigned-symbols.md).  
  
### <a name="to-change-a-symbol-value-assigned-to-a-single-resource-or-object"></a>Chcete-li změnit hodnotu symbol přiřazené k jedinému prostředku nebo k objektu  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), vyberte prostředek.  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  V **vlastnosti** zadejte názvu symbolu následuje znak rovná a celé číslo **ID** pole, například:  
  
    ```  
    IDC_EDITNAME=5100  
    ```  
  
 Nová hodnota je uložen v záhlaví souboru symbol při příštím uložení projektu. V poli ID; zůstává viditelná jenom názvu symbolu rovná se a hodnota se nezobrazují po jejich ověření.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace o ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a prostředky řetězce přiřazení k vlastnosti a [návod: použití prostředků pro lokalizaci pomocí technologie ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Omezení hodnoty symbolu](../windows/symbol-value-restrictions.md)   
 [ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)