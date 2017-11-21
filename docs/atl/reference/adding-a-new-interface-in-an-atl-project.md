---
title: "Přidání nového rozhraní v projektu knihovny ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.appwiz.ATL.interface
dev_langs: C++
helpviewer_keywords:
- interfaces, adding to ATL objects
- Implement Interface ATL wizard
- controls [ATL], interfaces
- ATL projects, adding interfaces
ms.assetid: 7d34b023-2c6b-4155-aca3-d47a40968063
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 21aeda51a917bcb48b16ff8f9c2bc505adc18f1d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="adding-a-new-interface-in-an-atl-project"></a>Přidání nového rozhraní v projektu knihovny ATL
Když přidáte do objektu nebo ovládacího prvku rozhraní, můžete vytvořit prázdná funkce pro každou metodu v tomto rozhraní. V objektu nebo ovládací prvek můžete přidat pouze rozhraní, které jsou v existující knihovně typu. Navíc musí implementovat třídu, ve kterém můžete přidat rozhraní [BEGIN_COM_MAP](com-map-macros.md#begin_com_map) makro nebo, pokud je projekt s atributy, musí mít `coclass` atribut.  
  
 Nové rozhraní můžete přidat do vašeho ovládacího prvku v jednom ze dvou způsobů: ručně nebo pomocí průvodců kódem v zobrazení tříd.  
  
### <a name="to-use-code-wizards-in-class-view-to-add-an-interface-to-an-existing-object-or-control"></a>Přidání rozhraní ke stávající objekt nebo ovládací prvek pomocí průvodců kódem v zobrazení tříd  
  
1.  V [zobrazení tříd](http://msdn.microsoft.com/en-us/8d7430a9-3e33-454c-a9e1-a85e3d2db925), klikněte pravým tlačítkem na název třídy ovládacího prvku. Například Úplné řízení nebo složeného ovládacího prvku nebo jiné třídě ovládacího prvku, která implementuje makro BEGIN_COM_MAP ve svém záhlaví souboru.  
  
2.  V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na **implementovat rozhraní**.  
  
3.  Vyberte rozhraní k implementaci v [implementovat rozhraní průvodce](../../ide/implement-interface-wizard.md). Pokud rozhraní neexistuje v jakékoli typelib, pak je třeba přidat ji ručně do souboru IDL.  
  
### <a name="to-add-a-new-interface-manually"></a>Přidat nové rozhraní ručně  
  
1.  Přidejte definici nového rozhraní do souboru IDL.  
  
2.  Odvození objekt nebo ovládací prvek z rozhraní.  
  
3.  Vytvořte novou [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) pro rozhraní nebo, pokud je projekt s atributy, přidejte `coclass` atribut.  
  
4.  Implementace metody na rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce projektem knihovny ATL](../../atl/reference/atl-project-wizard.md)   
 [Typy projektů Visual C++](../../ide/visual-cpp-project-types.md)   
 [Tvorba běžných projektů pomocí průvodců aplikací](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programování s použitím knihovny ATL a běhového kódu jazyka C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Základy ATL COM – objekty](../../atl/fundamentals-of-atl-com-objects.md)   
 [Výchozí konfigurace projektu knihovny ATL](../../atl/reference/default-atl-project-configurations.md)

