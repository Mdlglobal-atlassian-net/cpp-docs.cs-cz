---
title: "Chyba sestavení projektu PRJ0050 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: PRJ0050
dev_langs: C++
helpviewer_keywords: PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a712c370de6f5a3a8cc9d0fd96e7937deddd201e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="project-build-error-prj0050"></a>Chyba sestavení projektu PRJ0050
Nepodařilo se zaregistrovat výstup. Zkontrolujte, zda že máte příslušná oprávnění k úpravě registru.  
  
 Sestavení systému Visual C++ se nepodařilo zaregistrovat výstup sestavení (dll nebo .exe). Je třeba být přihlášen jako správce s úpravou registru.  
  
 Pokud vytváříte ve formátu .dll, můžete se pokusit zaregistrovat .dll ručně pomocí regsvr32.exe, to by měl zobrazit informace o nezdaru sestavení.  
  
 Pokud nejsou sestavování ve formátu .dll, naleznete v protokolu sestavení pro příkaz, který má za následek chyby.