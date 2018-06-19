---
title: 'Příklad zahrnutí aktivního dokumentu: modul vazby sady Office | Microsoft Docs'
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
ms.openlocfilehash: b7e4f82840a4c5620762ad57b5b9fa8dd7e62d0a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345957"
---
# <a name="example-of-active-document-containment-office-binder"></a>Příklad zahrnutí aktivního dokumentu: modul vazby sady Office
Microsoft Office Binder je příkladem kontejner. Aplikace Office Binder obsahuje dvě podokna primární, stejně jako kontejnery obvykle. V levém podokně obsahuje ikony, které odpovídají aktivní dokumenty v vazače. Je volána každý dokument *části* v rámci vazače. Vazač může například obsahovat dokumenty aplikace Word, PowerPoint soubory, tabulky aplikace Excel a tak dále.  
  
 Kliknutím na ikonu v levém podokně aktivuje odpovídající aktivní dokument. V pravém podokně vazač pak zobrazí obsah aktuálně vybrané aktivní dokument.  
  
 Pokud otevřete a aktivovat dokument aplikace Word v vazač, Word řádku nabídek a panelů nástrojů zobrazí v horní části rámečku zobrazení a můžete upravit obsah dokumentu pomocí žádný příkaz slovo nebo nástroj. Kombinace nabídek na vazač i Word. je však řádku nabídek. Protože vazač a Word **pomoci** slučování nabídek, obsah odpovídajících nabídek. Kontejnery pro aktivní dokument například vazby sady Office automaticky získávat **pomoci** nabídky slučování; Další informace najdete v tématu [pomoci slučování nabídek](../mfc/help-menu-merging.md).  
  
 Když vyberete dokument active jiného typu aplikace, změny vazač rozhraní pro přizpůsobení, která typu aplikace aktivní dokument. Například pokud vazač obsahuje tabulky aplikace Excel, zjistíte, že nabídky v vazač změnit při výběru části tabulky aplikace Excel.  
  
 Existují samozřejmě další možné typy kontejnery vedle vazače. Průzkumník souborů používá rozhraní typické duální podokně, ve kterém v levém podokně pomocí ovládacím prvkem strom zobrazí hierarchické seznamu adresářů v síti, nebo jednotku při pravý panel zobrazuje soubory obsažené v aktuálně vybraném adresáři. Internetové prohlížeče – typ kontejneru (například aplikace Microsoft Internet Explorer), nikoli pomocí rozhraní duální podokně, obvykle má jeden snímek a poskytuje navigační pomocí hypertextové odkazy.  
  
## <a name="see-also"></a>Viz také  
 [Zahrnutí aktivního dokumentu](../mfc/active-document-containment.md)

