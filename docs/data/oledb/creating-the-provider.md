---
title: Vytvoření zprostředkovatele
ms.date: 10/15/2018
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 05ab045e104e3035f8ccd2fa1924b6959164b8d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50538183"
---
# <a name="creating-the-provider"></a>Vytvoření zprostředkovatele

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Vytvoření zprostředkovatele OLE DB pomocí Průvodce zprostředkovatelem ATL OLE DB

1. Klikněte pravým tlačítkem na projekt.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.

1. V **přidat třídu** dialogovém okně **nainstalováno** > **Visual C++** > **ATL**, vyberte **Zprostředkovatele služeb OLEDB knihovny ATL** ikonu a pak klikněte na tlačítko **otevřít**.

1. V **Průvodce zprostředkovatelem ATL OLE DB**, zadejte krátký název pro váš poskytovatel v **krátký název** pole. V následujících tématech použijte krátký název *vlastní*, ale můžete použít jiný název. Ostatní naplnit podle názvu, kterou zadáte.

1. V případě potřeby upravte další pole názvů. Kromě názvů objektu a souboru můžete upravit následující:

   - **Coclass**: název, který COM používá k vytvoření poskytovatele.

   - **ProgID**: programový identifikátor, který je textový řetězec, který je možné použít místo identifikátoru GUID.

   - **Verze**: sloužícího ke generování programový identifikátor závislé na verzi s identifikátorem ProgID a Coclass

1. Klikněte na tlačítko **Dokončit**.

## <a name="see-also"></a>Viz také

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
