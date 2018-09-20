---
title: Záhlaví a zápatí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- printing [MFC], multipage documents
- page headers [MFC], printing
- headers [MFC], printing
- footers [MFC], printing
- page footers [MFC], printing
- page headers [MFC]
- printing [MFC], headers and footers
- page footers [MFC]
ms.assetid: b0be9c53-5773-4955-a777-3c15da745128
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 825a74ebe53b934df6a85b3c06fc7df4f0bc135c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383100"
---
# <a name="headers-and-footers"></a>Záhlaví a zápatí

Tento článek vysvětluje, jak přidat záhlaví a zápatí tisk dokumentu.

Když se podíváte na dokument na obrazovce, název dokumentu a vaše aktuální umístění v dokumentu se běžně zobrazují v záhlaví a stavový řádek. Při prohlížení Vytištěná kopie dokumentu, je užitečné mít název a číslo stránky zobrazí v záhlaví nebo zápatí stránky. Toto je běžný způsob, ve které WYSIWYG i programy se liší v jejich výkon tisku a displejem.

[OnPrint –](../mfc/reference/cview-class.md#onprint) členská funkce je na příslušné místo k vytištění záhlaví a zápatí, protože je volána pro každou stránku, a protože je volána pouze pro tisk, ne pro zobrazení obrazovky. Můžete definovat samostatnou funkci, která vypíše záhlaví nebo zápatí stránky a předat ji kontextu zařízení tiskárny z `OnPrint`. Možná budete muset upravit původu okna nebo v rozsahu před voláním [OnDraw](../mfc/reference/cview-class.md#ondraw) vyhnout tělo stránky překrytí záhlaví nebo zápatí. Budete také muset upravit `OnDraw` vzhledem k tomu, že se snížením množství dokumentu, který se vejde na stránce.

Jeden ze způsobů, jak kompenzovat oblasti provedenou na základě záhlaví nebo zápatí je použít **m_rectDraw** členem [cprintinfo –](../mfc/reference/cprintinfo-structure.md). Pokaždé, když tisku stránky tento člen je inicializován s použitelné oblasti na stránce. Pokud tisknete záhlaví nebo zápatí stránky před tiskem těla stránky, můžete zmenšit velikost pravoúhelníku uložené v **m_rectDraw** pro oblasti provedenou na základě záhlaví nebo zápatí. Potom `OnPrint` mohou odkazovat na **m_rectDraw** a zjistěte, kolik oblast zůstane pro tisk těla stránky.

Nelze tisknout záhlaví nebo cokoli jiného, z [OnPrepareDC](../mfc/reference/cview-class.md#onpreparedc), protože je volána před provedením `StartPage` členskou funkci [CDC](../mfc/reference/cdc-class.md) byla volána. V tomto okamžiku kontextu zařízení tiskárny se považuje za hranice stránky. Tisk pouze z můžete provádět `OnPrint` členskou funkci.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Tisk více dokumentů](../mfc/multipage-documents.md)

- [Přidělování prostředků GDI pro tisk](../mfc/allocating-gdi-resources.md)

## <a name="see-also"></a>Viz také

[Tisk](../mfc/printing.md)

