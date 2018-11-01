---
title: Doporučení k výběru mezi ATL a MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, ATL support
- ATL, vs. MFC
ms.assetid: 269325bb-11a8-4330-ad2b-a14a2458679e
ms.openlocfilehash: b3c01a54c1250ae97d5377cb0b1ff49a17c3f7c3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468247"
---
# <a name="recommendations-for-choosing-between-atl-and-mfc"></a>Doporučení k výběru mezi ATL a MFC

Při vytváření komponent a aplikací, můžete si vybrat mezi dva přístupy – knihovny ATL a MFC (knihovny Microsoft Foundation Class).

## <a name="using-atl"></a>Pomocí knihovny ATL

Knihovna ATL je rychlý a snadný způsob, jak vytvořit komponentu modelu COM v jazyce C++ a udržovat malou stopu. Použití knihovny ATL vytvoření ovládacího prvku, pokud nepotřebujete všechny integrované funkce, který automaticky poskytuje knihovny MFC.

## <a name="using-mfc"></a>Použití prostředí MFC

Knihovny MFC můžete vytvářet celých aplikací, ovládací prvky ActiveX a aktivní dokumenty. Pokud jste již vytvořili ovládacího prvku s knihovnou MFC, můžete pokračovat ve vývoji v knihovně MFC. Při vytváření nového ovládacího prvku, zvažte použití knihovny ATL, pokud nepotřebujete všechny integrované funkce knihovny MFC.

## <a name="using-atl-in-an-mfc-project"></a>Pomocí knihovny ATL v projektu knihovny MFC

Můžete přidat podporu pro použití knihovny ATL v existujícím projektu knihovny MFC pomocí průvodce. Podrobnosti najdete v tématu [přidání podpory knihovny ATL do projektu knihovny MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md).

## <a name="see-also"></a>Viz také

[Úvod do ATL](../atl/introduction-to-atl.md)

