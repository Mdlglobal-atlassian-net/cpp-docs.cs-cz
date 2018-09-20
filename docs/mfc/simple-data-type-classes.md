---
title: Třídy jednoduchého datového typu | Dokumentace Microsoftu
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
ms.openlocfilehash: 4ca6eb22ea596b39f417813ad5072dd1a72e270e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46418772"
---
# <a name="simple-data-type-classes"></a>Třídy jednoduchého datového typu

Následující třídy zapouzdření výkresu souřadnice, řetězce znaků a čas a datum informací, což umožňuje pohodlný pomocí syntaxe jazyka C++. Tyto objekty se běžně používají jako parametry pro členské funkce tříd Windows v knihovně tříd. Protože `CPoint`, `CSize`, a `CRect` odpovídají **bodu**, **velikost**, a **RECT** struktury, v uvedeném pořadí, v sadě Windows SDK bez ohledu na to můžete použít tyto struktury jazyka C, můžete použít objekty z těchto tříd jazyka C++. Třídy poskytují užitečné rozhraní prostřednictvím jejich členské funkce. `CStringT` poskytuje flexibilní dynamické znakové řetězce. `CTime`, `COleDateTime`, `CTimeSpan`, a `COleTimeSpan` představují hodnoty data a času. Další informace o těchto tříd naleznete v článku [datum a čas](../atl-mfc-shared/date-and-time.md).

Třídy, které začínají řetězcem "`COle`" jsou encapsulations datových typů poskytuje OLE. Tyto datové typy lze použít v aplikacích Windows bez ohledu na to, zda se používají jiné funkce OLE.

[CStringT – třída](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Obsahuje znak řetězce.

[CTime –](../atl-mfc-shared/reference/ctime-class.md)<br/>
Obsahuje absolutní hodnoty data a času.

[COleDateTime –](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Obálka pro typ automatizace OLE **datum**. Představuje hodnoty data a času.

[Ctimespan –](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
Obsahuje relativní hodnoty data a času.

[Coledatetimespan –](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
Obsahuje relativní `COleDateTime` hodnoty, jako je rozdíl mezi dvěma `COleDateTime` hodnoty.

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Obsahuje dvojice souřadnic (x, y).

[Csize –](../atl-mfc-shared/reference/csize-class.md)<br/>
Obsahuje vzdálenost, relativní pozice nebo dvojice hodnot.

[Crect –](../atl-mfc-shared/reference/crect-class.md)<br/>
Obsahuje souřadnice obdélníkového oblastí.

[Cimagelist –](../mfc/reference/cimagelist-class.md)<br/>
Poskytuje funkce pro seznam obrázků Windows. Seznamy obrázků se používají s ovládacími prvky seznam a stromu ovládacích prvků. Můžete také používají k ukládání a archivovat sadu rastrové obrázky stejné velikosti.

[COleVariant](../mfc/reference/colevariant-class.md)<br/>
Obálka pro typ automatizace OLE **VARIANT**. Data v **VARIANT**s mohou být uloženy v mnoha formátech.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Obálka pro typ automatizace OLE **měny**, s pevnou desetinnou čárkou aritmetického typu, s 15 číslic od desetinné čárky a po 4 číslice.

> [!NOTE]
>  `CRect`, `CSize`, a `CPoint` lze použít v aplikacích knihovny ATL nebo MFC. Kromě toho `CStringT` poskytuje nezávislou MFC `CString`-, jako jsou třídy. Další informace o sdílených užitkové třídy, naleznete v tématu [sdílené třídy](../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="see-also"></a>Viz také

[Přehled tříd](../mfc/class-library-overview.md)

