---
title: Jak řízení uživatelských účtů (UAC) ovlivňuje vaši aplikaci | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UAC [C++]
- security [C++], User Account Control
- user accounts [C++]
- User Account Control [C++]
ms.assetid: 0d001870-253e-4989-b689-f78035953799
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c313a72a3c76b65476659e463076d61383dd43a5
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43682080"
---
# <a name="how-user-account-control-uac-affects-your-application"></a>Jak ovlivňuje nástroj Řízení uživatelských účtů (UAC) vaši aplikaci
Řízení uživatelských účtů (UAC) je funkce systému Windows Vista, ve které uživatelské účty mají omezená oprávnění. Můžete najít podrobné informace o nástroji Řízení uživatelských účtů na těchto místech:  
  
-   [Doporučené postupy pro vývojáře a pokyny pro aplikace v prostředí s nejnižšími oprávněními](/windows/desktop/uxguide/winenv-uac)  
  
## <a name="building-projects-after-enabling-uac"></a>Vytváření projektů po povolení nástroje Řízení uživatelských účtů  
 Pokud vytváříte projekt jazyka Visual C++ v systému Windows Vista s nástroji Řízení uživatelských účtů, které jsou zakázané a později povolit nástroj Řízení uživatelských účtů, musí vyčistit a znovu sestavte projekt, aby mohly fungovat správně.  
  
## <a name="applications-that-require-administrative-privileges"></a>Aplikace, které vyžadují oprávnění správce  
 Jako výchozí, linker Visual C++ vloží fragment nástroje Řízení uživatelských účtů do manifestu aplikace s úrovní provádění `asInvoker`. Pokud vaše aplikace vyžaduje oprávnění správce pro správnou funkci (například v případě, že upraví HKLM uzlu registru nebo pokud se zapíše do chráněných oblastech disku, jako je například adresář Windows), je třeba upravit vaší aplikace.  
  
 Prvním způsobem je upravit fragment nástroje Řízení uživatelských účtů v manifestu pro změnu úrovně spuštění na *requireAdministrator*. Aplikace pak vyzve uživatele pro přihlašovací údaje pro správu před jejím spuštěním. Informace o tom, jak to provést, najdete v tématu [/MANIFESTUAC (vložené informace UAC v manifestu)](../build/reference/manifestuac-embeds-uac-information-in-manifest.md).  
  
 Druhou možností je nevkládat fragment nástroje Řízení uživatelských účtů do manifestu tak, že zadáte `/MANIFESTUAC:NO` – možnost linkeru. Vaše aplikace poběží v tomto případě virtualizované. Všechny změny, které provedete v registru nebo systému souborů nebude zachována po ukončení vaší aplikace.  
  
 Následující diagram popisuje, jak vaše aplikace poběží v závislosti na tom, zda je povoleno nástroje Řízení uživatelských účtů a určuje, zda má aplikace manifestu nástroje Řízení uživatelských účtů:  
  
 ![Chování zaváděcího programu systému Windows Vista](media/uacflowchart.png "UACflowchart")  
  
## <a name="see-also"></a>Viz také  
 [Osvědčené postupy zabezpečení](security-best-practices-for-cpp.md)