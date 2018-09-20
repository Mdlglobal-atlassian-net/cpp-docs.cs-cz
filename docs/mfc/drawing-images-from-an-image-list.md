---
title: Vykreslování obrázků ze seznamu obrázků | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4d1a3d2004f0e939cef562ae7972fca88a2f31e2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46409898"
---
# <a name="drawing-images-from-an-image-list"></a>Vykreslování obrázků ze seznamu obrázků

Chcete-li nakreslit bitovou kopii, použijte [CImageList::Draw](../mfc/reference/cimagelist-class.md#draw) členskou funkci. Určete ukazatel na objekt kontextu zařízení, index obrázku pro kreslení, umístění v kontextu zařízení, ve kterém se má nakreslit obrázek a sada příznaků označíte styl vykreslování.

Pokud zadáte **ILD_TRANSPARENT** styl, `Draw` používá k vykreslení maskované image dvoustupňový proces. Nejprve provádí logické- a operace na bitů bitové kopie a bits masky. Pak provede operaci s logické XOR výsledky první operace a na pozadí bits kontextu cílového zařízení. Tento proces vytvoří průhledné oblasti v bude výsledkem obraz; To znamená každý bit bílé v masce způsobí, že odpovídající bit v bude výsledkem obraz transparentní.

Před kreslením maskované obrázku na pozadí, měli byste použít [SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor) členskou funkci pro nastavení barvy pozadí ze seznamu obrázků na stejnou barvu jako cíl. Nastavení barvy eliminuje potřebu vytvářet průhledné oblasti v obrázku a umožňuje `Draw` jednoduše zkopírovat bitovou kopii do kontextu cílového zařízení, což vede k velký nárůst výkon. Chcete-li nakreslit obrázek, zadejte **ILD_NORMAL** stylu při volání `Draw`.

Můžete nastavit barvu pozadí maskované obrázek seznamu ([atributu CImageList](../mfc/reference/cimagelist-class.md)) kdykoli tak, že nakreslí správně na jakékoli jednobarevné pozadí. Nastavení barvy pozadí **CLR_NONE** způsobí, že Image chcete kreslit transparentně ve výchozím nastavení. Pokud chcete načíst barvu pozadí ze seznamu obrázků, použijte [GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor) členskou funkci.

**ILD_BLEND25** a **ILD_BLEND50** styly tónování obrázku barvou zvýraznění systému. Tyto styly jsou užitečné, pokud použijete maskované image pro reprezentaci objektu, který může uživatel vybrat. Například můžete použít **ILD_BLEND50** styl kreslení obrázku, když ho uživatel vybere.

Nonmasked bitová kopie zkopírována na použití kontextu cílového zařízení `SRCCOPY` rastrovou operaci. Barvy na obrázku se zobrazí stejný bez ohledu na barvu pozadí kontextu zařízení. Kreslení styly definované v `Draw` také nemají žádný vliv na vzhled nonmasked bitové kopie.

Kromě členskou funkcí vykreslení jinou funkci, [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect), rozšiřuje možnosti, aby se vykreslil obraz. `DrawIndirect` přijímá jako parametr, [IMAGELISTDRAWPARAMS](/windows/desktop/api/commctrl/ns-commctrl-_imagelistdrawparams) struktury. Tato struktura je možné přizpůsobit vykreslení aktuální obrázek, včetně použití kódy rastrové operace (mohli). Další informace o kódech mohli, naleznete v tématu [kódy rastrové operace](/windows/desktop/gdi/raster-operation-codes) a [bitmap jako štětce](/windows/desktop/gdi/bitmaps-as-brushes) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)

