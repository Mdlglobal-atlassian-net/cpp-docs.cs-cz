---
title: ATL – podpora ovládacích prvků DHTML | Dokumentace Microsoftu
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
- DHTML controls
ms.assetid: 4ba98098-da5d-4362-96ad-8372f816c307
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 281b767151726f695e23c4cf2b2df26f8690c5c5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063993"
---
# <a name="atl-support-for-dhtml-controls"></a>ATL – podpora pro ovládací prvky DHTML

Pomocí knihovny ATL, můžete vytvořit ovládací prvek s funkcí Dynamic HTML (DHTML). Ovládacího prvku ATL DHTML:

- Hostuje ovládací prvek WebBrowser.

- Určuje, v jazyce HTML, uživatelské rozhraní (UI) ovládací prvek DHTML.

- Prostřednictvím rozhraní, nemá přístup k objektu WebBrowser a její metody [rozhraní IWebBrowser2](https://msdn.microsoft.com/library/aa752127.aspx).

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

