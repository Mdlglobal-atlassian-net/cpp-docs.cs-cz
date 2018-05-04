---
title: Použití oken s omezením | Microsoft Docs
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
ms.openlocfilehash: f6c3b439baf05c4e4287613e9b6b5a9b1c2546b6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="using-contained-windows"></a>Pomocí omezením systému Windows
ATL implementuje obsažené windows s [CContainedWindowT](../atl/reference/ccontainedwindowt-class.md). Okno obsažené představuje okno, které deleguje jeho zprávy na objekt kontejneru místo jejich zpracování ve své vlastní třídy.  
  
> [!NOTE]
>  Není potřeba odvození třídy z `CContainedWindowT` Chcete-li použít obsažené windows.  
  
 S omezením windows můžete buď supertřídě existující třídy Windows nebo podtřídou existujícího okna. Vytvoření okna této nadřazených tříd Windows pro existující třídy, nejprve zadejte název existující třída v konstruktoru pro `CContainedWindowT` objektu. Potom zavolejte `CContainedWindowT::Create`. K podtřídami existujícího okna, nemusíte zadejte název třídy systému Windows (předat **NULL** konstruktoru). Jednoduše volání `CContainedWindowT::SubclassWindow` metoda s popisovačem do okna se rozčlenění.  
  
 Obsažené windows se obvykle používají jako datové členy třídy kontejneru. Kontejner nemusí být okno; ale musí být odvozený od [CMessageMap](../atl/reference/cmessagemap-class.md).  
  
 Okno obsažené můžete použít mapy alternativní zpráv pro zpracování zprávy. Pokud máte více než jeden obsažené interval, by měly deklarovat, že některé alternativní mapy zpráv, každý odpovídající samostatném okně obsažené.  
  
## <a name="example"></a>Příklad  
 Tady je příklad třídy kontejner s dvěma obsažené windows:  
  
 [!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]  
  
 Další informace o obsažené windows najdete v tématu [SUBEDIT](../visual-cpp-samples.md) ukázka.  
  
## <a name="see-also"></a>Viz také  
 [Třídy oken](../atl/atl-window-classes.md)

