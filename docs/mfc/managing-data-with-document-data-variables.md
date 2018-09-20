---
title: Správa dat s použitím datových proměnných dokumentu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0a1db1e15733a0a3cd217c44aaaa325c146ee64
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435880"
---
# <a name="managing-data-with-document-data-variables"></a>Správa dat s použitím datových proměnných dokumentu

Data vašeho dokumentu implementujte jako členské proměnné třídy dokumentu. Například Scribble program deklaruje datový člen typu `CObList` – propojený seznam, který ukládá ukazatele do `CObject` objekty. Tento seznam slouží k uložení pole body, které tvoří od ruky Perokresba.

Jak implementovat členská data vašeho dokumentu závisí na povaze vašich aplikací. Abychom si MFC poskytuje skupinu "kolekce tříd" – pole, seznamy a mapy (slovníky), včetně kolekcí, které jsou založené na šablonách C++ – spolu s třídy, které zapouzdřují různé běžné typy dat, jako `CString`, `CRect`, `CPoint`, `CSize`, a `CTime`. Další informace o těchto tříd, najdete v článku [– přehled knihovny tříd](../mfc/class-library-overview.md) v *odkaz knihovny MFC*.

Při definování vašeho dokumentu členská data obvykle přidáte členské funkce třídy dokumentu k nastavení a získání datových položek a provádět s nimi další užitečné operace.

Zobrazení přístup k dokumentu objektu pomocí ukazatele zobrazení v dokumentu, nainstalovaná v zobrazení v okamžiku vytvoření. Ukazatel this v zobrazení pro členské funkce můžete načíst pomocí volání `CView` členskou funkci `GetDocument`. Ujistěte se, že přetypování tohoto ukazatele na typ dokumentu. Členové veřejné dokumenty pak můžete přistupovat prostřednictvím ukazatele.

Pokud přenos dat často vyžaduje přímý přístup, nebo chcete použít neveřejné členy třídy dokumentu, můžete vytvořit zobrazení tříd – přátelská třída dokumentu (v C++ podmínky).

## <a name="see-also"></a>Viz také

[Použití dokumentů](../mfc/using-documents.md)

