---
title: "Volání kódu jazyka C++ z DHTML | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8e2d0da431249ef886ceca1e2b7f6cbfc99418dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="calling-c-code-from-dhtml"></a>Volání kódu C++ z jazyka DHTML
Ovládací prvek DHTML může být hostovaný v kontejneru, například – kontejner testů nebo Internet Explorer. V tématu [testování vlastností a událostí pomocí testovacího kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak přístup – kontejner testů.  
  
 Hostování ovládacího prvku kontejner komunikuje pomocí ovládacího prvku pomocí rozhraní pro běžné řízení. DHTML používá rozhraní odesílání, který končí řetězcem "Uživatelského rozhraní" ke komunikaci s kódu C++ a prostředek HTML. V [úprava ovládací prvek DHTML ATL](../atl/modifying-the-atl-dhtml-control.md), praxi, přidejte metody, která má být volána tyto různé rozhraní.  
  
 Chcete-li zobrazit příklad volání C++ kódu z jazyka DHTML, [vytvořit ovládací prvek DHTML](../atl/creating-an-atl-dhtml-control.md) pomocí Průvodce ovládacím prvkem ATL a kontrola kódu v záhlaví souboru a v souboru HTML.  
  
## <a name="declaring-webbrowser-methods-in-the-header-file"></a>Deklarování WebBrowser metody v záhlaví souboru  
 K vyvolání metody jazyka C++ z uživatelského rozhraní DHTML, je nutné přidat metody do ovládacího prvku uživatelského rozhraní. Například soubor hlaviček vytvořené Průvodcem knihovnou ATL ovládací prvek obsahuje metodu C++ `OnClick`, který je členem uživatelského rozhraní ovládacího prvku generované v průvodci.  
  
 Zkontrolujte `OnClick` v souboru .h ovládacího prvku:  
  
 [!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]  
  
 První parametr `pdispBody`, je zde ukazatel na rozhraní dispatch objekt textu. Druhý parametr `varColor`, identifikuje barvu, která platí pro ovládací prvek.  
  
## <a name="calling-c-code-in-the-html-file"></a>Volání kódu C++ v soubor HTML  
 Jakmile deklarujete metody WebBrowser v záhlaví souboru, můžete vyvolat metodu ze souboru HTML. Všimněte si v souboru HTML, Průvodce ovládacím prvkem ATL vloží tři metody odesílání Windows: tři `OnClick` metody, které odesílání zprávy a pokuste se změnit barvu pozadí ovládacího prvku.  
  
 Zkontrolujte jednu z metod v souboru HTML:  
  
 `<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`  
  
 V kódu HTML výše, externí metodu okno `OnClick`, je volána v rámci tlačítko značky. Metoda má dva parametry: `theBody`, který odkazuje na text dokumentu HTML a `"red"`, což naznačuje, že barva pozadí ovládacího prvku se změní na červený při kliknutí na tlačítko. `Red` Následující značky je popisek tlačítka.  
  
 V tématu [úprava ovládací prvek DHTML ATL](../atl/modifying-the-atl-dhtml-control.md) Další informace o poskytování vlastních metod. V tématu [identifikace prvky jazyka DHTML řízení projektu](../atl/identifying-the-elements-of-the-dhtml-control-project.md) Další informace o souboru HTML.  
  
## <a name="see-also"></a>Viz také  
 [Podpora pro ovládací prvek DHTML](../atl/atl-support-for-dhtml-controls.md)

