---
title: "Názvy ovládacích prvků, Průvodce ovládacím prvkem ActiveX knihovny MFC | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.ctl.names
dev_langs: C++
helpviewer_keywords: MFC ActiveX Control Wizard, control names
ms.assetid: 9b8b81d2-36df-48ed-b58a-a771a0e269ee
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f3444ec69ea96ee89ed7a0965f3575fc79e3b9c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="control-names-mfc-activex-control-wizard"></a>Názvy ovládacích prvků, Průvodce ovládacím prvkem ActiveX v prostředí MFC
Zadejte názvy pro ovládací prvek třídy a třídy stránky vlastností, názvy typů a zadejte identifikátory pro vlastní ovládací prvek. S výjimkou produktů **krátký název**, ostatní pole můžete upravovat nezávisle. Pokud změníte text pro **krátký název**, změny se projeví v názvech všechna pole na této stránce. Toto chování je navržená tak, aby bylo možné všechny názvy snadno identifikovat jako vývoje ovládacího prvku.  
  
 **Krátký název**  
 Poskytuje zkrácený název pro ovládací prvek. Ve výchozím nastavení je tento název založen na název projektu, který jste zadali v **nový projekt** dialogové okno. Poskytnutý název určuje názvy tříd, názvy typů a identifikátory typu, pokud nezměníte tato pole samostatně.  
  
 **Název třídy ovládacího prvku**  
 Ve výchozím nastavení, je název třídy ovládacího prvku založený na krátký název, s `C` jako předponu a `Ctrl` jako příponu. Například pokud krátký název je `Price`, je název třídy ovládacího prvku `CPriceCtrl`.  
  
 **Soubor h ovládacího prvku**  
 Ve výchozím nastavení, je název souboru hlaviček založen na krátký název, s `Ctrl` jako příponu a `.h` jako přípona souboru. Například pokud krátký název je `Price`, je název souboru záhlaví `PriceCtrl.h`. Název v tomto poli by měl odpovídat názvu třídy ovládacího prvku.  
  
 **Soubor sada ovládacího prvku**  
 Ve výchozím nastavení, je název souboru hlaviček založen na krátký název, s `Ctrl` jako příponu a `.cpp` jako přípona souboru. Například pokud krátký název je `Price`, je název souboru záhlaví `PriceCtrl.cpp`. Název v tomto poli by měl odpovídat název hlavičky.  
  
 **Název typu ovládacího prvku**  
 Ve výchozím nastavení, název typu ovládacího prvku podle krátký název, za nímž následuje `Control`. Například pokud krátký název je `Price`, je typ názvu třídy ovládacího prvku `Price Control`. Pokud změníte hodnotu v tomto poli, zkontrolujte, zda že název značí dědičnosti.  
  
 **ID typu ovládacího prvku**  
 Nastaví ID typu třídy ovládacího prvku. Ovládací prvek zapíše tento řetězec do registru při jejím přidání do projektu. Aplikace typu kontejner, použijte tento řetězec k vytvoření instance ovládacího prvku.  
  
 Ve výchozím nastavení je ID typu ovládacího prvku založen na název projektu, který jste zadali v **nový projekt** dialogové okno a krátký název. Tento název by měl odpovídat názvu typu.  
  
 Ve výchozím nastavení zobrazí se následující ID typu:  
  
 *ProjectName.ShortName*Ctrl.1  
  
 Pokud změníte krátký název v tomto dialogovém, zobrazí se následující ID typu:  
  
 *ProjectName.NewShortName*Ctrl.1  
  
 **Název třídy PropPage**  
 Ve výchozím nastavení, je název třídy stránky vlastností založen na krátký název, s `C` jako předponu a `PropPage` jako příponu. Například pokud krátký název je `Price`, je název třídy stránky vlastností `CPricePropPage`. Tento název by měl odpovídat názvu třídy ovládacího prvku s příponou `PropPage`.  
  
 **Soubor PropPage h**  
 Ve výchozím nastavení je název souboru záhlaví stránky vlastností založen na krátký název, s `PropPage` jako příponu a `.h` jako přípona souboru. Například pokud krátký název je `Price`, je název souboru záhlaví stránky vlastností `PricePropPage.h`. Tento název by měl odpovídat názvu třídy.  
  
 **PropPage souboru**  
 Ve výchozím nastavení je název souboru implementace stránky vlastností založen na krátký název, s `PropPage` jako příponu a `.cpp` jako přípona souboru. Například pokud krátký název je `Price`, je název souboru záhlaví stránky vlastností `PricePropPage.cpp`. Tento název by měl odpovídat názvu záhlaví souboru.  
  
 **Název typu PropPage**  
 Ve výchozím nastavení, název typu stránky vlastností podle krátký název, za nímž následuje `Property Page`. Například pokud krátký název je `Price`, je název typu stránky vlastností `Price Property Page`. Pokud změníte hodnotu v tomto poli, zkontrolujte, zda že název označuje třída ovládacích prvků.  
  
 **ID typu PropPage**  
 Nastaví ID třídy stránky vlastností. Ovládací prvek zapíše tento řetězec v registru, pokud bylo použito k projektu. Aplikace typu kontejner tento řetězec používá k vytvoření instance ze stránky vlastností ovládacího prvku.  
  
 Ve výchozím nastavení je ID typu stránky vlastností založen na název projektu, který jste zadali v **nový projekt** dialogové okno a krátký název. Tento název by měl odpovídat názvu typu.  
  
 Ve výchozím nastavení zobrazí se následující ID typu stránky vlastností:  
  
 *ProjectName.ShortName*PropPage.1  
  
 Pokud změníte krátký název v tomto dialogovém, zobrazí se následující ID typu stránky vlastností:  
  
 *ProjectName.NewShortName*PropPage.1  
  
## <a name="see-also"></a>Viz také  
 [Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Nastavení aplikace, Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Nastavení ovládacího prvku, Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)   
 [Typy souborů vytvořených pro projekty Visual C++](../../ide/file-types-created-for-visual-cpp-projects.md)

