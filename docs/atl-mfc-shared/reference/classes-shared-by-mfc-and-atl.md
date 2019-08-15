---
title: Třídy sdílené mezi MFC a ATL
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: e3e4b35721e84e289aed586c4d010a6986dcc61c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491457"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Třídy sdílené mezi MFC a ATL

V následující tabulce jsou uvedeny třídy sdílené mezi knihovnou MFC a knihovnou ATL.

|Třída|Popis|Hlavičkový soubor|
|-----------|-----------------|-----------------|
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Poskytuje metody pro správu hodnot data a času přidružených k souboru.|atltime. h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Poskytuje metody pro správu relativních hodnot data a času přidružených k souboru.|atltime. h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Představuje objekt řetězce s pevnou vyrovnávací pamětí znaků.|CStringT. h|
|[Služby CImage ve](../../atl-mfc-shared/reference/cimage-class.md)|Poskytuje rozšířenou podporu rastrového obrázku, včetně možnosti načítání a ukládání obrázků ve formátech JPEG, GIF, BMP a PNG (Portable Network Graphics).|atlimage. h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Zapouzdřuje datový typ DATE používaný v automatizaci OLE.|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Představuje relativní čas, časové rozmezí.|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Třída podobná struktuře [bodů](/windows/win32/api/windef/ns-windef-point) systému Windows, která také obsahuje členské funkce pro manipulaci `CPoint` s strukturami a. `POINT`|atltypes. h|
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Třída podobná struktuře Windows [Rect](/windows/win32/api/windef/ns-windef-rect) , která také obsahuje členské funkce pro manipulaci s `CRect` objekty a strukturami systému Windows. `RECT`|atltypes. h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|`CSimpleStringT` Představuje objekt.|atlsimpstr.h|
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Třída podobná struktuře [velikosti](/windows/win32/api/windef/ns-windef-size) systému Windows, která implementuje relativní souřadnici nebo polohu.|atltypes. h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Poskytuje automatické čištění prostředků pro `GetBuffer` a `ReleaseBuffer` volání existujícího `CStringT` objektu.|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Představuje data objektu String.|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|`CStringT` Představuje objekt.|CStringT. h (závislá na knihovně MFC) atlstr. h (nezávislá na knihovně MFC)|
|[CTime –](../../atl-mfc-shared/reference/ctime-class.md)|Představuje absolutní datum a čas.|atltime. h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Množství času, které je interně uloženo jako počet sekund v časovém intervalu.|atltime. h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Představuje rozhraní pro `CStringT` správce paměti.|atlsimpstr.h|

## <a name="see-also"></a>Viz také:

[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
