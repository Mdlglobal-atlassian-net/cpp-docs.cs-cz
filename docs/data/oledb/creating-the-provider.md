---
title: Vytvoření zprostředkovatele
ms.date: 10/15/2018
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 6258b5247e4d9d027e0f03bc133dff1a059665bd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361854"
---
# <a name="creating-the-provider"></a>Vytvoření zprostředkovatele

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Vytvoření zprostředkovatele OLE DB pomocí Průvodce zprostředkovatelem ATL OLE DB

1. Klikněte pravým tlačítkem na projekt.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.

1. V **přidat třídu** dialogovém okně **nainstalováno** > **Visual C++** > **ATL**, vyberte **Zprostředkovatele služeb OLEDB knihovny ATL** ikonu a pak klikněte na tlačítko **otevřít**.

1. V **Průvodce zprostředkovatelem ATL OLE DB**, zadejte krátký název pro váš poskytovatel v **krátký název** pole. V následujících tématech použijte krátký název *vlastní*, ale můžete použít jiný název. Ostatní naplnit podle názvu, kterou zadáte.

1. V případě potřeby upravte další pole názvů. Kromě názvů objektu a souboru můžete upravit následující:

   - **Coclass**: Název, který COM používá k vytvoření poskytovatele.

   - **ProgID**: Programový identifikátor, který je textový řetězec, který je možné použít místo identifikátoru GUID.

   - **Verze**: ProgID a Coclass sloužícího ke generování programový identifikátor závislé na verzi

1. Klikněte na tlačítko **Dokončit**.

## <a name="see-also"></a>Viz také:

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
