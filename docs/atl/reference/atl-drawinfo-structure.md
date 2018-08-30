---
title: Atl_drawinfo – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::ATL_DRAWINFO
- ATL_DRAWINFO
- ATL.ATL_DRAWINFO
dev_langs:
- C++
helpviewer_keywords:
- ATL_DRAWINFO structure
ms.assetid: dd2e2aa8-e8c5-403b-b4df-35c0f6f57fb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 76f21f93bbd8386bbf0b4b63f3cf7c8b34057145
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43210654"
---
# <a name="atldrawinfo-structure"></a>Atl_drawinfo – struktura
Obsahuje informace, které slouží pro vykreslení na různé cíle, například tiskárny, metafile nebo ovládací prvek ActiveX.  
  
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
 `cbSize`  
 Velikost struktury, v bajtech.  
  
 `dwDrawAspect`  
 Určuje, jak má být reprezentován cíl. Reprezentace může zahrnovat obsah, ikony, miniaturu nebo tisk dokumentu. Seznam možných hodnot najdete v tématu [DVASPECT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect) a [DVASPECT2](/windows/desktop/api/ocidl/ne-ocidl-tagdvaspect2).  
  
 `lindex`  
 Část, která je zapotřebí pro operaci příkazu pro vykreslení cíle. Jeho interpretace se liší v závislosti na hodnotě v `dwDrawAspect` člena.  
  
 `ptd`  
 Ukazatel [DVTARGETDEVICE](/windows/desktop/api/objidl/ns-objidl-tagdvtargetdevice) struktura, která povolí optimalizace vykreslování v závislosti na aspekt zadán. Všimněte si, že novější objektů a kontejnerů, které podporují optimalizované vykreslení rozhraní podporují také tohoto člena. Starší objektů a kontejnerů, které nepodporuje optimalizované vykreslení rozhraní vždycky zadejte hodnotu NULL pro tento člen.  
  
 `hicTargetDev`  
 Kontextové informace pro cílové zařízení odkazované `ptd` ze kterého můžete objekt extrahovat metriky zařízení a testovat funkce zařízení. Pokud `ptd` má hodnotu NULL, objekt by měl ignorovat hodnotu v `hicTargetDev` člena.  
  
 `hdcDraw`  
 Kontext zařízení, na kterém chcete-li nakreslit. Pro objekt bez oken `hdcDraw` člen `MM_TEXT` režim mapování s jeho logické souřadnice odpovídající souřadnice klienta obsahujícího okna. Kromě toho by měl být kontext zařízení v takovém stavu, jako je obvykle předávána `WM_PAINT` zprávy.  
  
 `prcBounds`  
 Ukazatel na [RECTL](https://msdn.microsoft.com/library/windows/desktop/dd162907) struktura určující obdélník na `hdcDraw` a ve kterém má být vykreslena objektu. Tento člen Určuje umístění a roztažení objektu. Tento člen by měl mít hodnotu NULL k vykreslení objektu active bez oken na místě. V každé situaci, hodnota NULL není platná hodnota a by měl vést `E_INVALIDARG` kód chyby. Pokud kontejner předá objekt bez oken hodnota jiná než NULL, objekt vykreslovat požadovaný aspekt do kontextu zadané zařízení a obdélník. Kontejner můžete takový požadavek z objektu bez oken pro vykreslení zobrazení druhé, neaktivní objektu nebo vytisknutí objektu.  
  
 `prcWBounds`  
 Pokud `hdcDraw` je kontextu zařízení metasouboru (naleznete v tématu [GetDeviceCaps](/windows/desktop/api/wingdi/nf-wingdi-getdevicecaps) v sadě Windows SDK), tím je ukazatel na `RECTL` struktura určení ohraničující obdélník v podkladové metasouboru. Obdélník struktura obsahuje rozsah okna a okna původu. Tyto hodnoty jsou užitečné pro kreslení metasoubory. Obdélník indikován `prcBounds` je vnořená do to `prcWBounds` obdélník; jsou ve stejném souřadnicového prostoru.  
  
 `bOptimize`  
 Nenulové, pokud je kreslení ovládacího prvku být optimalizován, jinak 0. Pokud je optimalizované pro kreslení stav kontextu zařízení se automaticky obnoví, až budete hotovi vykreslování.  
  
 `bZoomed`  
 Nenulové, pokud cíl obsahuje faktor zvětšování, jinak 0. Na faktor zvětšování je uložen v `ZoomNum`.  
  
 `bRectInHimetric`  
 Nenulovou hodnotu, pokud rozměry `prcBounds` jsou v HIMETRIC, jinak 0.  
  
 `ZoomNum`  
 Šířka a výška rámečku, do kterého je objekt vykreslen. Na faktor zvětšování podél osy x (podíl fyzická velikost objektu na jeho aktuální rozsah) cíle je hodnota `ZoomNum.cx` dělená hodnota `ZoomDen.cx`. Podobným způsobem je dosaženo na faktor zvětšování podél osy y.  
  
 `ZoomDen`  
 Skutečné šířku a výšku cíle.  
  
## <a name="remarks"></a>Poznámky  
 Typická využití této struktury by načítání informací o během vykreslování cílového objektu. Například může načíst hodnoty z atl_drawinfo – uvnitř vaší přetížení [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).  
  
 Tato struktura ukládá relevantní informace, které se použije k vykreslení vzhledu objektu pro cílové zařízení. Poskytnuté informace lze použít v kresby na obrazovce, tiskárnu nebo dokonce metasoubor.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
## <a name="see-also"></a>Viz také  
  [Třídy a struktury](../../atl/reference/atl-classes.md) [IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)





