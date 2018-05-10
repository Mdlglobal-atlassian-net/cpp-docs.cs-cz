---
title: Změna symbolu&#39;číselnou hodnotu s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.value
dev_langs:
- C++
helpviewer_keywords:
- numeric values
- symbols, numeric values
- numeric values, changing symbols
ms.assetid: 468e903b-9c07-4251-ae09-3b6cb754cc2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8beacf5195e108d98a0004fe79c2a66cb2b3b610
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="changing-a-symbol39s-numeric-value"></a>Změna symbolu&#39;s číselná hodnota
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