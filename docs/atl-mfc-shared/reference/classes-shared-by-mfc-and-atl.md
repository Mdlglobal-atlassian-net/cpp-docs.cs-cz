---
title: Třídy, které jsou sdíleny MFC a knihovna ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- shared classes, classes
ms.assetid: ca8b4b6b-744d-430b-b31f-d5b2f17bf210
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ea651297503210a78f3ee189c57e37bcc3e99c6a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356971"
---
# <a name="classes-shared-by-mfc-and-atl"></a>Třídy sdílí MFC a knihovny ATL
Následující tabulka uvádí třídy sdílena mezi MFC a ATL.  
  
|Třída|Popis|Soubor hlaviček|  
|-----------|-----------------|-----------------|  
|[CFileTime](../../atl-mfc-shared/reference/cfiletime-class.md)|Poskytuje metody pro správu hodnoty data a času, které jsou přidružené k souboru.|atltime.h|  
|[CFileTimeSpan](../../atl-mfc-shared/reference/cfiletimespan-class.md)|Poskytuje metody pro správu relativní datum a čas hodnoty přidružené k souboru.|atltime.h|  
|[CFixedStringT](../../atl-mfc-shared/reference/cfixedstringt-class.md)|Představuje objekt řetězec s pevnou znak vyrovnávací paměti.|cstringt.h|  
|[CImage](../../atl-mfc-shared/reference/cimage-class.md)|Poskytuje podporu rozšířené rastrového obrázku, včetně možnosti spouštění a ukládání bitových kopií ve formátech JPEG, GIF, BMP a Portable Network Graphics (PNG).|atlimage.h|  
|[COleDateTime](../../atl-mfc-shared/reference/coledatetime-class.md)|Zapouzdří **datum** datový typ používaný v automatizace OLE.|atlcomtime.h|  
|[COleDateTimeSpan](../../atl-mfc-shared/reference/coledatetimespan-class.md)|Představuje relativní čas, časové období.|atlcomtime.h|  
|[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)|Třídu podobná Windows [bodu](../../mfc/reference/point-structure1.md) struktura, která zahrnuje i členské funkce k manipulaci s `CPoint` a **bodu** struktury.|atltypes.h|  
|[CRect](../../atl-mfc-shared/reference/crect-class.md)|Třídu podobná Windows [Rect –](../../mfc/reference/rect-structure1.md) struktura, která zahrnuje i členské funkce k manipulaci s `CRect` objekty a Windows `RECT` struktury.|atltypes.h|  
|[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)|Představuje `CSimpleStringT` objektu.|atlsimpstr.h|  
|[CSize](../../atl-mfc-shared/reference/csize-class.md)|Třída, která je podobná strukturu Windows velikost, která implementuje relativní souřadnice nebo pozice.|atltypes.h|  
|[CStrBufT](../../atl-mfc-shared/reference/cstrbuft-class.md)|Poskytuje vyčištění automatické prostředků pro `GetBuffer` a `ReleaseBuffer` volání na existující `CStringT` objektu.|atlsimpstr.h|  
|[CStringData](../../atl-mfc-shared/reference/cstringdata-class.md)|Představuje data objektu řetězce.|atlsimpstr.h|  
|[CStringT](../../atl-mfc-shared/reference/cstringt-class.md)|Představuje `CStringT` objektu.|atlstr.h cstringt.h (MFC závislé) (MFC nezávislé)|  
|[CTime –](../../atl-mfc-shared/reference/ctime-class.md)|Představuje absolutní data a času.|atltime.h|  
|[CTimeSpan](../../atl-mfc-shared/reference/ctimespan-class.md)|Určenou dobu, která je uložena interně jako počet sekund v časové rozpětí.|atltime.h|  
|[IAtlStringMgr](../../atl-mfc-shared/reference/iatlstringmgr-class.md)|Představuje rozhraní pro `CStringT` správce paměti.|atlsimpstr.h|  
  
## <a name="see-also"></a>Viz také  
 [ATL a MFC sdílené třídy](../../atl-mfc-shared/atl-mfc-shared-classes.md)


