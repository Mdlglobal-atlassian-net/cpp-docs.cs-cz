---
title: Vytvoření zprostředkovatele
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 7a8b4caf85ff7d0310c97cb953739796cca21c43
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707579"
---
# <a name="creating-the-provider"></a>Vytvoření zprostředkovatele

::: moniker range="vs-2019"

Průvodce zprostředkovatele ATL OLE DB není k dispozici v aplikaci Visual Studio 2019 a novějším.

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Vytvoření zprostředkovatele OLE DB pomocí Průvodce zprostředkovatelem ATL OLE DB

1. Klikněte pravým tlačítkem na projekt.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.

1. V **přidat třídu** dialogovém okně **nainstalováno** > **Visual C++**  > **ATL**, vyberte **Zprostředkovatele služeb OLEDB knihovny ATL** ikonu a pak klikněte na tlačítko **otevřít**.

1. V **Průvodce zprostředkovatelem ATL OLE DB**, zadejte krátký název pro váš poskytovatel v **krátký název** pole. V následujících tématech použijte krátký název *vlastní*, ale můžete použít jiný název. Ostatní naplnit podle názvu, kterou zadáte.

1. V případě potřeby upravte další pole názvů. Kromě názvů objektu a souboru můžete upravit následující:

   - **Coclass**: Název, který COM používá k vytvoření poskytovatele.

   - **ProgID**: Programový identifikátor, který je textový řetězec, který je možné použít místo identifikátoru GUID.

   - **Verze**: ProgID a Coclass sloužícího ke generování programový identifikátor závislé na verzi

1. Klikněte na tlačítko **Dokončit**.

::: moniker-end

## <a name="see-also"></a>Viz také:

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
