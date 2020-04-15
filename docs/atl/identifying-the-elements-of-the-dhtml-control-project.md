---
title: Identifikace prvků řídicího projektu DHTML
ms.date: 11/19/2018
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
ms.assetid: b627547a-3768-4346-9900-4b7a21fb8e27
ms.openlocfilehash: 5fabdc815989c21bdf6b0932b9d6826e28d7012a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319507"
---
# <a name="identifying-the-elements-of-the-dhtml-control-project"></a>Identifikace prvků řídicího projektu DHTML

Většina dhtml řídicí kód je přesně jako to, které vytvořené pro všechny ovládací prvek ATL. Pro základní znalost i obecný kód, práce prostřednictvím [kurzu ATL](../atl/active-template-library-atl-tutorial.md)a přečtěte si části [Vytvoření atl projektu](../atl/reference/creating-an-atl-project.md) a [základy objektů ATL COM](../atl/fundamentals-of-atl-com-objects.md).

Ovládací prvek DHTML je podobný všem ovládacím prvkem ATL, s výjimkou:

- Kromě běžných rozhraní, které ovládací prvek implementuje, implementuje další rozhraní, které se používá ke komunikaci mezi kódem Jazyka C++ a uživatelským rozhraním (UI) JAZYKA HTML. Uživatelské rozhraní HTML volá do kódu Jazyka C++ pomocí tohoto rozhraní.

- Vytvoří prostředek HTML pro ovládací ui.

- Umožňuje přístup k objektovému modelu DHTML prostřednictvím členské proměnné `m_spBrowser`, což je inteligentní ukazatel typu [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\)). Pomocí tohoto ukazatele můžete získat přístup k libovolné části objektového modelu DHTML.

Následující obrázek znázorňuje vztah mezi dll, ovládacím prvkem DHTML, webovým prohlížečem a prostředkem HTML.

![Prvky řídicího projektu DHTML](../atl/media/vc52en1.gif "Prvky řídicího projektu DHTML")

> [!NOTE]
> Názvy na této grafice jsou zástupné symboly. Názvy prostředku HTML a rozhraní vystavených v ovládacím prvku jsou založeny na názvech, které jim přiřadíte v Průvodci řízením knihovny ATL.

V této grafice jsou prvky:

- **Moje dll** DLL vytvořená pomocí Průvodce projektem atl.

- **DHTML** Control`m_spBrowser`( ) Ovládací prvek DHTML vytvořený pomocí Průvodce objektem KNIHOVNY ATL. Tento ovládací prvek přistupuje k objektu webového `IWebBrowser2`prohlížeče a jeho metodám prostřednictvím rozhraní objektu webového prohlížeče . Samotný ovládací prvek zpřístupňuje následující dvě rozhraní, kromě jiných standardních rozhraní požadovaných pro ovládací prvek.

  - `IDHCTL1`Rozhraní vystavené ovládacím prvkem pro použití pouze kontejneru.

  - `IDHCTLUI1`Odeslání rozhraní pro komunikaci mezi kódem C++ a uživatelským rozhraním HTML. Webový prohlížeč používá k zobrazení ovládacího prvku rozhraní pro odesílání ovládacího prvku. Můžete volat různé metody tohoto odeslání rozhraní z uživatelského rozhraní `window.external`ovládacího prvku vyvoláním , následovaný název metody na tomto odeslání rozhraní, které chcete vyvolat. Přístup byste `window.external` měli ze značky SCRIPT v rámci html, která tvoří uI pro tento ovládací prvek. Další informace o vyvolání externích metod v souboru prostředků naleznete v [tématu Volání kódu Jazyka C++ z DHTML](../atl/calling-cpp-code-from-dhtml.md).

- **IDR_CTL1** ID prostředku prostředku HTML. Jeho název souboru, v tomto případě, je DHCTL1UI.htm. Ovládací prvek DHTML používá prostředek HTML, který obsahuje standardní značky HTML a příkazy externího odeslání okna, které můžete upravovat pomocí textového editoru.

- **Webový prohlížeč** Webový prohlížeč zobrazí uživatelské prostředí ovládacího prvku na základě kódu HTML v prostředku HTML. Ukazatel na rozhraní webového `IWebBrowser2` prohlížeče je k dispozici v ovládacím prvku DHTML, který umožňuje přístup k objektovému modelu DHTML.

Průvodce ovládacím prvkem ATL generuje ovládací prvek s výchozím kódem v prostředku HTML i v souboru CPP. Ovládací prvek můžete zkompilovat a spustit tak, jak je generován průvodcem, a potom jej zobrazit ve webovém prohlížeči nebo v testovacím kontejneru ovládacího prvku ActiveX. Na obrázku níže je zobrazen výchozí ovládací prvek ATL DHTML se třemi tlačítky zobrazenými v testovacím kontejneru:

![Ovládací prvek ATL DHTML](../atl/media/vc52en2.gif "Ovládací prvek ATL DHTML")

Informace o vytváření ovládacího prvku DHTML v [tématu Vytvoření ovládacího prvku ATL DHTML](../atl/creating-an-atl-dhtml-control.md) najdete v tématu Vytvoření ovládacího prvku DHTML. Informace o tom, jak získat přístup k testovacímu kontejneru, najdete v tématu [Testování vlastností a událostí pomocí testovacího kontejneru.](../mfc/testing-properties-and-events-with-test-container.md)

## <a name="see-also"></a>Viz také

[Podpora pro Řízení DHTML](../atl/atl-support-for-dhtml-controls.md)
