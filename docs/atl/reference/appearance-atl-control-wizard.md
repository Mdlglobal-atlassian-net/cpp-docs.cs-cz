---
title: Vzhled, Průvodce ovládacím prvkem ATL
ms.date: 08/31/2018
f1_keywords:
- vc.codewiz.class.atl.control.misc
helpviewer_keywords:
- ATL Control Wizard, appearance
ms.assetid: cc16d7ff-74d7-4c15-9ebd-4b19201ff457
ms.openlocfilehash: e07dc017241848f1a670c17b12c2254de6d1b8e1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492186"
---
# <a name="appearance-atl-control-wizard"></a>Vzhled, Průvodce ovládacím prvkem ATL

Pomocí této stránky průvodce Identifikujte další možnosti prvků uživatele pro ovládací prvek. Tato stránka je k dispozici pro ovládací prvky, které jsou označeny jako **standardní ovládací prvky** v nabídce **typ ovládacího prvku** , na stránce [Průvodce ovládací prvek ATL](../../atl/reference/options-atl-control-wizard.md) .

## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní

- **Zobrazit stav**

   Nastaví vzhled ovládacího prvku v rámci kontejneru.

   - Neprůhledný: Nastaví bit VIEWSTATUS_OPAQUE ve výčtu [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) a vykreslí celý obdélník ovládacího prvku předaný metodě [CComControlBase:: Draw](../../atl/reference/ccomcontrolbase-class.md#ondraw) . Ovládací prvek se zobrazí zcela neprůhledný a žádný z kontejnerů se zobrazí za hranicemi ovládacího prvku.

      Toto nastavení pomáhá kontejneru rychleji nakreslit ovládací prvek. Pokud tato možnost není vybrána, ovládací prvek může obsahovat průhledné části.

      Pouze neprůhledný ovládací prvek může mít plné pozadí.

   - **Plné pozadí**: Nastaví bit VIEWSTATUS_SOLIDBKGND ve výčtu VIEWSTATUS. Pozadí ovládacího prvku se zobrazí jako plná barva bez vzoru.

      Tato možnost je dostupná jenom v případě , že je vybraná taky možnost neprůhledná.

- **Přidat ovládací prvek založený na**

   Nastaví ovládací prvek tak, aby byl založen na typu ovládacího prvku systému Windows přidáním datového členu [CContainedWindow](ccontainedwindowt-class.md) do třídy, která implementuje ovládací prvek. Přidá také mapu zpráv a funkce obslužné rutiny zpráv pro zpracování zpráv systému Windows pro ovládací prvek. Vyberte ze seznamu typ ovládacího prvku systému Windows, který chcete vytvořit (pokud nějaký existuje).

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

- **Různé stavy**

   Nastaví další možnosti vzhledu a chování ovládacího prvku.

   - **Neviditelné v době běhu**: Nastaví ovládací prvek jako neviditelný v době běhu. Neviditelné ovládací prvky můžete použít k provádění operací na pozadí, jako je například Vyvolávání událostí v časových intervalech.

   - **Funguje jako tlačítko**: Nastaví bit OLEMISC_ACTSLIKEBUTTON ve výčtu [OLEMISC](/windows/win32/api/oleidl/ne-oleidl-olemisc) , aby ovládací prvek mohl fungovat jako tlačítko. Pokud kontejner označil klientský web ovládacího prvku jako výchozí tlačítko, výběrem této možnosti umožníte ovládacímu prvku tlačítko Zobrazit sám sebe jako výchozí tlačítko, a to tak, že se sekreslíte přes silný rám. Další informace naleznete v tématu [CComControlBase:: GetAmbientDisplayAsDefault](../../atl/reference/ccomcontrolbase-class.md#getambientdisplayasdefault) .

   - **Funguje jako popisek**: Nastaví bit OLEMISC_ACTSLIKELABEL ve výčtu OLEMISC, aby ovládací prvek mohl nahradit nativní popisek kontejneru. Kontejner určuje, co dělat s tímto příznakem, pokud cokoli.

- **Jiné**

   Nastaví další možnosti chování pro ovládací prvek.

   - **Normalizovaný řadič domény**: Nastaví ovládací prvek tak, aby vytvořil normalizovaný kontext zařízení při volání, aby se nakreslil sám. Tato akce sjednotí vzhled ovládacího prvku, ale jeho vykreslování je méně efektivní.

   - **Pouze okno**: Určuje, že ovládací prvek nemůže být bez okna. Pokud tuto možnost nevyberete, váš ovládací prvek bude automaticky bez oken v kontejnerech podporujících objekty bez oken a automaticky se zobrazí v kontejnerech, které nepodporují objekty bez oken. Výběrem této možnosti vynutíte, aby byl ovládací prvek zobrazen v okně, dokonce i v kontejnerech podporujících objekty bez oken.

   - **Vložená**: Tuto možnost vyberte, pokud chcete ovládací prvek zobrazit v dialogovém okně **Vložit objekt** v aplikacích, jako je Word a Excel. Ovládací prvek může být vložen libovolnou aplikací, která podporuje vložené objekty prostřednictvím tohoto dialogového okna.

## <a name="see-also"></a>Viz také:

[Průvodce ovládacími prvky ATL](../../atl/reference/atl-control-wizard.md)<br/>
[Ukázka SUBEDIT: Základní třída standardní ovládací prvek Windows](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)
