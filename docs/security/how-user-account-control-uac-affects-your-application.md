---
title: "Jak ovlivňuje nástroj Řízení uživatelských účtů (UAC) vaší aplikace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
caps.latest.revision: "5"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e609c16d63974506a06d6ec553cf4be09509acb9
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2018
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Jak ovlivňuje nástroj Řízení uživatelských účtů (UAC) vaši aplikaci
Řízení uživatelských účtů (UAC) je funkce systému Windows Vista, ve které uživatelské účty mají omezená oprávnění. Najdete podrobné informace o řízení uživatelských účtů na těchto místech:  
  
-   [Průvodce krok za krokem řízení uživatelských účtů aplikace systému Windows Vista](http://go.microsoft.com/fwlink/p/?linkid=53781)  
  
-   [Doporučené postupy a pokyny pro aplikace v prostředí s nejnižšími oprávněními](http://go.microsoft.com/fwlink/p/?linkid=82444)  
  
-   [Při plánování a konfiguraci řízení uživatelských účtů v systému Windows Vista](http://go.microsoft.com/fwlink/p/?linkid=82445)  
  
## <a name="building-projects-after-enabling-uac"></a>Sestavování projektů po povolení nástroje Řízení uživatelských účtů  
 Pokud při vytváření projektu Visual C++ v systému Windows Vista s nástroje Řízení uživatelských účtů, které jsou zakázané, a později povolit nástroj Řízení uživatelských účtů, musí vyčistit a znovu sestavte projekt, aby fungovala správně.  
  
## <a name="applications-that-require-administrative-privileges"></a>Aplikace, které vyžadují oprávnění správce  
 Jako výchozí, linkeru jazyka Visual C++ vloží fragment nástroje Řízení uživatelských účtů do manifestu aplikace s úrovní spuštění `asInvoker`. Pokud vaše aplikace vyžaduje oprávnění správce pro správné fungování (například v případě, že upraví uzlu HKLM registru nebo pokud zapisuje do chráněných oblastech disku, jako je například adresáři systému Windows), musíte upravit vaší aplikace.  
  
 První možností je upravit fragment nástroje Řízení uživatelských účtů manifestu, který chcete změnit úroveň provádění na *requireAdministrator*. Aplikace pak vyzve uživatele k zadání pověření pro správu, před spuštěním. Informace o tom, jak to udělat najdete v tématu [/MANIFESTUAC (vložené informace UAC v manifestu)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).  
  
 Druhou možností není Vložit fragment nástroje Řízení uživatelských účtů do manifestu zadáním **/MANIFESTUAC:NO** – možnost linkeru. V takovém případě se spustí aplikace virtualizované. Všechny změny, které provedete v registru nebo systému souborů neuchovává po ukončení aplikace.  
  
 Následující vývojový diagram popisuje, jak vaše aplikace poběží v závislosti na tom, zda je povolen nástroj Řízení uživatelských účtů a zda má aplikace manifestu nástroje Řízení uživatelských účtů:  
  
 ![Windows Vista zavaděč chování](media/uacflowchart.png "UACflowchart")  
  
## <a name="see-also"></a>Viz také  
 [Osvědčené postupy zabezpečení](security-best-practices-for-cpp.md)