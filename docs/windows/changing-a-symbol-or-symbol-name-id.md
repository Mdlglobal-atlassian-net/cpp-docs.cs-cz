---
title: "Změna symbolu nebo názvu symbolu (ID) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.changing
dev_langs: C++
helpviewer_keywords:
- symbol names
- symbols, names
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 300c83a256e2a60ce9f7605093a2016f2d322785
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="changing-a-symbol-or-symbol-name-id"></a>Změna symbolu nebo názvu symbolu (ID)
Když vytvoříte nový prostředek nebo objektu prostředků, přiřadí ji vývojového prostředí symbol výchozí název, například IDD_DIALOG1. Můžete použít [vlastnosti – okno](/visualstudio/ide/reference/properties-window) Chcete-li změnit výchozí název symbolu nebo chcete změnit název žádné symbolu již přidružených k prostředku.  
  
### <a name="to-change-a-resources-symbol-name"></a>Chcete-li změnit název prostředku symbolu  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), vyberte prostředek.  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  V **vlastnosti** okno, zadejte nový název symbolu nebo vyberte ze seznamu existující symboly v **ID** pole.  
  
     Pokud zadáte nový název symbolu, je automaticky přiřazovat hodnota.  
  
 Můžete použít [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md) změnit názvy symbolů prostředek není aktuálně přiřazen. Další informace najdete v tématu [změna nepřiřazených symbolů](../windows/changing-unassigned-symbols.md).  
  

  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Omezení názvu symbolu](../windows/symbol-name-restrictions.md)   
 [ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)