---
title: Přidělování prostředků GDI
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 149aefeade6f99c294b12bfb294cdf1addb9e5e0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370853"
---
# <a name="allocating-gdi-resources"></a>Přidělování prostředků GDI

Tento článek vysvětluje, jak přidělit a navrátit objekty rozhraní grafického zařízení systému Windows (GDI) potřebné pro tisk.

> [!NOTE]
> Další informace naleznete v [dokumentaci k gdi+ sdk .](/windows/win32/gdiplus/-gdiplus-gdi-start)

Předpokládejme, že potřebujete použít určitá písma, pera nebo jiné objekty GDI pro tisk, ale ne pro zobrazení na obrazovce. Z důvodu paměti, které vyžadují, je neefektivní přidělit tyto objekty při spuštění aplikace. Pokud aplikace netiskne dokument, může být tato paměť potřebná pro jiné účely. Je lepší je přidělit při zahájení tisku a poté je odstranit po ukončení tisku.

Chcete-li přidělit tyto objekty GDI, přepište členskou funkci [OnBeginPrinting.](../mfc/reference/cview-class.md#onbeginprinting) Tato funkce je pro tento účel vhodná ze dvou důvodů: framework volá tuto funkci jednou na začátku každé tiskové úlohy a na rozdíl od [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)má tato funkce přístup k objektu [CDC](../mfc/reference/cdc-class.md) představujícímu ovladač zařízení tiskárny. Tyto objekty můžete uložit pro použití během tiskové úlohy definováním členských proměnných ve třídě `CFont *` zobrazení, které odkazují na objekty GDI (například členy a tak dále).

Chcete-li použít objekty GDI, které jste vytvořili, vyberte je do kontextu zařízení tiskárny v členské funkci [OnPrint.](../mfc/reference/cview-class.md#onprint) Pokud potřebujete různé objekty GDI pro různé stránky `m_nCurPage` dokumentu, můžete prozkoumat člen [cPrintInfo](../mfc/reference/cprintinfo-structure.md) struktury a odpovídajícím způsobem vybrat objekt GDI. Pokud potřebujete objekt GDI pro několik po sobě jdoucích stránek, systém `OnPrint` Windows vyžaduje, abyste jej vybrali do kontextu zařízení pokaždé, když je volána.

Chcete-li tyto objekty GDI zrušit, přepište členskou funkci [OnEndPrinting.](../mfc/reference/cview-class.md#onendprinting) Framework volá tuto funkci na konci každé tiskové úlohy, což vám dává možnost navrátit objekty GDI specifické pro tisk, než se aplikace vrátí k jiným úlohám.

## <a name="see-also"></a>Viz také

[Tisk](../mfc/printing.md)<br/>
[Jak probíhá výchozí tisk](../mfc/how-default-printing-is-done.md)
