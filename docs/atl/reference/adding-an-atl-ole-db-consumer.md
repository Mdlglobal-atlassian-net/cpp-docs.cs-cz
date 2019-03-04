---
title: Přidání příjemce ATL OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- OLE DB, adding ATL OLE DB consumer to projects
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
ms.openlocfilehash: d93bf715f8fd8a03c75b1d1bf2e44f12c1d1b9c0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57277648"
---
# <a name="adding-an-atl-ole-db-consumer"></a>Přidání příjemce ATL OLE DB

Tohoto průvodce použijte k přidání příjemce technologie OLE DB knihovny ATL do projektu. Příjemce knihovny ATL technologie OLE DB se skládá ze OLE DB přístupový objekt třídy a datových vazeb nezbytná pro přístup ke zdroji dat. Projekt musí být vytvořen jako aplikace knihovny ATL modelu COM, nebo jako aplikace knihovny MFC nebo Win32, který obsahuje podpory knihovny ATL (který automaticky přidá průvodce příjemcem ATL OLE DB).

> [!NOTE]
> Příjemce technologie OLE DB můžete přidat do projektu MFC. Pokud to uděláte, průvodce příjemcem ATL OLE DB přidá potřebné podporu modelu COM do vašeho projektu. Předpokladem je, že při vytváření projektu knihovny MFC, vyberete **ovládací prvky ActiveX** zaškrtávací políčko (v **rozšířené funkce** stránky Průvodce aplikací MFC projektu), který je ve výchozím nastavení zaškrtnuto. Výběrem této možnosti zajistíte, že aplikace volá `CoInitialize` a `CoUninitialize`. Pokud jste nevybrali **ovládací prvky ActiveX** při vytváření projektu knihovny MFC, je třeba volat `CoInitialize` a `CoUninitialize` v hlavním kódu.

## <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>Chcete-li přidat příjemce technologie OLE DB knihovny ATL do projektu

1. V **zobrazení tříd**, klikněte pravým tlačítkem na projekt. V místní nabídce klikněte na tlačítko **přidat** a potom klikněte na tlačítko **přidat třídu**.

1. Ve složce Visual C++, dvakrát klikněte **příjemce ATL OLE DB** ikonu nebo ho vyberte a klikněte na tlačítko **otevřít**.

   Otevře se průvodce příjemcem ATL OLE DB.

1. Definujte nastavení, jak je popsáno v [průvodce příjemcem ATL OLE DB](../../atl/reference/atl-ole-db-consumer-wizard.md).

1. Klikněte na tlačítko **Dokončit** zavřete průvodce. Nově vytvořený kód příjemce technologie OLE DB bude vložen do vašeho projektu.

## <a name="see-also"></a>Viz také:

[Přidání funkce pomocí průvodců kódem](../../ide/adding-functionality-with-code-wizards-cpp.md)
