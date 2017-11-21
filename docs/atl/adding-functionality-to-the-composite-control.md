---
title: "Přidání funkcí do složeného ovládacího prvku | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- event handlers [C++], ActiveX controls
- composite controls, handling events
- ActiveX controls [C++], events
ms.assetid: 98f85681-9564-480d-af38-03f9733fe58b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7282ba7eb80fd30175751bb5234818a5e3cf1431
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="adding-functionality-to-the-composite-control"></a>Přidání funkcí do složeného ovládacího prvku
Po vložení všech příslušných ovládacích prvků do složeného ovládacího prvku vyžaduje další krok, přidání nové funkce. Tato nová funkce obvykle spadá do dvou kategorií:  
  
-   Podpora dalších rozhraní a přizpůsobení chování vaší složeného ovládacího prvku pomocí dalších, konkrétní funkce.  
  
-   Zpracování událostí z obsažené ovládacího prvku ActiveX (nebo ovládací prvky).  
  
 Zbytek této části se pro účel a rozsah tohoto článku, zaměřuje výhradně na zpracování událostí z ovládacích prvků ActiveX.  
  
> [!NOTE]
>  Pokud potřebujete pro zpracování zprávy z ovládacích prvků Windows, přečtěte si [implementace okno](../atl/implementing-a-window.md) Další informace o zpracování zpráv v ATL.  
  
 Po vložení ovládacího prvku ActiveX v prostředku dialogového okna, klikněte pravým tlačítkem na ovládací prvek a klikněte na tlačítko **přidejte obslužné rutiny události**. Vyberte události chcete zpracovávat a klikněte na tlačítko **přidávat a upravovat**. Kód obslužné rutiny události přidá do souboru .h ovládacího prvku.  
  
 Body připojení pro ovládací prvky ActiveX v složeného ovládacího prvku se automaticky připojení a odpojení prostřednictvím volání [CComCompositeControl::AdviseSinkMap](../atl/reference/ccomcompositecontrol-class.md#advisesinkmap).  
  
## <a name="see-also"></a>Viz také  
 [Principy vytváření složených prvků](../atl/atl-composite-control-fundamentals.md)

