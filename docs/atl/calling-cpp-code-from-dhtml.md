---
title: Volání kódu C++ z DHTML
ms.date: 11/04/2016
helpviewer_keywords:
- DHTML, calling C++ code from
ms.assetid: 37329acd-4c22-40ca-a85a-b7480748f75f
ms.openlocfilehash: fb63f8671770f57972a4c789d983bdf9658d5ecb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62251724"
---
# <a name="calling-c-code-from-dhtml"></a>Volání kódu C++ z DHTML

Ovládací prvek DHTML, mohou být hostovány v kontejneru, jako je například kontejner testu nebo Internet Explorer. Zobrazit [testování vlastností a událostí pomocí testovacího kontejneru](../mfc/testing-properties-and-events-with-test-container.md) informace o tom, jak získat přístup ke kontejneru testů.

Hostování ovládacího prvku kontejnerů komunikuje pomocí ovládacího prvku pomocí rozhraní pro běžné řízení. DHTML používá rozhraní odbavení končícím na "Rozhraní" ke komunikaci s kódu jazyka C++ a váš prostředek ve formátu HTML. V [úprav ovládacího prvku ATL DHTML](../atl/modifying-the-atl-dhtml-control.md), si můžete procvičit přidejte metody, které jsou volány těchto různých rozhraní.

Chcete-li zobrazit příklad volání kódu C++ z DHTML, [vytvořit ovládací prvek DHTML](../atl/creating-an-atl-dhtml-control.md) pomocí Průvodce ovládacími prvky ATL a prozkoumat kód v souboru hlaviček a v souboru HTML.

## <a name="declaring-webbrowser-methods-in-the-header-file"></a>Deklarace metody WebBrowser v hlavičkovém souboru

K vyvolání metody jazyka C++ z DHTML uživatelského rozhraní, je nutné přidat metody do ovládacího prvku uživatelského rozhraní. Například hlavičkový soubor vytvořil Průvodce ovládacím prvkem ATL obsahuje metodu C++ `OnClick`, který je členem rozhraní uživatelského ovládacího prvku generované v průvodci.

Prozkoumejte `OnClick` v souboru .h ovládacího prvku:

[!code-cpp[NVC_ATL_COM#4](../atl/codesnippet/cpp/calling-cpp-code-from-dhtml_1.h)]

První parametr *pdispBody*, je ukazatel na rozhraní odbavení objekt textu. Druhý parametr *varColor*, určuje barvu, která platí pro ovládací prvek.

## <a name="calling-c-code-in-the-html-file"></a>Volání kódu C++ v souboru HTML

Jakmile je deklarován metody WebBrowser v souboru hlaviček, můžete vyvolávat metody ze souboru HTML. Všimněte si, že v souboru HTML, Průvodce ovládacím prvkem ATL vloží tři metody odeslání Windows: tři `OnClick` metody, které odesílají zprávy a změňte barvu pozadí ovládacího prvku.

Prozkoumejte jedné z metod v souboru HTML:

`<BUTTON onclick='window.external.OnClick(theBody, "red");'>Red</BUTTON>`

V kódu HTML nad metodu okno externí `OnClick`, se nazývá jako součást značky tlačítko. Tato metoda má dva parametry: `theBody`, které se odkazuje na obsah dokumentu HTML a `"red"`, což znamená, že barva pozadí ovládacího prvku se změní na červený, po kliknutí na tlačítko. `Red` Následující značky je popisek tlačítka.

Zobrazit [úprav ovládacího prvku ATL DHTML](../atl/modifying-the-atl-dhtml-control.md) Další informace o poskytování vlastních metod. Zobrazit [identifikace prvků projektu ovládací prvek DHTML](../atl/identifying-the-elements-of-the-dhtml-control-project.md) Další informace o souboru HTML.

## <a name="see-also"></a>Viz také:

[Podpora pro ovládací prvek DHTML](../atl/atl-support-for-dhtml-controls.md)
