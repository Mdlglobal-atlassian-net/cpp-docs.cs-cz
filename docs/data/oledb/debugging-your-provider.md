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
ms.openlocfilehash: 03f8ebdf74dfcf8962b4308c467984d0a63c7968
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
 [Práce s šablonami zprostředkovatele OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)