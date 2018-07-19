---
title: Identifikace prvků projektu ovládací prvek DHTML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f415d9b52179d83617cefe94d4f4525d3cf9808e
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37852431"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identifikace prvků projektu ovládací prvek DHTML
Většinu kódu pro ovládací prvek DHTML přesně takového pro libovolný ovládací prvek ATL vytvoří. Pro základní znalosti o obecný kód projít [ATL – tutoriál](../atl/active-template-library-atl-tutorial.md), si můžete přečíst části [vytvoření projektu ATL](../atl/reference/creating-an-atl-project.md) a [základy ATL COM objekty](../atl/fundamentals-of-atl-com-objects.md).  
  
 Ovládací prvek DHTML je podobný s žádným ovládacím prvkem ATL s výjimkou:  
  
-   Kromě regulárních rozhraní, které implementuje ovládací prvek implementuje další rozhraní, které slouží ke komunikaci mezi kódu jazyka C++ a HTML uživatelské rozhraní (UI). Uživatelské rozhraní HTML volá kód C++ pomocí tohoto rozhraní.  
  
-   Vytvoří prostředek ve formátu HTML pro ovládací prvek uživatelského rozhraní.  
  
-   Umožňuje přístup k objektovému modelu DHTML prostřednictvím členskou proměnnou `m_spBrowser`, což je inteligentní ukazatel typu [rozhraní IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx). Použijte tento ukazatel pro přístup k libovolné části objektovém modelu DHTML.  
  
 Následující obrázek znázorňuje vztah mezi knihovnou DLL, ovládací prvek DHTML, webový prohlížeč a prostředku HTML.  
  
 ![Prvky projektu ovládací prvek DHTML](../atl/media/vc52en1.gif "vc52en1")  
  
> [!NOTE]
>  Názvy na tomto obrázku jsou zástupné symboly. Název prostředku HTML a vystavených ovládacího prvku jsou založeny na názvy, které můžete přiřadit v Průvodce ovládacími prvky ATL.  
  
 Na tomto obrázku jsou prvky:  
  
-   **Moje DLL** knihovna DLL vytvořené pomocí Průvodce projektem ATL.  
  
-   **Ovládací prvek DHTML** (`m_spBrowser`) ovládací prvek The DHTML, vytvořené pomocí Průvodce objektem ATL. Tento ovládací prvek nemá přístup k objektu webové prohlížeče a její metody přes webový prohlížeč objekt rozhraní `IWebBrowser2`. Samotný ovládací prvek zveřejňuje následující dvě rozhraní, kromě dalších standardních rozhraní požadované pro ovládací prvek.  
  
    -   `IDHCTL1` Rozhraní vystavené pro použití pouze kontejnerem ovládacího prvku.  
  
    -   `IDHCTLUI1` Rozhraní odbavení pro komunikaci mezi kódu jazyka C++ a uživatelským rozhraním HTML. Webový prohlížeč používá rozhraní odbavení ovládacího prvku k zobrazení ovládacího prvku. Různé metody tohoto rozhraní odbavení můžete volat z ovládacího prvku uživatelského rozhraní vyvoláním `window.external`následovaný název metody na tomto odeslání rozhraní, které chcete vyvolat. Můžete k `window.external` ze skriptu značky v kódu HTML, který vytvoří pro tento ovládací prvek uživatelského rozhraní. Další informace o volání externí metody v souboru prostředků najdete v tématu [volání kódu C++ z DHTML](../atl/calling-cpp-code-from-dhtml.md).  
  
-   **IDR_CTL1** ID prostředku prostředku HTML. Její název souboru je v tomto případě DHCTL1UI.htm. Ovládací prvek DHTML používá prostředek ve formátu HTML, který obsahuje standardní značky HTML a externím okně rozeslání příkazů, které lze upravovat pomocí textového editoru.  
  
-   **Webový prohlížeč** ovládacího prvku uživatelského rozhraní, podle jazyka HTML v prostředku HTML zobrazí ve webovém prohlížeči. Ukazatel na webový prohlížeč `IWebBrowser2` je k dispozici v ovládací prvek DHTML umožňující přístup k objektovému modelu DHTML rozhraní.  
  
 Průvodce ovládacími prvky ATL generuje ve zdroji HTML a soubor .cpp ovládacího prvku pomocí výchozího kódu. Můžete zkompilovat a spustit ovládací prvek, protože generované průvodcem knihovnou a pak zobrazit ovládací prvek ve webovém prohlížeči nebo kontejner testu ovládacího prvku ActiveX. Následující obrázek ukazuje výchozí ovládacího prvku ATL DHTML s tři tlačítka zobrazí v kontejneru testů:  
  
 ![Ovládacího prvku ATL DHTML](../atl/media/vc52en2.gif "vc52en2")  
  
 Zobrazit [vytvoření ovládacího prvku ATL DHTML](../atl/creating-an-atl-dhtml-control.md) začít sestavovat ovládací prvek DHTML. Zobrazit [testování vlastností a událostí pomocí testovacího kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak získat přístup ke kontejneru testů.  
  
## <a name="see-also"></a>Viz také  
 [Podpora pro ovládací prvek DHTML](../atl/atl-support-for-dhtml-controls.md)

