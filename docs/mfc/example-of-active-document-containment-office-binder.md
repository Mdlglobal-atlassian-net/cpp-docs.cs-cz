---
title: 'Příklad zahrnutí aktivního dokumentu: modul vazby sady Office | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- active documents [MFC], containers
- examples [MFC], active document containment
- containers [MFC], active document
- active document containers [MFC], examples
- Office Binder [MFC]
- MFC COM, active document containment
ms.assetid: 70dd8568-e8bc-44ac-bf5e-678767efe8e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 757fb13ac93fdf26aec67d570ab097b353975604
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408541"
---
# <a name="example-of-active-document-containment-office-binder"></a>Příklad zahrnutí aktivního dokumentu: modul vazby sady Office

Modul vazby sady Office Microsoft je příkladem kontejner pro aktivní dokument. Modul vazby sady Office zahrnuje dvě primární podokna, jako jsou kontejnery to obvykle děláte. Levé podokno obsahuje ikonami, které odpovídají aktivní dokumenty v vazače. Je volána každý dokument *části* v rámci vazače. Vazač může například obsahovat dokumentů aplikace Word, PowerPoint soubory, tabulky aplikace Excel a tak dále.

Kliknutím na ikony v levém podokně aktivuje odpovídající aktivní dokument. Pravém podokně vazače zobrazí obsah aktuálně vybraného aktivního dokumentu.

Pokud otevřete a aktivovat Wordový dokument v vazač, Word nabídek a panelů nástrojů se zobrazí v horní části zobrazení snímků a upravíte obsah dokumentu pomocí libovolného příkazu slova nebo nástroj. Ale nabídek je kombinací vazače společnosti i Wordu nabídek. Protože vazače a Word **pomáhají** slučování nabídek, obsah příslušné nabídky. Kontejnery pro aktivní dokument jako je například modul vazby sady Office automaticky poskytují **pomáhají** nabídky sloučení; Další informace najdete v tématu [slučování nabídek nápovědy](../mfc/help-menu-merging.md).

Když vyberete aktivní dokument jiného typu aplikace, má vazač rozhraní změny, které aplikace typu aktivní dokument. Například pokud vazač obsahuje Excelové tabulky, si můžete všimnout, že nabídky vazače změnit při výběru oddíl tabulky aplikace Excel.

Existují, samozřejmě, další možné typy kontejnerů vedle vazače. Průzkumník souborů používá rozhraní typické duální podokně ve kterém v levém podokně používá ovládací prvek stromu k zobrazení hierarchického seznamu adresářů v disku nebo sítě, v pravém podokně zobrazuje soubory obsažené v aktuálně vybraném adresáři. Internetové prohlížeče – typ kontejneru (např. Microsoft Internet Explorer), a ne pomocí podokna duální rozhraní, obvykle obsahuje jeden snímek a poskytuje navigace pomocí hypertextových odkazů.

## <a name="see-also"></a>Viz také

[Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)

