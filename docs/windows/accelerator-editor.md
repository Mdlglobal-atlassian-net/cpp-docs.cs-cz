---
title: "Editor akcelerátorů | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.accelerator.F1
dev_langs: C++
helpviewer_keywords:
- accelerator tables [C++], editing
- tables [Visual Studio], accelerator key
- accelerator keys
- resource editors, Accelerator editor
- keyboard shortcuts [C++], Accelerator editor
- Accelerator editor
ms.assetid: 013c30b6-5d61-4f1c-acef-8bd15bed7060
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e078dbd3dc8d462ef4bca6e6f1056afb9ce8724c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="accelerator-editor"></a>Editor akcelerátorů
Tabulky akcelerátorů je prostředek systému Windows, který obsahuje seznam klávesy akcelerátoru (také označované jako klávesové zkratky) a identifikátory příkazů, které jsou spojeny s nimi. Program může mít více než jedné tabulky akcelerátorů.  
  
 Za normálních okolností akcelerátorů jsou použity jako klávesové zkratky pro program příkazy, které jsou také k dispozici v nabídce nebo na panelu nástrojů. Můžete však použít tabulky akcelerátorů k definování kombinace kláves pro příkazy, které nemají objekt uživatelského rozhraní s nimi spojených.  
  
 Můžete použít [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925) napojit akcelerátoru klíče příkazy ke kódu.  
  
 Editor akcelerátorů můžete:  
  
-   [Nastavení vlastností akcelerátoru](../windows/setting-accelerator-properties.md)  
  
-   [Přidružení klíče akcelerátoru k položce nabídky](../windows/associating-an-accelerator-key-with-a-menu-item.md)  
  
-   [Úprava tabulek akcelerátorů](../windows/editing-accelerator-tables.md)  
  
-   [Použít předdefinované klávesy akcelerátoru](../windows/predefined-accelerator-keys.md)  
  
    > [!TIP]
    >  Při použití editor akcelerátorů, kliknete pravým tlačítkem na zobrazení místní nabídky často používané příkazy. Příkazy, které jsou k dispozici závisí na ukazatele odkazující na.  
  
    > [!NOTE]
    >  Windows neumožňuje vytvářet tabulky akcelerátorů prázdný. Pokud vytvoříte tabulky akcelerátorů s žádné položky, odstraní se automaticky při ukládání tabulky.  
  
 Informace o přidávání zdrojů do spravovaných projekty, najdete v tématu [prostředků v aplikacích plochy](/dotnet/framework/resources/index) v *rozhraní .NET Framework – příručka vývojáře.* Informace na ručně přidejte soubory prostředků na spravované projekty, přístup k prostředkům, zobrazení statické prostředky a přiřazení k vlastnosti řetězce prostředků najdete v tématu [vytváření souborů prostředků pro aplikace plochy](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Informace o globalizace a lokalizace prostředků do spravovaných aplikací najdete v tématu [Globalizing a lokalizace aplikací .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Požadavky  
 Win32  
  
## <a name="see-also"></a>Viz také  
 [Editory prostředků](../windows/resource-editors.md)

