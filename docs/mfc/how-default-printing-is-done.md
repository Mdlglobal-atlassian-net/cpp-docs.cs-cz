---
title: Jak probíhá výchozí tisk | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- default printing
- printing [MFC], default
- defaults, printing
ms.assetid: 0f698459-0fc9-4d43-97da-29cf0f65daa2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90f6559459bed9376dba8b7d9059761e9ace5ac8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43202827"
---
# <a name="how-default-printing-is-done"></a>Jak probíhá výchozí tisk
Tento článek vysvětluje výchozí proces tisku ve Windows z hlediska rozhraní MFC.  
  
 V aplikacích MFC, třídy zobrazení má členská funkce s názvem `OnDraw` , který obsahuje všechny kód výkresu. `OnDraw` přijímá ukazatel [CDC](../mfc/reference/cdc-class.md) objektu jako parametr. Že `CDC` objekt představuje kontext zařízení pro příjem image vytvořené metodou `OnDraw`. Když v okně zobrazení dokumentu obdrží [WM_PAINT](/windows/desktop/gdi/wm-paint) zprávy, rámec volá `OnDraw` a předává je kontext zařízení pro obrazovky ( [cpaintdc –](../mfc/reference/cpaintdc-class.md) objektu, konkrétně). Proto `OnDraw`výstupní přejde na obrazovku.  
  
 V programování pro Windows, je velmi podobný jako poslání výstupu na obrazovku odesílající výstup na tiskárnu. Je to proto, že rozhraní Windows grafiky zařízení (GDI) je nezávislé na hardwaru. Jednoduše tak, že použití kontextu příslušné zařízení můžete použít stejné funkce rozhraní GDI pro zobrazení nebo tisk. Pokud `CDC` objekt, který `OnDraw` obdrží tiskárny, `OnDraw`výstupní přejde do tiskárny.  
  
 To vysvětluje, jak můžete provádět jednoduché tisk bez nutnosti vynakládat další úsilí na vaší aplikace knihovny MFC. Rámec pečuje o zobrazení dialogového okna Tisk a vytváření kontext zařízení pro tiskárny. Když uživatel vybere příkaz Tisk z nabídky soubor, zobrazení předá tento kontext zařízení pro `OnDraw`, který vykreslí dokument na tiskárně.  
  
 Existují však některé důležité rozdíly mezi tisku a displejem. Při tisku, je nutné rozdělení na různé stránky a zobrazení je postupně, spíše než zobrazení libovolné části je vidět v okně dokumentu. Jako důsledkem budete muset mějte na paměti o velikosti papíru (Určuje, zda je velikost písmeno, právní nebo obálky). Můžete chtít tisk v různých orientace, jako je například režimu na šířku nebo výšku. Knihovny Microsoft Foundation Class nelze předvídat, jak aplikace bude zpracovávat tyto problémy, takže poskytuje protokol pro přidání těchto funkcí.  
  
 Protokol je popsán v článku [více stránek dokumenty](../mfc/multipage-documents.md).  
  
## <a name="see-also"></a>Viz také  
 [Tisk](../mfc/printing.md)

