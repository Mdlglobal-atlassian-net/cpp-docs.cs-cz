---
title: Úvod do modelu COM
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
ms.openlocfilehash: e29f761e0380357bc999af82cc4bde8bfbaf4d6e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492356"
---
# <a name="introduction-to-com"></a>Úvod do modelu COM

COM je základní objektový model, na kterém jsou vytvořeny ovládací prvky ActiveX a OLE. Model COM umožňuje objektu zpřístupnit své funkce ostatním komponentám a hostování aplikací. Definuje jak objekt zpřístupňuje sebe, a jak toto ozáření funguje napříč procesy a napříč sítěmi. COM také definuje životní cyklus objektu.

Základem modelu COM jsou tyto koncepty:

- [Rozhraní](../atl/interfaces-atl.md) – mechanismus, pomocí kterého objekt zpřístupňuje jeho funkci.

- [IUnknown](../atl/iunknown.md) – základní rozhraní, na kterém jsou všechna ostatní založena. Implementuje mechanismy odkazů a mechanizmy dotazování rozhraní spuštěné prostřednictvím modelu COM.

- [Počítání odkazů](../atl/reference-counting.md) – způsob, jakým se objekt (nebo výhradně rozhraní) rozhodne, kdy se již nepoužívá a je proto zdarma odebrat sám sebe.

- [QueryInterface](../atl/queryinterface.md) – metoda použitá pro dotazování objektu pro dané rozhraní.

- [Zařazování](../atl/marshaling.md) – mechanismus, který umožňuje použití objektů napříč vlákny, procesy a síťovými hranicemi, což umožňuje nezávisle na umístění.

- [Agregace](../atl/aggregation.md) – způsob, jakým může jeden objekt využít jiné.

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM a knihovny ATL](../atl/introduction-to-com-and-atl.md)<br/>
[Objektový model součásti](/windows/win32/com/the-component-object-model)
