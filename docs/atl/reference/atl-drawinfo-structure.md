---
title: ATL_DRAWINFO struktura
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: fb50f49d387e8620f3d5bbb41263738adbd8b437
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748802"
---
# <a name="atl_drawinfo-structure"></a>ATL_DRAWINFO struktura

Obsahuje informace používané pro vykreslování různých cílů, jako je například tiskárna, metasoubor nebo ovládací prvek ActiveX.

## <a name="syntax"></a>Syntaxe

```
struct ATL_DRAWINFO {
    UINT cbSize;
    DWORD dwDrawAspect;
    LONG lindex;
    DVTARGETDEVICE* ptd;
    HDC hicTargetDev;
    HDC hdcDraw;
    LPCRECTL prcBounds;
    LPCRECTL prcWBounds;
    BOOL bOptimize;
    BOOL bZoomed;
    BOOL bRectInHimetric;
    SIZEL ZoomNum;
    SIZEL ZoomDen;
};
```

## <a name="members"></a>Členové

`cbSize`<br/>
Velikost struktury v bajtů.

`dwDrawAspect`<br/>
Určuje, jak má být cíl reprezentován. Reprezentace mohou zahrnovat obsah, ikonu, miniaturu nebo tištěný dokument. Seznam možných hodnot naleznete v tématech [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) a [DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2).

`lindex`<br/>
Část cíle, která je v zájmu pro operaci kreslení. Jeho interpretace se liší v `dwDrawAspect` závislosti na hodnotě v členu.

`ptd`<br/>
Ukazatel na strukturu [DVTARGETDEVICE,](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) která umožňuje optimalizace výkresu v závislosti na zadaném aspektu. Všimněte si, že novější objekty a kontejnery, které podporují optimalizované rozhraní výkresu podporují také tento člen. Starší objekty a kontejnery, které nepodporují optimalizovaná rozhraní výkresu, vždy určují hodnotu NULL pro tohoto člena.

`hicTargetDev`<br/>
Kontext informací pro cílové zařízení, na `ptd` které je objekt určen k extrakci metrik zařízení a testování možností zařízení. Pokud `ptd` je NULL, objekt by měl `hicTargetDev` ignorovat hodnotu v členu.

`hdcDraw`<br/>
Kontext zařízení, na kterém chcete kreslit. Pro objekt bez oken `hdcDraw` je člen `MM_TEXT` v režimu mapování s logickými souřadnicemi odpovídajícími souřadnicím klienta obsahujícího okna. Kromě toho kontext zařízení by měl být ve stejném stavu `WM_PAINT` jako obvykle předávané zprávou.

`prcBounds`<br/>
Ukazatel na [rectl](/windows/win32/api/windef/ns-windef-rectl) strukturu určující `hdcDraw` obdélník na a ve kterém by měl být nakreslenobjekt. Tento člen řídí umístění a roztažení objektu. Tento člen by měl být NULL nakreslit aktivní objekt bez oken na místě. V každé jiné situaci null není právní hodnotu `E_INVALIDARG` a by mělo mít za následek kód chyby. Pokud kontejner předá hodnotu bez hodnoty NULL objektu bez oken, objekt by měl vykreslit požadovaný aspekt do zadaného kontextu zařízení a obdélníku. Kontejner můžete požadovat z objektu bez oken k vykreslení druhé, neaktivní zobrazení objektu nebo k tisku objektu.

`prcWBounds`<br/>
Pokud `hdcDraw` je kontext zařízení metasouboru (viz [GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) v sadě Windows `RECTL` SDK), toto je ukazatel na strukturu určující ohraničující obdélník v podkladovém metasouboru. Obdélníková struktura obsahuje rozsah okna a původ okna. Tyto hodnoty jsou užitečné pro kreslení metasouborů. Obdélník označený je `prcBounds` vnořen `prcWBounds` uvnitř tohoto obdélníku; jsou ve stejném souřadnicovém prostoru.

`bOptimize`<br/>
Nenulová, pokud má být optimalizován výkres ovládacího prvku, jinak 0. Pokud je výkres optimalizován, stav kontextu zařízení se po dokončení vykreslování automaticky obnoví.

`bZoomed`<br/>
Nenulová, pokud má cíl faktor zvětšení, jinak 0. Faktor zvětšení je `ZoomNum`uložen v aplikaci .

`bRectInHimetric`<br/>
Nenulová, pokud `prcBounds` jsou rozměry himetrické, jinak 0.

`ZoomNum`<br/>
Šířka a výška obdélníku, do kterého je objekt vykreslen. Faktor zvětšení podél osy x (podíl přirozené velikosti objektu na jeho aktuální `ZoomNum.cx` množiny) `ZoomDen.cx`cíle je hodnota dělená hodnotou . Faktor zvětšení podél osy y je dosažen podobným způsobem.

`ZoomDen`<br/>
Skutečná šířka a výška cíle.

## <a name="remarks"></a>Poznámky

Typické použití této struktury by načítání informací během vykreslování cílového objektu. Můžete například načíst hodnoty z ATL_DRAWINFO uvnitř přetížení [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).

Tato struktura ukládá relevantní informace používané k vykreslení vzhledu objektu pro cílové zařízení. Poskytnuté informace lze použít při kreslení na obrazovku, tiskárnu nebo dokonce metasoubor.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)<br/>
[IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
