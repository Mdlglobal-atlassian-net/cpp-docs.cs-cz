---
title: Třídy sdílené mezi MFC a ATL
ms.date: 11/04/2016
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
ms.openlocfilehash: 5376a87aac2b82615cd48f80e0e95208b8132bf0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62235143"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Třídy sdílené mezi MFC a ATL

V následující tabulce jsou uvedeny třídy sdílené mezi MFC a ATL.

|Třída|Popis|Hlavičkový soubor|
|-----------|-----------------|-----------------|
|[Cfiletime –](../../atl-mfc-shared/reference/cfiletime-class.md)|Poskytuje metody pro správu přidružené k souboru hodnoty data a času.|atltime.h|
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Poskytuje metody pro správu relativní hodnoty data a času přidružených k souboru.|atltime.h|
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Představuje objekt řetězce s pevnou znak vyrovnávací paměti.|cstringt.h|
|[Cimage –](../../atl-mfc-shared/reference/cimage-class.md)|poskytuje podporu rozšířenou rastrový obrázek, včetně možnosti k načtení a uložení Image ve formátu JPEG, GIF, BMP a Portable Network Graphics (PNG).|atlimage.h|
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Zapouzdřuje datový typ datum používaný v automatizace OLE.|atlcomtime.h|
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Představuje relativní časové rozpětí času.|atlcomtime.h|
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Podobně jako Windows třída [bodu](/windows/desktop/api/windef/ns-windef-tagpoint) struktura, která zahrnuje také členské funkce pro manipulaci s `CPoint` a `POINT` struktury.|atltypes.h|
|[Crect –](../../atl-mfc-shared/reference/crect-class.md)|Třída podobně jako Windows [RECT](/windows/desktop/api/windef/ns-windef-tagrect) struktura, která zahrnuje také členské funkce pro manipulaci s `CRect` objekty a Windows `RECT` struktury.|atltypes.h|
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|Představuje `CSimpleStringT` objektu.|atlsimpstr.h|
|[Csize –](../../atl-mfc-shared/reference/csize-class.md)|Podobně jako Windows třída [velikost](/windows/desktop/api/windef/ns-windef-tagsize) struktura, která implementuje relativní souřadnice nebo pozici.|atltypes.h|
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Nabízí automatické prostředků vyčištění `GetBuffer` a `ReleaseBuffer` volá existující `CStringT` objektu.|atlsimpstr.h|
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Představuje datový objekt řetězce.|atlsimpstr.h|
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|Představuje `CStringT` objektu.|atlstr.h cstringt.h (MFC závislé) (MFC nezávislé)|
|[CTime –](../../atl-mfc-shared/reference/ctime-class.md)|Představuje datum a absolutní čas.|atltime.h|
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Časový úsek, který interně uložená jako počet sekund v časové období.|atltime.h|
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Představuje rozhraní pro `CStringT` správce paměti.|atlsimpstr.h|

## <a name="see-also"></a>Viz také:

[Sdílené třídy ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
