---
title: "ODBC – třídy a vlákna | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ODBC classes, and threads
- ODBC, multithreaded applications
- threading [MFC], ODBC support
ms.assetid: 16543926-7331-41a6-ba50-72288f2a61b7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c71005e4cce6f62ca4dceb1c618f2ffd18b2bbab
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="odbc-classes-and-threads"></a>ODBC – třídy a vlákna
Počínaje MFC 4.2, je podpora více vláken pro třídy MFC rozhraní ODBC. Upozorňujeme však, že MFC pro třídy DAO nenabízí podpora více vláken.  
  
 Podpora více vláken pro třídy ODBC má určitá omezení. Protože tyto třídy zabalí rozhraní API ODBC, jsou omezeny na podpora více vláken komponent, na kterých jsou vytvořeny. Například mnoho ovladačů ODBC nejsou bezpečné pro přístup z více vláken; třídy MFC rozhraní ODBC proto nejsou bezpečné pro vlákna Pokud používat s jedním z těchto ovladačů. Měli byste ověřit, jestli je konkrétní ovladač bezpečné pro přístup z více vláken.  
  
 Při vytváření aplikace s více vlákny, byste měli být velmi opatrní při použití více vláken k manipulaci s stejný objekt. Například používající stejný `CRecordset` objekt v dvěma vlákny, může dojít k problémům při načítání dat; operace fetch v jedno vlákno může přepsat dat načtených v jiné vlákno. Další běžné použití tříd MFC rozhraní ODBC v samostatných vláknech je sdílení otevřenou `CDatabase` objekt napříč vlákny pro použití stejného připojení rozhraní ODBC s samostatné `CRecordset` objekt v každé vlákno. Všimněte si, že byste neměli poslat vyberte `CDatabase` do objektu `CRecordset` objekt v jiné vlákno.  
  
> [!NOTE]
>  Pokud máte více vláken pracovalo stejný objekt, měli byste implementovat příslušné synchronizační mechanismy, jako je například kritické oddíly. Mějte na paměti to některé operace, jako například **otevřete**, nejsou chráněné. Měli byste si být jisti, že tyto operace nebude volán souběžně z samostatných vláknech.  
  
 Další informace o vytváření vícevláknové aplikace najdete v tématu [Multithreading témata](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
## <a name="see-also"></a>Viz také  
 [Open Database Connectivity (ODBC)](../../data/odbc/open-database-connectivity-odbc.md)   
 [Přístup k datům programování (MFC/ATL)](../../data/data-access-programming-mfc-atl.md)