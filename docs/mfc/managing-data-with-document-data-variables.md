---
title: Správa dat s použitím datových proměnných dokumentu
ms.date: 11/04/2016
helpviewer_keywords:
- documents [MFC], data storage
- friend classes [MFC]
- classes [MFC], friend
- data [MFC]
- data [MFC], documents
- collection classes [MFC], used by document object
- document data [MFC]
- member variables [MFC], document class [MFC]
ms.assetid: e70b87f4-8c30-49e5-8986-521c2ff91704
ms.openlocfilehash: dc21bd4b3dbe7609a33af4b4f93f15a3f5c9a64e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259968"
---
# <a name="managing-data-with-document-data-variables"></a>Správa dat s použitím datových proměnných dokumentu

Data vašeho dokumentu implementujte jako členské proměnné třídy dokumentu. Například Scribble program deklaruje datový člen typu `CObList` – propojený seznam, který ukládá ukazatele do `CObject` objekty. Tento seznam slouží k uložení pole body, které tvoří od ruky Perokresba.

Jak implementovat členská data vašeho dokumentu závisí na povaze vašich aplikací. Abychom si MFC poskytuje skupinu "kolekce tříd" – pole, seznamy a mapy (slovníky), včetně kolekcí, které jsou založené na šablonách C++ – spolu s třídy, které zapouzdřují různé běžné typy dat, jako `CString`, `CRect`, `CPoint`, `CSize`, a `CTime`. Další informace o těchto tříd, najdete v článku [– přehled knihovny tříd](../mfc/class-library-overview.md) v *odkaz knihovny MFC*.

Při definování vašeho dokumentu členská data obvykle přidáte členské funkce třídy dokumentu k nastavení a získání datových položek a provádět s nimi další užitečné operace.

Zobrazení přístup k dokumentu objektu pomocí ukazatele zobrazení v dokumentu, nainstalovaná v zobrazení v okamžiku vytvoření. Ukazatel this v zobrazení pro členské funkce můžete načíst pomocí volání `CView` členskou funkci `GetDocument`. Ujistěte se, že přetypování tohoto ukazatele na typ dokumentu. Členové veřejné dokumenty pak můžete přistupovat prostřednictvím ukazatele.

Pokud přenos dat často vyžaduje přímý přístup, nebo chcete použít neveřejné členy třídy dokumentu, můžete vytvořit zobrazení tříd – přátelská třída dokumentu (v C++ podmínky).

## <a name="see-also"></a>Viz také:

[Použití dokumentů](../mfc/using-documents.md)
