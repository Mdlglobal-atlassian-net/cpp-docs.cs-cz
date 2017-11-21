---
title: "Identifikace prvky jazyka DHTML řízení projektu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0dfa6a3a2e399ff108bdd97b3dfb9a16b627aefe
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identifikace prvky jazyka DHTML řízení projektu
Většinu kódu ovládací prvek DHTML je přesně jako je například vytvořit pro libovolný ovládací prvek ATL. Pro základní znalosti o obecném kódu, postupujte [ATL – tutoriál](../atl/active-template-library-atl-tutorial.md), a čtení v částech [vytváření projektu knihovny ATL](../atl/reference/creating-an-atl-project.md) a [základy objektů COM ATL](../atl/fundamentals-of-atl-com-objects.md).  
  
 Ovládací prvek DHTML je podobná libovolný ovládací prvek ATL s výjimkou:  
  
-   Kromě regulární rozhraní, které implementuje ovládacího prvku implementuje další rozhraní, které se používá ke komunikaci mezi kódu C++ a HTML uživatelské rozhraní (UI). Rozhraní HTML volá kód C++ pomocí tohoto rozhraní.  
  
-   Vytvoří prostředek HTML pro ovládací prvek uživatelského rozhraní.  
  
-   Umožní přístup k modelu objektu DHTML prostřednictvím členské proměnné `m_spBrowser`, což je inteligentní ukazatel typu [rozhraní IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx). Ukazatel this použijte pro přístup k libovolná součást DHTML objektový model.  
  
 Následující obrázek ukazuje vztah mezi knihovnou DLL, ovládací prvek DHTML, webový prohlížeč a prostředek HTML.  
  
 ![Prvky jazyka DHTML řízení projektu](../atl/media/vc52en1.gif "vc52en1")  
  
> [!NOTE]
>  Názvy v této grafiky jsou zástupné symboly. Názvy prostředku HTML a rozhraní, které jsou zveřejněné na vlastní ovládací prvek jsou založené na názvy, které je třeba je přiřadit v Průvodce ovládacím prvkem ATL.  
  
 V této grafiky jsou elementy:  
  
-   **Moje DLL** knihovna DLL vytvořených pomocí průvodce ATL projektu.  
  
-   **Ovládací prvek DHTML** (`m_spBrowser`) DHTML řízení, vytvořených pomocí průvodce ATL objektu. Tento ovládací prvek přístup k objektu webového prohlížeče a její metody přes rozhraní objektu webového prohlížeče, **rozhraní IWebBrowser2**. Vlastní ovládací prvek na zpřístupní následující dvě rozhraní, kromě jiných standardní rozhraní požadované pro ovládací prvek.  
  
    -   **IDHCTL1** rozhraní vystavené pro použití pouze v kontejneru ovládacího prvku.  
  
    -   **IDHCTLUI1** rozhraní dispatch pro komunikaci mezi kódu C++ a uživatelské rozhraní HTML. Webový prohlížeč používá rozhraní dispatch ovládacího prvku pro zobrazení ovládacího prvku. Různé metody tohoto rozhraní dispatch můžete volat z uživatelské rozhraní ovládacího prvku vyvoláním `window.external`, následuje název metody na tomto rozhraní odesílání, který chcete volat. By přístup `window.external` ze skriptu značky v kódu HTML, která tvoří rozhraní pro tento ovládací prvek. Další informace o volání externí metod v souboru prostředků najdete v tématu [volání C++ – kód z DHTML](../atl/calling-cpp-code-from-dhtml.md).  
  
-   **IDR_CTL1** ID prostředku prostředku HTML. Název souboru, v takovém případě je DHCTL1UI.htm. Ovládací prvek DHTML používá prostředek HTML, který obsahuje standardní značky HTML a příkazy odesílání externí okna, které můžete upravit pomocí textového editoru.  
  
-   **Webové prohlížeče** webový prohlížeč zobrazí uživatelské rozhraní ovládacího prvku, založené na kódu HTML v prostředku HTML. Ukazatel na webový prohlížeč **rozhraní IWebBrowser2** rozhraní je k dispozici v ovládacím prvku DHTML pro povolení přístupu k DHTML objektový model.  
  
 Průvodce ovládacím prvkem ATL generuje ovládacího prvku s výchozím kódu v prostředku HTML a souboru. Můžete zkompilovat a spustit ovládacího prvku, jako je vygenerovat průvodcem a zobrazte ovládacího prvku ve webovém prohlížeči nebo kontejner testů ovládacích prvků ActiveX. Následující obrázek ukazuje výchozí ovládací prvek ATL DHTML s tři tlačítka zobrazená v testu kontejneru:  
  
 ![Ovládací prvek ATL DHTML](../atl/media/vc52en2.gif "vc52en2")  
  
 V tématu [vytvoření ovládacího prvku ATL DHTML](../atl/creating-an-atl-dhtml-control.md) začít vytváření ovládací prvek DHTML. V tématu [testování vlastností a událostí pomocí testovacího kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak přístup – kontejner testů.  
  
## <a name="see-also"></a>Viz také  
 [Podpora pro ovládací prvek DHTML](../atl/atl-support-for-dhtml-controls.md)

