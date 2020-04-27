---
title: Struktura ATL_DRAWINFO
ms.date: 11/04/2016
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
ms.openlocfilehash: 00d93b3dd8b060a21b6ff4083bb9880d8d836a19
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168615"
---
# <a name="atl_drawinfo-structure"></a>Struktura ATL_DRAWINFO

Obsahuje informace používané pro vykreslování do různých cílů, jako je například tiskárna, metasoubor nebo ovládací prvek ActiveX.

## <a name="syntax"></a>Syntaxe

```cpp
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
Velikost struktury (v bajtech).

`dwDrawAspect`<br/>
Určuje, jak má být cíl reprezentován. Reprezentace mohou zahrnovat obsah, ikonu, miniaturu nebo vytištěný dokument. Seznam možných hodnot naleznete v tématu [DVASPECT](/windows/win32/api/wtypes/ne-wtypes-dvaspect) a [DVASPECT2](/windows/win32/api/ocidl/ne-ocidl-dvaspect2).

`lindex`<br/>
Část cíle, která je pro operaci Draw zajímavá. Jeho interpretace se liší v závislosti na hodnotě v `dwDrawAspect` členu.

`ptd`<br/>
Ukazatel na strukturu [DVTARGETDEVICE](/windows/win32/api/objidl/ns-objidl-dvtargetdevice) , která umožňuje optimalizace kreslení v závislosti na určeném aspektu. Všimněte si, že novější objekty a kontejnery, které podporují optimalizovaná kreslicí rozhraní, podporují i tento člen. Starší objekty a kontejnery, které nepodporují optimalizovaná kreslicí rozhraní, vždy pro tento člen zadáte hodnotu NULL.

`hicTargetDev`<br/>
Informační kontext pro cílové zařízení odkazoval na, `ptd` ze kterého může objekt extrahovat metriky zařízení a testovat schopnosti zařízení. Pokud `ptd` je null, objekt by měl ignorovat hodnotu v `hicTargetDev` členu.

`hdcDraw`<br/>
Kontext zařízení, na kterém se má kreslit. V případě objektu bez oken je `hdcDraw` člen v režimu `MM_TEXT` mapování s jeho logickými souřadnicemi, které odpovídají souřadnicím klienta v nadřazeném okně. Kromě toho by měl být kontext zařízení ve stejném stavu jako ten, který obvykle předává `WM_PAINT` zpráva.

`prcBounds`<br/>
Ukazatel na strukturu [Rect](/windows/win32/api/windef/ns-windef-rectl) určující obdélník `hdcDraw` , ve kterém má být objekt vykreslen. Tento člen ovládá umístění a roztažení objektu. Tento člen by měl mít hodnotu NULL, aby se nakreslil místní aktivní objekt bez okna. V každé jiné situaci hodnota NULL není platnou hodnotou a měla by mít za následek kód `E_INVALIDARG` chyby. Pokud kontejner předá hodnotu, která není NULL, do objektu bez oken, objekt by měl vykreslovat požadovaný aspekt do určeného kontextu zařízení a obdélníku. Kontejner může vyžádat to z objektu bez okna pro vykreslení druhého, neaktivního zobrazení objektu nebo pro tisk objektu.

`prcWBounds`<br/>
Pokud `hdcDraw` je kontext zařízení metasouboru (viz [GetDeviceCaps](/windows/win32/api/wingdi/nf-wingdi-getdevicecaps) v Windows SDK), jedná se o ukazatel na `RECTL` strukturu, která určuje ohraničující obdélník v podkladovém metasouboru. Struktura obdélníku obsahuje rozsah okna a počátek okna. Tyto hodnoty jsou užitečné pro kreslení metasouborů. Obdélník, který je `prcBounds` označen jako, je `prcWBounds` vnořen do tohoto obdélníku; jsou ve stejném souřadnicovém prostoru.

`bOptimize`<br/>
Nenulové, pokud je vykreslování ovládacího prvku optimalizováno, jinak 0. Pokud je výkres optimalizovaný, stav kontextu zařízení se po dokončení vykreslování automaticky obnoví.

`bZoomed`<br/>
Nenulová, pokud má cíl faktor přiblížení, jinak 0. Faktor přiblížení je uložen v `ZoomNum`.

`bRectInHimetric`<br/>
Nenulové, pokud `prcBounds` jsou dimenze v HIMETRIC, jinak 0.

`ZoomNum`<br/>
Šířka a výška obdélníku, do kterého je objekt vykreslen. Faktor přiblížení podél osy x (podíl přirozené velikosti objektu na jeho aktuální rozsah) cíle je hodnota `ZoomNum.cx` dělená hodnotou. `ZoomDen.cx` Faktor přiblížení podél osy y se dosahuje podobným způsobem.

`ZoomDen`<br/>
Skutečná šířka a výška cíle

## <a name="remarks"></a>Poznámky

Typické použití této struktury by bylo načítání informací během vykreslování cílového objektu. Můžete například načíst hodnoty z ATL_DRAWINFO v rámci přetížení [CComControlBase:: OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).

Tato struktura ukládá relevantní informace, které slouží k vykreslování vzhledu objektu pro cílové zařízení. Poskytnuté informace se dají použít při kreslení na obrazovku, na tiskárnu nebo dokonce na metasoubor.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

## <a name="see-also"></a>Viz také

[Třídy a struktury](../../atl/reference/atl-classes.md)<br/>
[IViewObject: nezpracované:D](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw)<br/>
[CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)
