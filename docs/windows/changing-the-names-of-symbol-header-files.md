---
title: "Změna názvů hlavičkových souborů symbolu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.changing.header
dev_langs: C++
helpviewer_keywords:
- resource files, multiple
- Resource Includes dialog box
- symbol header files, changing names
- symbol header files
- header files, changing names
- names [C++], symbol header files
- symbols, symbol header files
- Resource.h
ms.assetid: b948284a-7899-402e-ab12-9f2c8480ca9d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8ccc7cc8662e33e5999ceafbcd8f029e2675341b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="changing-the-names-of-symbol-header-files"></a>Změna názvů hlavičkových souborů symbolu
Za normálních okolností všechny symbol definice se ukládají do Resource.h. Budete ale muset toto nastavení změnit, patří název souboru, například může pracovat s více než jeden soubor prostředků ve stejném adresáři.  
  
### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Chcete-li změnit název souboru prostředků symbol záhlaví  
  
1.  V [zobrazení prostředků](../windows/resource-view-window.md), klikněte pravým tlačítkem na váš soubor .rc a zvolte [prostředek zahrnuje](../windows/resource-includes-dialog-box.md) z místní nabídky.  
  
    > [!NOTE]
    >  Pokud váš projekt již neobsahuje soubor .rc, najdete v tématu [vytvoření nového souboru skriptu prostředků](../windows/how-to-create-a-resource-script-file.md).  
  
2.  V **Symbol hlavičkový soubor** zadejte nový název pro soubor.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.*  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení symbolů prostředků](../windows/viewing-resource-symbols.md)   
 [ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)