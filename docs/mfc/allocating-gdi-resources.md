---
title: Přidělování prostředků GDI
ms.date: 06/03/2019
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
ms.openlocfilehash: 672a9a2ce103ae7f53f61ae955f77276eb1d2945
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509272"
---
# <a name="allocating-gdi-resources"></a>Přidělování prostředků GDI

Tento článek vysvětluje, jak přidělit a uvolnit objekty GDI (Windows Graphics Device Interface) potřebné pro tisk.

> [!NOTE]
>  Další informace najdete v [dokumentaci k rozhraní GDI+ SDK](/windows/win32/gdiplus/-gdiplus-gdi-start).

Předpokládejme, že pro tisk potřebujete použít určitá písma, pera nebo jiné objekty GDI, ale ne pro zobrazení obrazovky. Z důvodu paměti, kterou vyžadují, je při spuštění aplikace neefektivní přidělit tyto objekty. Když aplikace netiskne dokument, může být tato paměť nutná pro jiné účely. Při zahájení tisku je lepší je přidělit a při tisku skončí jejich odstranění.

Chcete-li tyto objekty GDI přidělit, přepište členskou funkci [OnBeginPrinting](../mfc/reference/cview-class.md#onbeginprinting) . Tato funkce je vhodná pro tento účel, a to ze dvou důvodů: rozhraní volá tuto funkci jednou na začátku každé tiskové úlohy a na rozdíl od [OnPreparePrinting](../mfc/reference/cview-class.md#onprepareprinting)Tato funkce má přístup k objektu [CDC](../mfc/reference/cdc-class.md) představujícímu zařízení tiskárny. faktorů. Tyto objekty lze uložit pro použití během tiskové úlohy definováním proměnných členů ve třídě zobrazení, které odkazují na objekty GDI (například `CFont *` členy atd.).

Chcete-li použít objekty GDI, které jste vytvořili, vyberte je do kontextu zařízení tiskárny ve funkci pro [Tisk](../mfc/reference/cview-class.md#onprint) členů. Pokud pro různé stránky dokumentu potřebujete jiné objekty GDI, můžete si prohlédnout `m_nCurPage` člena struktury [CPrintInfo –](../mfc/reference/cprintinfo-structure.md) a odpovídajícím způsobem vybrat objekt GDI. Pokud pro několik po sobě jdoucích stránek potřebujete objekt GDI, Windows `OnPrint` je vyžaduje, abyste ho při každém volání vybrali do kontextu zařízení.

Chcete-li zrušit přidělení těchto objektů GDI, přepište členskou funkci [OnEndPrinting](../mfc/reference/cview-class.md#onendprinting) . Rozhraní volá tuto funkci na konci každé tiskové úlohy a dává vám možnost zrušit přidělení objektů GDI specifických pro tisk před tím, než se aplikace vrátí jiným úlohám.

## <a name="see-also"></a>Viz také:

[Tisk](../mfc/printing.md)<br/>
[Jak probíhá výchozí tisk](../mfc/how-default-printing-is-done.md)
