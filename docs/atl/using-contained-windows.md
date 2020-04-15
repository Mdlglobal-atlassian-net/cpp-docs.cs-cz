---
title: Použití obsaženého systému Windows
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 5da765eae28d411c98e79af5b9173f48ea66ef8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329310"
---
# <a name="using-contained-windows"></a>Použití obsaženého systému Windows

ATL implementuje obsahovala okna s [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Obsažené okno představuje okno, které deleguje své zprávy na objekt kontejneru namísto jejich zpracování ve vlastní třídě.

> [!NOTE]
> Není nutné odvodit `CContainedWindowT` třídu z, aby bylo možné použít obsažená okna.

S obsaženými okny můžete buď nadtřídit existující třídu systému Windows, nebo podtřídu existujícího okna. Chcete-li vytvořit okno, které přeřazuje existující třídu systému Windows, nejprve zadejte existující název třídy v konstruktoru objektu. `CContainedWindowT` Pak `CContainedWindowT::Create`volejte . Chcete-li podtřídit existující okno, nemusíte zadávat název třídy systému Windows (předat null konstruktoru). Jednoduše zavolejte metodu `CContainedWindowT::SubclassWindow` s popisovačem do okna, které je podtřídou.

Obvykle používáte obsažené okna jako datové členy třídy kontejneru. Kontejner nemusí být okno; však musí být odvozen z [CMessageMap](../atl/reference/cmessagemap-class.md).

Obsažené okno můžete použít alternativní mapy zpráv ke zpracování jeho zprávy. Pokud máte více než jedno obsažené okno, měli byste deklarovat několik alternativních map zpráv, z nichž každá odpovídá samostatnému obsaženému oknu.

## <a name="example"></a>Příklad

Následuje příklad třídy kontejneru se dvěma obsaženými okny:

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

Další informace o obsažených oknech naleznete v [ukázce SUBEDIT.](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)

## <a name="see-also"></a>Viz také

[Třídy oken](../atl/atl-window-classes.md)
