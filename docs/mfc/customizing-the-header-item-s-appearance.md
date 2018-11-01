---
title: Přizpůsobení položky záhlaví&#39;vzhled
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], customization of items
- CHeaderCtrl class [MFC], customizing the items
- HDS_ styles
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
ms.openlocfilehash: 8610a3fcc489e69d95f0b0d2e78987664130555e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511017"
---
# <a name="customizing-the-header-item39s-appearance"></a>Přizpůsobení položky záhlaví&#39;vzhled

Tím, že nastavíte *dwStyle* parametr při prvním vytvoření ovládacího prvku záhlaví ([CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create)), můžete definovat vzhled a chování, hlavičce položky nebo hlavičky samotného ovládacího prvku.

Tady je vzorkování styly, které můžete nastavit a jejich účel:

- Chcete-li položka záhlaví vypadat jako pushbutton, použijte **HDS_BUTTONS** style.

   Tento styl použijte, pokud chcete provádět akce v reakci na kliknutí myší na záhlaví položek, jako je například řazení dat podle konkrétního sloupce, jak je tomu v aplikaci Microsoft Outlook.

- Položky hlavičky vzhled "hot sledování" Pokud je přes ně přesunut ukazatel myši, použijte **HDS_HOTTRACK** style.

   Zvýraznění zobrazí 3D osnovy jak předává ukazatel myši na položku. v opačném případě plochý panelu.

- Chcete-li označit, že by měl být skrytý ovládací prvek hlavičky, použijte **HDS_HIDDEN** style.

   **HDS_HIDDEN** styl označuje, že ovládacího prvku záhlaví je určena pro použití jako datový zásobník a není vizuální ovládací prvek. Tento styl automaticky neskrývá ovládacího prvku, ale místo toho má vliv na chování `CHeaderCtrl::Layout`. Hodnota vrácená v *cy* člena `WINDOWPOS` struktura bude nula označující, že ovládací prvek by neměly být viditelné pro uživatele.

Další informace o těchto vlastnostech najdete v tématu [položky](/windows/desktop/Controls/header-controls) v sadě Windows SDK. Informace o přidávání položek do ovládacího prvku záhlaví najdete v tématu [přidávání položek do ovládacího prvku záhlaví](../mfc/adding-items-to-the-header-control.md).

## <a name="see-also"></a>Viz také

[Používání atributu CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

