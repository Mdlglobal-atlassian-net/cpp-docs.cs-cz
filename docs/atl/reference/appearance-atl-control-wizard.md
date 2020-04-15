---
title: Vzhled, Průvodce řízením atl
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: 3484fb5d0f919af0dfd18b584e96d4675e2baea8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319399"
---
# <a name="appearance-atl-control-wizard"></a>Vzhled, Průvodce řízením atl

Na této stránce průvodce můžete určit další možnosti uživatelského prvku ovládacího prvku. Tato stránka je k dispozici pro ovládací prvky označené jako **standardní ovládací prvky** v části **Typ ovládacího prvku** na stránce Průvodce [řízením atl.](../../atl/reference/options-atl-control-wizard.md)

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Zobrazit stav**

   Nastaví vzhled ovládacího prvku v kontejneru.

  - **Opaque**: Nastaví VIEWSTATUS_OPAQUE bit ve výčtu [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) a nakreslí celý obdélník ovládacího prvku předaný metodě [CComControlBase::OnDraw.](../../atl/reference/ccomcontrolbase-class.md#ondraw) Ovládací prvek se zobrazí zcela neprůhledné a žádný z kontejneru se zobrazí za hranice ovládacího prvku.

      Toto nastavení pomáhá kontejneru nakreslit ovládací prvek rychleji. Pokud tato volba není vybraná, ovládací prvek může obsahovat průhledné součásti.

      Pouze neprůhledný ovládací prvek může mít plné pozadí.

  - **Plné pozadí**: Nastaví VIEWSTATUS_SOLIDBKGND bit ve výčtu VIEWSTATUS. Pozadí ovládacího prvku se zobrazí jako plná barva bez vzorku.

      Tato volba je dostupná pouze v případě, že je vybraná i volba **Neprůhledné.**

- **Přidat ovládací prvek na základě**

   Nastaví ovládací prvek, který má být založen na typu ovládacího prvku systému Windows přidáním datového člena [CContainedWindow](ccontainedwindowt-class.md) do třídy implementující ovládací prvek. Přidá také mapu zpráv a funkce obslužné rutiny zpráv pro zpracování zpráv systému Windows pro ovládací prvek. V seznamu vyberte typ ovládacího prvku systému Windows, který chcete vytvořit, pokud existuje.

  - **Tlačítko**

  - **ListBox**

  - **SysAnimate32**

  - **SysListView32**

  - **ComboBox**

  - **Richedit**

  - **SysDateTimePick32**

  - **SysMěsícCal32**

  - **SeznamKrabičkaEx32**

  - **ScrollBar**

  - **SysHeader32**

  - **SysTabControl32**

  - **Upravit**

  - **Statické**

  - **SysIPAdresa32**

  - **SysTreeView32**

- **Stav Různé**

   Nastaví další možnosti vzhledu a chování ovládacího prvku.

  - **Neviditelný za běhu**: Nastaví ovládací prvek jako neviditelný za běhu. Neviditelné ovládací prvky můžete použít k provádění operací na pozadí, jako je například spouštění událostí v časových intervalech.

  - **Funguje jako tlačítko**: Nastaví OLEMISC_ACTSLIKEBUTTON bit ve výčtu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) povolit ovládací prvek fungovat jako tlačítko. Pokud kontejner označil klientskou lokalitu ovládacího prvku jako výchozí, výběrtéto možnosti umožní ovládacímu prvku tlačítka zobrazit se jako výchozí tlačítko kreslením s tlustším rámečkem. Další informace naleznete [v tématu CComControlBase::GetAmbientDisplayAsDefault.](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault)

  - **Chová se jako popisek**: Nastaví OLEMISC_ACTSLIKELABEL bit ve výčtu OLEMISC tak, aby ovládací prvek nahradil nativní popisek kontejneru. Kontejner určuje, co dělat s tímto příznakem, pokud vůbec něco.

- **Další**

   Nastaví další možnosti chování ovládacího prvku.

  - **Normalizované řadiče domény**: Nastaví ovládací prvek k vytvoření normalizovaného kontextu zařízení, když je volána k tomu sám. Tato akce standardizuje vzhled ovládacího prvku, ale snižuje efektivitu kreslení.

  - **Pouze okno**: Určuje, že ovládací prvek nemůže být bez oken. Pokud tuto možnost nevyberete, bude ovládací prvek automaticky bez oken v kontejnerech, které podporují objekty bez oken, a automaticky se vytání v kontejnerech, které nepodporují objekty bez oken. Výběr této možnosti vynutí, aby byl ovládací prvek v okně, a to i v kontejnerech, které podporují objekty bez oken.

  - **Vložitelný**: Tuto možnost vyberte, aby se ovládací prvek zobrazil v dialogovém okně **Vložit objekt** u aplikací, jako jsou Word a Excel. Ovládací prvek pak může vložit libovolná aplikace, která podporuje vložené objekty prostřednictvím tohoto dialogového okna.

## <a name="see-also"></a>Viz také

[Průvodce ovládacími prvky ATL](../../atl/reference/atl-control-wizard.md)<br/>
[Ukázka subedit: Superclasses standardní ovládací prvek systému Windows](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
