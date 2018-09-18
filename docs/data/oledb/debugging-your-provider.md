---
title: Ladění zprostředkovatele | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5552b9c3d3d697b322b8c1d71eaf0e71630fac38
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040196"
---
# <a name="debugging-your-provider"></a>Ladění zprostředkovatele

Chcete-li ladit poskytovatele dvěma způsoby:  
  
- Protože zprostředkovatelé jsou vytvářeny v procesu, můžete vytvořit příjemce kódu s využitím technologie OLE DB – šablony příjemce a krokování s vnořením poskytovateli normálně.  
  
- Můžete použít nástroj ITEST, která se dodává s jazykem Visual C++.  
  
### <a name="to-use-the-itest-utility"></a>Chcete-li použít nástroj ITEST  
  
1. Otevřete projekt zprostředkovatele.  
  
1. Na **projekty** nabídky, klikněte na tlačítko **nastavení**.  
  
1. V **stránky vlastností** dialogové okno, klikněte na tlačítko **ladění** kartu.  
  
1. V **spustitelný soubor pro relaci ladění** vyberte ITEST aplikaci.  
  
1. Nastavit zarážky a ladění obvyklým způsobem.  
  
## <a name="see-also"></a>Viz také  

[Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)