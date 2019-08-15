---
title: Jak probíhá výchozí tisk
ms.date: 11/04/2016
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
ms.openlocfilehash: 5019bcad769c4b7cdb699facef145a21d9b5e11c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508422"
---
# <a name="how-default-printing-is-done"></a>Jak probíhá výchozí tisk

Tento článek popisuje výchozí proces tisku ve Windows v souvislosti s architekturou MFC.

V aplikacích MFC má třída zobrazení členskou funkci s názvem `OnDraw` , která obsahuje veškerý kód kresby. `OnDraw`bere ukazatel na objekt [CDC](../mfc/reference/cdc-class.md) jako parametr. Tento `CDC` objekt představuje kontext zařízení pro příjem image `OnDraw`vytvořenou. Když okno zobrazující dokument obdrží zprávu [WM_PAINT](/windows/win32/gdi/wm-paint) , rozhraní zavolá `OnDraw` a předá jí kontext zařízení (objekt [CPaintDC –](../mfc/reference/cpaintdc-class.md) , který bude specifický). `OnDraw`Proto výstup přejde na obrazovku.

Při programování pro Windows je odesílání výstupu na tiskárnu velmi podobné odesílání výstupu na obrazovku. Důvodem je to, že rozhraní GDI (Windows Graphics Device Interface) je nezávislé na hardwaru. Můžete použít stejné funkce GDI pro zobrazení obrazovky nebo pro tisk jednoduše pomocí vhodného kontextu zařízení. Pokud objekt, který `OnDraw` přijímá, představuje tiskárnu, `OnDraw`výstup přejde na tiskárnu. `CDC`

Vysvětluje, jak mohou aplikace MFC provádět jednoduchý tisk bez nutnosti dalšího úsilí na vaši část. Rozhraní se postará o zobrazení dialogového okna Tisk a vytvoření kontextu zařízení pro tiskárnu. Když uživatel vybere příkaz Tisk v nabídce soubor, toto zobrazení předá tento kontext `OnDraw`zařízení, což nakreslí dokument na tiskárně.

Mezi tiskem a zobrazením obrazovky ale dochází k významným rozdílům. Po vytištění je třeba rozdělit dokument na samostatné stránky a zobrazit je po jednom, nikoli zobrazit libovolnou část zobrazenou v okně. Jako corollary si musíte být vědomi velikosti papíru (ať už se jedná o velikost písmen, platnou velikost nebo obálku). Možná budete chtít tisknout v různých orientcích, například v režimu na šířku nebo na výšku. Knihovna Microsoft Foundation Class nemůže předpovědět, jak vaše aplikace tyto problémy zpracuje, takže poskytuje protokol pro přidání těchto možností.

Tento protokol je popsaný v článku [vícestránkové dokumenty](../mfc/multipage-documents.md).

## <a name="see-also"></a>Viz také:

[Tisk](../mfc/printing.md)
