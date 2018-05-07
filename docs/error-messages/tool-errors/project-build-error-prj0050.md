---
title: Chyba sestavení projektu PRJ0050 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0050
dev_langs:
- C++
helpviewer_keywords:
- PRJ0050
ms.assetid: ceef3b37-0acf-4abd-ac62-aa830b4fa145
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0ad17614f693e313190dba9cc767c023981dec34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="project-build-error-prj0050"></a>Chyba sestavení projektu PRJ0050
Nepodařilo se zaregistrovat výstup. Zkontrolujte, zda že máte příslušná oprávnění k úpravě registru.  
  
 Sestavení systému Visual C++ se nepodařilo zaregistrovat výstup sestavení (dll nebo .exe). Je třeba být přihlášen jako správce s úpravou registru.  
  
 Pokud vytváříte ve formátu .dll, můžete se pokusit zaregistrovat .dll ručně pomocí regsvr32.exe, to by měl zobrazit informace o nezdaru sestavení.  
  
 Pokud nejsou sestavování ve formátu .dll, naleznete v protokolu sestavení pro příkaz, který má za následek chyby.