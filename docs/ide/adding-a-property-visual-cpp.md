---
title: "Přidání vlastnosti (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interfaces, adding properties
- properties [C++], adding to interfaces
ms.assetid: 37bd4db7-efd3-4faa-87ad-64902ed16a36
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d8cc313fd677d56e00c883bf1c32d8154edcce8b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="adding-a-property-visual-c"></a>Přidání vlastnosti (Visual C++)
Můžete použít [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md) přidání metody do rozhraní ve vašem projektu.  
  
### <a name="to-add-a-property-to-your-object"></a>Přidání vlastnosti do objektu  
  
1.  V [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), klikněte pravým tlačítkem na název rozhraní, do které chcete přidat vlastnost.  
  
    > [!NOTE]
    >  Můžete také přidávat vlastnosti pro odesílající rozhraní, která, pokud je projekt s atributy, jsou vnořené do uzlu knihovny.  
  
2.  V místní nabídce klikněte na **přidat**a potom klikněte na **přidat vlastnost**.  
  
3.  V [Průvodce přidáním vlastnosti](../ide/names-add-property-wizard.md), zadejte informace k vytvoření vlastnosti.  
  
4.  Zadejte nastavení rozhraní definice jazyka IDL () pro vlastnost v [IDL – atributy](../ide/idl-attributes-add-property-wizard.md) stránce průvodce.  
  
5.  Klikněte na tlačítko **Dokončit** přidat vlastnost.  
  
 **Získat** a `Put` metody vlastnosti se zobrazí jako dvě ikony v zobrazení tříd v rámci rozhraní, ve kterých byla definována. Dvakrát klikněte na ikonu se zobrazí deklarace vlastnosti v souboru.  
  
-   Pro rozhraní knihovny ATL **získat** a **Put** přidány do souboru a odkazy na tyto funkce jsou přidány do souboru h.  
  
-   Pro odesílající rozhraní MFC, pokud vyberete **členské proměnné** jako typ implementace metody a proměnné se přidají do třídy, která implementuje ho. Pokud vyberete **metody Get/Set** jako typ implementace dvě metody se přidají do třídy, která implementuje ho.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření rozhraní modelu COM](../ide/creating-a-com-interface-visual-cpp.md)   
 [Úpravy rozhraní modelu COM](../ide/editing-a-com-interface.md)   
 [Komponentový objektový Model](http://msdn.microsoft.com/library/windows/desktop/ms694363)   
 [Ukazatele rozhraní a rozhraní](http://msdn.microsoft.com/library/windows/desktop/ms688484)