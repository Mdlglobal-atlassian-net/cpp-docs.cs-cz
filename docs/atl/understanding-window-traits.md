---
title: "Vlastnosti – okno ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: window traits
ms.assetid: c90cf850-9e91-49da-9cf3-ad4efb30347d
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fda95e4517d2717a89310a8e49a0c5b337feebcf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="understanding-window-traits"></a>Principy vlastnosti – okno
Třídy vlastností okna zadejte jednoduše standardizace styly využívané pro vytvoření objektu knihovny ATL okno. Okno Vlastnosti, bude přijato jako parametry šablony podle [CWindowImpl](../atl/reference/cwindowimpl-class.md) a dalších tříd oken ATL jako poskytnout výchozí styly oken na úrovni třídy.  
  
 Pokud tvůrce instance okno neposkytuje styly explicitně ve volání [vytvořit](../atl/reference/cwindowimpl-class.md#create), můžete použít třídu vlastnosti a ověřte, že je okno stále vytvořen s správné styly. Dokonce můžete zajistit, že určité styly jsou nastavené pro všechny instance této třídy okno při umožňující další styly nastavení na základě instance.  
  
## <a name="atl-window-traits-templates"></a>ATL – okno Vlastnosti šablony  
 ATL poskytuje dvě šablony okno Vlastnosti, které vám umožní nastavit výchozí styly v době kompilace pomocí jejich parametrů šablony.  
  
|Třída|Popis|  
|-----------|-----------------|  
|[CWinTraits](../atl/reference/cwintraits-class.md)|Tuto šablonu použít, pokud chcete zadat výchozí styly oken, které se použijí jenom v případě, že nejsou zadány žádné jiné styly ve volání **vytvořit**. Styly získanou styly nastavit v době běhu mají přednost doba kompilace.|  
|[CWinTraitsOR](../atl/reference/cwintraitsor-class.md)|Tuto třídu používejte, pokud chcete zadat stylů, které musí být vždycky nastavená pro třídu oken. Styly zadaný v době běhu spolu se styly, nastavte v době kompilace pomocí bitový operátor OR.|  
  
 Kromě těchto šablon ATL poskytuje řadu předdefinovaných specializací `CWinTraits` šablonu pro běžně používané kombinace styly oken. Najdete v článku [CWinTraits](../atl/reference/cwintraits-class.md) referenční dokumentace pro úplné podrobnosti.  
  
## <a name="custom-window-traits"></a>Okno Vlastní vlastnosti  
 V situaci, pravděpodobně není dostatečná že specializing jedna z šablon, které aplikace ATL a je potřeba vytvořit vlastní vlastnosti třídy, stačí vytvořit třídu, která implementuje dvě statické funkce: `GetWndStyle` a **GetWndStyleEx** :  
  
 [!code-cpp[NVC_ATL_Windowing#68](../atl/codesnippet/cpp/understanding-window-traits_1.h)]  
  
 Každá z těchto funkcí v době běhu, který můžete použít k vytvoření nové hodnoty styl předat některé hodnotou style. Pokud třídě vlastnosti okna je používán jako argument šablony třídy oken ATL, se tyto hodnoty styl předaný tyto statické funkce, ať byl předán jako argumenty stylu, které mají [vytvořit](../atl/reference/cwindowimpl-class.md#create).  
  
## <a name="see-also"></a>Viz také  
 [Třídy oken](../atl/atl-window-classes.md)

