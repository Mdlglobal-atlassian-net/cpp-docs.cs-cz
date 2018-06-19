---
title: Změna názvů hlavičkových souborů symbolu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.header
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 953ac59958748bd58fa7e9027c595bf7905e5f27
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864226"
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