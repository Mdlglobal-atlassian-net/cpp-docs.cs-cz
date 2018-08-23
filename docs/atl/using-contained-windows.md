---
title: Pomocí Windows omezením | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 64a2f9d5d296e28b4b773e072edc90e1b339feae
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465008"
---
# <a name="using-contained-windows"></a>Pomocí obsaženého Windows
ATL – implementuje omezením windows s [ccontainedwindowt –](../atl/reference/ccontainedwindowt-class.md). Obsaženého okna představuje okno, které deleguje své zprávy na kontejnerovém objektu namísto jeho vlastní třídy.  
  
> [!NOTE]
>  Není nutné odvozovat třídu z `CContainedWindowT` Chcete-li použít omezením windows.  
  
 S omezením windows můžete buď nadřazené třídy existující třídu Windows nebo podtřídou existujícímu oknu. Vytvoření časového období této nadřazené třídy existující Windows třídy, nejdřív zadat název existující třídy v konstruktoru pro `CContainedWindowT` objektu. Poté zavolejte `CContainedWindowT::Create`. K podtřídou existujícímu oknu není nutné zadat název třídy Windows (pass NULL do konstruktoru). Jednoduše zavoláte `CContainedWindowT::SubclassWindow` metoda s popisovačem okna se rozčlenit do podtříd.  
  
 Omezením windows se obvykle používají jako datové členy třídy kontejneru. Kontejner nemusí být okno; ale to musí být odvozen od [cmessagemap –](../atl/reference/cmessagemap-class.md).  
  
 Obsaženého okna můžete použít mapy alternativní zpráv pro zpracování zprávy. Pokud máte více než jeden obsaženého okna, by měla deklarovat, že několik alternativní mapy zpráv, každý odpovídající samostatné obsaženého okna.  
  
## <a name="example"></a>Příklad  
 Následuje příklad třídy kontejneru s omezením dvě okna:  
  
 [!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]  
  
 Další informace o časových obdobích omezením, najdete v článku [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit) vzorku.  
  
## <a name="see-also"></a>Viz také  
 [Třídy oken](../atl/atl-window-classes.md)

