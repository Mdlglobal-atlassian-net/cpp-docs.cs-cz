---
title: Ladění zprostředkovatele | Microsoft Docs
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
ms.openlocfilehash: c6258ddd3fd4317c608cb20486c364918fb5c73a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33106388"
---
# <a name="debugging-your-provider"></a>Ladění zprostředkovatele
Existují dva způsoby, jak ladit svého poskytovatele:  
  
-   Protože poskytovatelé jsou vytvářeny v procesu, můžete vytvořit některé příjemce kódu použitím šablony příjemce technologie OLE DB a krokování s vnořením zprostředkovatele normálně.  
  
-   Můžete použít nástroj ITEST, která se dodává s Visual C++.  
  
### <a name="to-use-the-itest-utility"></a>Chcete-li použít nástroj ITEST  
  
1.  Otevřete projekt zprostředkovatele.  
  
2.  Na **projekty** nabídky, klikněte na tlačítko **nastavení**.  
  
3.  V **stránky vlastností** dialogové okno, klikněte **ladění** kartě.  
  
4.  V **spustitelný soubor pro relaci ladění** vyberte ITEST aplikaci.  
  
5.  Nastavte zarážky a pak ladění jako obvykle.  
  
## <a name="see-also"></a>Viz také  
 [Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)