---
title: "Vzhled, Průvodce ovládacím prvkem ATL | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.codewiz.class.atl.control.misc
dev_langs: C++
helpviewer_keywords: ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8869df577dfbc541b989beb4b4f3117d7d12feea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="appearance-atl-control-wizard"></a>Vzhled, Průvodce ovládacím prvkem knihovny ATL
Sem vložte "Search" shrnutí výsledků.  
  
 Tato stránka průvodce slouží k určení dalších možností elementu uživatele pro ovládací prvek. Tato stránka je k dispozici pro ovládací prvky identifikovat jako **standardní ovládací prvky** pod **řízení typu** na [možnosti, Průvodce ovládacím prvkem ATL](../../atl/reference/options-atl-control-wizard.md) stránky.  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Zobrazit stav**  
 Nastaví vzhled ovládacího prvku v kontejneru.  
  
-   **Neprůhledné**: Nastaví `VIEWSTATUS_OPAQUE` bit ve [stavu](http://msdn.microsoft.com/library/windows/desktop/ms687201) výčet a nakreslí předaný rámeček celý ovládací prvek [CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) metoda. Ovládací prvek se zobrazí zcela neprůhledný a žádný z kontejneru zobrazí za hranicemi ovládacího prvku.  
  
     Toto nastavení pomůže rychleji vykreslení ovládacího prvku kontejneru. Pokud tuto možnost nevyberete, ovládacího prvku může obsahovat části transparentní.  
  
     Pouze neprůhledný ovládací prvek může mít plnou pozadí.  
  
-   Nastaví `VIEWSTATUS_SOLIDBKGND` bit ve `VIEWSTATUS` výčtu. Pozadí ovládacího prvku se zobrazí jako plnobarevné pomocí žádné vzoru.  
  
     Tato možnost je dostupná pouze tehdy, pokud **neprůhledného** vybrané možnosti.  
  
 **Přidání ovládacího prvku na základě**  
 Nastaví ovládací prvek byl založený na typu ovládacího prvku Windows přidáním [CContainedWindow](ccontainedwindowt-class.md) – datový člen třídy implementující ovládacího prvku. Také přidá mapy zpráv a funkce obslužných rutin zpráv pro zpracování zpráv systému Windows pro ovládací prvek. Vyberte ze seznamu typ ovládacího prvku systému Windows, které chcete vytvořit, pokud existuje.  

  
-   `Button`  
  
-   `ListBox`  
  
-   `SysAnimate32`  
  
-   `SysListView32`  
  
-   `ComboBox`  
  
-   `RichEdit`  
  
-   `SysDateTimePick32`  
  
-   `SysMonthCal32`  
  
-   `ComboBoxEx32`  
  
-   `ScrollBar`  
  
-   `SysHeader32`  
  
-   `SysTabControl32`  
  
-   `Edit`  
  
-   `Static`  
  
-   `SysIPAddress32`  
  
-   `SysTreeView32`  
  
 **Stav – různé**  
 Nastaví další možnosti vzhled a chování pro ovládací prvek.  
  
-   **Při spuštění neviditelná**: Nastaví ovládacího prvku v době běhu byla neviditelná. Neviditelné prvky můžete použít k provádění operací na pozadí, jako je například aktivaci událostí v určitých intervalech.  
  
-   **Pracuje stejně jako tlačítko**: Nastaví `OLEMISC_ACTSLIKEBUTTON` bit ve [OLEMISC](http://msdn.microsoft.com/library/windows/desktop/ms678497) výčtu povolit ovládacího prvku tak, aby fungoval jako tlačítko. Pokud kontejner označila ovládacího prvku lokality klienta jako výchozího tlačítka, tato volba umožňuje zobrazit sám sebe jako výchozího tlačítka podle kreslení samotné se silnějším rámečkem ovládacího prvku tlačítka. V tématu [CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) Další informace.  
  
-   **Chová jako popisek**: Nastaví `OLEMISC_ACTSLIKELABEL` bit ve `OLEMISC` výčtu povolení řízení nahradit nativní jmenovku kontejneru. Kontejner co dělat s Tento příznak určuje, zda nic.  
  
 **Jiné**  
 Nastaví možnosti Další chování pro ovládací prvek.  
  
-   **Normalizované DC**: Nastaví ovládacího prvku k vytvoření kontextu normalizovaný zařízení, když je volána k vykreslení sám sebe. Tato akce standardizuje vzhled ovládacího prvku, ale umožňuje méně efektivní kreslení.  
  
-   **Okno pouze**: Určuje, že vlastní ovládací prvek nemůže být bez oken. Pokud tuto možnost nevyberete, vlastní ovládací prvek je automaticky bez oken v kontejnerech, které podporují objekty bez oken a je automaticky oddílové v kontejnerech, které nepodporují objekty bez oken. Výběrem této možnosti vynutí ovládací prvek se oddílové i v kontejnery, které podporují objekty bez oken.  
  
-   **Vložitelný**: Vyberte tuto možnost, chcete-li ovládací prvek zobrazit v **vložit objekt** dialogové okno aplikací, jako jsou aplikace Word a Excel. Vlastní ovládací prvek může pak vložit jakékoli aplikace, která podporuje vložené objekty prostřednictvím tohoto dialogového okna.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce ovládacím prvkem knihovny ATL](../../atl/reference/atl-control-wizard.md)   
 [SUBEDIT ukázka: Nadřazených tříd ovládacího prvku standardní Windows](http://msdn.microsoft.com/en-us/30e46bdc-ed92-417c-b6b8-359017265a7b)

