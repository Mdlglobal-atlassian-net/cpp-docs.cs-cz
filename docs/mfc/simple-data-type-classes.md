---
title: Třídy jednoduchého datového typu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.data
dev_langs:
- C++
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 176ad940e95fbbf18e4ea86800111b483ee32135
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953593"
---
# <a name="simple-data-type-classes"></a>Třídy jednoduchého datového typu
Následující třídy zapouzdření kreslení souřadnice, znakové řetězce a času a informace o datu, což pohodlný pomocí syntaxe jazyka C++. Tyto objekty se často používají jako parametry pro členské funkce tříd Windows v knihovně tříd. Protože `CPoint`, `CSize`, a `CRect` odpovídají **bodu**, **velikost**, a **Rect –** struktur v uvedeném pořadí, ve Windows SDK vždy, když můžete použít tyto struktury jazyka C, můžete použít objekty tyto třídy jazyka C++. Třídy poskytují užitečné rozhraní prostřednictvím svých členských funkcí. `CStringT` poskytuje velmi flexibilní dynamické znakových řetězců. `CTime`, `COleDateTime`, `CTimeSpan`, a `COleTimeSpan` představují hodnoty data a času. Další informace o těchto tříd naleznete v článku [datum a čas](../atl-mfc-shared/date-and-time.md).  
  
 Třídy, které začínají řetězcem "`COle`" jsou encapsulations datových typů poskytované OLE. Tyto datové typy lze použít v aplikacích Windows bez ohledu na to, jestli se používají jiné funkce OLE.  
  
 [CStringT – třída](../atl-mfc-shared/reference/cstringt-class.md)  
 Obsahuje řetězce znaků.  
  
 [CTime –](../atl-mfc-shared/reference/ctime-class.md)  
 Obsahuje absolutní hodnoty data a času.  
  
 [COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)  
 Obálka pro typ automatizace OLE **datum**. Představuje hodnoty data a času.  
  
 [CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)  
 Obsahuje relativní hodnoty data a času.  
  
 [COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)  
 Obsahuje relativní `COleDateTime` hodnoty, například rozdíl mezi dvěma `COleDateTime` hodnoty.  
  
 [CPoint](../atl-mfc-shared/reference/cpoint-class.md)  
 Blokování dvojice souřadnic (x, y).  
  
 [CSize](../atl-mfc-shared/reference/csize-class.md)  
 Obsahuje vzdálenost, relativní umístění nebo spárované hodnoty.  
  
 [CRect](../atl-mfc-shared/reference/crect-class.md)  
 Obsahuje souřadnice obdélníkovou oblastí.  
  
 [CImageList](../mfc/reference/cimagelist-class.md)  
 Poskytuje funkci seznamu obrázků systému Windows. Seznamy obrázků se používají s ovládacími prvky seznam a ovládací prvky stromů. Můžete také používají k ukládání a archivaci sadu bitmap stejnou velikost.  
  
 [COleVariant](../mfc/reference/colevariant-class.md)  
 Obálka pro typ automatizace OLE **VARIANT**. Data v **VARIANT**s mohou být uloženy v mnoha různých formátech.  
  
 [COleCurrency](../mfc/reference/colecurrency-class.md)  
 Obálka pro typ automatizace OLE **MĚNA**, s pevnou desetinnou čárkou aritmetické typu, s 15 číslic od desetinné čárky a po 4 číslice.  
  
> [!NOTE]
>  `CRect`, `CSize`, a `CPoint` lze použít ve ATL nebo MFC aplikací. Kromě toho `CStringT` poskytuje nezávislou MFC `CString`-jako třída. Další informace o sdílené nástroj třídy najdete v tématu [sdílené třídy](../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../mfc/class-library-overview.md)

