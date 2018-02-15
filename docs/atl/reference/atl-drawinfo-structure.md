---
title: Struktura ATL_DRAWINFO | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f7a10932fd43e89af6d98d3d931d43810c710000
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="atldrawinfo-structure"></a>ATL_DRAWINFO Structure
Obsahuje informace, které slouží pro vykreslení na různé cíle, jako jsou tiskárny, metafile nebo ovládací prvek ActiveX.  
  
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
 Velikost struktury v bajtech.  
  
 **dwDrawAspect**  
 Určuje, jak má být reprezentován cíl. Reprezentace může zahrnovat obsah, ikonu, miniaturu nebo tištěných dokumentu. Seznam možných hodnot najdete v tématu [DVASPECT](http://msdn.microsoft.com/library/windows/desktop/ms690318) a [DVASPECT2](http://msdn.microsoft.com/library/windows/desktop/ms688644).  
  
 **lindex**  
 Část cíl, který je určen pro kreslení operaci. Jeho interpretace se liší v závislosti na hodnotě v **dwDrawAspect** člen.  
  
 **ptd**  
 Ukazatel na [DVTARGETDEVICE](http://msdn.microsoft.com/library/windows/desktop/ms686613) struktura, která umožňuje kreslení optimalizace v závislosti na aspekt zadán. Všimněte si, že novější objektů a kontejnerů, které podporují optimalizované kreslení rozhraní, podporují tento člen také. Starší objektů a kontejnerů, které nepodporují optimalizované kreslení rozhraní vždycky zadat **NULL** pro tento člen.  
  
 **hicTargetDev**  
 Kontextové informace pro cílové zařízení na kterou odkazuje **ptd** ze kterého můžete objekt extrahovat zařízení metriky a testování funkcí v zařízení. Pokud **ptd** je **NULL**, objekt by měl ignorovat hodnotu v **hicTargetDev** člen.  
  
 **hdcDraw**  
 Kontext zařízení, ve kterém k vykreslení. Pro objekt bez oken **hdcDraw** člen přítomen v `MM_TEXT` mapování režimu s jeho logické souřadnice odpovídající souřadnice klienta obsahující okno. Kromě toho kontextu zařízení musí být v takovém stavu, jako je obvykle předaná `WM_PAINT` zprávy.  
  
 **prcBounds**  
 Ukazatel na [RECTL](http://msdn.microsoft.com/library/windows/desktop/dd162907) struktura zadání rámeček na **hdcDraw** a které mají být vykresleny objektu. Tento člen Určuje umístění a roztažení objektu. Tento člen by měl být **NULL** k vykreslení objekt aktivní bez oken na místě. V každé situaci **NULL** není platnou hodnotou a by měla vést `E_INVALIDARG` kód chyby. V případě úspěšného kontejneru jinou hodnotu než**NULL** hodnotu na objekt bez oken objekt vykreslovat požadovaný aspekt do kontextu zadané zařízení a rámečku. Kontejner můžete žádost z objektu bez oken pro vykreslení zobrazení druhou, neaktivní objektu nebo tisknout objektu.  
  
 **prcWBounds**  
 Pokud **hdcDraw** je kontextu zařízení metafile (najdete v části [GetDeviceCaps](http://msdn.microsoft.com/library/windows/desktop/dd144877) ve Windows SDK), to je ukazatel na **RECTL** struktura zadání ohraničující obdélník v základní metafile. Struktura obdélníku obsahuje okno rozsah a okno původu. Tyto hodnoty jsou užitečné pro kreslení metasoubory. Rámeček indikován **prcBounds** je vnořit to **prcWBounds** obdélníku; jsou ve stejné souřadnicového prostoru.  
  
 **bOptimize**  
 Nenulové hodnoty, pokud je vykreslování ovládacího prvku jako optimalizovaná, jinak hodnota 0. Pokud je optimalizována kreslení, se automaticky obnoví stav kontextu zařízení po dokončení vykreslování.  
  
 **bZoomed**  
 Nenulové hodnoty, pokud má cílový faktor zvětšování, jinak hodnota 0. Na faktor zvětšování je uložen v **ZoomNum**.  
  
 **bRectInHimetric**  
 Pokud nenulové hodnoty rozměry **prcBounds** v **HIMETRIC**, jinak hodnota 0.  
  
 **ZoomNum**  
 Šířka a výška rámečku, do kterého je objekt vykreslen. Na faktor zvětšování podél osy x (podíl přirozené velikost objektu na aktuální velikost) cíle je hodnota **ZoomNum.cx** dělený hodnotu **ZoomDen.cx**. Podobně se dosahuje na faktor zvětšování podél osy y.  
  
 **ZoomDen**  
 Skutečná šířka a výška cíle.  
  
## <a name="remarks"></a>Poznámky  
 Typická využití této struktury by načtení informace během vykreslování cílového objektu. Například je může načíst hodnoty z `ATL_DRAWINFO` uvnitř vaší přetížení [CComControlBase::OnDrawAdvanced](ccomcontrolbase-class.md#ondrawadvanced).  
  
 Tato struktura ukládá důležité informace, které se použije k vykreslení vzhled objektu pro cílové zařízení. Poskytnuté informace lze použít v kreslení na obrazovce, tiskárnu nebo i metafile.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlctl.h  
  
## <a name="see-also"></a>Viz také  
 [Struktury](../../atl/reference/atl-structures.md)   
 [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)   
 [CComControlBase::OnDrawAdvanced](../../atl/reference/ccomcontrolbase-class.md#ondrawadvanced)





