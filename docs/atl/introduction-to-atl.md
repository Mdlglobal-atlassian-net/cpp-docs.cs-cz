---
title: Úvod do ATL
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- COM objects, creating in ATL
- ATL
ms.assetid: 77f565e8-c4ec-4a80-af4b-7278fcfe5c98
ms.openlocfilehash: 5eba816bc87eeebea2c41489a5d15c48645739e8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492111"
---
# <a name="introduction-to-atl"></a>Úvod do ATL

ATL je knihovna aktivních šablon, sada tříd založených na C++ šablonách, pomocí kterých lze snadno vytvořit malé objekty modelu COM (Fast Component Object Model). Má speciální podporu pro klíčové funkce modelu COM `IDispatch`, mezi které patří: základní implementace rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), [IClassFactory](/windows/win32/api/unknwnbase/nn-unknwnbase-iclassfactory), [IClassFactory2](/windows/win32/api/ocidl/nn-ocidl-iclassfactory2)a; duální rozhraní; standardní rozhraní enumerátorů com; spojovací body; odtrhnout Interfaces a ovládací prvky ActiveX.

Kód ATL lze použít k vytvoření objektů s jedním vláknem, objektů typu apartment, objektů s volnými vlákny nebo objektů modelu apartment.

Témata, která jsou popsaná v tomto oddílu, zahrnují:

- Způsob, jakým se [Knihovna šablon](../atl/using-a-template-library.md) liší od standardní knihovny.

- Co můžete [a nelze s knihovnou ATL dělat](../atl/scope-of-atl.md).

- [Doporučení pro výběr mezi ATL a MFC](../atl/recommendations-for-choosing-between-atl-and-mfc.md).

## <a name="see-also"></a>Viz také:

[Úvod do modelu COM a knihovny ATL](../atl/introduction-to-com-and-atl.md)
