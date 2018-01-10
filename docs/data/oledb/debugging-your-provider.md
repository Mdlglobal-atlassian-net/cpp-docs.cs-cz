---
title: "Ladění zprostředkovatele | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6cfcb90daaf23a5fd8e248d43b920340e38d8057
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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