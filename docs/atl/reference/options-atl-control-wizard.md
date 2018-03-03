---
title: "Možnosti, Průvodce ovládacím prvkem ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.codewiz.class.atl.control.options
dev_langs:
- C++
helpviewer_keywords:
- ATL Control Wizard, options
ms.assetid: 4607c51a-992d-433e-9281-919c6f519a3d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 60cc90ca5d5c374c223f9fe350d1a6a7357329ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="options-atl-control-wizard"></a>Možnosti, Průvodce ovládacím prvkem knihovny ATL
Sem vložte "Search" shrnutí výsledků.  
  
 Na této stránce průvodce zadat typ ovládacího prvku, který vytváříte a úroveň podpory rozhraní, které obsahuje.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **– Typ ovládacího prvku**  
 Druh řízení, které chcete vytvořit.  
  
-   **Standardního ovládacího prvku: ovládací prvek ActiveX.**  
  
-   **Složeného ovládacího prvku**: ovládací prvek ActiveX, který může obsahovat (podobně jako do dialogového okna) další ovládací prvky ActiveX nebo ovládací prvky systému Windows. Složeného ovládacího prvku zahrnuje následující položky:  
  
    -   Šablona pro okno, které implementuje složeného ovládacího prvku.  
  
    -   Vlastní prostředek REGISTRU, který automaticky registruje složeného ovládacího prvku při vyvolání.  
  
    -   Třídy C++, která implementuje složeného ovládacího prvku.  
  
    -   Rozhraní COM vystavené složeného ovládacího prvku.  
  
    -   Testovací stránka HTML obsahující složeného ovládacího prvku.  
  
     Ve výchozím nastavení, nastaví tento ovládací prvek [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) na hodnotu true indikující, že se jedná o prvek okna. Mapy jímek implementuje. Další informace najdete v tématu [podpora pro ovládací prvek DHTML](../../atl/atl-support-for-dhtml-controls.md).  
  
-   **Ovládací prvek DHTML**: ovládací prvek DHTML ATL určuje uživatelské rozhraní, pomocí HTML. Třída DHTML uživatelského rozhraní obsahuje COM mapy. Ve výchozím nastavení, nastaví tento ovládací prvek [CComControlBase::m_bWindowOnly](../../atl/reference/ccomcontrolbase-class.md#m_bwindowonly) na hodnotu true indikující, že se jedná o prvek okna.  
  
     Další informace najdete v tématu [identifikace prvky jazyka DHTML řízení projektu](../../atl/identifying-the-elements-of-the-dhtml-control-project.md).  
  
 **Minimální ovládací prvek**  
 Podporuje pouze rozhraní, která jsou nezbytně nutné většina kontejneru. Můžete nastavit **minimální ovládací prvek** pro všechny typy ovládacích prvků: můžete vytvořit minimální standardního ovládacího prvku, minimální složeného ovládacího prvku nebo minimální ovládací prvek DHTML.  
  
 **Agregace**  
 Přidá podporu agregace pro ovládací prvek, který vytváříte. Další informace najdete v tématu [agregace](../../atl/aggregation.md).  
  
-   **Ano**: vytvoření ovládacího prvku, který se dají agregovat.  
  
-   **Ne**: vytvoření ovládacího prvku, který se nedá agregovat.  
  
-   **Pouze**: vytvoření ovládacího prvku, který může být vytvořená pouze prostřednictvím agregace.  
  
 **Model vláken**  
 Určuje, že model vláken používat ovládací prvek.  
  
-   **Jeden**: ovládací prvek se spustí pouze v primárním vlákně COM.  
  
-   **Apartment**: řízení lze vytvořit v jakémkoliv jeden vlákně. Výchozí nastavení  
  
 **Rozhraní**  
 Typ rozhraní, tento ovládací prvek zpřístupní do kontejneru.  
  
-   **Duální**: vytvoří rozhraní, které poskytuje vlastnosti a metody prostřednictvím `IDispatch` a přímo prostřednictvím VTBL.  
  
-   **Vlastní**: vytvoří rozhraní, které zpřístupní metody přímo prostřednictvím VTBL.  
  
     Pokud vyberete **vlastní**, potom můžete zadat, že je ovládací prvek **kompatibilní automatizace**. Pokud vyberete **automatizace kompatibilní**, přidá průvodce [oleautomation](../../windows/oleautomation.md) atribut rozhraní v IDL, a rozhraní může být zařazeno univerzální zařazování vláken v oleaut32.dll. V tématu [zařazování podrobnosti](http://msdn.microsoft.com/library/windows/desktop/ms692621) ve Windows SDK pro další informace.  
  
     Kromě toho pokud vyberete **automatizace kompatibilní**, musí být všechny parametry pro všechny metody v ovládacím prvku **VARIANT** kompatibilní.  
  
 **Podpora**  
 Nastaví další různé podporu pro ovládací prvek.  
  
-   **Body připojení**: povoluje bod připojení pro objekt tím, že třídu objektu, které jsou odvozeny od [IConnectionPointContainerImpl](../../atl/reference/iconnectionpointcontainerimpl-class.md) a umožní tak jeho vystavení zdrojového rozhraní.  
  
-   **Licenci**: přidává podporu pro ovládací prvek pro [licencování](http://msdn.microsoft.com/library/windows/desktop/ms690543). Licencované ovládací prvky může být hostovaný, pouze pokud má klientský počítač správnou licenci.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce ovládacími prvky ATL](../../atl/reference/atl-control-wizard.md)

