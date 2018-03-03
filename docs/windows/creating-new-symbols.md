---
title: "Vytváření nových symbolů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.editors.symbol.creating
dev_langs:
- C++
helpviewer_keywords:
- New Symbol dialog box
- symbols, creating
ms.assetid: 35168d31-3af6-4ecd-9362-3707d47b53f3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b01146297307de92d3e79844ac0488b5ff13e29
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="creating-new-symbols"></a>Vytváření nových symbolů
Když zahájíte nový projekt, může být vhodnější zmapování symbol názvy, které je nutné před vytvořením prostředky, ke kterým budou přiřazena.  
  
### <a name="to-create-a-new-symbol-using-the-resource-symbols-dialog-box"></a>Chcete-li vytvořit nový symbol pomocí dialogového okna symboly prostředků  
  
1.  V [symboly prostředků – dialogové okno](../windows/resource-symbols-dialog-box.md), zvolte **nový**.  
  
2.  V **název** zadejte název symbolu.  
  
3.  Přijměte hodnotu přiřazenou symbol.  
  
     -nebo-  
  
     V **hodnotu** zadejte novou hodnotu.  
  
4.  Klikněte na tlačítko **OK** nový symbol přidat do seznamu symbol.  
  
 Pokud zadáte název symbol, který již existuje, zobrazí se okno zprávy s oznámením, že symbol s tímto názvem je již definován. Nelze definovat dvě nebo více symboly se stejným názvem, ale můžete definovat různé symboly se stejnou číselnou hodnotou. Další informace najdete v tématu [omezení názvu symbolu](../windows/symbol-name-restrictions.md) a [omezení hodnoty symbolu](../windows/symbol-value-restrictions.md).  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace o ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a prostředky řetězce přiřazení k vlastnosti a [návod: použití prostředků pro lokalizaci pomocí technologie ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 Požadavky  
  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Zobrazení symbolů prostředků](../windows/viewing-resource-symbols.md)   
 [ID předdefinovaných symbolů](../windows/predefined-symbol-ids.md)