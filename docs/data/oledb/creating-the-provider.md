---
title: Vytvoření zprostředkovatele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 1063b3418df0c9dd45848ea71cdd7717c2dd1427
ms.sourcegitcommit: 997e6b7d336cddb388bb6e9e56527725fcaa0624
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48859585"
---
# <a name="creating-the-provider"></a>Vytvoření zprostředkovatele

#### <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Vytvoření zprostředkovatele OLE DB pomocí Průvodce zprostředkovatelem ATL OLE DB

1. Klikněte pravým tlačítkem na projekt.

1. V místní nabídce klikněte na tlačítko **přidat**a potom klikněte na tlačítko **přidat třídu**.

1. V **přidat třídu** dialogové okno, vyberte **ATL OLE DB Provider** ikonu a pak klikněte na tlačítko **otevřít**.

1. V Průvodci zprostředkovatel knihovny ATL technologie OLE DB zadejte krátký název pro váš poskytovatel v **krátký název** pole. V následujících tématech použijte krátký název "MyProvider", ale můžete použít jiný název. Ostatní naplnit podle názvu, kterou zadáte.

1. V případě potřeby upravte další pole názvů. Kromě názvů objektu a souboru můžete upravit následující:

   - **Coclass**: název, který COM používá k vytvoření poskytovatele.

   - **ProgID**: programový identifikátor, který je textový řetězec, který je možné použít místo identifikátoru GUID.

   - **Verze**: sloužícího ke generování programový identifikátor závislé na verzi s identifikátorem ProgID a coclass

1. Klikněte na tlačítko **Dokončit**.

## <a name="see-also"></a>Viz také

[Vytvoření zprostředkovatele OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
