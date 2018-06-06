---
title: Průvodce přidáním události | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.event.overview
dev_langs:
- C++
helpviewer_keywords:
- Add Event Wizard [C++]
ms.assetid: bdd2a7bb-13d5-44d7-abc9-e785ba4e05ce
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f92f871f22fb01f3f0f37677c393fcd481c08120
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "33325192"
---
# <a name="add-event-wizard"></a>Průvodce přidáním události
Tento průvodce přidá událost do projektu MFC ActiveX ovládacího prvku. Můžete zadat vlastní událost, můžete přizpůsobit uloženou událost nebo můžete vybrat ze seznamu uložených událostí.  
  
 **Název události**  
 Nastaví název používají klienti automatizace pro vyžádání události ze třídy. Zadejte název nebo vyberte ze seznamu.  
  
 **Typ události**  
 Určuje typ události, které chcete přidat. K dispozici pouze v případě, že je vyberete z **název události** seznamu.  
  
|Možnost|Popis|  
|------------|-----------------|  
|**Stock**|Určuje, že uložená událost, jako je například kliknutí na tlačítko se implementuje pro tuto třídu. Uložené události jsou definovány v knihovně Microsoft Foundation Class (MFC).|  
|**Vlastní**|Určuje, že zadáváte svoji vlastní implementaci události.|  
  
 **Interní název**  
 Nastaví název členské funkce, která odesílá události. K dispozici pouze pro vlastní události. Název je založen na **název události**. Interní název můžete změnit, pokud chcete zadat název jiný než **název události**.  
  
 **Typ parametru**  
 Nastaví typ **název parametru**. Vyberte typ ze seznamu.  
  
 **Název parametru**  
 Nastaví název parametru k předání události. Po zadání názvu, musíte kliknout na **přidat** ho přidejte do seznamu parametrů.  
  
 Po kliknutí na tlačítko **přidat**, název parametru se zobrazí v **seznam parametrů**.  
  
> [!NOTE]
>  Pokud zadáte název parametru a pak klikněte na tlačítko **Dokončit** před kliknutím na **přidat**, pak parametr nebyla přidána událost. Je nutné vyhledat metodu a vložit parametr ručně. **Seznam parametrů**  
  
 **Přidat**  
 Přidá parametr zadáte v **název parametru**a její typ k **seznam parametrů**. Musíte kliknout na **přidat** přidání parametru do seznamu.  
  
 **Odebrat**  
 Odebere parametr vyberete v **seznam parametrů** ze seznamu.  
  
 **Seznam parametrů**  
 Zobrazí všechny parametry a jejich typy aktuálně přidané do metody. Po přidání parametrů, bude průvodce aktualizovat **seznam parametrů** zobrazíte každý parametr s příslušným typem.  
  
## <a name="see-also"></a>Viz také  
 [Přidání události](../ide/adding-an-event-visual-cpp.md)