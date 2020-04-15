---
title: Třídy jednoduchého datového typu
ms.date: 11/04/2016
f1_keywords:
- vc.classes.data
helpviewer_keywords:
- scalar classes [MFC]
- data classes [MFC]
- simple data type classes [MFC]
ms.assetid: 0d591d68-0a33-49e9-8a6d-90c90de5c16a
ms.openlocfilehash: d4038334e35b734370a437d35519498b96c00770
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365402"
---
# <a name="simple-data-type-classes"></a>Třídy jednoduchého datového typu

Následující třídy zapouzdřují souřadnice výkresu, řetězce znaků a informace o čase a datu, což umožňuje pohodlné použití syntaxe jazyka C++. Tyto objekty jsou široce používány jako parametry pro členské funkce tříd systému Windows v knihovně tříd. Vzhledem `CSize`k `CRect` tomu `CPoint`, , a odpovídají **point**, **SIZE**, a **RECT** struktury, v uvedeném pořadí v sadě Windows SDK, můžete použít objekty těchto tříd jazyka C++ všude tam, kde můžete použít tyto struktury jazyka C. Třídy poskytují užitečné rozhraní prostřednictvím svých členských funkcí. `CStringT`poskytuje velmi flexibilní řetězce dynamických znaků. `CTime`, `COleDateTime` `CTimeSpan`, `COleTimeSpan` a představují hodnoty času a data. Další informace o těchto třídách naleznete v článku [Datum a čas](../atl-mfc-shared/date-and-time.md).

Třídy začínající "`COle`" jsou zapouzdření datových typů poskytovaných OLE. Tyto datové typy lze použít v programech systému Windows bez ohledu na to, zda jsou použity další funkce OLE.

[CStringT – třída](../atl-mfc-shared/reference/cstringt-class.md)<br/>
Obsahuje řetězce znaků.

[CTime](../atl-mfc-shared/reference/ctime-class.md)<br/>
Obsahuje absolutní hodnoty času a data.

[COleDateTime](../atl-mfc-shared/reference/coledatetime-class.md)<br/>
Obálka pro automatizaci OLE typu **DATE**. Představuje hodnoty data a času.

[CTimeSpan](../atl-mfc-shared/reference/ctimespan-class.md)<br/>
Obsahuje relativní hodnoty času a data.

[COleDateTimeSpan](../atl-mfc-shared/reference/coledatetimespan-class.md)<br/>
Obsahuje `COleDateTime` relativní hodnoty, například `COleDateTime` rozdíl mezi dvěma hodnotami.

[CPoint](../atl-mfc-shared/reference/cpoint-class.md)<br/>
Drží souřadnice (x, y) páry.

[Velikost CSize](../atl-mfc-shared/reference/csize-class.md)<br/>
Uchovává vzdálenost, relativní polohy nebo spárované hodnoty.

[CRect](../atl-mfc-shared/reference/crect-class.md)<br/>
Drží souřadnice obdélníkových oblastí.

[Seznam CImageList](../mfc/reference/cimagelist-class.md)<br/>
Poskytuje funkce seznamu bitových obrázků systému Windows. Seznamy obrázků se používají s ovládacími prvky seznamu a ovládacími prvky stromu. Lze je také použít k uložení a archivaci sady bitmap stejné velikosti.

[Varianta COle](../mfc/reference/colevariant-class.md)<br/>
Obálka pro automatizaci OLE typu **VARIANT**. Data v **variantách**s mohou být uložena v mnoha formátech.

[COleCurrency](../mfc/reference/colecurrency-class.md)<br/>
Obálka pro typ automatizace OLE **CURRENCY**, aritmetický typ s pevnou desetinnou čárkou, s 15 číslicemi před desetinnou čárkou a 4 číslicemi za ním.

> [!NOTE]
> `CRect`, `CSize`a `CPoint` jsou použitelné v aplikacích ATL nebo MFC. Kromě toho `CStringT` poskytuje třídu `CString`nezávislou na knihovně MFC. Další informace o sdílených třídách nástrojů naleznete [v tématu Sdílené třídy](../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="see-also"></a>Viz také

[Přehled třídy](../mfc/class-library-overview.md)
