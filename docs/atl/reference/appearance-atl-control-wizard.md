---
title: Vzhled, Průvodce ovládacím prvkem ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: 4d3b0519951636fad4175dc35261ba35b3694ffa
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280404"
---
# <a name="appearance-atl-control-wizard"></a>Vzhled, Průvodce ovládacím prvkem ATL

Na této stránce průvodce k identifikaci další uživatelské možnosti elementu ovládacího prvku. Tato stránka je k dispozici pro ovládací prvky, které jsou identifikovány jako **standardní ovládací prvky** pod **ovládací prvek typu** na [možnosti, Průvodce ovládacím prvkem ATL](../../atl/reference/options-atl-control-wizard.md) stránky.

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Zobrazit stav**

   Nastaví vzhled ovládacího prvku v rámci kontejneru.

   - **Opaque**: Nastaví bit v VIEWSTATUS_OPAQUE [které](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus) výčet a nakreslí obdélník celý ovládací prvek předán [CComControlBase::OnDraw](../../atl/reference/ccomcontrolbase-class.md#ondraw) metody. Ovládací prvek zobrazí se stane zcela neprůhledný, a žádný z kontejneru za hranice ovládacího prvku.

      Toto nastavení pomůže rychleji nakreslete ovládací prvek kontejneru. Pokud tato možnost není vybraná, může obsahovat ovládací prvek průhledné části.

      Pouze neprůhledné ovládací prvek může mít jednobarevné pozadí.

   - **Plné pozadí**: Nastaví VIEWSTATUS_SOLIDBKGND bit ve které výčtu. Pozadí ovládacího prvku se zobrazí jako plná barva žádné vzorem.

      Tato možnost je dostupná pouze tehdy, pokud **neprůhledné** je vybraná možnost.

- **Přidání ovládacího prvku na základě**

   Nastaví ovládací prvek byl založený na typu ovládacího prvku Windows tak, že přidáte [CContainedWindow](ccontainedwindowt-class.md) datový člen třídy implementující ovládací prvek. Také přidá mapy zpráv a funkce obslužné rutiny zpráv pro zpracování zpráv Windows pro ovládací prvek. Zvolte ze seznamu typ ovládacího prvku Windows, který chcete vytvořit, pokud existuje.

   - **Tlačítko**

   - **ListBox**

   - **SysAnimate32**

   - **SysListView32**

   - **ComboBox**

   - **RichEdit**

   - **SysDateTimePick32**

   - **SysMonthCal32**

   - **ComboBoxEx32**

   - **ScrollBar**

   - **SysHeader32**

   - **SysTabControl32**

   - **Upravit**

   - **Static**

   - **SysIPAddress32**

   - **SysTreeView32**

- **Stav různé**

   Nastaví další možnosti vzhledu a chování ovládacího prvku.

   - **Neviditelné při spuštění**: Nastaví ovládací prvek v době běhu byla neviditelná. Neviditelné prvky můžete použít k provádění operací na pozadí, jako je například vyvolává události v časových intervalech.

   - **Slouží jako tlačítko**: Nastaví bit v OLEMISC_ACTSLIKEBUTTON [OLEMISC](/windows/desktop/api/oleidl/ne-oleidl-tagolemisc) výčet umožňuje ovládat tak, aby fungoval jako tlačítko. Pokud kontejneru označil lokality klienta ovládacího prvku jako výchozího tlačítka, výběr této možnosti umožní zobrazení samotného jako výchozího tlačítka nakreslením samotného objektu Frame silnější ovládacího prvku tlačítka. Zobrazit [CComControlBase::GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) Další informace.

   - **Funguje jako popisek**: Nastaví OLEMISC_ACTSLIKELABEL bit ve výčtu OLEMISC umožňuje ovládat nahradit nativní popisku kontejneru. Kontejner co dělat s Tento příznak určuje, zda cokoli.

- **Jiné**

   Nastaví další chování možnosti pro ovládací prvek.

   - **Normalizované DC**: Nastaví ovládacího prvku k vytvoření normalizovaný kontext zařízení, když je volána k nakreslení sebe sama. Tím se standardizuje vzhled ovládacího prvku, ale je méně efektivní kreslení.

   - **Okno pouze**: Určuje, zda ovládací prvek nemůže být bez oken. Pokud tuto možnost nevyberete, je váš ovládací prvek automaticky bez oken v kontejnerech, které podporují bez oken objekty a je automaticky oddílové v kontejnerech, které nepodporují objekty bez oken. Výběrem této možnosti způsobí, že ovládací prvek se zobrazením, dokonce i v kontejnerech, které podporují objekty bez oken.

   - **Vložitelný**: Vyberte tuto možnost, chcete-li ovládací prvek se zobrazí v **vložit objekt** dialogového okna aplikace, jako je Word a Excel. Ovládací prvek pak může být vložen aplikací, která podporuje vložené objekty prostřednictvím tohoto dialogového okna.

## <a name="see-also"></a>Viz také:

[Průvodce ovládacími prvky ATL](../../atl/reference/atl-control-wizard.md)<br/>
[SUBEDIT vzorku: Nadřazené třídy ovládacího prvku standardní Windows](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
