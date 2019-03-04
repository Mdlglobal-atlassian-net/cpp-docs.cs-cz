---
title: Přidělování prostředků GDI
ms.date: 11/04/2016
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 5f5f6c6585217393a6008fafa875a83e67ab8016
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57305000"
---
# <a name="allocating-gdi-resources"></a>Přidělování prostředků GDI

Tento článek vysvětluje, jak přidělit a uvolnit objekty pro zařízení rozhraní GDI systému Windows grafiky potřebné pro tisk.

> [!NOTE]
>  Další informace najdete v dokumentaci sady SDK rozhraní GDI + na: [ https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp ](https://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp).

Předpokládejme, že budete muset použít některá písma, pera nebo jiné objekty GDI pro tisk, ale ne pro zobrazení obrazovky. Z důvodu paměti, které potřebují je neefektivní přidělení paměti pro tyto objekty při spuštění aplikace. Když aplikace není tisk dokumentu, může být nutné, tato paměť pro jiné účely. Je lepší přidělovat po zahájení tisk a potom je odstraňte při tisku skončí.

Přidělení paměti pro tyto objekty GDI, přepsat [OnBeginPrinting –](../mfc/reference/cview-class.md#onbeginprinting) členskou funkci. Tato funkce je vhodné pro tento účel dvou důvodů: rozhraní volá tuto funkci jednou na začátku tiskové úlohy a na rozdíl od [OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting), tato funkce má přístup k [CDC](../mfc/reference/cdc-class.md) objekt představující ovladač zařízení. Tyto objekty pro použití během tiskové úlohy můžete ukládat pomocí definování členských proměnných ve třídě zobrazení, které odkazují na objekty GDI (například `CFont *` členy a tak dále).

Pokud chcete používat objekty GDI jste vytvořili, vyberte je do kontextu zařízení tiskárny v [OnPrint –](../mfc/reference/cview-class.md#onprint) členskou funkci. Pokud potřebujete různé objekty GDI pro různé stránky dokumentu, můžete zkontrolovat `m_nCurPage` člen [cprintinfo –](../mfc/reference/cprintinfo-structure.md) strukturu a vyberte objekt rozhraní GDI odpovídajícím způsobem. Pokud potřebujete GDI objektu pro několik po sobě jdoucích stránky, Windows vyžaduje, abyste vybrali ji do kontextu zařízení pokaždé, když `OnPrint` je volána.

Chcete-li uvolnit tyto objekty GDI, přepište [OnEndPrinting –](../mfc/reference/cview-class.md#onendprinting) členskou funkci. Rozhraní volá tuto funkci na konci každého tiskové úlohy, získáte možnost uvolnit objekty GDI specifické pro tisk dříve, než aplikace vrátí jiných úloh.

## <a name="see-also"></a>Viz také:

[Tisk](../mfc/printing.md)<br/>
[Jak probíhá výchozí tisk](../mfc/how-default-printing-is-done.md)
