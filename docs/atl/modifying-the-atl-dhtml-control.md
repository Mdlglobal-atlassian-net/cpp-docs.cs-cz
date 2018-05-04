---
title: Úprava ovládací prvek ATL DHTML | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, modifying
- DHTML controls
- DHTML controls, modifying
ms.assetid: c053f35f-8629-4600-9595-721f5956777a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3810236aca4661a6cdcd8399294cdb73e97948fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="modifying-the-atl-dhtml-control"></a>Úprava ovládací prvek DHTML knihovny ATL
Průvodce ovládacím prvkem ATL poskytuje počáteční kód tak můžete sestavit a spustit řízení, a abyste viděli, jak jsou metody napsané v souborech projektu a jak DHTML volá kód C++ ovládacího prvku pomocí metody odesílání. Můžete přidat libovolné metody odesílání rozhraní. Potom můžete volat metody v prostředku HTML.  
  
#### <a name="to-modify-the-atl-dhtml-control"></a>Chcete-li upravit ovládací prvek DHTML knihovny ATL  
  
1.  V zobrazení tříd rozbalte položku řízení projektu.  
  
     Všimněte si, že rozhraní, které končí na "Uživatelského rozhraní" má jednu metodu `OnClick`. Rozhraní, které nemá příponu "Uživatelského rozhraní" nemá žádné metody.  
  
2.  Přidejte metodu s názvem `MethodInvoked` rozhraní, která nemá příponu "Uživatelského rozhraní."  
  
     Tato metoda se zařadí do rozhraní, které se používá v kontejneru ovládacího prvku pro interakci s kontejneru, se používají k interakci s ovládacím prvkem DHTML rozhraní. Tuto metodu můžete vyvolat jenom kontejneru.  
  
3.  V souboru nalezena metoda prázdná a přidejte kód, který zobrazit okno se zprávou, například:  
  
 [!code-cpp[NVC_ATL_COM#5](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_1.cpp)]  
  
4.  Přidat další metodu s názvem `HelloHTML`, pouze v tomto případě, přidejte ji do rozhraní, které končí na "Uživatelského rozhraní." Najít prázdná out `HelloHTML` metoda v sada souborů a přidejte kód, který zobrazit okno se zprávou, například:  
  
 [!code-cpp[NVC_ATL_COM#6](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_2.cpp)]  
  
5.  Přidání třetí metody `GoToURL`, rozhraní, která nemá příponu "Uživatelského rozhraní." Tuto metodu implementovat voláním [IWebBrowser2::Navigate](https://msdn.microsoft.com/library/aa752133.aspx), a to takto:  
  
 [!code-cpp[NVC_ATL_COM#7](../atl/codesnippet/cpp/modifying-the-atl-dhtml-control_3.cpp)]  
  
     Můžete použít **rozhraní IWebBrowser2** metody protože ATL poskytuje ukazatel na tomto rozhraní pro vás v souboru .h.  
  
 V dalším kroku upravte prostředek HTML k vyvolání metody, kterou jste vytvořili. Přidejte tři tlačítka pro volání těchto metod.  
  
#### <a name="to-modify-the-html-resource"></a>Chcete-li upravit prostředek HTML  
  
1.  V Průzkumníku řešení poklikejte na soubor HTM k zobrazení prostředků HTML.  
  
     Zkontrolujte HTML, zejména volání metody externí odesílání Windows. HTML volá projektu `OnClick` metoda a parametry indikovat text ovládacího prvku (`theBody`) a barvu přiřadit ("`red`"). Text následující volání metody, které je štítek, který se zobrazí na tlačítko.  
  
2.  Přidejte další `OnClick` metody pouze změn barvu. Příklad:  
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.OnClick(theBody, "white");'>Refresh</BUTTON>  
 ```  
  
     Tato metoda vytvoří tlačítko s názvem bez přípony **aktualizovat**, že uživatel můžete kliknout na obnovíte na původní, bílé pozadí ovládacího prvku.  
  
3.  Přidejte volání `HelloHTML` metoda jste vytvořili. Příklad:  
  
 ```  
 <br>  
 <br>  
 <BUTTON onclick='window.external.HelloHTML();'>HelloHTML</BUTTON>  
 ```  
  
     Tato metoda vytvoří tlačítko s názvem bez přípony **HelloHTML**, který uživatel mohou kliknout a zobrazit `HelloHTML` okno se zprávou.  
  
 Teď můžete sestavit a [testování upravené ovládací prvek DHTML](../atl/testing-the-modified-atl-dhtml-control.md).  
  
## <a name="see-also"></a>Viz také  
 [Podpora pro ovládací prvek DHTML](../atl/atl-support-for-dhtml-controls.md)

