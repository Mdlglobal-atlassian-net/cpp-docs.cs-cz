---
title: "Přidělování prostředků GDI | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- resources [MFC], printing
- GDI objects [MFC], allocating during printing
- printing [MFC], allocating GDI resources
ms.assetid: cef7e94d-5a27-4aea-a9ee-8369fc895d3a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 976852b11101a608a47f37ec1c796ef1363ec648
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="allocating-gdi-resources"></a>Přidělování prostředků GDI
Tento článek vysvětluje, jak přidělit a navrátit Windows grafiky zařízení rozhraní GDI objektů nezbytných pro tisk.  
  
> [!NOTE]
>  Rozhraní GDI + je součástí systému Windows XP a je k dispozici jako redistributable pro systém Windows NT 4.0 SP6, Windows 2000, Windows 98 a Windows Me. Si můžete stáhnout nejnovější distribuovatelné [http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdkredist.htm](http://www.microsoft.com/msdownload/platformsdk/sdkupdate/psdkredist.htm). Další informace najdete v dokumentaci rozhraní GDI + SDK na: [http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/GDIPlus/GDIPlus.asp](http://msdn.microsoft.com/library/default.aspurl=/library/gdicpp/gdiplus/gdiplus.asp).  
  
 Předpokládejme, že budete muset použít určitých písem, pera nebo jiné objekty GDI pro tisk, ale ne pro zobrazení na obrazovce. Z důvodu paměti, které vyžadují je neefektivní přidělit tyto objekty při spuštění aplikace. Pokud aplikace není tisk dokumentu, že paměť mohou být potřebné pro jiné účely. Je lepší a po přidělovat je při zahájení tisk při tisku končí je odstranit.  
  
 Chcete-li přidělit tyto objekty GDI, přepište [OnBeginPrinting –](../mfc/reference/cview-class.md#onbeginprinting) – členská funkce. Tato funkce je skvěle hodí pro tento účel dvou důvodů: systém volá tuto funkci jednou na každou tiskovou úlohu a, na rozdíl od začátku [OnPreparePrinting –](../mfc/reference/cview-class.md#onprepareprinting), tato funkce má přístup k [CDC](../mfc/reference/cdc-class.md) objekt reprezentující zařízení ovladač tiskárny. Tyto objekty pro použití během tiskové úlohy můžete ukládat pomocí definování členských proměnných ve třídě zobrazení, které odkazují na objekty GDI (například **CFont \***  členy a tak dále).  
  
 Chcete-li použít objekty GDI jste vytvořili, vyberte je do kontextu zařízení tiskárny v [při tisku](../mfc/reference/cview-class.md#onprint) – členská funkce. Pokud potřebujete různé objekty GDI pro různé stránky dokumentu, můžete zkontrolovat `m_nCurPage` členem [cprintinfo –](../mfc/reference/cprintinfo-structure.md) struktury a vyberte objekt GDI odpovídajícím způsobem. Pokud potřebujete objekt GDI pro několik po sobě jdoucí stránky, Windows vyžaduje, že ji vyberete do kontextu zařízení pokaždé, když `OnPrint` je volána.  
  
 Chcete-li se navrátit tyto objekty GDI, přepište [OnEndPrinting –](../mfc/reference/cview-class.md#onendprinting) – členská funkce. Rozhraní framework volá tuto funkci na konci každou tiskovou úlohu, která poskytuje možnost navrácení objekty GDI specifické pro tisk, než aplikace vrátí do dalších úloh.  
  
## <a name="see-also"></a>Viz také  
 [Tisk](../mfc/printing.md)   
 [Jak probíhá výchozí tisk](../mfc/how-default-printing-is-done.md)

