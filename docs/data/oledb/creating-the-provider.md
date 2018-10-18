---
title: Vytvoření zprostředkovatele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 10/15/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0dbdf7350eeba1a29392bafc2f099a857e212e37
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410743"
---
# <a name="creating-the-provider"></a>Vytvoření zprostředkovatele

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Vytvoření zprostředkovatele OLE DB pomocí Průvodce zprostředkovatelem ATL OLE DB

1. Klikněte pravým tlačítkem na projekt.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.

1. V **přidat třídu** dialogovém okně **nainstalováno** > **Visual C++** > **ATL**, vyberte **Zprostředkovatele služeb OLEDB knihovny ATL** ikonu a pak klikněte na tlačítko **otevřít**.

1. V **Průvodce zprostředkovatelem ATL OLE DB**, zadejte krátký název pro váš poskytovatel v **krátký název** pole. V následujících tématech použijte krátký název "MyProvider", ale můžete použít jiný název. Ostatní naplnit podle názvu, kterou zadáte.

1. V případě potřeby upravte další pole názvů. Kromě názvů objektu a souboru můžete upravit následující:

   - **Coclass**: název, který COM používá k vytvoření poskytovatele.

   - **ProgID**: programový identifikátor, který je textový řetězec, který je možné použít místo identifikátoru GUID.

   - **Verze**: sloužícího ke generování programový identifikátor závislé na verzi s identifikátorem ProgID a Coclass

1. Klikněte na tlačítko **Dokončit**.

## <a name="see-also"></a>Viz také

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
