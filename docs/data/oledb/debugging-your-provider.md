---
title: Ladění zprostředkovatele
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
ms.openlocfilehash: e79719075bcd98733031abd63708bea861388cff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466209"
---
# <a name="debugging-your-provider"></a>Ladění zprostředkovatele

Chcete-li ladit poskytovatele dvěma způsoby:

- Protože zprostředkovatelé jsou vytvářeny v procesu, můžete vytvořit příjemce kódu s využitím technologie OLE DB – šablony příjemce a krokování s vnořením poskytovateli normálně.

- Můžete použít nástroj ITEST, která se dodává s jazykem Visual C++.

## <a name="to-use-the-itest-utility"></a>Chcete-li použít nástroj ITEST

1. Otevřete projekt zprostředkovatele.

1. Na **projekty** nabídky, klikněte na tlačítko **nastavení**.

1. V **stránky vlastností** dialogové okno, klikněte na tlačítko **ladění** kartu.

1. V **spustitelný soubor pro relaci ladění** vyberte ITEST aplikaci.

1. Nastavit zarážky a ladění obvyklým způsobem.

## <a name="see-also"></a>Viz také

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)