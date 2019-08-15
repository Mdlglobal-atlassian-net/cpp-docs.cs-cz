---
title: Vykreslování obrázků ze seznamu obrázků
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
ms.openlocfilehash: fb307d5557c0e136c1c44c29f08af6062bb1c19d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508608"
---
# <a name="drawing-images-from-an-image-list"></a>Vykreslování obrázků ze seznamu obrázků

Chcete-li nakreslit obrázek, použijte funkci [atributu cimagelist:D: unraw](../mfc/reference/cimagelist-class.md#draw) member. Určíte ukazatel na objekt kontextu zařízení, index obrázku, který se má vykreslit, umístění v kontextu zařízení, ve kterém se má obrázek nakreslit, a sadu příznaků, které označují styl vykreslování.

Když zadáte styl **ILD_TRANSPARENT** , `Draw` použije se proces nakreslení maskovaného obrázku se dvěma kroky. Nejprve provede logickou a operaci na bitech obrázku a bitů masky. Pak provede operaci Logical-XOR u výsledků první operace a bitů na pozadí kontextu cílového zařízení. Tento proces ve výsledné imagi vytvoří průhledné oblasti. To znamená, že každý bílý bit v masce způsobí, že odpovídající bit ve výsledné imagi bude transparentní.

Předtím, než nakreslíte maskovaný obrázek na pozadí s plnou barvou, byste měli použít členskou funkci [SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor) k nastavení barvy pozadí seznamu obrázků na stejnou barvu jako cíl. Nastavením barvy se eliminuje nutnost vytvářet průhledné oblasti v imagi a umožňují `Draw` jednoduše zkopírovat image do kontextu cílového zařízení, což vede k výraznému nárůstu výkonu. Chcete-li nakreslit obrázek, určete styl **ILD_NORMAL** při volání `Draw`.

Můžete nastavit barvu pozadí pro seznam s maskovánými obrázky ([atributu CImageList](../mfc/reference/cimagelist-class.md)) kdykoli, aby správně nastavila na jakémkoli pevném pozadí. Nastavením barvy pozadí na **CLR_NONE** dojde k transparentnímu vykreslování obrázků ve výchozím nastavení. Chcete-li načíst barvu pozadí seznamu obrázků, použijte členskou funkci [GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor) .

Styly **ILD_BLEND25** a **ILD_BLEND50** rozkladou obrázek pomocí barvy zvýraznění systému. Tyto styly jsou užitečné, pokud použijete maskovaný obrázek k reprezentaci objektu, který uživatel může vybrat. Například můžete použít styl **ILD_BLEND50** k vykreslení obrázku, když ho uživatel vybere.

Nemaskovatelné obrázky se zkopírují do kontextu cílového zařízení pomocí `SRCCOPY` operace rastrového obrázku. Barvy v obrázku vypadají stejně bez ohledu na barvu pozadí kontextu zařízení. Styly kresby zadané v `Draw` také nemají žádný vliv na vzhled nemaskované image.

Kromě funkce Draw member, další funkce, [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect), rozšiřuje schopnost vykreslování obrázku. `DrawIndirect`přebírá jako parametr strukturu [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) . Tato struktura se dá použít k přizpůsobení vykreslování aktuálního obrázku, včetně použití rastrových kódů operace (pravém). Další informace o kódech pravém naleznete v tématu [rastrové kódy operací](/windows/win32/gdi/raster-operation-codes) a [bitmapy jako štětce](/windows/win32/gdi/bitmaps-as-brushes) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Používání atributu CImageList](../mfc/using-cimagelist.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
