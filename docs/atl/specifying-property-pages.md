---
title: "Určení stránky vlastností (ATL) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ISpecifyPropertyPages
dev_langs:
- C++
helpviewer_keywords:
- ISpecifyPropertyPages method
- property pages, specifying
ms.assetid: ee8678cf-c708-49ab-b0ad-fc2db31f1ac3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8985499c76a7dc65523a5c2904bcb774a4364d41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-property-pages"></a>Určení stránky vlastností
Když vytvoříte ovládací prvek ActiveX, často můžete přidružit stránky vlastností, které umožňuje nastavit vlastnosti vlastního ovládacího prvku. Řídí použití kontejnery **ISpecifyPropertyPages** rozhraní a zjistěte, které stránky vlastností lze použít k nastavení vlastností ovládacího prvku. Musíte pro toto rozhraní implementovat ovládacího prvku.  
  
 K implementaci **ISpecifyPropertyPages** pomocí knihovny ATL, proveďte následující kroky:  
  
1.  Odvození třídě z [ISpecifyPropertyPagesImpl](../atl/reference/ispecifypropertypagesimpl-class.md).  
  
2.  Přidejte záznam pro **ISpecifyPropertyPages** do vaší třídy COM mapy.  
  
3.  Přidat [PROP_PAGE](reference/property-map-macros.md#prop_page) položku pro vlastnost mapy pro každou stránku přidružené vlastního ovládacího prvku.  
  
> [!NOTE]
>  Při generování standardního ovládacího prvku pomocí [Průvodce ovládacím prvkem ATL](../atl/reference/atl-control-wizard.md), pouze je nutné přidat `PROP_PAGE` položek do mapa vlastností. Průvodce generuje kód nezbytné pro další kroky.  
  
 Které jsou v pořádku kontejnery Zobrazí zadanou vlastnost stránky ve stejném pořadí jako `PROP_PAGE` položky v mapě vlastností. Obecně byste měli umístit položkách stránky standardní vlastností po položky pro svoje vlastní stránky v mapě vlastností tak, aby uživatelé nejdřív najdete na stránkách, které jsou specifické pro vaše ovládací prvek.  
  
## <a name="example"></a>Příklad  
 Následující třídy pro kalendář řízení používá **ISpecifyPropertyPages** rozhraní říct kontejnery, které jeho vlastnosti se dá nastavit pomocí vlastní datum stránky a stránky uložených barev.  
  
 [!code-cpp[NVC_ATL_Windowing#72](../atl/codesnippet/cpp/specifying-property-pages_1.h)]  
  
## <a name="see-also"></a>Viz také  
 [Stránky vlastností](../atl/atl-com-property-pages.md)   
 [Ukázka ATLPages](../visual-cpp-samples.md)

