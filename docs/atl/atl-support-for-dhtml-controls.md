---
title: ATL – podpora pro ovládací prvky DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML controls, ATL support
- DHTML controls, ATL support
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
ms.openlocfilehash: dd8ac616d127c3307c1c432c0b3c9bc2ef1d6181
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223287"
---
# <a name="atl-support-for-dhtml-controls"></a>ATL – podpora pro ovládací prvky DHTML

Pomocí knihovny ATL, můžete vytvořit ovládací prvek s funkcí Dynamic HTML (DHTML). Ovládacího prvku ATL DHTML:

- Hostuje ovládací prvek WebBrowser.

- Určuje, v jazyce HTML, uživatelské rozhraní (UI) ovládací prvek DHTML.

- Prostřednictvím rozhraní, nemá přístup k objektu WebBrowser a její metody [rozhraní IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127\(v=vs.85\)).

- Spravuje komunikace mezi kódem C++ a HTML.

Ovládací prvek DHTML je podobně jako všechny ostatní ovládací prvek ATL, s výjimkou ovládací prvek DHTML zahrnuje další odesílající rozhraní. Podívejte se na obrázek v [identifikace prvků projektu ovládací prvek DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) ilustraci rozhraní poskytovaných v projektu DHTML výchozí.

Ovládacího prvku ATL DHTML můžete zobrazit v prohlížeči nebo jiném kontejneru, jako je například kontejner testů ovládacích prvků ActiveX.

## <a name="in-this-section"></a>V tomto oddílu

[Identifikace prvků projektu správy zdrojového kódu DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md)<br/>
Popisuje prvky DHTML řízení projektu.

[Volání kódu C++ z DHTML](../atl/calling-cpp-code-from-dhtml.md)<br/>
Poskytuje příklad volání kódu C++ z DHTML ovládacího prvku.

[Vytváření ovládacího prvku ATL DHTML](../atl/creating-an-atl-dhtml-control.md)<br/>
Seznam kroků pro vytvoření ovládacího prvku DHTML.

[Testování ovládacího prvku ATL DHTML](../atl/testing-the-atl-dhtml-control.md)<br/>
Ukazuje, jak vytvářet a testovat počáteční projekt ovládací prvek DHTML.

[Změna ovládacího prvku ATL DHTML](../atl/modifying-the-atl-dhtml-control.md)<br/>
Ukazuje, jak přidat některé funkce do ovládacího prvku.

[Testování ovládacího prvku ATL DHTML upravený](../atl/testing-the-modified-atl-dhtml-control.md)<br/>
Ukazuje, jak vytvářet a testovat přidané funkce ovládacího prvku.

## <a name="related-sections"></a>Související oddíly

[ATL](../atl/active-template-library-atl-concepts.md)<br/>
Obsahuje odkazy na koncepční témata o tom, jak programovat pomocí knihovnu Active Template Library.
